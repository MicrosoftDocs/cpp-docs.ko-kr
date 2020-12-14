---
description: '자세히 알아보기: &lt; long double 복합&gt;'
title: complex&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 5dd3b50c28b889a2e1fafba37cc24fda832f5975
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233827"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

명시적으로 특수화 된이 클래스 템플릿은 형식의 개체를 저장 하는 개체를 설명 하며, **`long double`** 첫 번째 개체는 복소수의 실수 부분을 나타내고 두 번째 개체는 허수 부분을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);

// rest same as class template complex
};
```

### <a name="parameters"></a>매개 변수

*_RealVal*\
**`long double`** 생성 되는 복소수의 실수 부분에 대 한 형식의 값입니다.

*_ImagVal*\
**`long double`** 생성 되는 복소수의 허수 부분에 대 한 형식의 값입니다.

*complexNum*\
**`double`** **`float`** 생성 되는 형식의 복소수를 초기화 하는 데 사용 되는 실수 및 허수 부분을 포함 하는 형식의 복소수입니다 **`long double`** .

## <a name="return-value"></a>반환 값

형식의 복소수입니다 **`long double`** .

## <a name="remarks"></a>설명

형식의 복합 클래스에 대 한 클래스 템플릿의 명시적 특수화는 `complex` **`long double`** 정의 하는 생성자 에서만 클래스 템플릿과 다릅니다. 에서로의 **`long double`** 변환은 **`float`** 암시적 일 수 있지만에서로의 변환은 **`double`** **`long double`** 여야 **`explicit`** 합니다. 를 사용 하면 **`explicit`** 할당 구문을 사용 하는 형식 변환과 함께 시작 됩니다.

클래스 템플릿 및 해당 멤버에 대 한 자세한 내용은 `complex` [complex 클래스](../standard-library/complex-class.md)를 참조 하세요.

**Microsoft 전용**: **`long double`** 및 **`double`** 형식은 동일한 표현을 갖지만 고유 형식입니다. 자세한 내용은 [기본 제공 형식](../cpp/fundamental-types-cpp.md)을 참조 하세요.

## <a name="example"></a>예제

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>요구 사항

**헤더**: \<complex>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[복합 클래스](../standard-library/complex-class.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
