---
title: '&lt;string_view&gt;'
description: 의 개요는 `basic_string_view` char와 유사한 개체의 일정 한 연속 시퀀스를 참조 합니다.
ms.date: 9/4/2020
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: f74f6c5855f71b0df46f585e874002cdb4308e42
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039913"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

클래스 템플릿과 `basic_string_view` 관련 형식 및 연산자를 정의 합니다. 컴파일러 옵션 [std: c + + 17](../build/reference/std-specify-language-standard-version.md) 이상이 필요 합니다.

## <a name="syntax"></a>구문

```cpp
#include <string_view>
```

## <a name="remarks"></a>설명

`string_view`템플릿 특수화의 패밀리는 위치 0에 있는 시퀀스의 첫 번째 요소를 사용 하 여 문자열 형식 개체의 문자 데이터에 대 한 읽기 전용, 예외 안전, 소유 하지 않는 핸들을 전달 하는 효율적인 방법을 제공 합니다. 형식의 함수 매개 변수 `string_view` (에 대 한 typedef)는 `basic_string_view<char>` `std::string` , `char*` 또는에 대 한 암시적 변환이 정의 되는 기타 모든 문자열 유사 문자 클래스와 같은 인수를 사용할 수 있습니다 `string_view` . 마찬가지로, 또는의 매개 변수는 `wstring_view` `u16string_view` `u32string_view` 암시적 변환이 정의 된 모든 문자열 형식을 허용할 수 있습니다. 자세한 내용은 [Basic_string_view 클래스](../standard-library/basic-string-view-class.md)를 참조 하세요.

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|`basic_string_view`형식의 요소를 포함 하는 클래스 템플릿의 특수화입니다 **`char`** .|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|`basic_string_view`형식의 요소를 포함 하는 클래스 템플릿의 특수화입니다 **`wchar_t`** .|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|`basic_string_view`형식의 요소를 포함 하는 클래스 템플릿의 특수화입니다 **`char16_t`** .|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|`basic_string_view`형식의 요소를 포함 하는 클래스 템플릿의 특수화입니다 **`char32_t`** .|

### <a name="operators"></a>연산자

\<string_view>연산자는 `string_view` 개체를 변환할 수 있는 문자열 형식의 개체와 비교할 수 있습니다.

|연산자|Description|
|-|-|
|[연산자! =](../standard-library/string-view-operators.md#op_neq)|연산자의 좌변에 있는 개체가 우변에 있는 개체와 같지 않은지 테스트합니다.|
|[연산자 = =](../standard-library/string-view-operators.md#op_eq_eq)|연산자의 좌변에 있는 개체가 우변에 있는 개체와 같은지 테스트합니다.|
|[연산자<](../standard-library/string-view-operators.md#op_lt)|연산자의 좌 변에 있는 개체가 우변에 있는 개체 보다 작음을 테스트 합니다.|
|[연산자<=](../standard-library/string-view-operators.md#op_lt_eq)|연산자의 좌변에 있는 개체가 우변에 있는 개체보다 작거나 같은지 테스트합니다.|
|[연산자<\<](../standard-library/string-view-operators.md#op_lt_lt)|를 출력 스트림에 삽입 하는 템플릿 함수 `string_view` 입니다.|
|[연산자>](../standard-library/string-view-operators.md#op_gt)|연산자의 좌 변에 있는 개체가 우변에 있는 개체 보다 큰지 테스트 합니다.|
|[연산자>=](../standard-library/string-view-operators.md#op_gt_eq)|연산자의 좌변에 있는 개체가 우변에 있는 개체보다 크거나 같은지 테스트합니다.|

### <a name="literals"></a>리터럴

|연산자|Description|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|`string_view` `wstring_view` `u16string_view` `u32string_view` 추가 되는 문자열 리터럴의 형식에 따라,, 또는를 생성 합니다.|

### <a name="classes"></a>클래스

|클래스|Description|
|-|-|
|[basic_string_view 클래스](../standard-library/basic-string-view-class.md)|임의의 문자 형식 개체 시퀀스에 읽기 전용 뷰를 제공 하는 클래스 템플릿입니다.|
|[hash](string-view-hash.md)|String_view에 대 한 해시 값을 생성 하는 함수 개체입니다.|

## <a name="requirements"></a>요구 사항

- **헤더:**\<string_view>

- **네임스페이스:** std

- **컴파일러 옵션:** [std: c + + 17](../build/reference/std-specify-language-standard-version.md) 이상

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
