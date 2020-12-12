---
description: '자세히 알아보기: `/Zc:ternary` (조건부 연산자 규칙 적용)'
title: /Zc:ternary(조건 연산자 규칙 적용)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: ea1cf57aa1633e08095dfd01964a2255cb0b3c70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271319"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>`/Zc:ternary` (조건부 연산자 규칙 적용)

조건 연산자 식에서 두 번째 및 세 번째 피연산자의 형식 및 const 또는 volatile (cv) 자격에 대 한 c + + 표준 규칙의 적용을 사용 하도록 설정 합니다.

## <a name="syntax"></a>Syntax

> **`/Zc:ternary`**[**`-`**]

## <a name="remarks"></a>설명

Visual Studio 2017부터 컴파일러는 c + + 표준 *조건부 연산자* ( **`?:`** ) 동작을 지원 합니다. *삼항 연산자* 라고도 합니다. C + + 표준에는 세 가지 조건 중 하나를 충족 해야 합니다. 피연산자는 동일한 형식 및 **`const`** 또는 **`volatile`** 정규화 (cv 한정자)를 사용 해야 합니다. 또는 하나의 피연산자만 다른 형식 및 cv 자격으로 명확 하 게 변환할 수 있어야 합니다. 또는 두 피연산자 중 하나 또는 둘 다 throw 식 이어야 합니다. Visual Studio 2017 버전 15.5 이전 버전에서 컴파일러는 표준에 의해 모호한 것으로 간주 되는 변환을 허용 했습니다.

**`/Zc:ternary`** 옵션이 지정 된 경우 컴파일러는 표준에 부합 합니다. 일치 하는 형식에 대 한 규칙 및 두 번째와 세 번째 피연산자의 cv 한정자를 충족 하지 않는 코드를 거부 합니다.

**`/Zc:ternary`** Visual Studio 2017에서이 옵션은 기본적으로 해제 되어 있습니다. **`/Zc:ternary`** 를 사용 하 여 준수 동작을 사용 하도록 설정 하거나 **`/Zc:ternary-`** 이전 비준수 컴파일러 동작을 명시적으로 지정 합니다. [`/permissive-`](permissive-standards-conformance.md)옵션은이 옵션을 암시적으로 사용 하도록 설정 하지만을 사용 하 여 재정의할 수 있습니다 **`/Zc:ternary-`** .

### <a name="examples"></a>예제

이 샘플에서는 형식에서 비 명시적 초기화를 모두 제공 하는 클래스와 형식으로의 변환이 모호한 변환을 발생 시킬 수 있는 방법을 보여 줍니다. 이 코드는 기본적으로 컴파일러에서 허용 되지만 **/`Zc:ternary`** 또는가 지정 된 경우에는 거부 됩니다 **`/permissive-`** .

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

이 코드를 수정 하려면 기본 설정 된 공용 형식으로 명시적으로 캐스팅 하거나 형식 변환의 한 방향을 사용 하지 않도록 설정 합니다. 변환을 명시적으로 설정 하 여 컴파일러가 형식 변환과 일치 하지 않도록 할 수 있습니다.

이 일반적인 패턴의 중요 한 예외는 피연산자의 형식이 null로 종료 되는 문자열 형식 (예:, 등) 중 하나인 경우입니다 `const char*` `const char16_t*` . 배열 형식 및 감소 하는 포인터 형식을 사용 하 여 효과를 재현할 수도 있습니다. 에 대 한 실제 두 번째 피연산자 또는 세 번째 피연산자 `?:` 가 해당 형식의 문자열 리터럴인 경우에 사용 되는 언어 표준에 따라 동작이 결정 됩니다. C + + 17에는 c + + 14에서이 경우의 의미 체계가 변경 되었습니다. 결과적으로 컴파일러는 다음 예제의 코드를 기본값 아래에서 허용 **`/std:c++14`** 하지만을 지정할 때이를 거부 **`/std:c++17`** 합니다.

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

이 코드를 수정 하려면 피연산자 중 하나를 명시적으로 캐스팅 합니다.

에서 **`/Zc:ternary`** 컴파일러는 인수 중 하나가 형식인 조건 연산자를 거부 **`void`** 하 고 다른 하나는 **`throw`** 식이 아닙니다. 이 패턴의 일반적인 용도는 다음과 같습니다.

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

일반적인 해결 방법은 void가 아닌 인수를로 바꾸는 것입니다 `void()` .

이 샘플에서는 및에서 오류를 생성 하는 코드를 보여 줍니다 **`/Zc:ternary`** **`/Zc:ternary-`** .

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

이 코드는 이전에이 오류가 발생 했습니다.

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

를 사용 하 **`/Zc:ternary`** 는 경우 실패의 이유가 명확 하 게 됩니다. 구현에 정의 된 여러 호출 규칙을 사용 하 여 각 람다를 생성할 수 있습니다. 그러나 컴파일러에는 가능한 람다 시그니처를 명확 하 게 구분 하는 기본 설정 규칙이 없습니다. 새 출력은 다음과 같습니다.

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

에서 발견 된 문제에 대 한 일반적인 출처는 **`/Zc:ternary`** 템플릿 메타 프로그래밍에서 사용 되는 조건부 연산자에서 제공 됩니다. 이 스위치에서 일부 결과 형식이 변경 됩니다. 다음 예제에서는 **`/Zc:ternary`** 가 비 메타 프로그래밍 컨텍스트에서 조건 식의 결과 형식을 변경 하는 두 가지 경우를 보여 줍니다.

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

일반적인 해결 방법은 결과 형식에 특성을 적용 하 여 이전 동작을 유지 해야 하는 것입니다 `std::remove_reference` .

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 또는를 포함 하도록 **추가 옵션** 속성을 수정한 **`/Zc:ternary`** **`/Zc:ternary-`** 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[`/Zc` 규칙](zc-conformance.md)
