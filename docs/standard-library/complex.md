---
description: '자세히 알아보기: &lt; 복합&gt;'
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: b16798cf1725ba6fa681b04f735d44f02a2b1b82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233840"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

컨테이너 클래스 템플릿 `complex` 및 해당 지원 템플릿을 정의 합니다.

## <a name="requirements"></a>요구 사항

**헤더**: \<complex>

**네임스페이스:** std

## <a name="remarks"></a>설명

복소수는 실수의 순서가 지정된 쌍입니다. 순수하게 기하학적 측면에서 복합 평면은 실제 2차원 평면입니다. 실제 평면과 구분되는 복합 평면의 특성은 추가 대수 구조가 있기 때문입니다. 이 대수 구조에는 두 가지 기본 작업이 있습니다.

- 더하기 (*a*, *b*) + (*c*, *d*) = (*a*  +  *c*, *b*  +  *d*)로 정의

- (*A*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad*  +  *bc*)로 정의 된 곱하기

복합 더하기 및 복합 곱하기 연산이 있는 복소수 집합은 표준 대수 측면에서 필드입니다.

- 더하기 및 곱하기 연산은 누적 및 연결되고, 실수 필드의 실제 더하기 및 곱하기와 마찬가지로 곱하기가 더하기에 배포됩니다.

- 복소수(0, 0)는 덧셈 ID이고 (1, 0)은 곱셈 ID입니다.

- 복소수 (*a*, *b*)의 덧셈 역 수는 (-*a*,-*b*)이 고 (0, 0)을 제외한 이러한 모든 복소수의 곱하기 역 수는입니다.

   (*a/*(*a*<sup>2</sup>  +  *b*<sup>2</sup>),-*b*/(*a*<sup>2</sup>  +  *b*<sup>2</sup>))

A 2 =-1 *형식의 복소수* *z* = (*a*, *b*)를 표시 하 여  =    +  실수 집합 <sup></sup> 의 대 수에 대 한 규칙을 복소수 집합 및 해당 구성 요소에 적용할 수 있습니다. 예를 들어:

   (1 + 2 *i*) \* (2 + 3 *i*) = 1 \* (2 + 3 *i*) + 2 *i* \* (2 + 3 *i*) = (2 + 3 *i*) + (4 *i* + 6 *i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7 *i*

복소수 시스템은 필드이지만 순서가 지정된 필드가 아닙니다. 실수와 해당 하위 집합의 필드에 대 한 복소수 순서를 지정 하지 않으므로 같지 복소수에 적용 될 수 없습니다.

복소수 *z* 를 나타내는 일반적인 형태로는 다음과 같이 세 가지가 있습니다.

- 데카르트: *z*  =  *a*  +  *bi*

- 극좌표 형: *z*  =  *r* (cos *p*  +  *i* sin *p*)

- 지 수: *z*  =  *r* \* *e*<sup>*ip*</sup>

복소수의 이러한 표준 표현에 사용되는 용어는 다음과 같이 참조됩니다.

- 직각좌표 실수 성분 또는 실수부 *a*

- 직각좌표 허수 성분 또는 허수부 *b*

- 복소수 *r* 의 모듈러스 또는 절대값입니다.

- 라디안의 인수 또는 위상 각도 *p* 입니다.

달리 지정 되지 않은 경우 여러 값을 반환할 수 있는 함수는 단일 값으로 유지 하기 위해-π 보다 크고 + π 보다 작거나 같은 인수에 대 한 보안 주체 값을 반환 해야 합니다. 모든 각도는 라디안으로 표현 되어야 합니다. 여기서 2π 라디안 (360도)은 원 안에 있습니다.

## <a name="members"></a>멤버

### <a name="functions"></a>Functions

|Name|설명|
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|복소수의 모듈러스를 계산합니다.|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[인수가](../standard-library/complex-functions.md#arg)|복소수에서 인수를 추출합니다.|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|복소수의 켤레 복소수를 반환합니다.|
|[cos](../standard-library/complex-functions.md#cos)|복소수의 코사인을 반환합니다.|
|[cosh](../standard-library/complex-functions.md#cosh)|복소수의 쌍곡 코사인을 반환합니다.|
|[exp](../standard-library/complex-functions.md#exp)|복소수의 지수 함수를 반환합니다.|
|[imag](../standard-library/complex-functions.md#imag)|복소수의 허수 구성 요소를 추출합니다.|
|[로깅할](../standard-library/complex-functions.md#log)|복소수의 자연 로그를 반환합니다.|
|[log10](../standard-library/complex-functions.md#log10)|복소수의 상용 로그를 반환합니다.|
|[norm](../standard-library/complex-functions.md#norm)|복소수 기준을 추출합니다.|
|[polar](../standard-library/complex-functions.md#polar)|지정한 모듈러스 및 인수에 해당하는 복소수를 데카르트 형태로 반환합니다.|
|[pow](../standard-library/complex-functions.md#pow)|복소수인 밑수를 다른 복소수로 거듭제곱하여 얻은 복소수를 계산합니다.|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|복소수의 실수 구성 요소를 추출합니다.|
|[사인](../standard-library/complex-functions.md#sin)|복소수의 사인을 반환합니다.|
|[sinh](../standard-library/complex-functions.md#sinh)|복소수의 쌍곡 사인을 반환합니다.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|복소수의 제곱근을 반환합니다.|
|[tan](../standard-library/complex-functions.md#tan)|복소수의 탄젠트를 반환합니다.|
|[tanh](../standard-library/complex-functions.md#tanh)|복소수의 쌍곡 탄젠트를 반환합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자! =](../standard-library/complex-operators.md#op_neq)|하나 또는 둘 모두 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 같지 않은지 테스트합니다.|
|[연산자](../standard-library/complex-operators.md#op_star)|하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 곱합니다.|
|[연산자 +](../standard-library/complex-operators.md#op_add)|하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 더합니다.|
|[연산자](../standard-library/complex-operators.md#operator-)|하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 뺍니다.|
|[연산자](../standard-library/complex-operators.md#op_div)|하나 또는 둘 다 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 나눕니다.|
|[연산자<\<](../standard-library/complex-operators.md#op_lt_lt)|출력 스트림에 복소수를 삽입하는 템플릿 함수입니다.|
|[연산자 = =](../standard-library/complex-operators.md#op_eq_eq)|하나 또는 둘 모두 실수 및 허수 부분에서 형식의 일부에 속할 수 있는 두 복소수를 같은지 테스트합니다.|
|[연산자>>](../standard-library/complex-operators.md#op_gt_gt)|입력 스트림에서 복소수를 추출하는 템플릿 함수입니다.|

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[하므로\<double>](../standard-library/complex-double.md)|명시적으로 특수화 된 클래스 템플릿은 형식이 인 개체의 순서가 지정 된 쌍을 저장 하는 개체를 설명 합니다 **`double`** . 여기서 첫 번째 개체는 복소수의 실수 부분을 나타내고 두 번째 개체는 허수 부분을 나타냅니다.|
|[하므로\<float>](../standard-library/complex-float.md)|명시적으로 특수화 된 클래스 템플릿은 형식이 인 개체의 순서가 지정 된 쌍을 저장 하는 개체를 설명 합니다 **`float`** . 여기서 첫 번째 개체는 복소수의 실수 부분을 나타내고 두 번째 개체는 허수 부분을 나타냅니다.|
|[하므로\<long double>](../standard-library/complex-long-double.md)|명시적으로 특수화 된 클래스 템플릿은 형식이 인 개체의 순서가 지정 된 쌍을 저장 하는 개체를 설명 합니다 **`long double`** . 여기서 첫 번째 개체는 복소수의 실수 부분을 나타내고 두 번째 개체는 허수 부분을 나타냅니다.|
|[하므로](../standard-library/complex-class.md)|클래스 템플릿은 복소수 시스템을 나타내고 복잡 한 산술 연산을 수행 하는 데 사용 되는 개체를 설명 합니다.|

### <a name="literals"></a>리터럴

\<complex>헤더는 실수 부분이 0이 고 허수 부분이 입력 매개 변수의 값이 되는 복소수를 만드는 다음 [사용자 정의 리터럴을](../cpp/user-defined-literals-cpp.md) 정의 합니다.

|선언|설명|
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|반환 값: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|`complex<double>{0.0, static_cast<double>(d)}`를 반환합니다.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|`complex<float>{0.0f, static_cast<float>(d)}`를 반환합니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
