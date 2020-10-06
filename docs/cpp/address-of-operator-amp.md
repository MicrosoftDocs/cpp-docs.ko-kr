---
title: '주소 연산자: &amp;'
description: C + + 언어의 주소 연산자입니다.
ms.date: 10/02/2020
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: 8ef7ad065281e4de58ddbdebea25950f8eb9dd06
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765288"
---
# <a name="address-of-operator-amp"></a>주소 연산자: &amp;

## <a name="syntax"></a>구문

> **`&`** *`cast-expression`*

## <a name="remarks"></a>설명

단항 주소 연산자 ( **`&`** )는 해당 피연산자의 주소를 사용 합니다. 주소 연산자의 피연산자는 함수 지정자 이거나 비트 필드가 아닌 개체를 지정 하는 l-value 일 수 있습니다.

주소 연산자는 파일 범위 수준에서 선언 된 기본, 구조체, 클래스 또는 공용 구조체 형식의 변수 또는 첨자 된 배열 참조에만 적용 될 수 있습니다. 이러한 식에서는 주소 연산자를 포함 하지 않는 상수 식을 식의 주소 식에 더하거나 뺄 수 있습니다.

함수 또는 l-value에 적용된 식의 결과는 피연산자의 형식에서 파생된 포인터 형식(r-value)입니다. 예를 들어 피연산자의 형식이 인 경우 **`char`** 식의 결과는에 대 한 포인터 형식입니다 **`char`** . 또는 개체에 적용 되는 주소 연산자 **`const`** 는 **`volatile`** 또는로 계산 `const type *` `volatile type *` `type` 됩니다. 여기서은 원본 개체의 형식입니다.

오버 로드 된 함수의 주소는 참조 되는 함수의 버전을 명확 하 게 알 수 있는 경우에만 수행할 수 있습니다. 오버 로드 된 특정 함수의 주소를 가져오는 방법에 대 한 자세한 내용은 [함수 오버 로드](function-overloading.md) 를 참조 하세요.

주소 연산자가 정규화 된 이름에 적용 되는 경우 결과는 *정규화 된 이름이* 정적 멤버를 지정 하는지 여부에 따라 달라 집니다. 그럴 경우 결과는 멤버의 선언에 지정된 형식의 포인터입니다. Static이 아닌 멤버의 경우 결과는 *정규화 된 클래스 이름*으로 표시 된 클래스의 멤버 *이름* 에 대 한 포인터입니다. *정규화 된 클래스 이름*에 대 한 자세한 내용은 [기본 식](../cpp/primary-expressions.md)을 참조 하세요.

## <a name="example-address-of-static-member"></a>예: 정적 멤버의 주소

다음 코드 조각에서는 클래스 멤버가 정적 인지 여부에 따라 연산자 결과의 주소가 어떻게 다른 지 보여 줍니다.

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

이 예제에서 `&PTM::fValue` 식은 `float *`가 정적 멤버이기 때문에 `float PTM::*` 형식이 아닌 `fValue` 형식이 됩니다.

## <a name="example-address-of-a-reference-type"></a>예: 참조 형식의 주소

주소 연산자를 참조 형식에 적용하면 해당 연산자를 참조가 바인딩된 개체에 적용하는 것과 같은 결과가 도출됩니다. 예를 들면 다음과 같습니다.

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

```Output
&d equals &rd
```

## <a name="example-function-address-as-parameter"></a>예: 함수 주소를 매개 변수로

다음 예제에서는 주소 연산자를 사용하여 포인터 인수를 함수에 전달합니다.

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

```Output
25
```

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[C + + 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Lvalue 참조 선언자: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[간접 참조 및 주소 연산자](../c-language/indirection-and-address-of-operators.md)
