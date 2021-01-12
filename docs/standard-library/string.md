---
description: '자세한 정보: &lt; 문자열&gt;'
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: d0c685eae1bb05faaac55aae614fc10e60472759
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126548"
---
# <a name="ltstringgt"></a>&lt;string&gt;

컨테이너 클래스 템플릿 `basic_string` 및 다양 한 지원 템플릿을 정의 합니다.

`basic_string`에 대한 자세한 내용은 [basic_string 클래스](../standard-library/basic-string-class.md)를 참조하세요.

## <a name="syntax"></a>구문

```cpp
#include <string>
```

## <a name="remarks"></a>설명

C++ 언어와 C++ 표준 라이브러리는 두 가지 문자열 형식을 지원합니다.

- Null로 종료되는 문자 배열은 보통 C 문자열이라고 합니다.

- `basic_string`모든 유사 템플릿 인수를 처리 하는 형식의 클래스 템플릿 개체입니다 **`char`** .

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|`basic_string`형식의 요소를으로 사용 하는 클래스 템플릿의 특수화를 설명 하는 형식입니다 **`char`** `string` .|
|[wstring](../standard-library/string-typedefs.md#wstring)|`basic_string`형식의 요소를으로 사용 하는 클래스 템플릿의 특수화를 설명 하는 형식입니다 **`wchar_t`** `wstring` .|
|[u16string](../standard-library/string-typedefs.md#u16string)|`basic_string`형식의 요소를 기준으로 클래스 템플릿의 특수화를 설명 하는 형식입니다 **`char16_t`** .|
|[u32string](../standard-library/string-typedefs.md#u32string)|`basic_string`형식의 요소를 기준으로 클래스 템플릿의 특수화를 설명 하는 형식입니다 **`char32_t`** .|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 +](../standard-library/string-operators.md#op_add)|두 문자열 개체를 연결합니다.|
|[연산자! =](../standard-library/string-operators.md#op_neq)|연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체와 같지 않은지 테스트합니다.|
|[연산자 = =](../standard-library/string-operators.md#op_eq_eq)|연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체와 같은지 테스트합니다.|
|[연산자<](../standard-library/string-operators.md#op_lt)|연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 작은지 테스트합니다.|
|[연산자<=](../standard-library/string-operators.md#op_lt_eq)|연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 작거나 같은지 테스트합니다.|
|[연산자<\<](../standard-library/string-operators.md#op_lt_lt)|문자열을 출력 스트림에 삽입하는 템플릿 함수입니다.|
|[연산자>](../standard-library/string-operators.md#op_gt)|연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 큰지 테스트합니다.|
|[연산자>=](../standard-library/string-operators.md#op_gt_eq)|연산자의 좌변에 있는 문자열 개체가 우변에 있는 문자열 개체보다 크거나 같은지 테스트합니다.|
|[연산자>>](../standard-library/string-operators.md#op_gt_gt)|입력 스트림에서 문자열을 추출하는 템플릿 함수입니다.|

### <a name="specialized-template-functions"></a>특별 템플릿 함수

|Name|설명|
|-|-|
|`hash`|문자열의 해시를 생성 합니다.|
|[스왑을](../standard-library/string-functions.md#swap)|두 문자열의 문자 배열을 교환합니다.|
|[stod](../standard-library/string-functions.md#stod)|문자 시퀀스를로 변환 **`double`** 합니다.|
|[stof](../standard-library/string-functions.md#stof)|문자 시퀀스를로 변환 **`float`** 합니다.|
|[stoi](../standard-library/string-functions.md#stoi)|문자 시퀀스를 정수로 변환합니다.|
|[stold](../standard-library/string-functions.md#stold)|문자 시퀀스를로 변환 **`long double`** 합니다.|
|[stoll](../standard-library/string-functions.md#stoll)|문자 시퀀스를로 변환 **`long long`** 합니다.|
|[stoul](../standard-library/string-functions.md#stoul)|문자 시퀀스를로 변환 **`unsigned long`** 합니다.|
|[stoull](../standard-library/string-functions.md#stoull)|문자 시퀀스를로 변환 **`unsigned long long`** 합니다.|
|[to_string](../standard-library/string-functions.md#to_string)|값을 `string`로 변환합니다.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|값을 와이드 `string`으로 변환합니다.|

### <a name="functions"></a>Functions

|함수|설명|
|-|-|
|[getline 템플릿](../standard-library/string-functions.md#getline)|입력 스트림에서 문자열을 한 줄씩 추출합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_string 클래스](../standard-library/basic-string-class.md)|임의의 문자 형식 개체 시퀀스를 저장할 수 있는 개체를 설명 하는 클래스 템플릿입니다.|
|[char_traits 구조체](../standard-library/char-traits-struct.md)|CharType 형식의 문자와 연결 된 특성을 설명 하는 클래스 템플릿입니다.|

### <a name="specializations"></a>특수화

|Name|설명|
|-|-|
|[char_traits \<char> 구조체](../standard-library/char-traits-char-struct.md)|`char_traits` \<CharType> 형식의 요소에 대 한 템플릿 구조체의 특수화 인 구조체입니다 **`char`** .|
|[char_traits<wchar_t> 구조체](../standard-library/char-traits-wchar-t-struct.md)|`char_traits` \<CharType> 형식의 요소에 대 한 템플릿 구조체의 특수화 인 구조체입니다 **`wchar_t`** .|
|[char_traits<char16_t> 구조체](../standard-library/char-traits-char16-t-struct.md)|`char_traits` \<CharType> 형식의 요소에 대 한 템플릿 구조체의 특수화 인 구조체입니다 **`char16_t`** .|
|[char_traits<char32_t> 구조체](../standard-library/char-traits-char32-t-struct.md)|`char_traits` \<CharType> 형식의 요소에 대 한 템플릿 구조체의 특수화 인 구조체입니다 **`char32_t`** .|

## <a name="requirements"></a>요구 사항

- **헤더:**\<string>

- **네임스페이스:** std

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
