---
description: '자세히 알아보기: &lt; 복합 &gt; 연산자'
title: '&lt;complex&gt; operators'
ms.date: 11/04/2016
f1_keywords:
- xcomplex/std::operator!=
- xcomplex/std::operator&gt;&gt;
- xcomplex/std::operator&lt;&lt;
- xcomplex/std::operator*
- xcomplex/std::operator+
- xcomplex/std::operator-
- xcomplex/std::operator/
- xcomplex/std::operator==
ms.assetid: aa282604-dcb9-46a2-bf1d-34c50aa6c4ba
helpviewer_keywords:
- std::operator!= (complex)
- std::operator&gt;&gt; (complex)
- std::operator&lt;&lt; (complex), std::operator== (complex)
ms.openlocfilehash: 88930dbf0b96d42c5c643305b56121cec8a1bacd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325012"
---
# <a name="ltcomplexgt-operators"></a>&lt;complex&gt; operators

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

하나 또는 둘 모두 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 같지 않은지 테스트합니다.

```cpp
template <class Type>
bool operator!=(
    const complex<Type>& left,
    const complex<Type>& right);

template <class Type>
bool operator!=(
    const complex<Type>& left,
    const Type& right);

template <class Type>
bool operator!=(
    const Type& left,
    const complex<Type>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
같지 않은지 테스트할 매개 변수 형식의 복소수 또는 개체입니다.

*오른쪽*\
같지 않은지 테스트할 매개 변수 형식의 복소수 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 숫자가 같지 않으면입니다. **`false`** 숫자가 같으면입니다.

### <a name="remarks"></a>설명

두 복소수는 해당 실수 부분도 같고 해당 허수 부분도 같은 경우에만 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

연산이 오버로드되어 특정 형식으로 데이터를 변환하지 않고 비교 테스트를 실행할 수 있습니다.

### <a name="example"></a>예제

```cpp
// complex_op_NE.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> compared with type complex<double>
   complex <double> cl1 ( polar (3.0, pi / 6 ) );
   complex <double> cr1a ( polar (3.0, pi /6 ) );
   complex <double> cr1b ( polar (2.0, pi / 3 ) );

   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The 1st right-side complex number is cr1a = " << cr1a << endl;
   cout << "The 2nd right-side complex number is cr1b = " << cr1b << endl;
   if ( cl1 != cr1a )
      cout << "The complex numbers cl1 & cr1a are not equal." << endl;
   else
      cout << "The complex numbers cl1 & cr1a are equal." << endl;
   if ( cl1 != cr1b )
      cout << "The complex numbers cl1 & cr1b are not equal." << endl;
   else
      cout << "The complex numbers cl1 & cr1b are equal." << endl;
   cout << endl;

   // Example of the second member function
   // type complex<int> compared with type int
   complex <int> cl2a ( 3, 4 );
   complex <int> cl2b ( 5,0 );
   int cr2a =3;
   int cr2b =5;

   cout << "The 1st left-side complex number is cl2a = " << cl2a << endl;
   cout << "The 1st right-side complex number is cr2a = " << cr2a << endl;
   if ( cl2a != cr2a )
      cout << "The complex numbers cl2a & cr2a are not equal." << endl;
   else
      cout << "The complex numbers cl2a & cr2a are equal." << endl;

   cout << "The 2nd left-side complex number is cl2b = " << cl2b << endl;
   cout << "The 2nd right-side complex number is cr2b = " << cr2b << endl;
   if ( cl2b != cr2b )
      cout << "The complex numbers cl2b & cr2b are not equal." << endl;
   else
      cout << "The complex numbers cl2b & cr2b are equal." << endl;
   cout << endl;

   // Example of the third member function
   // type double compared with type complex<double>
   double cl3a =3;
   double cl3b =5;
   complex <double> cr3a ( 3, 4 );
   complex <double> cr3b ( 5,0 );

   cout << "The 1st left-side complex number is cl3a = " << cl3a << endl;
   cout << "The 1st right-side complex number is cr3a = " << cr3a << endl;
   if ( cl3a != cr3a )
      cout << "The complex numbers cl3a & cr3a are not equal." << endl;
   else
      cout << "The complex numbers cl3a & cr3a are equal." << endl;

   cout << "The 2nd left-side complex number is cl3b = " << cl3b << endl;
   cout << "The 2nd right-side complex number is cr3b = " << cr3b << endl;
   if ( cl3b != cr3b )
      cout << "The complex numbers cl3b & cr3b are not equal." << endl;
   else
      cout << "The complex numbers cl3b & cr3b are equal." << endl;
   cout << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The 1st right-side complex number is cr1a = (2.59808,1.5)
The 2nd right-side complex number is cr1b = (1,1.73205)
The complex numbers cl1 & cr1a are equal.
The complex numbers cl1 & cr1b are not equal.

The 1st left-side complex number is cl2a = (3,4)
The 1st right-side complex number is cr2a = 3
The complex numbers cl2a & cr2a are not equal.
The 2nd left-side complex number is cl2b = (5,0)
The 2nd right-side complex number is cr2b = 5
The complex numbers cl2b & cr2b are equal.

The 1st left-side complex number is cl3a = 3
The 1st right-side complex number is cr3a = (3,4)
The complex numbers cl3a & cr3a are not equal.
The 2nd left-side complex number is cl3b = 5
The 2nd right-side complex number is cr3b = (5,0)
The complex numbers cl3b & cr3b are equal.
```

## <a name="operator"></a><a name="op_star"></a> 연산자\*

하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 곱합니다.

```cpp
template <class Type>
complex<Type> operator*(
    const complex<Type>& left,
    const complex<Type>& right);

template <class Type>
complex<Type> operator*(
    const complex<Type>& left,
    const Type& right);

template <class Type>
complex<Type> operator*(
    const Type& left,
    const complex<Type>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
두 복소수 중 첫 번째 복소수 이거나 연산을 통해 곱할 복소수의 매개 변수 형식에 해당 하는 숫자입니다 \* .

*오른쪽*\
두 복소수 중 두 번째 복소수 이거나 연산을 통해 곱할 복소수의 매개 변수 형식에 해당 하는 숫자입니다 \* .

### <a name="return-value"></a>반환 값

값과 형식이 매개 변수 입력으로 지정되는 두 숫자를 곱한 복소수입니다.

### <a name="remarks"></a>설명

연산이 오버로드되어 특정 형식으로 데이터를 변환하지 않고 단순한 산술 연산을 실행할 수 있습니다.

### <a name="example"></a>예제

```cpp
// complex_op_mult.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> times type complex<double>
   complex <double> cl1 ( polar (3.0, pi / 6 ) );
   complex <double> cr1 ( polar (2.0, pi / 3 ) );
   complex <double> cs1 = cl1 * cr1;

   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;
   cout << "Product of two complex numbers is: cs1 = " << cs1 << endl;
   double abscs1 = abs ( cs1 );
   double argcs1 = arg ( cs1 );
   cout << "The modulus of cs1 is: " << abscs1 << endl;
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "
        << argcs1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> times type double
   complex <double> cl2 ( polar ( 3.0, pi / 6 ) );
   double cr2 =5;
   complex <double> cs2 = cl2 * cr2;

   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;
   cout << "Product of two complex numbers is: cs2 = " << cs2 << endl;
   double abscs2 = abs ( cs2 );
   double argcs2 = arg ( cs2 );
   cout << "The modulus of cs2 is: " << abscs2 << endl;
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "
        << argcs2 * 180 / pi << " degrees." << endl << endl;

   // Example of the third member function
   // type double times type complex<double>
   double cl3 = 5;
   complex <double> cr3 ( polar (3.0, pi / 6 ) );
   complex <double> cs3 = cl3 * cr3;

   cout << "The left-side complex number is cl3 = " << cl3 << endl;
   cout << "The right-side complex number is cr3 = " << cr3 << endl;
   cout << "Product of two complex numbers is: cs3 = " << cs3 << endl;
   double abscs3 = abs ( cs3 );
   double argcs3 = arg ( cs3 );
   cout << "The modulus of cs3 is: " << abscs3 << endl;
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "
        << argcs3 * 180 / pi << " degrees." << endl << endl;
}
```

## <a name="operator"></a><a name="op_add"></a> 연산자 +

하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 더합니다.

```cpp
template <class Type>
complex<Type> operator+(
    const complex<Type>& left,
    const complex<Type>& right);

template <class Type>
complex<Type> operator+(
    const complex<Type>& left,
    const Type& right);

template <class Type>
complex<Type> operator+(
    const Type& left,
    const complex<Type>& right);

template <class Type>
complex<Type> operator+(const complex<Type>& left);
```

### <a name="parameters"></a>매개 변수

*비어*\
두 복소수 중 첫 번째 복소수이거나 + 연산으로 더할 복소수의 매개 변수 형식을 가진 숫자입니다.

*오른쪽*\
두 복소수 중 두 번째 복소수이거나 + 연산으로 더할 복소수의 매개 변수 형식을 가진 숫자입니다.

### <a name="return-value"></a>반환 값

값과 형식이 매개 변수 입력으로 지정되는 두 숫자를 더한 복소수입니다.

### <a name="remarks"></a>설명

연산이 오버로드되어 특정 형식으로 데이터를 변환하지 않고 단순한 산술 연산을 실행할 수 있습니다. 단항 연산자는 *left* 를 반환 합니다.

### <a name="example"></a>예제

```cpp
// complex_op_add.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> plus type complex<double>
   complex <double> cl1 ( 3.0, 4.0 );
   complex <double> cr1 ( 2.0, 5.0 );
   complex <double> cs1 = cl1 + cr1;

   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;
   cout << "The sum of the two complex numbers is: cs1 = " << cs1 << endl;
   double abscs1 = abs ( cs1 );
   double argcs1 = arg ( cs1 );
   cout << "The modulus of cs1 is: " << abscs1 << endl;
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "
        << argcs1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> plus type double
   complex <double> cl2 ( 3.0, 4.0 );
   double cr2 =5.0;
   complex <double> cs2 = cl2 + cr2;

   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;
   cout << "The sum of the two complex numbers is: cs2 = " << cs2 << endl;
   double abscs2 = abs ( cs2 );
   double argcs2 = arg ( cs2 );
   cout << "The modulus of cs2 is: " << abscs2 << endl;
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "
        << argcs2 * 180 / pi << " degrees." << endl << endl;

   // Example of the third member function
   // type double plus type complex<double>
   double cl3 = 5.0;
   complex <double> cr3 ( 3.0, 4.0 );
   complex <double> cs3 = cl3 + cr3;

   cout << "The left-side complex number is cl3 = " << cl3 << endl;
   cout << "The right-side complex number is cr3 = " << cr3 << endl;
   cout << "The sum of the two complex numbers is: cs3 = " << cs3 << endl;
   double abscs3 = abs ( cs3 );
   double argcs3 = arg ( cs3 );
   cout << "The modulus of cs3 is: " << abscs3 << endl;
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "
        << argcs3 * 180 / pi << " degrees." << endl << endl;

   // Example of the fourth member function
   // plus type complex<double>
   complex <double> cr4 ( 3.0, 4.0 );
   complex <double> cs4 = + cr4;

   cout << "The right-side complex number is cr4 = " << cr4 << endl;
   cout << "The result of the unary application of + to the right-side"
        << "\n complex number is: cs4 = " << cs4 << endl;
   double abscs4 = abs ( cs4 );
   double argcs4 = arg ( cs4 );
   cout << "The modulus of cs4 is: " << abscs4 << endl;
   cout << "The argument of cs4 is: "<< argcs4 << " radians, which is "
        << argcs4 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,5)
The sum of the two complex numbers is: cs1 = (5,9)
The modulus of cs1 is: 10.2956
The argument of cs1 is: 1.0637 radians, which is 60.9454 degrees.

The left-side complex number is cl2 = (3,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = (8,4)
The modulus of cs2 is: 8.94427
The argument of cs2 is: 0.463648 radians, which is 26.5651 degrees.

The left-side complex number is cl3 = 5
The right-side complex number is cr3 = (3,4)
The sum of the two complex numbers is: cs3 = (8,4)
The modulus of cs3 is: 8.94427
The argument of cs3 is: 0.463648 radians, which is 26.5651 degrees.

The right-side complex number is cr4 = (3,4)
The result of the unary application of + to the right-side
complex number is: cs4 = (3,4)
The modulus of cs4 is: 5
The argument of cs4 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="operator-"></a><a name="operator-"></a> 연산자

하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 뺍니다.

```cpp
template <class Type>
complex<Type> operator-(
    const complex<Type>& left,
    const complex<Type>& right);

template <class Type>
complex<Type> operator-(
    const complex<Type>& left,
    const Type& right);

template <class Type>
complex<Type> operator-(
    const Type& left,
    const complex<Type>& right);

template <class Type>
complex<Type> operator-(const complex<Type>& left);
```

### <a name="parameters"></a>매개 변수

*비어*\
두 복소수 중 첫 번째 복소수이거나 + 연산으로 뺄 복소수의 매개 변수 형식을 가진 숫자입니다.

*오른쪽*\
두 복소수 중 두 번째 복소수이거나 + 연산으로 뺄 복소수의 매개 변수 형식을 가진 숫자입니다.

### <a name="return-value"></a>반환 값

*왼쪽* 에서 *오른쪽* 의 빼기로 생성 된 복소수입니다. 값이 매개 변수 입력으로 지정 되는 두 숫자입니다.

### <a name="remarks"></a>설명

연산이 오버로드되어 특정 형식으로 데이터를 변환하지 않고 단순한 산술 연산을 실행할 수 있습니다.

단항 연산자는 복소수의 부호를 변경하고, 실수부가 숫자 입력에서 음의 실수부이고 허수부가 숫자 입력에서 음의 허수부인 값을 반환합니다.

### <a name="example"></a>예제

```cpp
// complex_op_sub.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> minus type complex<double>
   complex <double> cl1 ( 3.0, 4.0 );
   complex <double> cr1 ( 2.0, 5.0 );
   complex <double> cs1 = cl1 - cr1;

   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;
   cout << "Difference of two complex numbers is: cs1 = " << cs1 << endl;
   double abscs1 = abs ( cs1 );
   double argcs1 = arg ( cs1 );
   cout << "The modulus of cs1 is: " << abscs1 << endl;
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "
        << argcs1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> minus type double
   complex <double> cl2 ( 3.0, 4.0 );
   double cr2 =5.0;
   complex <double> cs2 = cl2 - cr2;

   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;
   cout << "Difference of two complex numbers is: cs2 = " << cs2 << endl;
   double abscs2 = abs ( cs2 );
   double argcs2 = arg ( cs2 );
   cout << "The modulus of cs2 is: " << abscs2 << endl;
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "
        << argcs2 * 180 / pi << " degrees." << endl << endl;

   // Example of the third member function
   // type double minus type complex<double>
   double cl3 = 5.0;
   complex <double> cr3 ( 3.0, 4.0 );
   complex <double> cs3 = cl3 - cr3;

   cout << "The left-side complex number is cl3 = " << cl3 << endl;
   cout << "The right-side complex number is cr3 = " << cr3 << endl;
   cout << "Difference of two complex numbers is: cs3 = " << cs3 << endl;
   double abscs3 = abs ( cs3 );
   double argcs3 = arg ( cs3 );
   cout << "The modulus of cs3 is: " << abscs3 << endl;
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "
        << argcs3 * 180 / pi << " degrees." << endl << endl;

   // Example of the fourth member function
   // minus type complex<double>
   complex <double> cr4 ( 3.0, 4.0 );
   complex <double> cs4 = - cr4;

   cout << "The right-side complex number is cr4 = " << cr4 << endl;
   cout << "The result of the unary application of - to the right-side"
        << "\n complex number is: cs4 = " << cs4 << endl;
   double abscs4 = abs ( cs4 );
   double argcs4 = arg ( cs4 );
   cout << "The modulus of cs4 is: " << abscs4 << endl;
   cout << "The argument of cs4 is: "<< argcs4 << " radians, which is "
        << argcs4 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,5)
Difference of two complex numbers is: cs1 = (1,-1)
The modulus of cs1 is: 1.41421
The argument of cs1 is: -0.785398 radians, which is -45 degrees.

The left-side complex number is cl2 = (3,4)
The right-side complex number is cr2 = 5
Difference of two complex numbers is: cs2 = (-2,4)
The modulus of cs2 is: 4.47214
The argument of cs2 is: 2.03444 radians, which is 116.565 degrees.

The left-side complex number is cl3 = 5
The right-side complex number is cr3 = (3,4)
Difference of two complex numbers is: cs3 = (2,-4)
The modulus of cs3 is: 4.47214
The argument of cs3 is: -1.10715 radians, which is -63.4349 degrees.

The right-side complex number is cr4 = (3,4)
The result of the unary application of - to the right-side
complex number is: cs4 = (-3,-4)
The modulus of cs4 is: 5
The argument of cs4 is: -2.2143 radians, which is -126.87 degrees.
```

## <a name="operator"></a><a name="op_div"></a> 연산자

하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 나눕니다.

```cpp
template <class Type>
complex<Type> operator*(
    const complex<Type>& left,
    const complex<Type>& right);

template <class Type>
complex<Type> operator*(
    const complex<Type>& left,
    const Type& right);

template <class Type>
complex<Type> operator*(
    const Type& left,
    const complex<Type>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
복소수이거나 / 연산으로 나눌 분모인 복소수의 매개 변수 형식을 가진 숫자입니다.

*오른쪽*\
복소수이거나 / 연산으로 분자를 나누는 데 사용할 분모인 복소수의 매개 변수 형식을 가진 숫자입니다.

### <a name="return-value"></a>반환 값

매개 변수 입력으로 지정되는 값인 분모로 분자를 나눈 복소수입니다.

### <a name="remarks"></a>설명

연산이 오버로드되어 특정 형식으로 데이터를 변환하지 않고 단순한 산술 연산을 실행할 수 있습니다.

### <a name="example"></a>예제

```cpp
// complex_op_div.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex <double> cl1 ( polar ( 3.0, pi / 6 ) );
   complex <double> cr1 ( polar ( 2.0, pi / 3 ) );
   complex <double> cs1 = cl1 / cr1;

   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;
   double abscs1 = abs ( cs1 );
   double argcs1 = arg ( cs1 );
   cout << "The modulus of cs1 is: " << abscs1 << endl;
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "
        << argcs1 * 180 / pi << " degrees." << endl << endl;

   // example of the second member function
   // type complex<double> divided by type double
   complex <double> cl2 ( polar (3.0, pi / 6 ) );
   double cr2 =5;
   complex <double> cs2 = cl2 / cr2;

   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;
   cout << "The quotient of the two complex numbers is: cs2 = cl2 /cr2 = "
        << cs2 << endl;
   double abscs2 = abs ( cs2 );
   double argcs2 = arg ( cs2 );
   cout << "The modulus of cs2 is: " << abscs2 << endl;
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "
        << argcs2 * 180 / pi << " degrees." << endl << endl;

   // Example of the third member function
   // type double divided by type complex<double>
   double cl3 = 5;
   complex <double> cr3 ( polar ( 3.0, pi / 6 ) );
   complex <double> cs3 = cl3 / cr3;

   cout << "The left-side complex number is cl3 = " << cl3 << endl;
   cout << "The right-side complex number is cr3 = " << cr3 << endl;
   cout << "The quotient of the two complex numbers is: cs3 = cl3 /cr2 = "
        << cs3 << endl;
   double abscs3 = abs ( cs3 );
   double argcs3 = arg ( cs3 );
   cout << "The modulus of cs3 is: " << abscs3 << endl;
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "
        << argcs3 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
The modulus of cs1 is: 1.5
The argument of cs1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 = cl2 /cr2 = (0.519615,0.3)
The modulus of cs2 is: 0.6
The argument of cs2 is: 0.523599 radians, which is 30 degrees.

The left-side complex number is cl3 = 5
The right-side complex number is cr3 = (2.59808,1.5)
The quotient of the two complex numbers is: cs3 = cl3 /cr2 = (1.44338,-0.833333)
The modulus of cs3 is: 1.66667
The argument of cs3 is: -0.523599 radians, which is -30 degrees.
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 연산자&lt;&lt;

지정된 복소수를 출력 스트림에 삽입합니다.

```cpp
template <class Type, class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(
    basic_ostream<Elem, Traits>& Ostr,
    const complex<Type>& right);
```

### <a name="parameters"></a>매개 변수

*Ostr*\
복소수를 입력하는 출력 스트림입니다.

*오른쪽*\
출력 스트림에 입력하는 복소수입니다.

### <a name="return-value"></a>반환 값

지정 된 복소수의 값을 데카르트 형식의 *Ostr* 에 씁니다. ( *실수, 허수 부분* )

### <a name="remarks"></a>설명

출력 스트림이 오버로드어 모든 형태의 복소수를 허용하며 기본 출력 형식은 직각좌표 형식입니다.

### <a name="example"></a>예제

```cpp
// complex_op_insert.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   complex <double> c1 ( 3.0, 4.0 );
   cout << "Complex number c1 = " << c1 << endl;

   complex <double> c2  ( polar ( 2.0, pi / 6 ) );
   cout << "Complex number c2 = " << c2 << endl;

   // To display in polar form
   double absc2 = abs ( c2 );
   double argc2 = arg ( c2 );
   cout << "The modulus of c2 is: " << absc2 << endl;
   cout << "The argument of c2 is: "<< argc2 << " radians, which is "
        << argc2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
Complex number c1 = (3,4)
Complex number c2 = (1.73205,1)
The modulus of c2 is: 2
The argument of c2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

하나 또는 둘 모두 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 같은지 테스트합니다.

```cpp
template <class Type>
bool operator==(
    const complex<Type>& left,
    const complex<Type>& right);

template <class Type>
bool operator==(
    const complex<Type>& left,
    const Type& right);

template <class Type>
bool operator==(
    const Type& left,
    const complex<Type>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
같지 않은지 테스트할 매개 변수 형식의 복소수 또는 개체입니다.

*오른쪽*\
같지 않은지 테스트할 매개 변수 형식의 복소수 또는 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 숫자가 같으면이 고, 그렇지 않으면입니다. **`false`** 숫자가 같지 않으면입니다.

### <a name="remarks"></a>설명

두 복소수는 해당 실수 부분도 같고 해당 허수 부분도 같은 경우에만 같은 것입니다. 그렇지 않으면 목록은 같지 않은 것입니다.

연산이 오버로드되어 특정 형식으로 데이터를 변환하지 않고 비교 테스트를 실행할 수 있습니다.

### <a name="example"></a>예제

```cpp
// complex_op_EQ.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> compared with type complex<double>
   complex <double> cl1 ( polar ( 3.0, pi / 6 ) );
   complex <double> cr1a ( polar ( 3.0, pi /6 ) );
   complex <double> cr1b ( polar ( 2.0, pi / 3 ) );

   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The 1st right-side complex number is cr1a = " << cr1a << endl;
   cout << "The 2nd right-side complex number is cr1b = " << cr1b << endl;
   if ( cl1 == cr1a )
      cout << "The complex numbers cl1 & cr1a are equal." << endl;
   else
      cout << "The complex numbers cl1 & cr1a are not equal." << endl;
   if ( cl1 == cr1b )
      cout << "The complex numbers cl1 & cr1b are equal." << endl;
   else
      cout << "The complex numbers cl1 & cr1b are not equal." << endl;
   cout << endl;

   // Example of the second member function
   // type complex<int> compared with type int
   complex <int> cl2a ( 3, 4 );
   complex <int> cl2b ( 5,0 );
   int cr2a =3;
   int cr2b =5;

   cout << "The 1st left-side complex number is cl2a = " << cl2a << endl;
   cout << "The 1st right-side complex number is cr2a = " << cr2a << endl;
   if ( cl2a == cr2a )
      cout << "The complex numbers cl2a & cr2a are equal." << endl;
   else
      cout << "The complex numbers cl2a & cr2a are not equal." << endl;

   cout << "The 2nd left-side complex number is cl2b = " << cl2b << endl;
   cout << "The 2nd right-side complex number is cr2b = " << cr2b << endl;
   if ( cl2b == cr2b )
      cout << "The complex numbers cl2b & cr2b are equal." << endl;
   else
      cout << "The complex numbers cl2b & cr2b are not equal." << endl;
   cout << endl;

   // Example of the third member function
   // type double compared with type complex<double>
   double cl3a =3;
   double cl3b =5;
   complex <double> cr3a (3, 4 );
   complex <double> cr3b (5,0 );

   cout << "The 1st left-side complex number is cl3a = " << cl3a << endl;
   cout << "The 1st right-side complex number is cr3a = " << cr3a << endl;
   if ( cl3a == cr3a )
      cout << "The complex numbers cl3a & cr3a are equal." << endl;
   else
      cout << "The complex numbers cl3a & cr3a are not equal." << endl;

   cout << "The 2nd left-side complex number is cl3b = " << cl3b << endl;
   cout << "The 2nd right-side complex number is cr3b = " << cr3b << endl;
   if ( cl3b == cr3b )
      cout << "The complex numbers cl3b & cr3b are equal." << endl;
   else
      cout << "The complex numbers cl3b & cr3b are not equal." << endl;
   cout << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The 1st right-side complex number is cr1a = (2.59808,1.5)
The 2nd right-side complex number is cr1b = (1,1.73205)
The complex numbers cl1 & cr1a are equal.
The complex numbers cl1 & cr1b are not equal.

The 1st left-side complex number is cl2a = (3,4)
The 1st right-side complex number is cr2a = 3
The complex numbers cl2a & cr2a are not equal.
The 2nd left-side complex number is cl2b = (5,0)
The 2nd right-side complex number is cr2b = 5
The complex numbers cl2b & cr2b are equal.

The 1st left-side complex number is cl3a = 3
The 1st right-side complex number is cr3a = (3,4)
The complex numbers cl3a & cr3a are not equal.
The 2nd left-side complex number is cl3b = 5
The 2nd right-side complex number is cr3b = (5,0)
The complex numbers cl3b & cr3b are equal.
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a> 연산자&gt;&gt;

입력 스트림에서 복소수 값을 추출합니다.

```cpp
template <class Type, class Elem, class Traits>
basic_istream<Elem, Traits>& operator>>(
   basic_istream<Elem, Traits>& Istr,
   complex<Type>& right);
```

### <a name="parameters"></a>매개 변수

*Istr*\
복소수를 추출할 입력 스트림입니다.

*오른쪽*\
입력 스트림에서 추출하는 복소수입니다.

### <a name="return-value"></a>반환 값

*Istr* 에서 지정 된 복소수의 값을 읽어 *오른쪽* 으로 반환 합니다.

### <a name="remarks"></a>설명

유효한 입력 형식은 다음과 같습니다.

- *(실수부, 허수부)*

- *(실수부)*

- *실수부*

### <a name="example"></a>예제

```cpp
// complex_op_extract.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   complex <double> c2;

   cout << "Input a complex number ( try: 2.0 ): ";
   cin >> c2;
   cout << c2 << endl;
}
```

```Output
Input a complex number ( try: 2.0 ): 2.0
2.0
```
