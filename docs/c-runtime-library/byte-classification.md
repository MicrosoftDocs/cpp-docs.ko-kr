---
description: '다음에 대 한 자세한 정보: 바이트 분류'
title: 바이트 분류
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 00691ca85366c5cbbe28b023f2a269838128fe9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221698"
---
# <a name="byte-classification"></a>바이트 분류

이러한 각 루틴은 지정된 바이트의 멀티바이트 문자가 조건을 충족하는지 테스트합니다. 달리 지정된 경우를 제외하고 출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따른 영향을 받습니다. 자세한 내용은 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다.

> [!NOTE]
> 정의된 대로 0에서 127 사이의 ASCII 문자는 모든 멀티바이트 문자 집합의 하위 집합입니다. 예를 들어 일본어 가타카나 문자 집합에는 ASCII 문자와 비 ASCII 문자가 모두 포함됩니다.

다음 표의 미리 정의 된 상수는에 정의 되어 \<ctype.h> 있습니다.

## <a name="multibyte-character-byte-classification-routines"></a>멀티바이트 문자의 바이트 분류 루틴

|루틴에서 반환된 값|바이트 테스트 조건|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|선행 바이트입니다. 테스트 결과는 현재 로캘의 **LC_CTYPE** 범주 설정에 따라 다릅니다.|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124;&#124; **_ismbbkalnum**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124;&#124; **_ismbbkalnum**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|**_ismbbprint** 와 같지만, **_ismbbgraph** 에는 공백 문자(0x20)가 포함되지 않습니다.|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|문장 부호 이외에 ASCII가 아닌 텍스트 기호. 예를 들어 **_ismbbkalnum** 은 932 코드 페이지에서만 가타카나 영숫자를 테스트합니다.|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|가타카나(0xA1-0xDF), 코드 페이지 932만|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|ASCII가 아닌 텍스트 또는 ASCII가 아닌 문장 부호 기호. 예를 들어 **_ismbbkprint** 는 932 코드 페이지에서만 가타카나 영숫자 또는 가타카나 문장 부호를 테스트합니다(범위: 0xA1 – 0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|ASCII가 아닌 문장 부호. 예를 들어 **_ismbbkpunct** 는 932 코드 페이지에서만 가타카나 문장 부호를 테스트합니다.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|멀티바이트 문자의 첫 번째 바이트. 예를 들어 코드 페이지 932에 한해 유효한 범위는 0x81 ~ 0x9F, 0xE0 ~ 0xFC입니다.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124;&#124; **_ismbbkprint** **ismbbprint** 에는 공백 문자 (0x20)가 포함 되어 있습니다.|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124;&#124; **_ismbbkpunct**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|멀티바이트 문자의 두 번째 바이트. 예를 들어 코드 페이지 932에 한해 유효한 범위는 0x40 ~ 0x7E, 0x80 ~ 0xEC입니다.|
|[_ismbslead, _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|선행 바이트(문자열 컨텍스트)|
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|후행 바이트(문자열 컨텍스트)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|이전 바이트에 따라 바이트 형식 반환|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|문자열 내 바이트의 형식 반환|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|멀티 바이트 문자 변환의 상태를 추적합니다.|

에 정의 된 **MB_LEN_MAX** 매크로는 \<limits.h> 멀티 바이트 문자의 최대 길이 (바이트)로 확장 됩니다. 에 정의 된 **MB_CUR_MAX** 는 \<stdlib.h> 현재 로캘의 모든 멀티 바이트 문자의 최대 길이 (바이트)로 확장 됩니다.

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)
