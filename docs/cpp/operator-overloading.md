---
description: '자세한 정보: 연산자 오버 로드'
title: 연산자 오버로드
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: 23a35a87f9f370a9bb8f268ac1637a4a899ee5f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146031"
---
# <a name="operator-overloading"></a>연산자 오버로드

**`operator`** 키워드는 클래스의 인스턴스에 적용 될 때 기호를 나타내는 *연산자* 를 지정 하는 함수를 선언 합니다. 이 키워드는 연산자에게 둘 이상의 의미를 제공 즉, 오버로드합니다. 컴파일러는 피연산자의 형식을 검사하여 연산자의 여러 가지 의미 간을 구분합니다.

## <a name="syntax"></a>Syntax

> *유형* **`operator`** *연산자-기호* **(** *매개 변수 목록* **)**

## <a name="remarks"></a>설명

대부분의 기본 제공 연산자의 함수는 전역적으로 또는 클래스 단위로 다시 정의할 수 있습니다. 오버로드된 연산자는 함수로 구현됩니다.

오버 로드 된 연산자의 이름은 **`operator`** *x* 입니다. 여기서 *x* 는 다음 표에 나와 있는 연산자입니다. 예를 들어 더하기 연산자를 오버 로드 하려면 **operator +** 라는 함수를 정의 합니다. 마찬가지로 더하기/할당 연산자를 오버 로드 하려면 **+=** **operator + =** 라는 함수를 정의 합니다.

### <a name="redefinable-operators"></a>다시 정의할 수 있는 연산자

|연산자|Name|유형|
|--------------|----------|----------|
|**,**|쉼표|이진|
|**!**|논리적 NOT|단항|
|**!=**|같지 않음|이진|
|**%**|모듈러스|이진|
|**%=**|모듈러스 대입|이진|
|**&**|비트 AND|이진|
|**&**|Address-of|단항|
|**&&**|논리적 AND|이진|
|**&=**|비트 AND 대입|이진|
|**( )**|함수 호출|—|
|**( )**|캐스트 연산자|단항|
|**&#42;**|곱하기|이진|
|**&#42;**|포인터 역참조|단항|
|**&#42;=**|곱하기 할당|이진|
|**+**|더하기|이진|
|**+**|단항 더하기|단항|
|**++**|증가값 <sup>1</sup>|단항|
|**+=**|더하기 할당|이진|
|**-**|빼기|이진|
|**-**|단항 부정 연산자|단항|
|**--**|감소 <sup>1</sup>|단항|
|**-=**|빼기 할당|이진|
|**->**|멤버 선택|이진|
|**->&#42;**|멤버 포인터 선택|이진|
|**/**|사업부|이진|
|**/=**|나누기 할당|이진|
|**\<**|보다 작음|이진|
|**<<**|왼쪽 |이진|
|**<<=**|왼쪽 시프트 할당|이진|
|**<=**|작거나 같음|이진|
|**=**|할당|이진|
|**==**|같음|이진|
|**>**|초과|이진|
|**>=**|크거나 같음|이진|
|**>>**|오른쪽 Shift|이진|
|**>>=**|오른쪽 시프트 할당|이진|
|**[ ]**|배열 첨자|—|
|**^**|배타적 OR|이진|
|**^=**|배타적 OR 할당|이진|
|**&#124;**|포괄적 비트 OR|이진|
|**&#124;=**|포괄적 비트 OR 대입|이진|
|**&#124;&#124;**|논리적 OR|이진|
|**~**|1의 보수|단항|
|**`delete`**|삭제|—|
|**`new`**|단추를 사용하여 새|—|
|conversion operators|conversion operators|단항|

<sup>1</sup> 단항 증가 및 감소 연산자의 두 가지 버전 (사전 증가 및 postincrement)이 있습니다.

자세한 내용은 [연산자 오버 로드에 대 한 일반 규칙](../cpp/general-rules-for-operator-overloading.md) 을 참조 하세요. 다양한 범주의 오버로드된 연산자에 대한 제약 조건이 다음 항목에 설명되어 있습니다.

- [단항 연산자](../cpp/overloading-unary-operators.md)

- [이항 연산자](../cpp/binary-operators.md)

- [할당](../cpp/assignment.md)

- [함수 호출](../cpp/function-call-cpp.md)

- [첨자](../cpp/subscripting.md)

- [클래스 멤버 액세스](../cpp/member-access.md)

- [증가 및 감소](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [사용자 정의 형식 변환](../cpp/user-defined-type-conversions-cpp.md)

다음 테이블의 연산자는 오버로드할 수 없습니다. 테이블에는 전처리기 기호 및가 포함 되어 있습니다 **#** **##** .

### <a name="nonredefinable-operators"></a>다시 정의할 수 없는 연산자

|연산자|Name|
|-|-|
|**.**|멤버 선택|
|**. &#42;**|멤버 포인터 선택|
|**::**|범위 확인|
|**? :**|조건부|
|**#**|문자열로 전처리기 변환|
|**##**|전처리기 연결|

오버로드된 연산자는 코드에서 발견되었을 때 일반적으로 컴파일러에 의해 암시적으로 호출되지만 다음과 같이 멤버 또는 비멤버 함수가 호출될 때처럼 명시적으로 호출할 수 있습니다.

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>예제

다음 예에서는 연산자를 오버 로드 **+** 하 여 두 개의 복소수를 추가 하 고 결과를 반환 합니다.

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>섹션 내용

- [연산자 오버 로드에 대 한 일반 규칙](../cpp/general-rules-for-operator-overloading.md)

- [단항 연산자 오버 로드](../cpp/overloading-unary-operators.md)

- [이항 연산자](../cpp/binary-operators.md)

- [할당](../cpp/assignment.md)

- [함수 호출](../cpp/function-call-cpp.md)

- [첨자](../cpp/subscripting.md)

- [멤버 액세스](../cpp/member-access.md)

## <a name="see-also"></a>참고 항목

[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[키워드](../cpp/keywords-cpp.md)
