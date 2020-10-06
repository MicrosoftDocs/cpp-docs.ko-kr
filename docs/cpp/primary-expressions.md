---
title: 기본 식
description: C + + 프로그래밍 언어의 기본 식입니다.
ms.date: 10/02/2020
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: 4c52992071453bc189a3078db9592b02dfb8ba9b
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765327"
---
# <a name="primary-expressions"></a>기본 식

기본 식은 더 복잡한 식의 구성 요소이며 이는 범위 결정 연산자 ()로 정규화 된 리터럴, 이름 및 이름이 될 수 있습니다 `::` . 기본 식의 형식은 다음 중 하나입니다.

*`primary-expression`*\
&emsp;*`literal`*\
&emsp;**`this`**\
&emsp;*`name`*\
&emsp;**`::`** *`name`* **`(`** *`expression`* **`)`**

는 *`literal`* 상수 기본 식입니다. 지정의 형태에 따라 형식이 결정됩니다. 리터럴을 지정 하는 방법에 대 한 자세한 내용은 [리터럴](../cpp/numeric-boolean-and-pointer-literals-cpp.md) 을 참조 하세요.

**`this`** 키워드는 클래스 개체에 대 한 포인터입니다. 비정적 멤버 함수 내에서 사용할 수 있습니다. 함수가 호출 된 클래스의 인스턴스를 가리킵니다. **`this`** 키워드는 클래스 멤버 함수 본문 외부에서 사용할 수 없습니다.

포인터의 형식은 **`this`** `type * const` `type` 포인터를 특별히 수정 하지 않는 함수 내의 (여기서는 클래스 이름)입니다 **`this`** . 다음 예제에서는 멤버 함수 선언과의 형식을 보여 줍니다 **`this`** .

```cpp
// expre_Primary_Expressions.cpp
// compile with: /LD
class Example
{
public:
    void Func();          //  * const this
    void Func() const;    //  const * const this
    void Func() volatile; //  volatile * const this
};
```

포인터의 형식을 수정 하는 방법에 대 한 자세한 내용은 **`this`** [ `this` 포인터](this-pointer.md)를 참조 하십시오.

이름 뒤에 오는 범위 결정 연산자 ( **`::`** )는 기본 식입니다.  이러한 이름은 멤버 이름이 아니라 전역 범위의 이름이어야 합니다. 식의 형식은 이름 선언에 의해 결정 됩니다. 선언 이름이 l-value 인 경우 l-value 이며 (즉, 할당 식의 왼쪽에 나타날 수 있습니다.)입니다. 범위 결정 연산자를 사용하면 전역 이름이 현재 범위에서 숨겨지더라도 해당 이름이 참조됩니다. 범위 결정 연산자를 사용 하는 방법에 대 한 예는 [범위](../cpp/scope-visual-cpp.md) 를 참조 하세요.

괄호로 묶인 식은 기본 식입니다. 해당 형식 및 값은 괄호로 묶인 식의 형식 및 값과 동일 합니다. 괄호로 묶은 식이 l-value 인 경우 l-value입니다.

기본 식의 예제는 다음과 같습니다.

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

이러한 예제는 다음과 같은 다양 한 형식의 기본 식과 같은 *이름*으로 간주 됩니다.

```cpp
MyClass // an identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>참조

[식 형식](../cpp/types-of-expressions.md)
