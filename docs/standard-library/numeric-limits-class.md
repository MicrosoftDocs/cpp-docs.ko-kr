---
title: numeric_limits 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- limits/std::numeric_limits
- limits/std::numeric_limits::denorm_min
- limits/std::numeric_limits::digits
- limits/std::numeric_limits::digits10
- limits/std::numeric_limits::epsilon
- limits/std::numeric_limits::has_denorm
- limits/std::numeric_limits::has_denorm_loss
- limits/std::numeric_limits::has_infinity
- limits/std::numeric_limits::has_quiet_NaN
- limits/std::numeric_limits::has_signaling_NaN
- limits/std::numeric_limits::infinity
- limits/std::numeric_limits::is_bounded
- limits/std::numeric_limits::is_exact
- limits/std::numeric_limits::is_iec559
- limits/std::numeric_limits::is_integer
- limits/std::numeric_limits::is_modulo
- limits/std::numeric_limits::is_signed
- limits/std::numeric_limits::is_specialized
- limits/std::numeric_limits::lowest
- limits/std::numeric_limits::max
- limits/std::numeric_limits::max_digits10
- limits/std::numeric_limits::max_exponent
- limits/std::numeric_limits::max_exponent10
- limits/std::numeric_limits::min
- limits/std::numeric_limits::min_exponent
- limits/std::numeric_limits::min_exponent10
- limits/std::numeric_limits::quiet_NaN
- limits/std::numeric_limits::radix
- limits/std::numeric_limits::round_error
- limits/std::numeric_limits::round_style
- limits/std::numeric_limits::signaling_NaN
- limits/std::numeric_limits::tinyness_before
- limits/std::numeric_limits::traps
dev_langs:
- C++
helpviewer_keywords:
- std::numeric_limits [C++]
- std::numeric_limits [C++], denorm_min
- std::numeric_limits [C++], digits
- std::numeric_limits [C++], digits10
- std::numeric_limits [C++], epsilon
- std::numeric_limits [C++], has_denorm
- std::numeric_limits [C++], has_denorm_loss
- std::numeric_limits [C++], has_infinity
- std::numeric_limits [C++], has_quiet_NaN
- std::numeric_limits [C++], has_signaling_NaN
- std::numeric_limits [C++], infinity
- std::numeric_limits [C++], is_bounded
- std::numeric_limits [C++], is_exact
- std::numeric_limits [C++], is_iec559
- std::numeric_limits [C++], is_integer
- std::numeric_limits [C++], is_modulo
- std::numeric_limits [C++], is_signed
- std::numeric_limits [C++], is_specialized
- std::numeric_limits [C++], lowest
- std::numeric_limits [C++], max
- std::numeric_limits [C++], max_digits10
- std::numeric_limits [C++], max_exponent
- std::numeric_limits [C++], max_exponent10
- std::numeric_limits [C++], min
- std::numeric_limits [C++], min_exponent
- std::numeric_limits [C++], min_exponent10
- std::numeric_limits [C++], quiet_NaN
- std::numeric_limits [C++], radix
- std::numeric_limits [C++], round_error
- std::numeric_limits [C++], round_style
- std::numeric_limits [C++], signaling_NaN
- std::numeric_limits [C++], tinyness_before
- std::numeric_limits [C++], traps
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f40635e3a3c4c00aa98a36ebddcdb5a29c2a66ab
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705928"
---
# <a name="numericlimits-class"></a>numeric_limits 클래스

이 템플릿 클래스는 기본 제공 숫자 형식의 산술 속성을 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type>
class numeric_limits
```

### <a name="parameters"></a>매개 변수

*Type*<br/>
속성이 테스트, 쿼리 또는 설정되는 기본 요소 데이터 형식입니다.

## <a name="remarks"></a>설명

형식에 대 한 명시적 특수화를 정의 하는 헤더 **wchar_t**, **bool**를 **char**를 **char 서명**, **부호 없는 char**, **짧은**를 **unsigned short**를 **int**를 **부호 없는 int**, **장기**, **부호 없는 long**를 **float**를 **double**를 **long double**, **long long**하십시오 **부호 없는 long long**, **char16_t**, 및 **char32_t**. 이러한 명시적 특수화의 경우 멤버에 대 한 [numeric_limits:: is_specialized](#is_specialized) 됩니다 **true**, 및 모든 관련 멤버에 의미 있는 값입니다. 프로그램에서 추가 명시적 특수화를 제공할 수 있습니다. 클래스의 대다수 멤버 함수에 설명 하거나 테스트의 가능한 구현을 **float**합니다.

임의 특수화의 경우 멤버에 의미 있는 값이 없습니다. 0을 저장 하는 의미 있는 값이 없는 멤버 개체 (또는 **false**)는 의미 있는 값을 반환 하지 않는 멤버 함수가 반환 하 고 `Type(0)`입니다.

### <a name="static-functions-and-constants"></a>정적 함수 및 상수

|||
|-|-|
|[denorm_min](#denorm_min)|0이 아닌 가장 작은 비정규화된 값을 반환합니다.|
|[digits](#digits)|정밀도의 손실 없이 형식이 나타낼 수 있는 기수 자릿수를 반환합니다.|
|[digits10](#digits10)|정밀도의 손실 없이 형식이 나타낼 수 있는 10진수 자릿수를 반환합니다.|
|[epsilon](#epsilon)|1과 데이터 형식이 나타낼 수 있는 1보다 큰 가장 작은 값 사이의 차이를 반환합니다.|
|[has_denorm](#has_denorm)|형식이 비정규화된 값을 허용하는지 테스트합니다.|
|[has_denorm_loss](#has_denorm_loss)|정밀도 손실이 부정확한 결과가 아니라 비정규화 손실로 검색되는지 테스트합니다.|
|[has_infinity](#has_infinity)|형식에 양의 무한대 표현이 있는지 테스트합니다.|
|[has_quiet_NaN](#has_quiet_nan)|형식에 신호를 보내지 않는 자동 NAN(숫자가 아님) 표현이 있는지 테스트합니다.|
|[has_signaling_NaN](#has_signaling_nan)|형식에 신호를 보내는 NAN(숫자가 아님) 표현이 있는지 테스트합니다.|
|[infinity](#infinity)|형식에 대한 양의 무한대 표현(사용 가능한 경우)입니다.|
|[is_bounded](#is_bounded)|형식이 나타낼 수 있는 값 집합이 유한한지 테스트합니다.|
|[is_exact](#is_exact)|형식에서 수행되는 계산에 반올림 오류가 없는지 테스트합니다.|
|[is_iec559](#is_iec559)|형식이 IEC 559 표준을 준수하는지 테스트합니다.|
|[is_integer](#is_integer)|형식이 정수 표현인지 테스트합니다.|
|[is_modulo](#is_modulo)|형식에 모듈로 표현이 있는지 테스트합니다.|
|[is_signed](#is_signed)|형식에 부호 있는 표현이 있는지 테스트합니다.|
|[is_specialized](#is_specialized)|형식에 템플릿 클래스 `numeric_limits`에 정의된 명시적 특수화가 있는지 테스트합니다.|
|[lowest](#lowest)|최대한의 음의 무한대 값을 반환합니다.|
|[max](#max)|형식에 대한 유한 최대값을 반환합니다.|
|[max_digits10](#max_digits10)|형식의 두 고유 값에 고유 10진수 표현이 있는지 확인하는 데 필요한 10진수 자릿수를 반환합니다.|
|[max_exponent](#max_exponent)|밑수 기수에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 양의 정수 지수를 반환합니다.|
|[max_exponent10](#max_exponent10)|밑수 10에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 양의 정수 지수를 반환합니다.|
|[분](#min)|형식에 대한 정규화된 최소값을 반환합니다.|
|[min_exponent](#min_exponent)|밑수 기수에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 음의 정수 지수를 반환합니다.|
|[min_exponent10](#min_exponent10)|밑수 10에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 음의 정수 지수를 반환합니다.|
|[quiet_NaN](#quiet_nan)|형식에 대한 자동 NAN(숫자가 아님) 표현을 반환합니다.|
|[radix](#radix)|형식 표현에 사용되는 정수 밑수(기수라고도 함)를 반환합니다.|
|[round_error](#round_error)|형식에 대한 최대 반올림 오차를 반환합니다.|
|[round_style](#round_style)|구현에서 부동 소수점 값을 정수 값으로 반올림하기 위해 선택할 수 있는 다양한 메서드를 설명하는 값을 반환합니다.|
|[signaling_NaN](#signaling_nan)|형식에 대한 신호를 보내는 NAN(숫자가 아님) 표현을 반환합니다.|
|[tinyness_before](#tinyness_before)|값이 너무 작아서 반올림하기 전에 정규화된 값으로 나타낼 수 없음을 형식이 확인할 수 있는지 테스트합니다.|
|[traps](#traps)|산술 예외를 보고하는 트래핑이 형식에 대해 구현되었는지 테스트합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<limits>

**네임스페이스:** std

## <a name="denorm_min"></a>  numeric_limits::denorm_min

0이 아닌 가장 작은 비정규화된 값을 반환합니다.

```cpp
static constexpr Type denorm_min() throw();
```

### <a name="return-value"></a>반환 값

0이 아닌 가장 작은 비정규화된 값입니다.

### <a name="remarks"></a>설명

**long double** 같습니다 **double** c + + 컴파일러.

동일한 형식에 대 한 최소값을 반환 하는 함수도 [min](#min) 경우 [has_denorm](#has_denorm) 같지 않은 `denorm_present`합니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_denorm_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The smallest nonzero denormalized value\n for float "
        << "objects is: " << numeric_limits<float>::denorm_min( )
        << endl;
   cout << "The smallest nonzero denormalized value\n for double "
        << "objects is: " << numeric_limits<double>::denorm_min( )
        << endl;
   cout << "The smallest nonzero denormalized value\n for long double "
        << "objects is: " << numeric_limits<long double>::denorm_min( )
        << endl;

   // A smaller value will round to zero
   cout << numeric_limits<float>::denorm_min( )/2 <<endl;
   cout << numeric_limits<double>::denorm_min( )/2 <<endl;
   cout << numeric_limits<long double>::denorm_min( )/2 <<endl;
}
```

```Output
The smallest nonzero denormalized value
 for float objects is: 1.4013e-045
The smallest nonzero denormalized value
 for double objects is: 4.94066e-324
The smallest nonzero denormalized value
 for long double objects is: 4.94066e-324
0
0
0
```

## <a name="digits"></a>  numeric_limits::digits

정밀도의 손실 없이 형식이 나타낼 수 있는 기수 자릿수를 반환합니다.

```cpp
static constexpr int digits = 0;
```

### <a name="return-value"></a>반환 값

정밀도의 손실 없이 형식이 나타낼 수 있는 기수 자릿수입니다.

### <a name="remarks"></a>설명

구성원은 형식이 변경 없이 나타낼 수 있는 기수 자릿수를 저장합니다. 이 자릿수는 미리 정의된 정수 형식의 경우 부호 비트를 제외한 비트의 수이고, 미리 정의된 부동 소수점 형식의 경우에는 가수의 자릿수입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_digits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits <<endl;
   cout << numeric_limits<double>::digits <<endl;
   cout << numeric_limits<long double>::digits <<endl;
   cout << numeric_limits<int>::digits <<endl;
   cout << numeric_limits<__int64>::digits <<endl;
}
```

```Output
24
53
53
31
63
```

## <a name="digits10"></a>  numeric_limits::digits10

정밀도의 손실 없이 형식이 나타낼 수 있는 10진수 자릿수를 반환합니다.

```cpp
static constexpr int digits10 = 0;
```

### <a name="return-value"></a>반환 값

정밀도의 손실 없이 형식이 나타낼 수 있는 10진수 자릿수입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_digits10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits10 <<endl;
   cout << numeric_limits<double>::digits10 <<endl;
   cout << numeric_limits<long double>::digits10 <<endl;
   cout << numeric_limits<int>::digits10 <<endl;
   cout << numeric_limits<__int64>::digits10 <<endl;
   float f = (float)99999999;
   cout.precision ( 10 );
   cout << "The float is; " << f << endl;
}
```

```Output
6
15
15
9
18
The float is; 100000000
```

## <a name="epsilon"></a>  numeric_limits::epsilon

함수는 1과 데이터 형식에 대해 나타낼 수 있는 1보다 큰 가장 작은 값 사이의 차이를 반환합니다.

```cpp
static constexpr Type epsilon() throw();
```

### <a name="return-value"></a>반환 값

1과 데이터 형식에 대해 나타낼 수 있는 1보다 큰 가장 작은 값 사이의 차이입니다.

### <a name="remarks"></a>설명

**float** 형식의 경우 값은 FLT_EPSILON입니다. 형식의 `epsilon`은 *N* + `epsilon` + *N*을 나타낼 수 있도록 하는 최소 양수 부동 소수점 숫자 *N*입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_epsilon.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The difference between 1 and the smallest "
        << "value greater than 1\n for float objects is: "
        << numeric_limits<float>::epsilon( )
        << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1\n for double objects is: "
        << numeric_limits<double>::epsilon( )
        << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1\n for long double objects is: "
        << numeric_limits<long double>::epsilon( )
        << endl;
}
```

```Output
The difference between 1 and the smallest value greater than 1
 for float objects is: 1.19209e-007
The difference between 1 and the smallest value greater than 1
 for double objects is: 2.22045e-016
The difference between 1 and the smallest value greater than 1
 for long double objects is: 2.22045e-016
```

## <a name="has_denorm"></a>  numeric_limits::has_denorm

형식이 비정규화된 값을 허용하는지 테스트합니다.

```cpp
static constexpr float_denorm_style has_denorm = denorm_absent;
```

### <a name="return-value"></a>반환 값

형식이 비정규화된 값을 허용하는지를 나타내는 **const**`float_denorm_style` 형식의 열거형 값입니다.

### <a name="remarks"></a>설명

멤버 저장소 `denorm_present` 에 비 정규화 하는 부동 소수점 형식 값을 효과적으로 다양 한 지 수 비트에 대 한 합니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_has_denorm.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects allow denormalized values: "
        << numeric_limits<float>::has_denorm
        << endl;
   cout << "Whether double objects allow denormalized values: "
        << numeric_limits<double>::has_denorm
        << endl;
   cout << "Whether long int objects allow denormalized values: "
        << numeric_limits<long int>::has_denorm
        << endl;
}
```

```Output
Whether float objects allow denormalized values: 1
Whether double objects allow denormalized values: 1
Whether long int objects allow denormalized values: 0
```

## <a name="has_denorm_loss"></a>  numeric_limits::has_denorm_loss

정밀도 손실이 부정확한 결과가 아니라 비정규화 손실로 검색되는지 테스트합니다.

```cpp
static constexpr bool has_denorm_loss = false;
```

### <a name="return-value"></a>반환 값

정밀도 손실이 비정규화 손실로 검색되면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

구성원은 값이 정규화된 값으로 나타내기에는 너무 작아서 비정규화된 결과로 전송되었거나 부정확하여(지수 범위와 정밀도의 제한이 적용되지 않은 결과와 동일하지 않음) 정확도가 손실되었는지를 결정하는 형식의 경우 true를 저장합니다. 이는 일부 결과에 영향을 줄 수 있는 IEC 559 부동 소수점 표현에서 사용 가능한 옵션입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_has_denorm_loss.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects can detect denormalized loss: "
        << numeric_limits<float>::has_denorm_loss
        << endl;
   cout << "Whether double objects can detect denormalized loss: "
        << numeric_limits<double>::has_denorm_loss
        << endl;
   cout << "Whether long int objects can detect denormalized loss: "
        << numeric_limits<long int>::has_denorm_loss
        << endl;
}
```

```Output
Whether float objects can detect denormalized loss: 1
Whether double objects can detect denormalized loss: 1
Whether long int objects can detect denormalized loss: 0
```

## <a name="has_infinity"></a>  numeric_limits::has_infinity

형식에 양의 무한대 표현이 있는지 테스트합니다.

```cpp
static constexpr bool has_infinity = false;
```

### <a name="return-value"></a>반환 값

형식에 양의 무한대 표현이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

구성원은 [is_iec559](#is_iec559)가 **true**이면 **true**를 반환합니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_has_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have infinity: "
        << numeric_limits<float>::has_infinity
        << endl;
   cout << "Whether double objects have infinity: "
        << numeric_limits<double>::has_infinity
        << endl;
   cout << "Whether long int objects have infinity: "
        << numeric_limits<long int>::has_infinity
        << endl;
}
```

```Output
Whether float objects have infinity: 1
Whether double objects have infinity: 1
Whether long int objects have infinity: 0
```

## <a name="has_quiet_nan"></a>  numeric_limits::has_quiet_NaN

형식에 신호를 보내지 않는 자동 NAN(숫자가 아님) 표현이 있는지 테스트합니다.

```cpp
static constexpr bool has_quiet_NaN = false;
```

### <a name="return-value"></a>반환 값

**형식**에 자동 NAN의 표현이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

자동 NAN은 식에 포함되어 있다는 신호를 보내지 않는 숫자가 아닌 항목에 대한 인코딩입니다. [is_iec559](#is_iec559)가 true이면 반환 값은 **true**입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_has_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have quiet_NaN: "
        << numeric_limits<float>::has_quiet_NaN
        << endl;
   cout << "Whether double objects have quiet_NaN: "
        << numeric_limits<double>::has_quiet_NaN
        << endl;
   cout << "Whether long int objects have quiet_NaN: "
        << numeric_limits<long int>::has_quiet_NaN
        << endl;
}
```

```Output
Whether float objects have quiet_NaN: 1
Whether double objects have quiet_NaN: 1
Whether long int objects have quiet_NaN: 0
```

## <a name="has_signaling_nan"></a>  numeric_limits::has_signaling_NaN

형식에 신호를 보내는 NAN(숫자가 아님) 표현이 있는지 테스트합니다.

```cpp
static constexpr bool has_signaling_NaN = false;
```

### <a name="return-value"></a>반환 값

형식에 신호를 보내는 NAN 표현이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

신호 NAN은 식에 포함되어 있다는 신호를 보내는 숫자가 아닌 항목에 대한 인코딩입니다. [is_iec559](#is_iec559)가 true이면 반환 값은 **true**입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_has_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signaling_NaN: "
        << numeric_limits<float>::has_signaling_NaN
        << endl;
   cout << "Whether double objects have a signaling_NaN: "
        << numeric_limits<double>::has_signaling_NaN
        << endl;
   cout << "Whether long int objects have a signaling_NaN: "
        << numeric_limits<long int>::has_signaling_NaN
        << endl;
}
```

```Output
Whether float objects have a signaling_NaN: 1
Whether double objects have a signaling_NaN: 1
Whether long int objects have a signaling_NaN: 0
```

## <a name="infinity"></a>  numeric_limits::infinity

형식의 양의 무한대 표현(사용 가능한 경우)입니다.

```cpp
static constexpr Type infinity() throw();
```

### <a name="return-value"></a>반환 값

형식의 양의 무한대 표현(사용 가능한 경우)입니다.

### <a name="remarks"></a>설명

반환 값은 [has_infinity](#has_infinity)가 **true**인 경우에만 의미가 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::has_infinity <<endl;
   cout << numeric_limits<double>::has_infinity<<endl;
   cout << numeric_limits<long double>::has_infinity <<endl;
   cout << numeric_limits<int>::has_infinity <<endl;
   cout << numeric_limits<__int64>::has_infinity <<endl;

   cout << "The representation of infinity for type float is: "
        << numeric_limits<float>::infinity( ) <<endl;
   cout << "The representation of infinity for type double is: "
        << numeric_limits<double>::infinity( ) <<endl;
   cout << "The representation of infinity for type long double is: "
        << numeric_limits<long double>::infinity( ) <<endl;
}
```

```Output
1
1
1
0
0
The representation of infinity for type float is: inf
The representation of infinity for type double is: inf
The representation of infinity for type long double is: inf
```

## <a name="is_bounded"></a>  numeric_limits::is_bounded

형식이 나타낼 수 있는 값 집합이 유한한지 테스트합니다.

```cpp
static constexpr bool is_bounded = false;
```

### <a name="return-value"></a>반환 값

형식에 경계가 지정된 나타낼 수 있는 값 집합이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

모든 미리 정의된 형식은 경계가 지정된 표현 가능한 값 집합을 포함하므로 **true**를 반환합니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_bounded.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have bounded set "
        << "of representable values: "
        << numeric_limits<float>::is_bounded
        << endl;
   cout << "Whether double objects have bounded set "
        << "of representable values: "
        << numeric_limits<double>::is_bounded
        << endl;
   cout << "Whether long int objects have bounded set "
        << "of representable values: "
        << numeric_limits<long int>::is_bounded
        << endl;
   cout << "Whether unsigned char objects have bounded set "
        << "of representable values: "
        << numeric_limits<unsigned char>::is_bounded
        << endl;
}
```

```Output
Whether float objects have bounded set of representable values: 1
Whether double objects have bounded set of representable values: 1
Whether long int objects have bounded set of representable values: 1
Whether unsigned char objects have bounded set of representable values: 1
```

## <a name="is_exact"></a>  numeric_limits::is_exact

형식에서 수행되는 계산에 반올림 오류가 없는지 테스트합니다.

```cpp
static constexpr bool is_exact = false;
```

### <a name="return-value"></a>반환 값

계산에 반올림 오류가 없으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

모든 미리 정의된 정수 형식은 값에 대한 정확한 표현을 포함하므로 **false**를 반환합니다. 고정 소수점 또는 유리수 표현도 정확한 표현으로 간주하지만 부동 소수점 표현은 정확한 표현으로 간주하지 않습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_exact.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<float>::is_exact
        << endl;
   cout << "Whether double objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<double>::is_exact
        << endl;
   cout << "Whether long int objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<long int>::is_exact
        << endl;
   cout << "Whether unsigned char objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<unsigned char>::is_exact
        << endl;
}
```

```Output
Whether float objects have calculations free of rounding errors: 0
Whether double objects have calculations free of rounding errors: 0
Whether long int objects have calculations free of rounding errors: 1
Whether unsigned char objects have calculations free of rounding errors: 1
```

## <a name="is_iec559"></a>  numeric_limits::is_iec559

형식이 IEC 559 표준을 준수하는지 테스트합니다.

```cpp
static constexpr bool is_iec559 = false;
```

### <a name="return-value"></a>반환 값

형식이 IEC 559 표준을 준수하면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

IEC 559는 부동 소수점 값을 나타내기 위한 국제 표준으로, 미국에서는 IEEE 754라고도 합니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_iec559.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects conform to iec559 standards: "
        << numeric_limits<float>::is_iec559
        << endl;
   cout << "Whether double objects conform to iec559 standards: "
        << numeric_limits<double>::is_iec559
        << endl;
   cout << "Whether int objects conform to iec559 standards: "
        << numeric_limits<int>::is_iec559
        << endl;
   cout << "Whether unsigned char objects conform to iec559 standards: "
        << numeric_limits<unsigned char>::is_iec559
        << endl;
}
```

```Output
Whether float objects conform to iec559 standards: 1
Whether double objects conform to iec559 standards: 1
Whether int objects conform to iec559 standards: 0
Whether unsigned char objects conform to iec559 standards: 0
```

## <a name="is_integer"></a>  numeric_limits::is_integer

형식이 정수 표현인지 테스트합니다.

```cpp
static constexpr bool is_integer = false;
```

### <a name="return-value"></a>반환 값

형식에 정수 표현이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

미리 정의된 모든 정수 형식에는 정수 표현이 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_integer.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an integral representation: "
        << numeric_limits<float>::is_integer
        << endl;
   cout << "Whether double objects have an integral representation: "
        << numeric_limits<double>::is_integer
        << endl;
   cout << "Whether int objects have an integral representation: "
        << numeric_limits<int>::is_integer
        << endl;
   cout << "Whether unsigned char objects have an integral representation: "
        << numeric_limits<unsigned char>::is_integer
        << endl;
}
```

```Output
Whether float objects have an integral representation: 0
Whether double objects have an integral representation: 0
Whether int objects have an integral representation: 1
Whether unsigned char objects have an integral representation: 1
```

## <a name="is_modulo"></a>  numeric_limits::is_modulo

**type**에 모듈로 표현이 있는지 테스트합니다.

```cpp
static constexpr bool is_modulo = false;
```

### <a name="return-value"></a>반환 값

형식에 모듈로 표현이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

모듈로 표현은 모든 결과가 일부 모듈로 값으로 감소하는 표현입니다. 미리 정의된 모든 부호 없는 정수 형식에는 모듈로 표현이 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_modulo.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a modulo representation: "
        << numeric_limits<float>::is_modulo
        << endl;
   cout << "Whether double objects have a modulo representation: "
        << numeric_limits<double>::is_modulo
        << endl;
   cout << "Whether signed char objects have a modulo representation: "
        << numeric_limits<signed char>::is_modulo
        << endl;
   cout << "Whether unsigned char objects have a modulo representation: "
        << numeric_limits<unsigned char>::is_modulo
        << endl;
}
```

```Output
Whether float objects have a modulo representation: 0
Whether double objects have a modulo representation: 0
Whether signed char objects have a modulo representation: 1
Whether unsigned char objects have a modulo representation: 1
```

## <a name="is_signed"></a>  numeric_limits::is_signed

형식에 부호 있는 표현이 있는지 테스트합니다.

```cpp
static constexpr bool is_signed = false;
```

### <a name="return-value"></a>반환 값

형식에 부호 있는 표현이 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

구성원은 부호 있는 표현이 있는 형식에 대해 true를 저장합니다. 미리 정의된 모든 부동 소수점 및 부호 있는 정수 형식의 경우 true가 저장됩니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_signaled.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signed representation: "
        << numeric_limits<float>::is_signed
        << endl;
   cout << "Whether double objects have a signed representation: "
        << numeric_limits<double>::is_signed
        << endl;
   cout << "Whether signed char objects have a signed representation: "
        << numeric_limits<signed char>::is_signed
        << endl;
   cout << "Whether unsigned char objects have a signed representation: "
        << numeric_limits<unsigned char>::is_signed
        << endl;
}
```

```Output
Whether float objects have a signed representation: 1
Whether double objects have a signed representation: 1
Whether signed char objects have a signed representation: 1
Whether unsigned char objects have a signed representation: 0
```

## <a name="is_specialized"></a>  numeric_limits::is_specialized

형식에 템플릿 클래스 `numeric_limits`에 정의된 명시적 특수화가 있는지 테스트합니다.

```cpp
static constexpr bool is_specialized = false;
```

### <a name="return-value"></a>반환 값

형식의 템플릿 클래스에 명시적 특수화가 정의되어 있으면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

포인터를 제외한 모든 스칼라 형식에는 템플릿 클래스 `numeric_limits`에 대해 명시적 특수화가 정의되어 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_is_specialized.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float>::is_specialized
        << endl;
   cout << "Whether float* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float*>::is_specialized
        << endl;
   cout << "Whether int objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int>::is_specialized
        << endl;
   cout << "Whether int* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int*>::is_specialized
        << endl;
}
```

```Output
Whether float objects have an explicit specialization in the class: 1
Whether float* objects have an explicit specialization in the class: 0
Whether int objects have an explicit specialization in the class: 1
Whether int* objects have an explicit specialization in the class: 0
```

## <a name="lowest"></a>  numeric_limits::lowest

최대한의 음의 무한대 값을 반환합니다.

```cpp
static constexpr Type lowest() throw();
```

### <a name="return-value"></a>반환 값

최대한의 음의 무한대 값을 반환합니다.

### <a name="remarks"></a>설명

형식에 대해 최대한의 음의 무한대 값을 반환 (일반적으로 `min()` 정수 형식에 대 한 및 `-max()` 부동 소수점 형식에 대 한). 반환 값은 의미 있는 경우 `is_bounded` 됩니다 **true**합니다.

## <a name="max"></a>  numeric_limits::max

형식에 대한 유한 최대값을 반환합니다.

```cpp
static constexpr Type max() throw();
```

### <a name="return-value"></a>반환 값

형식에 대한 유한 최대값입니다.

### <a name="remarks"></a>설명

형식에 대 한 유한 최대값이 int_max 인 **int** 및 형식에 대 한 FLT_MAX **float**합니다. 반환 값은 [is_bounded](#is_bounded)가 **true**인 경우 의미가 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_max.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main() {
   cout << "The maximum value for type float is:  "
        << numeric_limits<float>::max( )
        << endl;
   cout << "The maximum value for type double is:  "
        << numeric_limits<double>::max( )
        << endl;
   cout << "The maximum value for type int is:  "
        << numeric_limits<int>::max( )
        << endl;
   cout << "The maximum value for type short int is:  "
        << numeric_limits<short int>::max( )
        << endl;
}
```

## <a name="max_digits10"></a>  numeric_limits::max_digits10

형식의 두 고유 값에 고유 10진수 표현이 있는지 확인하는 데 필요한 10진수 자릿수를 반환합니다.

```cpp
static constexpr int max_digits10 = 0;
```

### <a name="return-value"></a>반환 값

형식의 두 고유 값에 고유 10진수 표현이 있는지 확인하는 데 필요한 10진수 자릿수를 반환합니다.

### <a name="remarks"></a>설명

멤버는 형식의 두 고유 값에 고유 10진수 표현이 있는지 확인하는 데 필요한 10진수 자릿수를 저장합니다.

## <a name="max_exponent"></a>  numeric_limits::max_exponent

밑수 기수에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 양의 정수 지수를 반환합니다.

```cpp
static constexpr int max_exponent = 0;
```

### <a name="return-value"></a>반환 값

형식으로 표현할 수 있는 최대 정수 계열 기수 기반 지수입니다.

### <a name="remarks"></a>설명

구성원 함수 반환 값은 부동 소수점 형식에만 의미가 있습니다. `max_exponent`는 **float** 형식의 경우 값 FLT_MAX_EXP입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_max_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum radix-based exponent for type float is:  "
        << numeric_limits<float>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type double is:  "
        << numeric_limits<double>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type long double is:  "
        << numeric_limits<long double>::max_exponent
        << endl;
}
```

```Output
The maximum radix-based exponent for type float is:  128
The maximum radix-based exponent for type double is:  1024
The maximum radix-based exponent for type long double is:  1024
```

## <a name="max_exponent10"></a>  numeric_limits::max_exponent10

밑수 10에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 양의 정수 지수를 반환합니다.

```cpp
static constexpr int max_exponent10 = 0;
```

### <a name="return-value"></a>반환 값

형식으로 표현할 수 있는 최대 정수 계열 상용 지수입니다.

### <a name="remarks"></a>설명

구성원 함수 반환 값은 부동 소수점 형식에만 의미가 있습니다. `max_exponent`는 **float** 형식의 경우 값 FLT_MAX_10입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_max_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum base 10 exponent for type float is:  "
           << numeric_limits<float>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type double is:  "
           << numeric_limits<double>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type long double is:  "
           << numeric_limits<long double>::max_exponent10
           << endl;
}
```

```Output
The maximum base 10 exponent for type float is:  38
The maximum base 10 exponent for type double is:  308
The maximum base 10 exponent for type long double is:  308
```

## <a name="min"></a>  numeric_limits::min

형식에 대한 정규화된 최소값을 반환합니다.

```cpp
static constexpr Type min() throw();
```

### <a name="return-value"></a>반환 값

형식에 대한 정규화된 최소값입니다.

### <a name="remarks"></a>설명

정규화 된 최소값 형식 INT_MIN입니다 **int** 및 형식의 경우 FLT_MIN입니다 **float**합니다. 반환 값은 의미 있는 경우 [is_bounded](#is_bounded) 됩니다 **true** 이거나 [is_signed](#is_signed) 는 **false**합니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum value for type float is:  "
        << numeric_limits<float>::min( )
        << endl;
   cout << "The minimum value for type double is:  "
        << numeric_limits<double>::min( )
        << endl;
   cout << "The minimum value for type int is:  "
        << numeric_limits<int>::min( )
        << endl;
   cout << "The minimum value for type short int is:  "
        << numeric_limits<short int>::min( )
        << endl;
}
```

```Output
The minimum value for type float is:  1.17549e-038
The minimum value for type double is:  2.22507e-308
The minimum value for type int is:  -2147483648
The minimum value for type short int is:  -32768
```

## <a name="min_exponent"></a>  numeric_limits::min_exponent

밑수 기수에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 음의 정수 지수를 반환합니다.

```cpp
static constexpr int min_exponent = 0;
```

### <a name="return-value"></a>반환 값

형식으로 표현할 수 있는 최소 정수 계열 기수 기반 지수입니다.

### <a name="remarks"></a>설명

구성원 함수는 부동 소수점 형식에만 의미가 있습니다. `min_exponent`는 **float** 형식의 경우 값 FLT_MIN_EXP입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_min_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum radix-based exponent for type float is:  "
        << numeric_limits<float>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type double is:  "
        << numeric_limits<double>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type long double is:  "
         << numeric_limits<long double>::min_exponent
        << endl;
}
```

```Output
The minimum radix-based exponent for type float is:  -125
The minimum radix-based exponent for type double is:  -1021
The minimum radix-based exponent for type long double is:  -1021
```

## <a name="min_exponent10"></a>  numeric_limits::min_exponent10

밑수 10에 대한 해당 거듭제곱을 계산할 때 부동 소수점 형식이 유한 값으로 나타낼 수 있는 최대 음의 정수 지수를 반환합니다.

```cpp
static constexpr int min_exponent10 = 0;
```

### <a name="return-value"></a>반환 값

형식으로 표현할 수 있는 최소 정수 계열 상용 지수입니다.

### <a name="remarks"></a>설명

구성원 함수는 부동 소수점 형식에만 의미가 있습니다. `min_exponent10`는 **float** 형식의 경우 값 FLT_MIN_10입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_min_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum base 10 exponent for type float is:  "
        << numeric_limits<float>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type double is:  "
        << numeric_limits<double>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type long double is:  "
        << numeric_limits<long double>::min_exponent10
        << endl;
}
```

```Output
The minimum base 10 exponent for type float is:  -37
The minimum base 10 exponent for type double is:  -307
The minimum base 10 exponent for type long double is:  -307
```

## <a name="quiet_nan"></a>  numeric_limits::quiet_NaN

형식에 대한 자동 NAN(숫자가 아님) 표현을 반환합니다.

```cpp
static constexpr Type quiet_NaN() throw();
```

### <a name="return-value"></a>반환 값

형식에 대한 자동 NAN 표현입니다.

### <a name="remarks"></a>설명

반환 값은 [has_quiet_NaN](#has_quiet_nan)이 **true**인 경우에만 의미가 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The quiet NaN for type float is:  "
        << numeric_limits<float>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type int is:  "
        << numeric_limits<int>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type long double is:  "
        << numeric_limits<long double>::quiet_NaN( )
        << endl;
}
```

```Output
The quiet NaN for type float is:  1.#QNAN
The quiet NaN for type int is:  0
The quiet NaN for type long double is:  1.#QNAN
```

## <a name="radix"></a>  numeric_limits::radix

형식 표현에 사용되는 정수 밑수(기수라고도 함)를 반환합니다.

```cpp
static constexpr int radix = 0;
```

### <a name="return-value"></a>반환 값

형식의 표현에 대한 정수 계열 밑수입니다.

### <a name="remarks"></a>설명

밑수는 미리 정의된 정수 형식의 경우 2이며 미리 정의된 부동 소수점 형식의 경우 지수가 증가하는 밑수 또는 FLT_RADIX입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_radix.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The base for type float is:  "
        << numeric_limits<float>::radix
        << endl;
   cout << "The base for type int is:  "
        << numeric_limits<int>::radix
        << endl;
   cout << "The base for type long double is:  "
        << numeric_limits<long double>::radix
        << endl;
}
```

```Output
The base for type float is:  2
The base for type int is:  2
The base for type long double is:  2
```

## <a name="round_error"></a>  numeric_limits::round_error

형식에 대한 최대 반올림 오차를 반환합니다.

```cpp
static constexpr Type round_error() throw();
```

### <a name="return-value"></a>반환 값

형식에 대한 최대 반올림 오차입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_round_error.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum rounding error for type float is:  "
        << numeric_limits<float>::round_error( )
        << endl;
   cout << "The maximum rounding error for type int is:  "
        << numeric_limits<int>::round_error( )
        << endl;
   cout << "The maximum rounding error for type long double is:  "
        << numeric_limits<long double>::round_error( )
        << endl;
}
```

```Output
The maximum rounding error for type float is:  0.5
The maximum rounding error for type int is:  0
The maximum rounding error for type long double is:  0.5
```

## <a name="round_style"></a>  numeric_limits::round_style

구현에서 부동 소수점 값을 정수 값으로 반올림하기 위해 선택할 수 있는 다양한 메서드를 설명하는 값을 반환합니다.

```cpp
static constexpr float_round_style round_style = round_toward_zero;
```

### <a name="return-value"></a>반환 값

반올림 스타일을 설명하는 `float_round_style` 열거형의 값입니다.

### <a name="remarks"></a>설명

구성원은 구현에서 부동 소수점 값을 정수값으로 반올림하기 위해 선택할 수 있는 다양한 메서드를 설명하는 값을 저장합니다.

반올림 스타일은 이 구현에 하드 코드되므로 프로그램이 다른 반올림 모드에서 시작되더라도 해당 값은 변경되지 않습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_round_style.cpp
// compile with: /EHsc
#include <iostream>
#include <float.h>
#include <limits>

using namespace std;

int main( )
{
   cout << "The rounding style for a double type is: "
        << numeric_limits<double>::round_style << endl;
   _controlfp_s(NULL,_RC_DOWN,_MCW_RC );
   cout << "The rounding style for a double type is now: "
        << numeric_limits<double>::round_style << endl;
   cout << "The rounding style for an int type is: "
        << numeric_limits<int>::round_style << endl;
}
```

```Output
The rounding style for a double type is: 1
The rounding style for a double type is now: 1
The rounding style for an int type is: 0
```

## <a name="signaling_nan"></a>  numeric_limits::signaling_NaN

형식에 대한 신호를 보내는 NAN(숫자가 아님) 표현을 반환합니다.

```cpp
static constexpr Type signaling_NaN() throw();
```

### <a name="return-value"></a>반환 값

형식에 대한 신호 NAN의 표현입니다.

### <a name="remarks"></a>설명

반환 값은 [has_signaling_NaN](#has_signaling_nan)이 **true**인 경우에만 의미가 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The signaling NaN for type float is:  "
        << numeric_limits<float>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type int is:  "
        << numeric_limits<int>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type long double is:  "
        << numeric_limits<long double>::signaling_NaN( )
        << endl;
}
```

## <a name="tinyness_before"></a>  numeric_limits::tinyness_before

값이 너무 작아서 반올림하기 전에 정규화된 값으로 나타낼 수 없음을 형식이 확인할 수 있는지 테스트합니다.

```cpp
static constexpr bool tinyness_before = false;
```

### <a name="return-value"></a>반환 값

**true** 반올림 전에 형식이 매우 작은 값을 검색할 수 있는 경우 **false** 수 없는 경우.

### <a name="remarks"></a>설명

작은 값을 검색할 수 있는 형식은 IEC 559 부동 소수점 표현을 사용하는 옵션으로 포함되었으며, 해당 구현은 일부 결과에 영향을 줄 수 있습니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_tinyness_before.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types can detect tinyness before rounding: "
        << numeric_limits<float>::tinyness_before
        << endl;
   cout << "Whether double types can detect tinyness before rounding: "
        << numeric_limits<double>::tinyness_before
        << endl;
   cout << "Whether long int types can detect tinyness before rounding: "
        << numeric_limits<long int>::tinyness_before
        << endl;
   cout << "Whether unsigned char types can detect tinyness before rounding: "
        << numeric_limits<unsigned char>::tinyness_before
        << endl;
}
```

```Output
Whether float types can detect tinyness before rounding: 1
Whether double types can detect tinyness before rounding: 1
Whether long int types can detect tinyness before rounding: 0
Whether unsigned char types can detect tinyness before rounding: 0
```

## <a name="traps"></a>  numeric_limits::traps

산술 예외를 보고하는 트래핑이 형식에 대해 구현되었는지 테스트합니다.

```cpp
static constexpr bool traps = false;
```

### <a name="return-value"></a>반환 값

형식에 대해 트래핑이 구현되면 **true**이고 그렇지 않으면 **false**입니다.

### <a name="example"></a>예제

```cpp
// numeric_limits_traps.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types have implemented trapping: "
        << numeric_limits<float>::traps
        << endl;
   cout << "Whether double types have implemented trapping: "
        << numeric_limits<double>::traps
        << endl;
   cout << "Whether long int types have implemented trapping: "
        << numeric_limits<long int>::traps
        << endl;
   cout << "Whether unsigned char types have implemented trapping: "
        << numeric_limits<unsigned char>::traps
        << endl;
}
```

```Output
Whether float types have implemented trapping: 1
Whether double types have implemented trapping: 1
Whether long int types have implemented trapping: 0
Whether unsigned char types have implemented trapping: 0
```

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
