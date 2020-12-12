---
description: '자세히 알아보기: 열거형 (c + +)'
title: 열거형(C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: c612628b141e60c02ac4d6d80506e77f7ef35761
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171064"
---
# <a name="enumerations-c"></a>열거형(C++)

열거형은 열거자라는 명명된 정수 상수 집합으로 구성된 사용자 정의 형식입니다.

> [!NOTE]
> 이 문서에서는 c + + 11에 도입 된 ISO 표준 c + + 언어 **`enum`** 형식 및 범위가 지정 된 (또는 강력한 형식의) **열거형 클래스** 형식에 대해 설명 합니다. C + +/CLI 및 c + +/CX의 **public enum 클래스** 또는 **private enum 클래스** 형식에 대 한 자세한 내용은 [enum 클래스](../extensions/enum-class-cpp-component-extensions.md)를 참조 하세요.

## <a name="syntax"></a>구문

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>매개 변수

*identifier*<br/>
열거형에 지정된 형식 이름입니다.

*type*<br/>
열거자의 기본 형식이며, 모든 열거자는 동일한 기본 형식을 갖습니다. 모든 정수 계열 형식이 가능합니다.

*열거 목록*<br/>
열거형에서 열거자의 쉼표로 구분된 목록입니다. 범위에 있는 모든 열거자 또는 변수 이름은 고유해야 합니다. 하지만 값이 중복될 수 있습니다. 범위가 없는 열거형에서 범위는 주변 범위입니다. 범위가 지정 된 열거형에서 범위는 *열거형 목록* 자체입니다.  범위가 지정 된 열거형에서이 목록은 적용 되는 새 정수 계열 형식을 정의 하는 비어 있을 수 있습니다.

*class*<br/>
선언에이 키워드를 사용 하 여 열거형의 범위가 지정 되 고 *식별자* 를 제공 해야 합니다. 대신 키워드를 사용할 수도 있습니다 **`struct`** **`class`** .이 경우에는이 컨텍스트에서 의미상 동일 합니다.

## <a name="enumerator-scope"></a>열거자 범위

열거형은 명명된 상수로 표현되고 열거자라고도 하는 값의 범위를 설명하기 위한 컨텍스트를 제공합니다. 원래 C 및 C++ 열거형 형식에서는 정규화되지 않은 열거자가 열거형이 선언되는 범위 전체에 표시됩니다. 범위가 지정된 열거형에서는 열거자 이름을 열거형 형식 이름으로 한정해야 합니다. 다음 예제에서는 두 가지 열거형의 이러한 기본적인 차이점을 보여 줍니다.

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

열거형의 각 이름은 열거형 값의 순서대로 해당 위치에 해당하는 정수 값이 할당됩니다. 기본적으로 첫 번째 값은 0이 할당되고 다음 값은 1이 할당되는 식이지만 여기에 나와 있는 대로 열거자의 값을 명시적으로 설정할 수 있습니다.

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

`Diamonds` 열거자에 값 `1`이 할당됩니다. 명시적인 값이 지정되지 않은 경우 다음 열거자는 이전 열거자에 1을 더한 값을 받습니다. 앞의 예제에서 `Hearts`의 값은 2, `Clubs`의 값은 3 등이 될 수 있습니다.

모든 열거자는 상수로 처리 되며가 정의 된 범위 내에서 **`enum`** (범위가 지정 되지 않은 열거형의 경우) 또는 **`enum`** 자체 (범위가 지정 된 열거형의 경우) 내에서 고유한 이름을 가져야 합니다. 이름에 지정되는 값은 고유하지 않아도 됩니다. 예를 들어, 범위가 지정되지 않은 열거형 `Suit`의 선언이 다음과 같은 경우

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

`Diamonds`, `Hearts`, `Clubs` 및 `Spades`의 값은 각각 5, 6, 4 및 5입니다. 5가 한 번 이상 사용되며 이는 의도한 것이 아니더라도 허용됩니다. 이러한 규칙은 범위가 지정된 열거형의 경우와 동일합니다.

## <a name="casting-rules"></a>캐스팅 규칙

범위가 없는 열거형 상수는로 암시적으로 변환 될 수 **`int`** 있지만는 **`int`** 열거형 값으로 암시적으로 변환할 수 없습니다. 다음 예제에서는 `hand`에 `Suit`가 아닌 값을 할당하면 어떻게 되는지를 보여 줍니다.

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

를 범위 지정 또는 범위가 지정 되지 않은 열거자로 변환 하려면 캐스트가 필요 **`int`** 합니다. 캐스팅하지 않고 범위가 지정된 열거자를 정수 값으로 승격할 수 있습니다.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

이러한 방식으로 암시적 변환을 사용할 경우 의도하지 않은 문제가 발생할 수 있습니다. 범위가 지정되지 않은 열거형과 관련된 프로그래밍 오류를 제거하기 위해 범위가 지정된 열거형 값은 강력한 형식입니다. 다음 예제에 표시된 것처럼 범위가 지정된 열거자는 열거형 형식 이름(식별자)으로 한정되어야 하며 암시적으로 변환할 수 없습니다.

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

선 `hand = account_num;`은 앞에서 보았듯이 범위가 지정되지 않은 열거형에 발생하는 오류를 초래합니다. 명시적 캐스트로 허용됩니다. 그러나 범위가 지정된 열거형을 사용하여 다음 문 `account_num = Suit::Hearts;`에서 시도된 변환은 명시적 캐스트 없이는 더 이상 허용되지 않습니다.

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a> 열거자가 없는 열거형

**Visual Studio 2017 버전 15.3** 이상 ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): 명시적 기본 형식으로 열거형 (regular 또는 범위)을 정의 하 고 열거자를 사용 하지 않으면 다른 형식으로 암시적으로 변환 되지 않는 새 정수 계열 형식을 적용할 수 있습니다. 기본 제공 형식 대신이 형식을 사용 하 여 실수로 인 한 암시적 변환으로 인해 발생 하는 미묘한 오류의 가능성을 없앨 수 있습니다.

```cpp
enum class byte : unsigned char { };
```

새 형식은 기본 형식의 정확한 복사본 이므로 호출 규칙이 동일 합니다. 즉, 모든 성능 저하 없이 ABIs에서 사용할 수 있습니다. 직접 목록 초기화를 사용 하 여 형식의 변수를 초기화 하는 경우 캐스트가 필요 하지 않습니다. 다음 예제에서는 다양 한 컨텍스트에서 열거자를 사용 하지 않고 열거형을 초기화 하는 방법을 보여 줍니다.

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>참고 항목

[C 열거형 선언](../c-language/c-enumeration-declarations.md)<br/>
[키워드](../cpp/keywords-cpp.md)
