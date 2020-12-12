---
description: '다음에 대 한 자세한 정보: &lt; valarray&gt;'
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: 7cc902a60a68f9cb667530dac76812d4a8e082be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168776"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

클래스 템플릿 valarray와 다양 한 지원 클래스 템플릿 및 함수를 정의 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<valarray>

**네임스페이스:** std

> [!NOTE]
> \<valarray>라이브러리는 ' #include <initializer_list> ' 문을 사용 합니다.

## <a name="remarks"></a>설명

이러한 클래스 템플릿 및 함수는 향상 된 성능을 위해 특이 한 위도를 사용할 수 있습니다. 특히 형식을 반환 하는 모든 함수는 `valarray<T1>` 다른 형식 t 2의 개체를 반환할 수 있습니다. 이 경우 형식의 인수를 하나 이상 허용 하는 함수에는 `valarray<T2>` 각각 T2 형식의 인수로 대체 된 인수의 임의 조합을 허용 하는 오버 로드가 있어야 합니다.

## <a name="members"></a>멤버

### <a name="functions"></a>Functions

|Name|설명|
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 절대값과 같은 valarray를 반환합니다.|
|[acos](../standard-library/valarray-functions.md#acos)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 아크코사인과 같은 valarray를 반환합니다.|
|[asin](../standard-library/valarray-functions.md#asin)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 아크사인과 같은 valarray를 반환합니다.|
|[atan](../standard-library/valarray-functions.md#atan)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 아크탄젠트 주요 값과 같은 valarray를 반환합니다.|
|[atan2](../standard-library/valarray-functions.md#atan2)|요소가 valarray의 요소 및 상수 조합에 의해 지정된 데카르트 구성 요소의 아크탄젠트와 같은 valarray를 반환합니다.|
|[시작](../standard-library/valarray-functions.md#begin)||
|[cos](../standard-library/valarray-functions.md#cos)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 코사인과 같은 valarray를 반환합니다.|
|[cosh](../standard-library/valarray-functions.md#cosh)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 쌍곡 코사인과 같은 valarray를 반환합니다.|
|[end](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 자연 지수와 같은 valarray를 반환합니다.|
|[로깅할](../standard-library/valarray-functions.md#log)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 자연 로그와 같은 valarray를 반환합니다.|
|[log10](../standard-library/valarray-functions.md#log10)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 base 10 또는 상용 로그와 같은 valarray를 반환합니다.|
|[pow](../standard-library/valarray-functions.md#pow)|입력 valarray 및 상수의 요소에서 작동하고 요소가 입력 valarray의 요소로 지정된 밑수 또는 입력 valarray 또는 상수의 요소로 지정된 지수의 상수 거듭제곱과 같은 valarray를 반환합니다.|
|[사인](../standard-library/valarray-functions.md#sin)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 사인과 같은 valarray를 반환합니다.|
|[sinh](../standard-library/valarray-functions.md#sinh)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 쌍곡 사인과 같은 valarray를 반환합니다.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 제곱근과 같은 valarray를 반환합니다.|
|[스왑을](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 탄젠트와 같은 valarray를 반환합니다.|
|[tanh](../standard-library/valarray-functions.md#tanh)|입력 valarray의 요소에서 작동하고 요소가 입력 valarray 요소의 쌍곡 탄젠트와 같은 valarray를 반환합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자! =](../standard-library/valarray-operators.md#op_neq)|크기가 같은 두 valarray의 해당 요소가 서로 같지 않은지 또는 valarray의 모든 요소가 valarray 요소 형식의 지정된 값과 같지 않은지 테스트합니다.|
|[연산자](../standard-library/valarray-operators.md#op_mod)|크기가 같은 두 valarray의 해당 요소를 나눈 나머지 또는 valarray를 valarray 요소 형식의 지정된 값으로 나누거나 지정된 값을 valarray로 나눈 나머지를 가져옵니다.|
|[연산자&](../standard-library/valarray-operators.md#op_amp)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 요소 형식의 지정된 값 간에 비트 `AND`을 가져옵니다.|
|[연산자&&](../standard-library/valarray-operators.md#op_amp_amp)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 valarray 요소 형식의 지정된 값 간에 논리적 `AND`을 가져옵니다.|
|[연산자>](../standard-library/valarray-operators.md#op_gt)|한 valarray의 요소가 크기가 같은 valarray의 요소보다 큰지 또는 valarray의 모든 요소가 valarray 요소 형식의 지정된 값보다 크거나 작은지 테스트합니다.|
|[연산자>=](../standard-library/valarray-operators.md#op_gt_eq)|한 valarray의 요소가 크기가 같은 valarray의 요소보다 크거나 같은지 또는 valarray의 모든 요소가 지정된 값보다 크거나 같거나 작거나 같은지 테스트합니다.|
|[연산자>>](../standard-library/valarray-operators.md#op_gt_gt)|valarray의 각 요소에 대한 비트를 지정된 위치 수 또는 두 번째 valarray에 지정된 요소 양만큼 오른쪽으로 이동합니다.|
|[연산자<](../standard-library/valarray-operators.md#op_lt)|한 valarray의 요소가 크기가 같은 valarray의 요소보다 작은지 또는 valarray의 모든 요소가 지정된 값보다 크거나 작은지 테스트합니다.|
|[연산자<=](../standard-library/valarray-operators.md#op_lt_eq)|한 valarray의 요소가 크기가 같은 valarray의 요소보다 작거나 같은지 또는 valarray의 모든 요소가 지정된 값보다 크거나 같거나 작거나 같은지 테스트합니다.|
|[연산자<<](../standard-library/valarray-operators.md#op_lt_lt)|valarray의 각 요소에 대한 비트를 지정된 위치 수 또는 두 번째 valarray에 지정된 요소 양만큼 왼쪽으로 이동합니다.|
|[연산자](../standard-library/valarray-operators.md#op_star)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 valarray 요소 형식의 지정된 값 간에 요소 곱을 가져옵니다.|
|[연산자 +](../standard-library/valarray-operators.md#op_add)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 valarray 요소 형식의 지정된 값 간에 요소 합계를 가져옵니다.|
|[연산자](../standard-library/valarray-operators.md#operator-)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 valarray 요소 형식의 지정된 값 간에 요소 차이를 가져옵니다.|
|[연산자](../standard-library/valarray-operators.md#op_div)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 valarray 요소 형식의 지정된 값 간에 요소 몫을 가져옵니다.|
|[연산자 = =](../standard-library/valarray-operators.md#op_eq_eq)|크기가 같은 두 valarray의 해당 요소가 서로 같은지 또는 valarray의 모든 요소가 valarray 요소 형식의 지정된 값과 같은지 테스트합니다.|
|[operator ^](../standard-library/valarray-operators.md#op_xor)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 요소 형식의 지정된 값 간에 비트 배타적 `OR`을 가져옵니다.|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 요소 형식의 지정된 값 간에 비트 `OR`을 가져옵니다.|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|크기가 같은 두 valarray의 해당 요소 간이나 valarray와 valarray 요소 형식의 지정된 값 간에 논리적 `OR`을 가져옵니다.|

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[gslice 클래스](../standard-library/gslice-class.md)|valarray의 다차원 조각을 정의하는 데 사용되는 valarray에 대한 유틸리티 클래스입니다.|
|[gslice_array 클래스](../standard-library/gslice-array-class.md)|Valarray의 일반 조각으로 정의 된 하위 집합 배열 간의 작업을 제공 하 여 일반 조각 개체를 지 원하는 내부 보조 클래스 템플릿입니다.|
|[indirect_array 클래스](../standard-library/indirect-array-class.md)|부모 valarray의 인덱스 하위 집합을 지정 하 여 정의 된 하위 집합 배열 간의 작업을 제공 하 여 valarray의 하위 집합인 개체를 지 원하는 내부 보조 클래스 템플릿입니다.|
|[mask_array 클래스](../standard-library/mask-array-class.md)|하위 집합 배열 간의 작업을 제공 하 여 부울 식으로 지정 되는 부모 valarrays의 하위 집합인 개체를 지 원하는 내부 보조 클래스 템플릿입니다.|
|[slice 클래스](../standard-library/slice-class.md)|valarray의 벡터와 유사한 1차원 하위 집합을 정의하는 데 사용되는 valarray에 대한 유틸리티 클래스입니다.|
|[slice_array 클래스](../standard-library/slice-array-class.md)|Valarray의 조각으로 정의 된 하위 집합 배열 간의 작업을 제공 하 여 조각 개체를 지 원하는 내부 보조 클래스 템플릿입니다.|
|[valarray 클래스](../standard-library/valarray-class.md)|클래스 템플릿은 배열로 저장 되 고 고속 수치 연산을 수행 하도록 설계 된 형식의 요소 시퀀스를 제어 하는 개체를 설명 `Type` 하며 계산 성능에 최적화 되어 있습니다.|

### <a name="specializations"></a>특수화

|Name|설명|
|-|-|
|[valarray \<bool> 클래스](../standard-library/valarray-bool-class.md)|형식의 요소에 대 한 클래스 템플릿 valarray의 특수화 된 버전입니다 \<**Type**> **`bool`** .|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
