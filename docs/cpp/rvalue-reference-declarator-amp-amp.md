---
description: '다음에 대해 자세히 알아보세요. Rvalue 참조 선언 자: &amp;&amp;'
title: 'Rvalue 참조 선언 자: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 6c88116c5834c027d72874d1377e79799faa80ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319380"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Rvalue 참조 선언 자: &amp;&amp;

rvalue 식에 대한 참조를 보유합니다.

## <a name="syntax"></a>구문

```
type-id && cast-expression
```

## <a name="remarks"></a>설명

rvalue 참조를 사용하면 lvalue와 rvalue를 구별할 수 있습니다. lvalue 참조와 rvalue 참조는 구문 및 의미 체계가 비슷하지만 다소 다른 규칙을 따릅니다. Lvalue 및 rvalue에 대 한 자세한 내용은 [lvalue 및 rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)를 참조 하세요. Lvalue 참조에 대 한 자세한 내용은 [Lvalue 참조 선언 자: &](../cpp/lvalue-reference-declarator-amp.md)를 참조 하세요.

다음 섹션에서는 rvalue 참조가 *의미 체계 이동* 및 *완벽 한 전달* 의 구현을 지 원하는 방법을 설명 합니다.

## <a name="move-semantics"></a>의미 체계 이동

Rvalue 참조는 응용 프로그램의 성능을 크게 향상 시킬 수 있는 *이동 의미 체계* 의 구현을 지원 합니다. 의미 체계 이동을 사용하여 한 개체에서 다른 개체로 리소스(예: 동적으로 할당된 메모리)를 전송하는 코드를 작성할 수 있습니다. 의미 체계 이동은 리소스가 프로그램의 다른 곳에서 참조될 수 없는 임시 개체에서 전송될 수 있도록 하기 때문에 작동합니다.

이동 의미 체계를 구현 하려면 일반적으로 *이동 생성자를* 제공 하 고 필요에 따라 이동 할당 연산자 (**operator =**)를 클래스에 제공 합니다. 이렇게 하면 해당 소스가 rvalue인 복사 및 할당 작업에서 자동으로 의미 체계 이동을 활용합니다. 기본 복사 생성자와 달리, 컴파일러는 기본 이동 생성자를 제공하지 않습니다. 이동 생성자를 작성 하는 방법과 응용 프로그램에서이 생성자를 사용 하는 방법에 대 한 자세한 내용은 [이동 생성자 및 이동 할당 연산자 (c + +)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)를 참조 하세요.

일반 함수 및 연산자를 오버로드하여 의미 체계 이동을 활용할 수도 있습니다. Visual Studio 2010에서는 c + + 표준 라이브러리에 대 한 이동 의미 체계를 소개 합니다. 예를 들어 `string` 클래스는 의미 체계 이동을 수행하는 작업을 구현합니다. 여러 문자열을 연결하고 결과를 출력하는 다음 예제를 살펴보십시오.

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Visual Studio 2010 이전에는 **operator +** 를 호출할 때마다 새 임시 개체 (rvalue)가 할당 되 고 반환 `string` 됩니다. **연산자 +** 는 소스 문자열이 lvalue 인지 또는 rvalue 인지를 알 수 없으므로 다른 문자열에 한 문자열을 추가할 수 없습니다. 소스 문자열이 둘 다 lvalue인 경우 프로그램의 다른 곳에서 참조될 수 있으므로 수정되지 않아야 합니다. Rvalue 참조를 사용 하 여 **연산자 +** 는 프로그램의 다른 곳에서 참조 될 수 없는 rvalue를 사용 하도록 수정할 수 있습니다. 따라서 **operator +** 는 이제 한 문자열을 다른 문자열에 추가할 수 있습니다. 이에 따라 `string` 클래스가 수행해야 하는 동적 메모리 할당 수가 크게 줄어들 수 있습니다. 클래스에 대 한 자세한 내용은 `string` [basic_string 클래스](../standard-library/basic-string-class.md)를 참조 하세요.

의미 체계 이동은 컴파일러에서 RVO(반환 값 최적화) 또는 NRVO(명명된 반환 값 최적화)를 사용할 수 없는 경우에도 도움이 됩니다. 이러한 경우에 컴파일러는 형식에 정의된 이동 생성자를 호출합니다.

의미 체계 이동에 대해 자세히 이해하려면 요소를 `vector` 개체에 삽입하는 예를 참조하십시오. `vector` 개체의 용량이 초과될 경우 `vector` 개체는 해당 요소를 위해 메모리를 재할당한 다음 각 요소를 다른 메모리 위치로 복사하여 삽입된 요소를 위한 공간을 만들어야 합니다. 삽입 작업은 요소를 복사할 때 새 요소를 만들고 데이터를 이전 요소에서 새 요소로 복사하는 복사 생성자를 호출한 후 이전 요소를 소멸시킵니다. 의미 체계 이동을 사용하면 비용이 많이 드는 메모리 할당 및 복사 작업을 수행할 필요 없이 개체를 직접 이동할 수 있습니다.

`vector` 예에서 의미 체계 이동을 활용하기 위해 한 개체에서 다른 개체로 데이터를 이동하는 이동 생성자를 작성할 수 있습니다.

Visual Studio 2010에서 c + + 표준 라이브러리에 의미 체계 이동을 소개 하는 방법에 대 한 자세한 내용은 [c + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)를 참조 하세요.

## <a name="perfect-forwarding"></a>완벽한 전달

완벽한 전달은 오버로드된 함수의 필요성을 줄이고 전달 문제를 방지하는 데 도움이 됩니다. *전달 문제* 는 참조를 매개 변수로 사용 하는 제네릭 함수를 작성 하 고 이러한 매개 변수를 다른 함수에 전달 하거나 *전달* 하는 경우에 발생할 수 있습니다. 예를 들어 제네릭 함수가 `const T&` 형식의 매개 변수를 사용하는 경우 호출된 함수는 해당 매개 변수의 값을 수정할 수 없습니다. 제네릭 함수가 `T&` 형식의 매개 변수를 사용하는 경우에는 rvalue(예: 임시 개체 또는 정수 리터럴)를 사용하여 해당 함수를 호출할 수 없습니다.

일반적으로 이 문제를 해결하려면 각 매개 변수에 대해 `T&` 및 `const T&`를 둘 다 사용하는 제네릭 함수의 오버로드된 버전을 제공해야 합니다. 따라서 오버로드된 함수의 수가 매개 변수의 수와 함께 급격하게 증가합니다. rvalue 참조를 사용하면 마치 다른 함수가 직접 호출된 것처럼 임의의 인수를 받아들여 다른 함수에 전달하는 함수의 버전을 작성할 수 있습니다.

`W`, `X`, `Y` 및 `Z`의 4가지 형식을 선언하는 다음 예제를 살펴보십시오. 각 형식에 대 한 생성자는 **`const`** 및 비 lvalue 참조의 다른 조합을 매개 변수로 사용 **`const`** 합니다.

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

개체를 생성하는 제네릭 함수를 작성한다고 가정합니다. 다음 예제에서는 이 함수를 작성하는 한 가지 방법을 보여 줍니다.

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

다음 예제에서는 `factory` 함수에 대한 유효한 호출을 보여 줍니다.

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

그러나 다음 예제에서는 `factory`가 매개 변수로 수정 가능한 lvalue 참조를 사용하지만 rvalue를 사용하여 호출되기 때문에 `factory` 함수에 대한 올바른 호출을 포함하고 있지 않습니다.

```cpp
Z* pz = factory<Z>(2, 2);
```

일반적으로 이 문제를 해결하려면 `factory` 및 `A&` 매개 변수의 모든 조합에 대해 `const A&` 함수의 오버로드된 버전을 만들어야 합니다. rvalue 참조를 사용하면 다음 예제와 같이 `factory` 함수의 버전을 작성할 수 있습니다.

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

이 예제에서는 rvalue 참조를 함수에 대 한 매개 변수로 사용 `factory` 합니다. [Std:: forward](../standard-library/utility-functions.md#forward) 함수의 용도는 팩터리 함수의 매개 변수를 템플릿 클래스의 생성자에 전달 하는 것입니다.

다음 예제에서는 `main`, `factory`, `W` 및 `X` 클래스의 인스턴스를 만들기 위해 수정된 `Y` 함수를 사용하는 `Z` 함수를 보여 줍니다. 수정된 `factory` 함수는 매개 변수(lvalue 또는 rvalue)를 적절한 클래스 생성자에 전달합니다.

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>rvalue 참조의 추가 속성

**lvalue 참조 및 rvalue 참조를 사용하는 함수를 오버로드할 수 있습니다.**

Lvalue 참조 또는 rvalue 참조를 사용 하도록 함수를 오버 로드 함으로써 **`const`** 수정할 수 없는 개체 (lvalues)와 수정할 수 있는 임시 값 (rvalue)을 구분 하는 코드를 작성할 수 있습니다. 개체가로 표시 되지 않은 경우 rvalue 참조를 사용 하는 함수에 개체를 전달할 수 있습니다 **`const`** . 다음 예제에서는 lvalue 참조 및 rvalue 참조를 사용하도록 오버로드되는 `f` 함수를 보여 줍니다. `main` 함수는 lvalue와 rvalue를 둘 다 사용하여 `f`를 호출합니다.

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

이 예제는 다음과 같은 출력을 생성합니다.

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

이 예제에서 첫 번째 `f` 호출은 지역 변수(lvalue)를 인수로 전달하고, 두 번째 `f` 호출은 임시 개체를 인수로 전달합니다. 임시 개체는 프로그램의 다른 곳에서 참조될 수 없기 때문에 호출은 개체를 언제든지 수정할 수 있는 rvalue 참조를 사용하는 `f`의 오버로드된 버전에 바인딩됩니다.

**컴파일러는 명명된 rvalue 참조를 lvalue로 처리하고 명명되지 않은 rvalue 참조를 rvalue로 처리합니다.**

rvalue 참조를 매개 변수로 사용하는 함수를 작성하는 경우, 해당 매개 변수는 함수 본문에서 lvalue로 처리됩니다. 컴파일러는 명명된 개체가 프로그램의 여러 부분에서 참조될 수 있기 때문에 명명된 rvalue 참조를 lvalue로 처리합니다. 프로그램의 여러 부분에서 해당 개체의 리소스를 수정하거나 제거할 수 있도록 허용하면 위험할 수 있습니다. 예를 들어 프로그램의 여러 부분이 동일한 개체에서 리소스를 전송하려고 하면 첫 번째 부분만 리소스를 성공적으로 전송합니다.

다음 예제에서는 lvalue 참조 및 rvalue 참조를 사용하도록 오버로드되는 `g` 함수를 보여 줍니다. `f` 함수는 rvalue 참조(명명된 rvalue 참조)를 매개 변수로 사용하고 rvalue 참조(명명되지 않은 rvalue 참조)를 반환합니다. `g`에서 `f`를 호출할 때 `g` 본문에서 매개 변수를 lvalue로 처리하기 때문에 오버로드 확인은 lvalue 참조를 사용하는 `f`의 버전을 선택합니다. `g`에서 `main`를 호출할 때 `g`에서 rvalue 참조를 반환하기 때문에 오버로드 확인은 rvalue 참조를 사용하는 `f`의 버전을 선택합니다.

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

이 예제는 다음과 같은 출력을 생성합니다.

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

이 예제에서 `main` 함수는 rvalue를 `f`에 전달합니다. `f`의 본문에서는 명명된 매개 변수를 lvalue로 처리합니다. `f`에서 `g`로의 호출은 매개 변수를 lvalue 참조(`g`의 첫 번째 오버로드된 버전)에 바인딩합니다.

- **lvalue를 rvalue 참조로 캐스팅할 수 있습니다.**

C + + 표준 라이브러리 [std:: move](../standard-library/utility-functions.md#move) 함수를 사용 하면 개체를 해당 개체에 대 한 rvalue 참조로 변환할 수 있습니다. 또는 **`static_cast`** 다음 예제와 같이 키워드를 사용 하 여 lvalue를 rvalue 참조로 캐스팅할 수 있습니다.

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

이 예제는 다음과 같은 출력을 생성합니다.

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**함수 템플릿은 해당 템플릿 인수 형식을 추론한 다음 참조 축소 규칙을 사용합니다.**

매개 변수를 다른 함수에 *전달 하거나 전달* 하는 함수 템플릿을 작성 하는 것이 일반적입니다. 템플릿 형식 추론이 rvalue 참조를 사용하는 함수 템플릿에 대해 어떻게 작용하는지를 이해해야 합니다.

함수 인수가 rvalue이면 컴파일러는 인수를 rvalue 참조로 추론합니다. 예를 들어 `X` 형식을 매개 변수로 사용하는 템플릿 함수에 `T&&` 형식의 개체에 대한 rvalue 참조를 전달하는 경우, 템플릿 인수 추론에서는 `T`가 `X`인 것으로 추론합니다. 따라서 매개 변수의 형식은 `X&&` 입니다. 함수 인수가 lvalue 또는 lvalue 인 경우 **`const`** 컴파일러는 해당 형식을 해당 형식의 lvalue 참조 또는 lvalue 참조로 추론 합니다 **`const`** .

다음 예제에서는 하나의 구조체 템플릿을 선언한 다음 다양한 참조 형식에 대해 특수화합니다. `print_type_and_value` 함수는 rvalue 참조를 매개 변수로 사용하고, 이를 `S::print` 메서드의 적절한 특수화된 버전에 전달합니다. `main` 함수에서는 `S::print` 메서드를 호출하는 다양한 방법을 보여 줍니다.

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

이 예제는 다음과 같은 출력을 생성합니다.

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

`print_type_and_value` 함수에 대한 각 호출을 확인하기 위해 컴파일러는 먼저 템플릿 인수 추론을 수행합니다. 그런 다음 컴파일러는 매개 변수 형식을 추론된 템플릿 인수로 대체할 때 참조 축소 규칙을 적용합니다. 예를 들어 지역 변수 `s1`을 `print_type_and_value` 함수에 전달하면 컴파일러에서 다음과 같은 함수 시그니처를 생성합니다.

```cpp
print_type_and_value<string&>(string& && t)
```

컴파일러는 참조 축소 규칙을 사용하여 시그니처를 다음과 같이 줄입니다.

```cpp
print_type_and_value<string&>(string& t)
```

이 `print_type_and_value` 함수 버전은 매개 변수를 `S::print` 메서드의 올바른 특수화된 버전에 전달합니다.

다음 표에는 템플릿 인수 형식 추론에 대한 참조 축소 규칙이 요약되어 있습니다.

| 확장된 형식 | 축소된 형식 |
|--|--|
| `T& &` | `T&` |
| `T& &&` | `T&` |
| `T&& &` | `T&` |
| `T&& &&` | `T&&` |

템플릿 인수 추론은 완벽한 전달을 구현하는 중요한 요소입니다. 이 항목의 앞부분에 제공된 완벽한 전달 단원에서는 완벽한 전달에 대해 자세히 설명합니다.

## <a name="summary"></a>요약

rvalue 참조는 rvalue와 lvalue를 구별합니다. rvalue 참조는 불필요한 메모리 할당 및 복사 작업의 필요성을 제거함으로써 애플리케이션의 성능을 높이는 데 도움을 줄 수 있습니다. rvalue 참조를 사용하면 마치 다른 함수가 직접 호출된 것처럼 임의의 인수를 받아들여 다른 함수에 전달하는 함수의 버전을 작성할 수도 있습니다.

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[Lvalue 참조 선언자: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues 및 Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[이동 생성자 및 이동 할당 연산자(C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
