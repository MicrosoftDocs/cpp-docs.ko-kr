---
description: '다음에 대 한 자세한 정보: &lt; system_error&gt;'
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: d2e08957933a6932e1ebb7a8c42214321cb3c406
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126418"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

하위 수준 시스템 오류 처리를 위한 예외 클래스 `system_error` 및 관련 템플릿을 정의하는 헤더 \<system_error>를 포함합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<system_error>

**네임스페이스:** std

## <a name="members"></a>멤버

### <a name="objects"></a>개체

|Name|설명|
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|일반 오류의 범주를 나타냅니다.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|하위 수준 시스템 오버플로로 인해 발생하는 오류의 범주를 나타냅니다.|

### <a name="functions"></a>Functions

|Name|설명|
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|`error_code` 개체를 만듭니다.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|`error_condition` 개체를 만듭니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 = =](../standard-library/system-error-operators.md#op_eq_eq)|연산자의 좌변에 있는 개체가 우변에 있는 개체와 같은지 테스트합니다.|
|[연산자! =](../standard-library/system-error-operators.md#op_neq)|연산자의 좌변에 있는 개체가 우변에 있는 개체와 같지 않은지 테스트합니다.|
|[연산자<](../standard-library/system-error-operators.md#op_lt)|개체가 비교를 위해 전달된 개체보다 작은지 여부를 테스트합니다.|
|[연산자<<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>열거형

|Name|설명|
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|에서 POSIX에 의해 정의 된 모든 오류 코드 매크로에 대해 기호화 된 이름을 제공 `<errno.h>` 합니다.|

### <a name="classes-and-structs"></a>클래스 및 구조체

|Name|설명|
|-|-|
|[error_category](../standard-library/error-category-class.md)|오류 코드 범주를 설명하는 개체에 대한 추상, 공통 기본을 나타냅니다.|
|[error_code](../standard-library/error-code-class.md)|구현에 관련된 하위 수준 시스템 오류를 나타냅니다.|
|[error_condition](../standard-library/error-condition-class.md)|사용자 정의 오류 코드를 나타냅니다.|
|[hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|[error_code 클래스](../standard-library/error-code-class.md) 열거형을 테스트하는 형식 조건자를 나타냅니다.|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|[error_condition 클래스](../standard-library/error-condition-class.md) 열거형을 테스트하는 형식 조건자를 나타냅니다.|
|[system_error](../standard-library/system-error-class.md)|하위 수준 시스템 오버플로를 보고하기 위해 throw되는 모든 예외에 대한 기본 클래스를 나타냅니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
