---
description: '자세한 정보: 형식 사양 필드: scanf 및 wscanf 함수'
title: '형식 사양 필드: scanf 및 wscanf 함수'
ms.date: 11/04/2016
ms.topic: reference
ms.custom: contperf-fy21q1
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 716d8a498fe8b4bc895d48bf136e87781f0e8718
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645139"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>형식 사양 필드: scanf 및 wscanf 함수

이 정보는 안전한 버전을 포함한 전체 `scanf` 함수 패밀리에 적용되며, `scanf`용 입력 스트림 `stdin`과 같은 입력 스트림을 프로그램 변수로 삽입된 값으로 구문 분석하는 방법을 `scanf` 함수에 지시하는 데 사용하는 기호를 설명합니다.

형식 지정은 다음과 같습니다.

`%`[`*`] [[width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][type](../c-runtime-library/scanf-type-field-characters.md)

`format` 인수는 입력에 대한 해석을 지정하고 다음 중 하나 이상을 포함할 수 있습니다.

- 공백 문자: 공백(' '), 탭('\t') 또는 줄 바꿈('\n'). 공백 문자는 `scanf`를 통해 읽을 수 있지만 입력에서 다음 공백이 아닌 문자까지의 모든 연속 공백 문자는 저장되지 않습니다. 형식의 공백 문자 하나는 입력의 모든 숫자(0 포함) 및 공백 문자 조합과 일치합니다.

- 백분율 기호(`%`)를 제외한 공백이 아닌 문자. 공백이 아닌 문자는 `scanf`를 통해 일치하는 공백이 아닌 문자를 읽을 수 있지만 저장하지는 않습니다. 입력 스트림의 다음 문자가 일치하지 않는 경우 `scanf`가 종료됩니다.

- 백분율 기호(`%`)를 포함한 형식 지정. 형식 지정은 `scanf`를 통해 입력의 문자를 읽고 지정된 형식의 값으로 변환합니다. 값은 인수 목록 중 하나에 할당됩니다.

형식은 왼쪽에서 오른쪽으로 읽습니다. 형식 지정 외부의 문자는 입력 스트림의 문자 시퀀스와 일치해야 합니다. 입력 스트림의 일치하는 문자는 검색되지만 저장되지는 않습니다. 입력 스트림의 문자가 형식 지정과 충돌할 경우 `scanf`는 종료되고 입력 스트림 안의 문자는 읽히지 않은 채로 남습니다.

첫 번째 형식 지정에서는 첫 번째 입력 필드의 값이 해당 지정에 따라 변환되어 첫 번째 `argument`에서 지정한 위치에 저장됩니다. 두 번째 형식 지정은 두 번째 입력 필드를 변환하여 두 번째 `argument`에 저장하고 이런 식으로 형식 문자열 끝까지 진행됩니다.

입력 필드는 첫 번째 공백 문자(공백, 탭 또는 줄 바꿈), 형식 지정에 따라 변환할 수 없는 첫 번째 문자 또는 필드 너비(지정된 경우)에 도달할 때까지의 모든 문자로 정의됩니다. 주어진 지정에 너무 많은 인수가 있을 경우 추가 인수들이 평가되지만 무시됩니다. 형식 지정에 충분한 인수가 없는 경우 결과를 예측할 수 없습니다.

형식 지정의 각 필드는 특정 형식 옵션을 나타내는 숫자 또는 단일 문자입니다. 마지막 선택적 형식 필드 뒤에 나타나는 `type` 문자는 입력 필드가 문자, 문자열 또는 숫자 중 어떤 것으로 해석될지를 결정합니다.

가장 간단한 형식 지정에는 백분율 기호와 `type` 문자만 포함됩니다(예: `%s`). 백분율 기호(`%`) 뒤에 아무 의미가 없는 형식 제어 문자가 올 경우, 해당 문자 및 이후의 문자(다음 백분율 기호까지)는 입력과 반드시 일치해야 하는 일반 문자 시퀀스로 처리됩니다. 예를 들어 백분율 기호 문자를 입력으로 지정하려면 `%%`를 사용합니다.

백분율 기호 다음에 나타나는 별표(`*`)는 지정된 형식의 필드로 해석되는 다음 입력 필드의 할당을 표시하지 않습니다. 필드가 검색되지만 저장되지 않습니다.

`_s` 함수 패밀리의 안전한 버전(`scanf` 접미사 포함)에는 `c`, `C`, `s`, `S` 또는 `[` 형식의 각 매개 변수 바로 뒤에 전달할 버퍼 크기 매개 변수가 필요합니다. `scanf` 함수 패밀리의 안전한 버전에 대한 자세한 내용은 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[scanf 너비 사양](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf 형식 필드 문자](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
