---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4840'
title: 컴파일러 경고 (수준 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a365dc38aff1ab9811407924f7f6e554d91c6f1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330466"
---
# <a name="compiler-warning-level-4-c4840"></a>컴파일러 경고 (수준 4) C4840

> variadic 함수의 인수로 서 '*type*' 클래스를 이식 불가능 하 게 사용 합니다.

## <a name="remarks"></a>설명

Variadic 함수에 전달 되는 클래스 또는 구조체는 일반적으로 copyable 이어야 합니다. 해당 개체를 전달할 때 컴파일러는 비트 복사본을 만들기만 하고 생성자 또는 소멸자를 호출하지 않습니다.

이 경고는 Visual Studio 2017부터 사용할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4840를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

를 사용 하 여 작성 및 관리 되는 문자열의 경우 `CStringW` 제공 된를 `operator LPCWSTR()` 사용 하 여 `CStringW` 개체를 서식 문자열에 필요한 C 스타일 문자열 포인터로 캐스팅 해야 합니다.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
