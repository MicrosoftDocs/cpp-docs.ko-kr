---
description: '자세한 정보: 복잡 한 &lt; 부동 소수점&gt;'
title: complex&lt;float&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<float>
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
ms.openlocfilehash: f3efa0425bbf7b6d1df4a6211d549ccf6693fd5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233853"
---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;

지정 된 개체의 순서가 지정 된 쌍을 저장 하는 개체를 설명 합니다 **`float`** . 첫 번째 개체는 복소수의 실수 부분을 나타내고 두 번째 개체는 허수 부분을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <>
class complex<float> {
public:
    constexpr complex(
    float _RealVal = 0,
    float _ImagVal = 0);

constexpr complex(
    const complex<float>& complexNum);

constexpr complex(
    const complex<double>& complexNum);

constexpr complex(
    const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>매개 변수

*_RealVal*\
**`float`** 생성 되는 복소수의 실수 부분에 대 한 형식의 값입니다.

*_ImagVal*\
**`float`** 생성 되는 복소수의 허수 부분에 대 한 형식의 값입니다.

*complexNum*\
**`double`** **`long double`** 생성 되는 형식의 복소수를 초기화 하는 데 사용 되는 실수 및 허수 부분을 포함 하는 형식의 복소수입니다 **`float`** .

## <a name="return-value"></a>반환 값

형식의 복소수입니다 **`float`** .

## <a name="remarks"></a>설명

형식의 복합 클래스에 대 한 클래스 템플릿 복합의 명시적 특수화는 **`float`** 정의 하는 생성자 에서만 클래스 템플릿과 다릅니다. 에서로의 **`float`** 변환은 **`double`** 암시적 일 수 있지만에서로의 안전 하지 **`float`** 않은 변환은 **`long double`** 여야 **`explicit`** 합니다. 를 사용 하면 **`explicit`** 할당 구문을 사용 하는 형식 변환과 함께 시작 됩니다.

클래스 템플릿에 대 한 자세한 내용은 `complex` [complex 클래스](../standard-library/complex-class.md)를 참조 하세요. 클래스 템플릿의 멤버 목록은 `complex` 를 참조 하십시오.

## <a name="example"></a>예제

```cpp
// complex_comp_flt.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <float> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type double
   complex <double> c2double ( 1.0 , 3.0 );
   complex <float> c2float ( c2double );
   cout << "Implicit conversion from type double to type float,"
        << endl << "gives c2float = " << c2float << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 3.0 , 4.0 );
   complex <float> c3float ( c3longdouble );
   cout << "Explicit conversion from type long double to type float,"
        << endl << "gives c3float = " << c3float << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3float);
   double argc3 = arg ( c3float);
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:"
        << endl << "arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type double to type float,
gives c2float = (1,3)
Explicit conversion from type long double to type float,
gives c3float = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*/
```

## <a name="requirements"></a>요구 사항

**헤더**: \<complex>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[복합 클래스](../standard-library/complex-class.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
