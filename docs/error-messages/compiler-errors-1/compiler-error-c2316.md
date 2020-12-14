---
description: '자세한 정보: 컴파일러 오류 C2316'
title: 컴파일러 오류 C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 0e2f528b3f13964a971b88fca110980947bd7d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282200"
---
# <a name="compiler-error-c2316"></a>컴파일러 오류 C2316

> '*class_type*': 소멸자로 catch 할 수 없거나 복사 생성자에 액세스할 수 없거나 삭제 되었습니다.

값 또는 참조로 예외가 catch 되었지만 복사 생성자, 할당 연산자 또는 둘 다에 액세스할 수 없습니다.

## <a name="remarks"></a>설명

Visual Studio 2015의 규칙 변경이 발생 했습니다 .이 오류는에서 파생 된 MFC 예외의 잘못 된 catch 문에 적용 `CException` 됩니다. 에는 `CException` 상속 된 전용 복사 생성자가 있기 때문에 클래스와 해당 파생 클래스는 복사할 수 없으며 값으로 전달할 수 없습니다 .이는 값으로 catch 할 수 없음을 의미 하기도 합니다. 이전에 값으로 MFC 예외를 catch 한 Catch 문은 런타임에 catch 되지 않은 예외를 발생 합니다. 이제 컴파일러에서이 상황을 정확 하 게 식별 하 고 오류 C2316 보고 합니다. 이 문제를 해결 하려면 고유한 예외 처리기를 작성 하는 대신 MFC TRY/CATCH 매크로를 사용 하는 것이 좋습니다. 코드에 적합 하지 않은 경우 대신 참조로 MFC 예외를 catch 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2316를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
