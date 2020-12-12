---
description: '자세한 정보: 컴파일러 오류 C2059'
title: 컴파일러 오류 C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 7de765a1985e67388f2853abb1d5dc2e1ecaf043
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328756"
---
# <a name="compiler-error-c2059"></a>컴파일러 오류 C2059

구문 오류: ' token '

토큰에서 구문 오류가 발생 했습니다.

다음 예제에서는를 선언 하는 줄에 대 한 오류 메시지를 생성 합니다 `j` .

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

오류의 원인을 확인 하려면 오류 메시지에 나열 된 줄 뿐만 아니라 위의 줄을 검사 합니다. 줄을 검사 하면 문제에 대 한 단서가 나타나지 않는 경우 오류 메시지에 나열 된 줄과 그 위에 있는 여러 줄을 주석으로 처리 해 보세요.

변수 바로 뒤에 오는 기호에서 오류 메시지가 발생 하면 **`typedef`** 소스 코드에 변수가 정의 되어 있는지 확인 합니다.

전처리기 기호 이름이 식별자로 다시 사용 되는 경우에는 C2059가 발생 합니다. 다음 예제에서 컴파일러는 `DIGITS.ONE` 열거형 요소 이름으로 유효 하지 않은 숫자 1로 간주 합니다.

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

**/D**_기호_ 를 **=** 사용 하 여 컴파일하는 경우에 발생할 수 있듯이 기호가 nothing으로 평가 되는 경우에는 C2059가 발생할 수 있습니다.

```cpp
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

C2059를 발생 시킬 수 있는 또 다른 사례는 함수에 대 한 기본 인수에서 구조체를 지정 하는 응용 프로그램을 컴파일하는 경우입니다. 인수의 기본값은 식 이어야 합니다. 구조체를 초기화 하는 데 사용 되는 이니셜라이저 목록 (예:)은 식이 아닙니다.  이 문제를 해결 하려면 필요한 초기화를 수행 하는 생성자를 정의 합니다.

다음 예제에서는 C2059를 생성 합니다.

```cpp
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

C2059는 잘못 된 형식의 캐스트에 대해 발생할 수 있습니다.

다음 샘플에서는 C2059를 생성 합니다.

```cpp
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

C2059는 마침표를 포함 하는 네임 스페이스 이름을 만들려고 할 때도 발생할 수 있습니다.

다음 샘플에서는 C2059를 생성 합니다.

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

`::` `->` `.` **`template`** 이 예에 표시 된 것 처럼 이름 (, 및)을 한정할 수 있는 연산자 뒤에 키워드를 입력 해야 하는 경우에는 C2059가 발생할 수 있습니다.

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

기본적으로 C++는 `AY::Rebind`이 템플릿이 아니라고 가정하기 때문에 다음 `<`는 보다 작음 기호로 해석됩니다.  꺾쇠 괄호로 올바르게 구문 분석될 수 있도록 `Rebind`이 템플릿임을 컴파일러에 명시적으로 알려야 합니다. 이 오류를 해결 하려면 다음과 같이 **`template`** 종속 형식의 이름에 키워드를 사용 합니다.

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
