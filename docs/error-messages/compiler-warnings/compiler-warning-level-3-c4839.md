---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4839'
title: 컴파일러 경고 (수준 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: a8ae0d3e3c74c62d05163edd981679e5390fb184
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332062"
---
# <a name="compiler-warning-level-3-c4839"></a>컴파일러 경고 (수준 3) C4839

> variadic 함수에 대 한 인수로 '*type*' 클래스의 비표준 사용

과 같은 variadic 함수로 전달 되는 클래스 또는 구조체는 `printf` 일반적으로 copyable 이어야 합니다. 해당 개체를 전달할 때 컴파일러는 비트 복사본을 만들기만 하고 생성자 또는 소멸자를 호출하지 않습니다.

이 경고는 Visual Studio 2017부터 사용할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4839를 생성 합니다.

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

오류를 수정하려면 일반적으로 복사 가능한 형식을 반환하는 멤버 함수를 호출하거나

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

`CStringW`을 사용하여 빌드 및 관리되는 문자열의 경우 제공된 `operator LPCWSTR()`를 사용하여 `CStringW` 개체를 서식 문자열에 필요한 C 포인터에 캐스팅해야 합니다.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
