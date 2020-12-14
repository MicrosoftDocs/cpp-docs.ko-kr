---
description: '자세히 알아보기: &lt; 변형&gt;'
title: '&lt;variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 994bd18a66dd78c8f6042afea10df69ff08a1487
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312474"
---
# <a name="ltvariantgt"></a>&lt;variant&gt;

Variant 개체는 값을 보유 하 고 관리 합니다. 변형에 값이 포함 된 경우 해당 값의 형식은 variant에 제공 된 템플릿 인수 형식 중 하나 여야 합니다. 이러한 템플릿 인수를 대체 항목 이라고 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<variant>

**네임스페이스:** std

## <a name="members"></a>멤버

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 = =](../standard-library/forward-list-operators.md#op_eq_eq)|연산자의 좌 변에 있는 variant 개체가 우변에 있는 variant 개체와 같은지 테스트 합니다.|
|[연산자! =](../standard-library/forward-list-operators.md#op_neq)|연산자의 좌 변에 있는 variant 개체가 우변에 있는 variant 개체와 같지 않은 지 테스트 합니다.|
|[연산자<](../standard-library/forward-list-operators.md#op_lt)|연산자의 좌 변에 있는 variant 개체가 우변에 있는 variant 개체 보다 작음을 테스트 합니다.|
|[연산자<=](../standard-library/forward-list-operators.md#op_lt_eq)|연산자의 좌 변에 있는 variant 개체가 우변에 있는 variant 개체 보다 작거나 같은지 테스트 합니다.|
|[연산자>](../standard-library/forward-list-operators.md#op_gt)|연산자의 좌 변에 있는 variant 개체가 우변에 있는 variant 개체 보다 큰지 테스트 합니다.|
|[연산자>=](../standard-library/forward-list-operators.md#op_lt_eq)|연산자의 좌 변에 있는 variant 개체가 우변에 있는 variant 개체 보다 크거나 같은지 테스트 합니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[get](../standard-library/variant-functions.md#get)|개체의 변형을 가져옵니다.|
|[get_if](../standard-library/variant-functions.md#get_if)|개체의 변형 (있는 경우)을 가져옵니다.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|**`true`** 변형이 있으면를 반환 합니다.|
|[스왑을](../standard-library/variant-functions.md#swap)|**변형을** 바꿉니다.|
|[열어](../standard-library/variant-functions.md#visit)|다음 **variant** 로 이동 합니다.|

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|변형 개체의 값에 대 한 잘못 된 액세스를 보고 하기 위해 throw 되는 개체입니다.|
|[variant](../standard-library/variant.md)|대체 형식 중 하나의 값을 보유 하거나 값을 보유 하지 않는 개체입니다.|

### <a name="structs"></a>구조체

|Name|설명|
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|변형 유형을 기본 생성 가능 하는 변형에 대 한 대체 유형입니다.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|변형 개체를 지원 합니다.|
|[variant_size](../standard-library/variant-size-structure.md)|변형 개체를 지원 합니다.|

### <a name="objects"></a>개체

|Name|설명|
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
