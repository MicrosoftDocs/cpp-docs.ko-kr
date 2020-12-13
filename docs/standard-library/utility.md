---
description: '자세히 알아보기: &lt; 유틸리티&gt;'
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 67472492acdb0ddbc1de957a69c01b1aafaf9367
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153436"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

두 개체를 하나인 것처럼 처리해야 할 때 유용한 개체 쌍을 생성 및 관리하는 데 도움이 되는 C++ 표준 라이브러리 형식, 함수 및 연산자를 정의합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<utility>

**네임스페이스:** std

## <a name="remarks"></a>설명

쌍은 C++ 표준 라이브러리에서 널리 사용됩니다. 쌍은 다양한 함수에 대한 인수 및 반환 값으로 필요하며, [map class](../standard-library/map-class.md) 및 [multimap class](../standard-library/multimap-class.md) 등의 컨테이너에 대한 요소 형식으로도 필요합니다. 헤더는의 \<utility> \<map> 키/값 쌍 형식 요소 관리를 지원 하기 위해에 자동으로 포함 됩니다.

> [!NOTE]
> \<utility>헤더는 문을 사용 합니다 `#include <initializer_list>` . 또한 `class tuple` 에 정의 된 것 처럼를 참조 \<tuple> 합니다.

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|형식|설명|
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|기본 숫자 변환을 위한 부동 소수점 형식입니다.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|`pair` 요소의 형식을 래핑하는 클래스입니다.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|`pair` 요소 수를 래핑하는 클래스입니다.|

### <a name="objects"></a>개체

|템플릿|설명|
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)|가 인 일반적인 경우에 대해 정의 된 별칭 템플릿 `T``std::size_t`  |
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)|모든 형식 매개 변수 팩을 동일한 길이의 인덱스 시퀀스로 변환 하는 도우미 별칭 템플릿|
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)| 형식 만들기를 간소화 하는 도우미 별칭 템플릿입니다 `std::index_sequence` . |
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)|형식 만들기를 간소화 하는 도우미 별칭 템플릿입니다 `std::integer_sequence` .|

### <a name="functions"></a>Functions

|함수|설명|
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|형식을 반환 합니다.|
|[declval](../standard-library/utility-functions.md#declval)|줄임 식 계산입니다.|
|[교환의](../standard-library/utility-functions.md#exchange)|개체에 새 값을 할당 하 고 이전 값을 반환 합니다.|
|[전환](../standard-library/utility-functions.md#forward)|완벽한 전달에 의해 가려지지 않도록 인수의 참조 형식(`lvalue` 또는 `rvalue` 중 하나)을 유지합니다.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|`pair` 개체에서 요소를 가져오는 함수입니다.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|`pair` 형식의 개체를 생성하는 데 사용되는 템플릿 도우미 함수입니다. 여기서 구성 요소 형식은 매개 변수로 전달된 데이터 형식을 기반으로 합니다.|
|[move](../standard-library/utility-functions.md#move)|전달된 인수를 `rvalue` 참조로 반환합니다.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[스왑을](../standard-library/utility-functions.md#swap)|두 `pair` 개체의 요소를 교환합니다.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|값을 문자열로 변환 합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자! =](../standard-library/utility-operators.md#op_neq)|연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체와 같지 않은지 테스트합니다.|
|[연산자 = =](../standard-library/utility-operators.md#op_eq_eq)|연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체와 같은지 테스트합니다.|
|[연산자\<](../standard-library/utility-operators.md#op_lt)|연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 작은지 테스트합니다.|
|[연산자\<=](../standard-library/utility-operators.md#op_gt_eq)|연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 작은지 테스트합니다.|
|[연산자>](../standard-library/utility-operators.md#op_gt)|연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 큰지 테스트합니다.|
|[연산자>=](../standard-library/utility-operators.md#op_gt_eq)|연산자의 좌변에 있는 pair 개체가 우변에 있는 pair 개체보다 크거나 같은지 테스트합니다.|

### <a name="structs"></a>구조체

|구조체|Description|
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|에 사용 되는 구조체 `from_chars` 입니다.|
|[identity](../standard-library/identity-structure.md)|형식 정의를 템플릿 매개 변수로 제공하는 구조체입니다.|
|[in_place_t](../standard-library/in-place-t-struct.md)|에는 구조체 및도 포함 됩니다 `in_place_type_t` `in_place_index_t` .|
|[integer_sequence](../standard-library/integer-sequence-class.md)|정수 시퀀스를 나타냅니다.|
|[큰따옴표](../standard-library/pair-structure.md)|두 개체를 단일 개체로 처리하는 기능을 제공하는 형식입니다.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|별도의 생성자와 함수 오버 로드를 유지 하는 데 사용 되는 형식입니다.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|에 사용 되는 구조체 `to_chars` 입니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
