---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4743'
title: 컴파일러 경고(수준 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: a8c8bcd4ef0e4d7084da34e033be4194da11727f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228484"
---
# <a name="compiler-warning-level-1-c4743"></a>컴파일러 경고(수준 1) C4743

' t *y* p e '의 크기가 '*file1*' 및 '*file2*' ( *숫자* 및 *숫자* 바이트)와 다릅니다.

두 파일에서 참조 또는 정의 된 외부 변수는 해당 파일에 서로 다른 형식이 있으며, 컴파일러는 *file1* 의 변수 크기가 *file2* 의 변수 크기와 다르다는 것을 확인 했습니다.

## <a name="remarks"></a>설명

C + +에 대해이 경고를 내보낼 수 있는 경우 중요 한 경우가 있습니다. 서로 다른 두 파일에 같은 이름을 사용 하 여 동일한 형식을 선언 하는 경우 해당 선언에 가상 함수가 포함 되어 있고 선언이 동일 하지 않은 경우 컴파일러는 가상 함수 테이블에 대해 C4744 경고를 내보낼 수 있습니다. 이 경고는 동일한 형식에 대해 서로 다른 두 가지 크기의 가상 함수 테이블이 있으므로 링커가 실행 파일 중 하나를 선택 하 여 실행 파일에 통합 해야 하기 때문에 발생 합니다.  프로그램에서 잘못 된 가상 함수를 호출 하 게 될 수도 있습니다.

이 경고를 해결 하려면 동일한 형식 정의를 사용 하거나 형식 또는 변수에 다른 이름을 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4743를 생성 합니다. 이를 컴파일하려면 두 파일을 동일한 폴더에 둔 다음를 실행 합니다.  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

```cpp
// C4743b.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```
