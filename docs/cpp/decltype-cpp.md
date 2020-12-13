---
description: '자세한 정보: decltype (c + +)'
title: decltype(C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: e581436a43fc9632961fcb888dfb0b23974fc2df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339503"
---
# <a name="decltype--c"></a>decltype(C++)

**`decltype`** 형식 지정자는 지정 된 식의 형식을 생성 합니다. **`decltype`** 형식 지정자는 [ `auto` 키워드](../cpp/auto-cpp.md)와 함께 주로 템플릿 라이브러리를 작성 하는 개발자에 게 유용 합니다. **`auto`** 및 **`decltype`** 를 사용 하 여 반환 형식이 해당 템플릿 인수의 형식에 종속 되는 템플릿 함수를 선언 합니다. 또는 및를 **`auto`** 사용 **`decltype`** 하 여 다른 함수에 대 한 호출을 래핑하는 템플릿 함수를 선언한 다음 래핑된 함수의 반환 형식을 반환 합니다.

## <a name="syntax"></a>Syntax

> **`decltype(`***식***`)`**

### <a name="parameters"></a>매개 변수

*식*\
식입니다. 자세한 내용은 [식](../cpp/expressions-cpp.md)을 참조 하세요.

## <a name="return-value"></a>반환 값

*식* 매개 변수의 형식입니다.

## <a name="remarks"></a>설명

**`decltype`** 형식 지정자는 Visual Studio 2010 이상 버전에서 지원 되며 네이티브 또는 관리 코드에서 사용할 수 있습니다. `decltype(auto)`(C++14)는 Visual Studio 2015 이상에서 지원됩니다.

컴파일러는 다음 규칙을 사용 하 여 *식* 매개 변수의 형식을 결정 합니다.

- *Expression* 매개 변수가 식별자 또는 [클래스 멤버 액세스](../cpp/member-access-operators-dot-and.md)인 경우 `decltype(expression)` 은 *식* 으로 이름이 지정 된 엔터티의 형식입니다. 이러한 엔터티가 없거나 *식* 매개 변수가 오버 로드 된 함수 집합의 이름을 가진 경우 컴파일러는 오류 메시지를 생성 합니다.

- *식* 매개 변수가 함수 또는 오버 로드 된 연산자 함수를 호출 하는 경우 `decltype(expression)` 은 함수의 반환 형식입니다. 오버로드된 연산자를 묶는 괄호는 무시됩니다.

- *식* 매개 변수가 [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)인 경우 `decltype(expression)` 은 *식* 의 형식입니다. *식* 매개 변수가 [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)인 경우 `decltype(expression)` 은 *식* 형식에 대 한 [lvalue 참조](../cpp/lvalue-reference-declarator-amp.md) 입니다.

다음 코드 예제에서는 형식 지정자의 일부를 사용 하는 방법을 보여 줍니다 **`decltype`** . 먼저 다음 문을 코딩한 것으로 가정합니다.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

다음으로 다음 표에 나와 있는 네 가지 문에 의해 반환 되는 형식을 검사 **`decltype`** 합니다.

|문|형식|참고|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|에 대 한 [rvalue 참조](../cpp/rvalue-reference-declarator-amp-amp.md) **`const int`** 입니다.|
|`decltype(var);`|**`int`**|`var` 변수의 형식입니다.|
|`decltype(a->x);`|**`double`**|멤버 액세스의 형식입니다.|
|`decltype((a->x));`|`const double&`|내부 괄호를 사용하면 문이 멤버 액세스가 아니라 식으로 평가됩니다. `a`가 포인터로 선언 되었으므로 **`const`** 형식은에 대 한 참조입니다 **`const double`** .|

## <a name="decltype-and-auto"></a>Decltype 및 Auto

C + + 14에서는 `decltype(auto)` 후행 반환 형식 없이를 사용 하 여 반환 형식이 해당 템플릿 인수의 형식에 종속 되는 템플릿 함수를 선언할 수 있습니다.

C + + 11에서는 **`decltype`** 후행 반환 형식에 대 한 형식 지정자와 키워드를 함께 사용 하 여 **`auto`** 반환 형식이 해당 템플릿 인수의 형식에 종속 되는 템플릿 함수를 선언할 수 있습니다. 예를 들어, 템플릿 함수의 반환 형식이 템플릿 인수의 형식에 종속되는 것을 보여 주는 다음 코드 예제를 살펴보세요. 코드 예제에서 *알 수 없는* 자리 표시자는 반환 형식을 지정할 수 없음을 나타냅니다.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

형식 지정자를 도입 하면 **`decltype`** 개발자가 템플릿 함수가 반환 하는 식의 형식을 가져올 수 있습니다. 나중에 표시 되는 *대체 함수 선언 구문* , **`auto`** 키워드 및 형식 지정자를 사용 **`decltype`** 하 여 *런타임에 지정* 된 반환 형식을 선언 합니다. 컴파일하면 지정되는 반환 형식은 코딩 시가 아니라 선언이 컴파일될 때 결정됩니다.

다음 프로토타입에서는 대체 함수 선언의 구문을 보여 줍니다. **`const`** 및 **`volatile`** 한정자와 **`throw`** [예외 사양](../cpp/exception-specifications-throw-cpp.md) 은 선택 사항입니다. *Function_body* 자리 표시자는 함수가 수행 하는 작업을 지정 하는 복합 문을 나타냅니다. 모범 사례에 따라 문의 *식* 자리 표시자는 **`decltype`** **`return`** *function_body* 에서 문에 지정 된 식 (있는 경우)과 일치 해야 합니다.

**`auto`***function_name* **`(`** *매개 변수*<sub>옵트인</sub> 옵트인 **`)`** **`const`** <sub></sub> **`volatile`** <sub></sub> **`->`** **`decltype(`** *식* **`)`** **`noexcept`** <sub>옵트인</sub> **`{`** *function_body***`};`**

다음 코드 예제에서는 `myFunc` 템플릿 함수의 컴파일하면 지정되는 반환 형식이 `t` 및 `u` 템플릿 인수의 형식에 따라 결정됩니다. 모범 사례에 따라 코드 예제에서는 rvalue 참조 및 `forward` 함수 템플릿을 사용 하 여 *완벽 한 전달을* 지원 합니다. 자세한 내용은 [RValue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Decltype 및 전달 함수(C++11)

전달 함수는 다른 함수에 대한 호출을 래핑합니다. 해당 인수 또는 이러한 인수를 포함하는 식의 결과를 다른 함수로 전달하는 함수 템플릿을 고려해 보십시오. 또한 전달 함수는 다른 함수를 호출한 결과를 반환합니다. 이 시나리오에서 전달 함수의 반환 형식은 래핑된 함수의 반환 형식과 동일해야 합니다.

이 시나리오에서는 형식 지정자 없이 적절 한 형식 식을 작성할 수 없습니다 **`decltype`** . **`decltype`** 형식 지정자는 함수가 참조 형식을 반환 하는지 여부에 대 한 필수 정보를 잃지 않기 때문에 제네릭 전달 함수를 사용 하도록 설정 합니다. 전달 함수의 코드 예제는 이전 `myFunc` 템플릿 함수 예제를 참조하세요.

## <a name="examples"></a>예제

다음 코드 예제는 템플릿 함수 `Plus()`의 컴파일하면 지정되는 반환 형식을 선언합니다. `Plus`함수는 오버 로드를 사용 하 여 두 피연산자를 처리 **`operator+`** 합니다. 따라서 더하기 연산자 ( **`+`** )와 함수의 반환 형식은 `Plus` 함수 인수의 형식에 따라 해석 됩니다.

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

**Visual Studio 2017 이상:** 컴파일러는 **`decltype`** 템플릿이 인스턴스화되지 않고 선언 될 때 인수를 구문 분석 합니다. 따라서 인수에 종속 되지 않은 특수화가 있는 경우이 특수화는 **`decltype`** 인스턴스화 시간으로 지연 되지 않고 즉시 처리 되며 결과 오류가 해당 시간에 진단 됩니다.

다음 예제에서는 선언 시점에 발생한 컴파일러 오류를 보여 줍니다.

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>요구 사항

Visual Studio 2010 이상 버전

`decltype(auto)` Visual Studio 2015 이상이 필요 합니다.
