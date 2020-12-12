---
description: '자세한 정보: &lt; 선택 사항&gt;'
title: '&lt;선택 사항&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: c1f1e6f99278abf296c361515953a931109f47ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201835"
---
# <a name="ltoptionalgt"></a>&lt;선택 사항&gt;

컨테이너 클래스 템플릿 `optional` 및 여러 지원 템플릿을 정의 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<optional>

**네임스페이스:** std

## <a name="members"></a>멤버

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 = =](../standard-library/optional-operators.md#op_eq_eq)|개체가 다른 개체와 같은지 여부를 테스트 합니다.|
|[연산자! =](../standard-library/optional-operators.md#op_neq)|개체가 다른 개체와 같지 않은 지 테스트 합니다.|
|[연산자<](../standard-library/optional-operators.md#op_lt)|왼쪽의 개체가 오른쪽에 있는 개체 보다 작음을 테스트 합니다.|
|[연산자<=](../standard-library/optional-operators.md#op_lt_eq)|왼쪽의 개체가 오른쪽에 있는 개체 보다 작거나 같은지 테스트 합니다.|
|[연산자>](../standard-library/optional-operators.md#op_gt)|왼쪽의 개체가 오른쪽에 있는 개체 보다 큰지 테스트 합니다.|
|[연산자>=](../standard-library/optional-operators.md#op_lt_eq)|왼쪽의 개체가 오른쪽에 있는 개체 보다 크거나 같은지 테스트 합니다.|

> [!NOTE]
> 연산자는 관계형 비교 외에 \<optional> 도 **nullopt** 및와의 비교를 지원 `T` 합니다.

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|개체를 선택적으로 만듭니다.|
|[스왑을](../standard-library/optional-functions.md#swap)|두 개체의 포함 된 값을 바꿉니다 `optional` .|

### <a name="classes-and-structs"></a>클래스 및 구조체

|Name|설명|
|-|-|
|hash|포함 된 개체의 해시를 반환 합니다.|
|[선택적 클래스](../standard-library/optional-class.md)|값을 포함 하거나 포함 하지 않을 수 있는 개체에 대해 설명 합니다.|
|[nullopt_t 구조체](../standard-library/nullopt-t-structure.md)|값을 포함 하지 않는 개체에 대해 설명 합니다.|
|[bad_optional_access 클래스](../standard-library/bad-optional-access-class.md)|없는 값에 대 한 액세스 시도를 보고 하기 위해 예외로 throw 되는 개체에 대해 설명 합니다.|

### <a name="objects"></a>개체

|Name|설명|
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|비교할의 인스턴스입니다 `nullopt_t` .|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
