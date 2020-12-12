---
description: '자세한 정보: 함수 오버 로드'
title: 함수 오버로드
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: 59fb43c849518251170b6f84a74cd8cbc2e2ed22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345552"
---
# <a name="function-overloading"></a>함수 오버로드

C++에서는 동일한 범위에서 이름이 같은 함수를 둘 이상 지정할 수 있습니다. 이러한 함수를 *오버 로드* 된 함수 라고 합니다. 오버 로드 된 함수를 사용 하면 인수의 형식 및 수에 따라 함수에 대해 다양 한 의미 체계를 제공할 수 있습니다.

예를 들어 `print` 인수를 사용 하는 함수는 `std::string`  형식의 인수를 사용 하는 것과 매우 다른 작업을 수행할 수 있습니다 **`double`** . 오버 로드를 사용 하면 또는와 같은 이름을 사용할 `print_string` 필요가 `print_double` 없습니다. 컴파일 시간에 컴파일러는 호출자가 전달 하는 인수 형식을 기반으로 사용할 오버 로드를 선택 합니다.  를 호출 하면 `print(42.0)` `void print(double d)` 함수가 호출 됩니다. 를 호출 하면 `print("hello world")` `void print(std::string)` 오버 로드가 호출 됩니다.

멤버 함수와 비멤버 함수를 모두 오버 로드할 수 있습니다. 다음 표에서는 C++에서 동일한 범위에서 이름이 동일한 함수 그룹 간을 구별하는 데 사용하는 함수 선언 부분을 보여 줍니다.

### <a name="overloading-considerations"></a>오버로드 고려 사항

|함수 선언 요소|오버로드에 사용되는지 여부|
|----------------------------------|---------------------------|
|함수 반환 형식|아니요|
|인수의 수|예|
|인수 형식|예|
|줄임표의 존재 여부|예|
|이름 사용 **`typedef`**|아니요|
|지정하지 않은 배열 범위|아니요|
|**`const`** 또는 **`volatile`**|예 (전체 함수에 적용 된 경우)|
|[참조-한정자](#ref-qualifiers)|예|

## <a name="example"></a>예제

다음 예제에서는 오버로드 사용 방법을 보여 줍니다.

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

앞의 코드에서는 파일 범위에서의 `print` 함수의 오버로드를 보여 줍니다.

기본 인수는 함수 형식의 일부로 간주 되지 않습니다. 따라서 오버 로드 된 함수를 선택 하는 데 사용 되지 않습니다. 해당 기본 인수에만 다른 두 개의 함수는 오버로드된 함수 대신 여러 정의로 간주됩니다.

오버 로드 된 연산자에는 기본 인수를 제공할 수 없습니다.

## <a name="argument-matching"></a>인수 일치

현재 범위에서 함수 호출에 제공된 인수와 가장 일치하는 함수 선언에 대해 오버로드된 함수가 선택됩니다. 적절한 함수를 찾으면 함수가 호출됩니다. 이 컨텍스트에서 "적합"은 다음 중 하나를 의미 합니다.

- 정확히 일치하는 항목을 찾았습니다.

- 간단한 변환을 수행했습니다.

- 정수 계열 확장이 수행되었습니다.

- 원하는 인수 형식에 대한 표준 변환이 존재합니다.

- 원하는 인수 형식에 대한 사용자 정의 변환(변환 연산자 또는 생성자)이 존재합니다.

- 줄임표로 나타낸 인수를 찾았습니다.

컴파일러가 각 인수의 후보 함수 집합을 만듭니다. 후보 함수는 해당 위치의 실제 인수를 형식 인수의 형식으로 변환할 수 있는 함수입니다.

"가장 일치하는 함수" 집합이 각 인수에 대해 빌드되고 모든 집합에 공통된 함수가 선택됩니다. 공통된 함수가 2개 이상일 경우 오버로드가 모호해지고 오류를 생성합니다. 최종적으로 선택되는 함수는 하나 이상의 인수에 대해 그룹의 다른 함수보다 일치합니다. 명확 하 게 적용 되지 않는 경우 함수 호출에서 오류를 생성 합니다.

다음과 같은 선언이 있습니다. 알아보기 쉽게 함수가 `Variant 1`, `Variant 2` 및 `Variant 3`으로 표시되었습니다.

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

다음과 같은 문이 있습니다.

```cpp
F1 = Add( F2, 23 );
```

위의 문에서는 두 집합을 빌드합니다.

|집합 1: 분수 형식의 첫 번째 인수가 있는 후보 함수|설정 2: 두 번째 인수를 형식으로 변환할 수 있는 후보 함수 **`int`**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|변형 1|변형 1 ( **`int`** **`long`** 표준 변환을 사용 하 여로 변환 가능)|
|변형 3||

집합 2의 함수는 실제 매개 변수 형식에서 정식 매개 변수 형식으로의 암시적 변환이 있는 함수 이며, 이러한 함수 중에 실제 매개 변수 형식을 정식 매개 변수 형식으로 변환 하는 "cost"가 가장 작은 함수가 있습니다.

두 집합의 공통된 함수는 변형 1입니다. 다음은 모호한 함수 호출의 예입니다.

```cpp
F1 = Add( 3, 6 );
```

앞의 함수 호출에서 다음 집합을 빌드합니다.

|설정 1: 형식의 첫 번째 인수가 있는 후보 함수 **`int`**|설정 2: 형식의 두 번째 인수가 있는 후보 함수 **`int`**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|변형 2 ( **`int`** **`long`** 표준 변환을 사용 하 여 변환 가능)|변형 1 ( **`int`** **`long`** 표준 변환을 사용 하 여로 변환 가능)|

이러한 두 집합의 교집합은 비어 있으므로 컴파일러는 오류 메시지를 생성 합니다.

인수 일치의 경우 *n* 개의 기본 인수가 있는 함수는 각각 서로 다른 개수의 인수를 갖는 *n*+ 1 개의 개별 함수로 처리 됩니다.

줄임표(...)는 와일드카드로 사용되어 실제 인수와 일치합니다. 매우 신중 하 게 오버 로드 된 함수 집합을 디자인 하지 않는 경우 모호한 집합을 많이 만들 수 있습니다.

> [!NOTE]
> 오버 로드 된 함수의 모호성은 함수 호출이 발생할 때까지 확인할 수 없습니다. 이때 함수 호출의 각 인수에 대해 집합이 빌드되고 명확한 오버로드가 존재하는지 여부를 확인할 수 있습니다. 즉, 특정 함수 호출에서 호출할 때까지 코드에 모호성이 남아있을 수 있습니다.

## <a name="argument-type-differences"></a>인수 형식 차이

오버로드된 함수는 다른 이니셜라이저를 사용하는 인수 형식을 구분합니다. 따라서, 주어진 형식의 인수와 그 형식에 대한 참조는 오버로드 목적의 형식과 동일한 것으로 간주됩니다. 이들은 같은 이니셜라이저를 사용하기 때문에 동일한 것으로 간주됩니다. 예를 들어, `max( double, double )`는 `max( double &, double & )`와 동일한 것으로 간주됩니다. 이러한 두 함수를 선언하면 오류가 발생합니다.

이와 같은 이유로 또는에 의해 수정 된 형식의 함수 인수 **`const`** **`volatile`** 는 오버 로드를 위해 기본 형식과 다르게 처리 되지 않습니다.

그러나 함수 오버 로드 메커니즘은 및로 정규화 된 참조 **`const`** **`volatile`** 와 기본 형식에 대 한 참조를 구분할 수 있습니다. 다음과 같은 코드를 사용할 수 있습니다.

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>출력

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

및 개체에 대 한 포인터 **`const`** **`volatile`** 는 오버 로드를 위해 기본 형식에 대 한 포인터와 다른 것으로 간주 됩니다.

## <a name="argument-matching-and-conversions"></a>인수 일치 및 변환

컴파일러가 실제 인수를 함수 선언의 인수와 일치시키려고 할 때 정확히 일치하는 항목이 없을 경우 표준 또는 사용자 정의 변환을 통해 올바른 형식을 가져오도록 할 수 있습니다. 변환 애플리케이션에는 다음의 규칙이 적용됩니다.

- 둘 이상의 사용자 정의 변환이 포함된 변환 시퀀스는 고려하지 않습니다.

- 중간 변환을 제거하여 단축할 수 있는 변환 시퀀스는 고려하지 않습니다.

변환 결과 시퀀스가 있을 경우 이를 가장 일치하는 시퀀스라고 합니다. **`int`** **`unsigned long`** 표준 변환 ( [표준 변환](../cpp/standard-conversions.md)참조)을 사용 하 여 형식의 개체를 형식으로 변환 하는 방법에는 여러 가지가 있습니다.

- 에서로 변환 하 **`int`** **`long`** 고,에서 **`long`** 로 변환 **`unsigned long`** 합니다.

- 에서 **`int`** 로 변환 **`unsigned long`** 합니다.

첫 번째 시퀀스는 원하는 목표를 달성 하는 것이 아니라 가장 일치 하는 시퀀스가 아니라 가장 짧은 시퀀스가 있습니다.

다음 표에서는 가장 일치하는 시퀀스를 결정하는 데 제한된 영향을 미치는 trivial 변환이라는 변환 그룹을 보여 줍니다. 이 표의 다음 목록에서는 시퀀스 선택에 영향을 미치는 trivial 변환이 이루어지는 인스턴스에 대해 설명합니다.

### <a name="trivial-conversions"></a>Trivial 변환

|변환 전 형식|변환 후 형식|
|-----------------------|---------------------|
|*유형-이름*|*유형-이름***&**|
|*유형-이름***&**|*유형-이름*|
|*유형-이름* **[]**|*유형-이름*__\*__|
|*형식 이름* **(** *인수 목록* **)**|**(** __\*__ *형식-이름* **) (** *인수 목록* **)**|
|*유형-이름*|**`const`***유형-이름*|
|*유형-이름*|**`volatile`***유형-이름*|
|*유형-이름*__\*__|**`const`***유형-이름*__\*__|
|*유형-이름*__\*__|**`volatile`***유형-이름*__\*__|

변환이 시도되는 시퀀스는 다음과 같습니다.

1. 정확한 일치. 함수가 호출되는 형식과 함수 프로토타입에서 선언된 형식 간 정확한 일치는 항상 가장 좋은 일치입니다. trivial 변환 시퀀스는 정확히 일치하는 항목으로 분류됩니다. 그러나 이러한 변환 작업을 수행 하지 않는 시퀀스는를 변환 하는 시퀀스 보다 더 나은 것으로 간주 됩니다.

   - 포인터에서 **`const`** (to)로의 포인터 `type` <strong>\*</strong> **`const`** `type` <strong>\*</strong> 입니다.

   - 포인터에서 **`volatile`** (to)로의 포인터 `type` <strong>\*</strong> **`volatile`** `type` <strong>\*</strong> 입니다.

   - 참조에서 **`const`** (으)로 참조 `type` **&** **`const`** `type` **&** 합니다.

   - 참조에서 **`volatile`** (으)로 참조 `type` **&** **`volatile`** `type` **&** 합니다.

1. 승격을 통한 일치. 정수 계열 확장만 포함 하는 정확히 일치 하는 것으로 분류 되지 않은 모든 시퀀스는 **`float`** **`double`** 승격을 사용 하 여 일치 항목으로 분류 됩니다. 승격을 통한 일치는 정확한 일치만큼 양호하지는 않지만 표준 변환을 통한 일치에 비해 좋습니다.

1. 표준 변환을 통한 일치. 표준 변환과 trivial 변환만 포함 포함하는, 정확한 일치 또는 승격을 통한 일치로 분류되지 않은 시퀀스는 표준 변환을 통한 일치로 분류됩니다. 이 범주에는 다음 규칙이 적용됩니다.

   - 파생 클래스에 대 한 포인터에서 직접 또는 간접 기본 클래스에 대 한 포인터로의 변환은 또는로 변환 하는 것 보다 좋습니다 `void *` `const void *` .

   - 파생 클래스에 대한 포인터에서 기본 클래스에 대한 포인터로 변환할 경우 기본 클래스가 직접 기본 클래스에 가까울수록 더 잘 일치합니다. 클래스 계층 구조가 다음 그림과 같다고 가정합니다.

![기본 변환 그래프](../cpp/media/vc391t1.gif "기본 변환 그래프") <br/>
기본 변환을 보여 주는 그래프

`D*` 형식에서 `C*` 형식으로 변환하는 것이 `D*` 형식에서 `B*` 형식으로 변환하는 것보다 좋습니다. 마찬가지로 `D*` 형식에서 `B*` 형식으로 변환하는 것이 `D*` 형식에서 `A*` 형식으로 변환하는 것보다 좋습니다.

이 규칙은 참조 변환에 동일하게 적용됩니다. `D&` 형식에서 `C&` 형식으로 변환하는 것이 `D&` 형식에서 `B&` 형식 등으로 변환하는 것보다 좋습니다.

이 규칙은 멤버 포인터 변환에 동일하게 적용됩니다. `T D::*` 형식에서 `T C::*` 형식으로 변환하는 것이 `T D::*` 형식에서 `T B::*` 형식 등으로 변환하는 것보다 좋습니다. 여기서 `T`는 멤버 형식입니다.

앞의 규칙은 지정된 파생 경로에만 적용됩니다. 다음 그림에 표시된 그래프를 살펴보세요.

![기본 변환을 보여 주는 다중&#45;상속](../cpp/media/vc391t2.gif "기본 변환을 보여 주는 다중&#45;상속") <br/>
기본 변환을 보여 주는 다중 상속 그래프

`C*` 형식에서 `B*` 형식으로 변환하는 것이 `C*` 형식에서 `A*` 형식으로 변환하는 것보다 좋습니다. 이유는 이들이 동일한 경로에 있고 `B*`가 더 가깝기 때문입니다. 그러나 형식에서 형식으로 변환 `C*` `D*` 하는 것은 형식으로 변환 하 `A*` 는 것이 더 좋습니다. 변환은 다른 경로를 따르기 때문에 기본 설정이 없습니다.

1. 사용자 정의 변환을 통한 일치. 이 시퀀스는 정확히 일치 하는 항목, 승격을 사용한 일치 항목 또는 표준 변환을 사용한 일치 항목으로 분류 될 수 없습니다. 이 시퀀스가 사용자 정의 변환을 통한 일치로 분류되려면 사용자 정의 변환, 표준 변환 또는 trivial 변환이 포함되어야 합니다. 사용자 정의 변환을 통한 일치는 줄임표를 통한 일치보다 좋은 것으로 간주되지만 표준 변환을 통한 일치만큼 양호하지는 않습니다.

1. 줄임표를 통한 일치. 선언에서 줄임표와 일치하는 모든 시퀀스는 줄임표를 통한 일치로 분류됩니다. 가장 약한 일치 항목으로 간주 됩니다.

기본 승격 또는 변환이 존재하지 않는 경우 사용자 정의 변환이 적용됩니다. 이러한 변환은 일치하는 인수의 형식을 기준으로 선택됩니다. 다음 코드를 생각해 봅시다.

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

클래스에 사용할 수 있는 사용자 정의 변환은 `UDC` 형식 및 형식에서 가져온 것 **`int`** **`long`** 입니다. 따라서 컴파일러가 일치하는 개체 형식을 위한 변환을 고려합니다(`UDC`). 가로 변환 **`int`** 되 고 선택 됩니다.

일치하는 인수를 처리하는 동안 인수 및 사용자 정의 변환 결과 모두에 표준 변환을 적용할 수 있습니다. 따라서 다음 코드가 작동합니다.

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

앞의 예제에서 사용자 정의 변환 **연산자 long** 은 형식으로 변환 하기 위해 호출 됩니다 `udc` **`long`** . 형식에 대 한 사용자 정의 변환이 정의 되지 않은 경우 **`long`** 변환은 다음과 같이 진행 됩니다. 형식이 `UDC` **`int`** 사용자 정의 변환을 사용 하 여 형식으로 변환 되었습니다. 그런 다음 형식에서 형식으로의 표준 변환이 **`int`** **`long`** 선언에 있는 인수와 일치 하도록 적용 되었습니다.

인수와 일치 하는 사용자 정의 변환이 필요한 경우 가장 일치 하는 항목을 평가할 때 표준 변환이 사용 되지 않습니다. 둘 이상의 후보 함수에 사용자 정의 변환이 필요한 경우에도 함수는 동일한 것으로 간주 됩니다. 예를 들어:

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

두 버전의 모두 `Func` 형식을 클래스 형식 인수로 변환 하려면 사용자 정의 변환이 필요 **`int`** 합니다. 가능한 변환은 다음과 같습니다.

- 형식에서 **`int`** 형식으로 변환 `UDC1` 합니다 (사용자 정의 변환).

- 형식에서 **`int`** 형식으로 변환한 **`long`** 다음 형식으로 변환 `UDC2` 합니다 (2 단계 변환).

두 번째 경우에도 표준 변환과 사용자 정의 변환이 모두 필요 하지만 두 변환은 동일 하 게 간주 됩니다.

> [!NOTE]
> 사용자 정의 변환은 생성 또는 초기화(함수 변환)에 의한 변환으로 간주됩니다. 두 메서드가 최상의 일치일 경우 동일하다고 간주됩니다.

## <a name="argument-matching-and-the-this-pointer"></a>인수 일치 및 this 포인터

클래스 멤버 함수는로 선언 되었는지 여부에 따라 다르게 처리 됩니다 **`static`** . 비정적 함수에는 포인터를 제공 하는 암시적 인수가 있으므로 **`this`** 비정적 함수는 정적 함수 보다 하나 이상의 인수를 포함 하는 것으로 간주 됩니다. 그렇지 않으면 동일 하 게 선언 됩니다.

이러한 비정적 멤버 함수는 **`this`** 함수가 호출 되는 개체 유형과 일치 하는 포인터가 필요 합니다. 또는 오버 로드 된 연산자의 경우 첫 번째 인수가 연산자가 적용 되는 개체와 일치 해야 합니다. 오버 로드 된 연산자에 대 한 자세한 내용은 [오버 로드 된 연산자](../cpp/operator-overloading.md)를 참조 하세요.

오버 로드 된 함수의 다른 인수와 달리 임시 개체는 도입 되지 않으며 포인터 인수와 일치 하려고 할 때 변환이 시도 되지 않습니다 **`this`** .

`->`멤버 선택 연산자를 사용 하 여 클래스의 멤버 함수에 액세스 하는 경우 `class_name` **`this`** 포인터 인수의 형식은 `class_name * const` 입니다. 멤버가 또는로 선언 된 경우 **`const`** **`volatile`** 형식은 `const class_name * const` `volatile class_name * const` 각각 및입니다.

명시적 `.` 주소 연산자가 개체 이름 앞에 추가된다는 점을 제외하면 `&` 멤버 선택 연산자는 동일하게 작동합니다. 다음 예제에서는 그 작동 방식을 보여 줍니다.

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

`->*`의 왼쪽 피연산자와 `.*`(멤버에 대한 포인터) 연산자는 인수 일치와 관련하여 `.` 및 `->`(멤버 선택) 연산자와 동일한 방식으로 처리됩니다.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a> 참조-멤버 함수의 한정자

Ref 한정자를 사용 하면가 가리키는 개체가 rvalue 인지 또는 lvalue 인지를 기준으로 멤버 함수를 오버 로드할 수 있습니다 **`this`** .  이 기능을 사용 하면 데이터에 대 한 포인터 액세스를 제공 하지 않도록 선택 하는 시나리오에서 불필요 한 복사 작업을 방지할 수 있습니다. 예를 들어 클래스에서 `C` 생성자의 일부 데이터를 초기화 하 고 멤버 함수에서 해당 데이터의 복사본을 반환 한다고 가정 합니다 `get_data()` . 형식의 개체가 소멸 되려고 하는 rvalue 인 경우 `C` 컴파일러는 데이터를 복사 하는 `get_data() &&` 대신 이동 하는 오버 로드를 선택 합니다.

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>오버 로드에 대 한 제한 사항

여러 제한은 사용할 수 있는 오버로드된 함수 집합을 관리합니다.

- 오버로드된 함수 집합의 임의의 두 함수에는 서로 다른 인수 목록이 있어야 합니다.

- 반환 형식을 기준으로 동일한 형식의 인수 목록을 가진 함수를 오버 로드하면 오류가 발생합니다.

     **Microsoft 전용**

지정 된 메모리 모델 한정자의 기반이 되는 반환 형식에 대해서만 **new 연산자** 를 오버 로드할 수 있습니다.

**Microsoft 전용 종료**

- 멤버 함수는 정적 함수 및 다른 비정적 항목의 기준 으로만 오버 로드 될 수 없습니다.

- **`typedef`** 선언은 새 형식을 정의 하지 않습니다. 기존 형식에 대 한 동의어를 소개 합니다. 오버 로드 메커니즘에는 영향을 주지 않습니다. 다음 코드를 생각해 봅시다.

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   위의 두 함수에는 동일한 인수 목록이 있습니다. `PSTR` 는 형식의 동의어입니다 `char *` . 멤버 범위에서 이 코드를 사용하면 오류가 발생합니다.

- 열거 형식은 고유한 형식이며 오버로드된 함수 사이를 구분하는 데 사용할 수 있습니다.

- "Array of" 및 "pointer to" 형식은 오버 로드 된 함수를 구별 하기 위해 동일한 것으로 간주 되지만 단일 차원이 사용 되는 배열에 대해서만 동일 하 게 간주 됩니다. 이러한 오버 로드 된 함수는 충돌 하 고 오류 메시지를 생성 합니다.

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   다차원 배열의 경우 둘째 및 이후의 모든 차원은 형식의 일부로 간주됩니다. 따라서 이들은 오버로드된 함수를 구별하는 데 사용됩니다.

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>오버 로드, 재정의 및 숨기기

동일한 범위에서 동일한 이름의 두 함수 선언은 같은 함수 또는 오버로드된 두 개별 함수를 참조할 수 있습니다. 선언의 인수 목록에 동일한 형식의 인수가 포함되어 있으면(이전 단원 참조) 함수 선언은 같은 함수를 참조하고, 그렇지 않으면 오버로드를 사용하여 선택된 서로 다른 두 함수를 참조합니다.

클래스 범위는 엄격 하 게 관찰 됩니다. 따라서 기본 클래스에서 선언 된 함수는 파생 클래스에 선언 된 함수와 같은 범위에 있지 않습니다. 파생 클래스의 함수가 기본 클래스의 가상 함수와 동일한 이름으로 선언 된 경우 파생 클래스 함수는 기본 클래스 함수를 *재정의* 합니다. 자세한 내용은 [가상 함수](../cpp/virtual-functions.md)를 참조 하세요.

기본 클래스 함수가 ' 가상 '으로 선언 되지 않은 경우 파생 클래스 함수에서이를 *숨깁니다* . 재정의와 숨기기는 오버 로드와는 다릅니다.

블록 범위는 엄격 하 게 관찰 됩니다. 따라서 파일 범위에서 선언 된 함수는 로컬로 선언 된 함수와 같은 범위에 있지 않습니다. 로컬로 선언된 함수의 이름이 파일 범위에서 선언된 함수의 이름과 같을 경우 로컬로 선언된 함수는 오버로드를 유발하는 대신 파일 범위의 함수를 숨깁니다. 예를 들어:

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

위의 코드에서는 `func` 함수의 두 정의를 보여 줍니다. 형식의 인수를 사용 하는 정의는 `char *` 문 때문에 로컬입니다 `main` **`extern`** . 따라서 형식의 인수를 사용 하는 정의는 **`int`** 숨겨져 있으며에 대 한 첫 번째 호출에서는 `func` 오류가 발생 합니다.

오버로드된 멤버 함수의 경우 함수의 버전마다 서로 다른 액세스 권한을 부여할 수 있습니다. 이러한 함수는 여전히 바깥쪽 클래스의 범위에 있는 것으로 간주되므로 오버로드된 함수입니다. 멤버 함수 `Deposit`가 오버로드되는 다음 코드를 살펴보겠습니다. 한 버전은 public이고 다른 버전은 private입니다.

이 샘플의 목적은 입금을 하려면 올바른 암호가 필요한 `Account` 클래스를 제공하는 것입니다. 오버 로드를 사용 하 여 수행 됩니다.

에서에 대 한 호출은 `Deposit` `Account::Deposit` 전용 멤버 함수를 호출 합니다. `Account::Deposit`가 멤버 함수 이며 클래스의 private 멤버에 액세스할 수 있기 때문에이 호출은 올바릅니다.

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>참고 항목

[함수 (c + +)](../cpp/functions-cpp.md)
