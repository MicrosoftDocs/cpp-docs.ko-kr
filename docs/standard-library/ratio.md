---
description: '자세히 알아보기: &lt; 비율&gt;'
title: '&lt;ratio&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ratio>
- ratio/std::mega
- ratio/std::peta
- ratio/std::ratio_greater
- ratio/std::micro
- ratio/std::ratio_add
- ratio/std::ratio_not_equal
- ratio/std::hecto
- ratio/std::nano
- ratio/std::ratio_less_equal
- ratio/std::ratio_less
- ratio/std::centi
- ratio/std::ratio_greater_equal
- ratio/std::ratio_subtract
- ratio/std::atto
- ratio/std::tera
- ratio/std::milli
- ratio/std::ratio_multiply
- ratio/std::kilo
- ratio/std::ratio_divide
- ratio/std::giga
- ratio/std::pico
- ratio/std::femto
- ratio/std::ratio_equal
- ratio/std::ratio
- ratio/std::exa
- ratio/std::deci
- ratio/std::deca
ms.assetid: 8543e912-2d84-45ea-b3c0-bd7bfacee405
ms.openlocfilehash: a32a8252347de1e6d7bfd5ffd29927c779ce8489
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126561"
---
# <a name="ltratiogt"></a>&lt;ratio&gt;

\<ratio>컴파일 시간에 유리수를 저장 하 고 조작 하는 데 사용 되는 상수와 템플릿을 정의 하려면 표준 헤더를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
#include <ratio>
```

### <a name="ratio-template"></a>비율 템플릿

```cpp
template<std::intmax_t Numerator, std::intmax_t Denominator = 1>
struct ratio // holds the ratio of Numerator to Denominator
{
   static constexpr std::intmax_t num;
   static constexpr std::intmax_t den;
   typedef ratio<num, den> type;
}
```

이 템플릿에서는 `ratio` `num` `den` `num`  /  `den` = = 분자/분모 및에 `num` 공통 된 `den` 요소가 없는 정적 상수를 정의 합니다. `num` / `den` 는 클래스 템플릿으로 표시 되는 값입니다. 따라서 `type` 는 인스턴스화를 지정 `ratio<num, den>` 합니다.

### <a name="specializations"></a>특수화

\<ratio> 는 다음과 같은 형식의 특수화도 정의 `ratio` 합니다.

`template <class R1, class R2> struct ratio_specialization`

각 특수화에서는 템플릿 매개 변수 두 개를 사용하는데, 이 두 매개 변수 역시 `ratio`의 특수화여야 합니다. `type`의 값은 관련 논리 연산을 통해 결정됩니다.

|Name|`type` 값|
|----------|------------------|
|`ratio_add`|`R1 + R2`|
|`ratio_divide`|`R1 / R2`|
|`ratio_equal`|`R1 == R2`|
|`ratio_greater`|`R1 > R2`|
|`ratio_greater_equal`|`R1 >= R2`|
|`ratio_less`|`R1 < R2`|
|`ratio_less_equal`|`R1 <= R2`|
|`ratio_multiply`|`R1 * R2`|
|`ratio_not_equal`|`!(R1 == R2)`|
|`ratio_subtract`|`R1 - R2`|

### <a name="typedefs"></a>형식 정의

편의를 위해 헤더는 표준 SI 접두사의 비율을 정의 합니다.

```cpp
typedef ratio<1, 1000000000000000000> atto;
typedef ratio<1, 1000000000000000> femto;
typedef ratio<1, 1000000000000> pico;
typedef ratio<1, 1000000000> nano;
typedef ratio<1, 1000000> micro;
typedef ratio<1, 1000> milli;
typedef ratio<1, 100> centi;
typedef ratio<1, 10> deci;
typedef ratio<10, 1> deca;
typedef ratio<100, 1> hecto;
typedef ratio<1000, 1> kilo;
typedef ratio<1000000, 1> mega;
typedef ratio<1000000000, 1> giga;
typedef ratio<1000000000000, 1> tera;
typedef ratio<1000000000000000, 1> peta;
typedef ratio<1000000000000000000, 1> exa;
```

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
