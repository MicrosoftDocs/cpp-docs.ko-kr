---
description: '자세한 정보: 비표준 동작'
title: 비표준 동작
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: 9f696582b23dfd4a22e6d48b9294a79787518b50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330848"
---
# <a name="nonstandard-behavior"></a>비표준 동작

다음 섹션에서는 c + +의 Microsoft 구현이 c + + 표준을 준수 하지 않는 위치 중 일부를 나열 합니다. 아래의 섹션 번호는 C++ 11 표준(ISO/IEC 14882:2011(E))의 섹션 번호를 나타냅니다.

C + + 표준에 정의 된 것과 다른 컴파일러 제한 목록은 [컴파일러 제한](../cpp/compiler-limits.md)에서 제공 됩니다.

## <a name="covariant-return-types"></a>공변 반환 형식

가상 함수에 개수가 가변적인 인수가 있을 때 가상 기본 클래스는 공변(covariant) 반환 형식으로 지원되지 않습니다. 이것은 C++ ISO 사양의 단원 10.3, 7항에 맞지 않습니다. 다음 샘플은 컴파일되지 않으며 컴파일러 오류 [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md) 제공 됩니다.

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>템플릿에서 독립적인 이름 바인딩

Microsoft c + + 컴파일러는 현재 템플릿을 처음 구문 분석할 때 종속 되지 않은 이름 바인딩을 지원 하지 않습니다. 이것은 C++ ISO 사양의 단원 14.6.3에 맞지 않습니다. 이로 인해 템플릿이 확인되고 인스턴스화되기 전에 오버로드가 선언될 수 있습니다.

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>함수 예외 지정자

`throw()` 이외의 함수 예외 지정자는 구문 분석되지만 사용되지 않습니다. 이것은 C++ 사양의 단원 15.4에 맞지 않습니다. 예를 들어:

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

예외 사양에 대 한 자세한 내용은 [예외 사양](../cpp/exception-specifications-throw-cpp.md)을 참조 하세요.

## <a name="char_traitseof"></a>char_traits::eof()

C + + 표준 상태 [char_traits:: eof](../standard-library/char-traits-struct.md#eof) 는 유효한 값과 일치 하지 않아야 합니다 `char_type` . Microsoft c + + 컴파일러는 형식에 대해서는이 제약 조건을 적용 하지만 형식에는 적용 **`char`** 하지 않습니다 **`wchar_t`** . 이것은 C++ ISO 사양의 단원 12.1.1, 표 62의 요구 사항에 맞지 않습니다. 아래 예제에서는 이 작업을 보여 줍니다.

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>개체 스토리지 위치

C++ 표준(단원 1.8, 6항)에서는 전체 C++ 개체에 고유한 스토리지 위치가 있어야 합니다. 그러나 Microsoft c + +를 사용 하는 경우 데이터 멤버가 없는 형식이 개체의 수명 동안 다른 형식으로 저장소 위치를 공유 하는 경우가 있습니다.
