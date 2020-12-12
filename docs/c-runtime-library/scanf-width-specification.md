---
description: '자세히 알아보기: `scanf` 너비 사양'
title: scanf 너비 사양
ms.date: 10/22/2019
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: f4b0e13ef87add74bc802ba11ea6b87d0dfc6b8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284436"
---
# <a name="scanf-width-specification"></a>`scanf` 너비 사양

이 정보는 `scanf_s`와 같은 보안 버전을 비롯하여 함수의 `scanf` 패밀리에서 형식 문자열의 해석에 적용됩니다. 다음 함수는 일반적으로 입력 스트림이 일련의 토큰으로 나뉜다고 가정합니다. 토큰은 공백 (공백, 탭 또는 줄 바꿈)으로 구분 되거나 숫자 형식의 경우 숫자 텍스트로 변환할 수 없는 첫 번째 문자가 나타내는 숫자 데이터 형식의 자연 스러운 끝으로 구분 됩니다. 입력 구문 분석을 토큰의 자연스러운 끝 이전에 중단하는 데 너비 지정을 사용할 수 있습니다.

*너비* 지정은 `%` *너비* 필드 라고 하는 양의 정수를 포함할 수 있는 형식 필드 지정자와 필드의 크기를 나타내는 하나 이상의 문자 (예: 정수 형식이 또는 인지 여부를 나타내는 필드의 형식 한정자로 간주할 수 있음)로 구성 됩니다 **`short`** **`long`** . 이러한 문자를 크기 접두사라고 합니다.

## <a name="the-width-field"></a>너비 필드

*너비* 필드는 해당 필드에 대해 읽을 최대 문자 수를 제어 하는 양의 10 진수 정수입니다. 해당 하는에서 *너비* 문자를 변환 하 고 저장 합니다 `argument` . 공백 문자 또는 지정 된 형식에 따라 변환할 수 없는 문자가 *너비* 에 도달 하기 전에 발생 하는 경우 *너비* 보다 적음을 읽을 수 있습니다.

너비 지정은 이러한 함수의 보안 버전 (예를 들어, 등)에서 요구 하는 버퍼 크기 인수와 별개입니다 `scanf_s` `wscanf_s` . 다음 예에서는 너비가 20으로 지정되어 있습니다. 즉, 입력 스트림에서 최대 20자를 읽습니다. 버퍼 길이는 읽을 수 있는 20자와 null 종결자를 위한 공간을 포함한 21입니다.

```C
char str[21];
scanf_s("%20s", str, 21);
```

*너비* 필드가 사용 되지 않는 경우는 `scanf_s` 전체 토큰을 문자열로 읽으려고 시도 합니다. 지정 된 크기가 전체 토큰을 저장 하기에 충분히 크지 않은 경우 대상 문자열에 아무 것도 쓰여지지 않습니다. *Width* 필드가 지정 된 경우 토큰의 첫 번째 *너비* 문자는 null 종결자와 함께 대상 문자열에 기록 됩니다.

## <a name="the-size-prefix"></a>크기 접두사

선택적 접두사 **h**, **hh**, **l**, **ll**, **I64** 및 **l** 은 `argument` (수정 하는 형식 문자에 따라 long 또는 short, 단일 바이트 문자 또는 와이드 문자)의 크기를 표시 합니다. 이러한 서식 지정 문자는 `scanf` 또는 `wscanf` 함수의 형식 문자와 함께 사용되어 다음 표에 표시된 것처럼 인수의 해석을 지정합니다. **I64** 형식 접두사는 Microsoft 확장 이며 표준 C와 호환 되지 않습니다. 형식 문자 및 해당 의미는 형식 [ `scanf` 필드 문자](../c-runtime-library/scanf-type-field-characters.md)의 "scanf 함수에 대 한 형식 문자" 표에 설명 되어 있습니다.

> [!NOTE]
> 형식의 데이터와 함께 사용 하는 경우 **h**, **l** 및 **l** 접두사는 Microsoft 확장 **`char`** 입니다.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>`scanf`및 `wscanf` 서식 형식 지정자에 대 한 크기 접두사

|지정할 함수|접두사 사용|형식 지정자 사용|
|----------------|----------------|-------------------------|
|**`double`**|**l**|**e**, **E**, **f**, **g** 또는 **G**|
|**`long double`** (와 동일 **`double`** )|**L**|**e**, **E**, **f**, **g** 또는 **G**|
|**`long int`**|**l**|**d**, **i**, **o**, **x** 또는 **X**|
|**`long unsigned int`**|**l**|**u**|
|**`long long`**|**드리겠습니다**|**d**, **i**, **o**, **x** 또는 **X**|
|**`short int`**|**h**|**d**, **i**, **o**, **x** 또는 **X**|
|**`short unsigned int`**|**h**|**u**|
|**`char`**|**hh**|**d**, **i**, **o**, **x** 또는 **X**|
|**`unsigned char`**|**hh**|**u**|
|**`int64`**|**I64**|**d**, **i**, **o**, **u**, **x** 또는 **X**|
|단일 바이트 문자(`scanf` 사용)|**h**|**c** 또는 **c**|
|단일 바이트 문자(`wscanf` 사용)|**h**|**c** 또는 **c**|
|와이드 문자(`scanf` 사용)|**l**|**c** 또는 **c**|
|와이드 문자(`wscanf` 사용)|**l**|**c** 또는 **c**|
|단일 바이트 문자열 (사용) `scanf`|**h**|**s** 또는 **S**|
|단일 바이트 문자열 (사용) `wscanf`|**h**|**s** 또는 **S**|
|을 사용 하는 와이드 문자열 `scanf`|**l**|**s** 또는 **S**|
|을 사용 하는 와이드 문자열 `wscanf`|**l**|**s** 또는 **S**|

다음 예에서는 `scanf_s` 함수 및 `wscanf_s` 함수와 함께 **h** 및 **l** 를 사용합니다.

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

`scanf` 패밀리에 비보안 함수를 사용하는 경우 이전 인수의 버퍼 길이를 나타내는 크기 매개 변수를 생략합니다.

## <a name="reading-undelimited-strings"></a>구분 되지 않은 문자열 읽기

공백 문자로 구분 되지 않는 문자열을 읽으려면 대괄호 ()의 문자 집합이 **`[ ]`** **s** (문자열) 형식 문자를 대체할 수 있습니다. 대괄호 안에 있는 문자 집합을 *제어 문자열* 이라고 합니다. 해당 입력 필드는 제어 문자열에 나타나지 않는 첫 번째 문자까지 읽습니다. 집합의 첫 번째 문자가 캐럿 () 인 경우 **`^`** 효과가 반대가 됩니다. 입력 필드는 문자 집합의 나머지 부분에 표시 되는 첫 번째 문자까지 읽힙니다.

% **[A-z]** 및 **% [z-a]** 는 모두 **% [abcde...z에 해당 하는 것으로 해석 됩니다. z]**. 일반적인 `scanf` 함수 확장 이지만 표준 C에서는 필요 하지 않습니다.

## <a name="reading-unterminated-strings"></a>종결 되지 않은 문자열 읽기

종료 null 문자 (' \ 0 ')를 저장 하지 않고 문자열을 저장 하려면 사양을 사용 합니다 `%Nc` . 여기서 *N* 은 10 진수 정수입니다. 이 경우에 **c** 형식 문자는 인수가 문자 배열에 대한 포인터임을 나타냅니다. 입력 스트림에서 지정 된 위치로 다음 *N 개* 문자를 읽고 null 문자 (' \ 0 ')는 추가 되지 않습니다. *N* 을 지정 하지 않으면 기본값은 1입니다.

## <a name="when-scanf-stops-reading-a-field"></a>`scanf`에서 필드 읽기를 중지 하는 경우

`scanf` 함수는 각 입력 필드를 문자 단위로 검색합니다. 다음과 같은 여러 가지 이유 중 하나로 인해 공백 문자에 도달 하기 전에 특정 입력 필드 읽기를 중지할 수 있습니다.

- 지정된 너비에 도달한 경우

- 지정 된 대로 다음 문자를 변환할 수 없습니다.

- 다음 문자가 일치 해야 하는 컨트롤 문자열의 문자와 충돌 합니다.

- 다음 문자가 지정된 문자 집합에 나타나지 않는 경우

어떤 이유로든 `scanf` 함수가 입력 필드 읽기를 중지한 경우 다음 입력 필드는 읽지 않은 첫 번째 문자에서 시작되는 것으로 간주됩니다. 충돌 하는 문자 (있는 경우)는 읽지 않은 것으로 간주 됩니다. 다음 입력 필드의 첫 번째 문자 또는 입력 스트림에서 후속 읽기 작업의 첫 번째 문자입니다.

## <a name="see-also"></a>참고 항목

[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[형식 사양 필드: `scanf` 및 `wscanf` 함수](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[`scanf` 형식 필드 문자](../c-runtime-library/scanf-type-field-characters.md)<br/>
