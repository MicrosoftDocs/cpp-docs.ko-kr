---
title: _ismbb 루틴 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _ismbb
- ismbb
dev_langs:
- C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86587495353090ced63d0487991f4275d3d0d5d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092532"
---
# <a name="ismbb-routines"></a>_ismbb 루틴

현재 로캘 또는 지정된 LC_CTYPE 변환 상태 범주를 사용하여 지정된 정수 값 `c` 를 특정 조건에 대해 테스트합니다.

|||
|-|-|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>설명

`_ismbb` 패밀리의 모든 루틴은 지정된 정수 값 `c` 를 특정 조건에 대해 테스트합니다. 테스트 결과는 적용되는 멀티바이트 코드 페이지에 따라 다릅니다. 기본적으로 멀티바이트 코드 페이지는 프로그램 시작 시 운영 체제에서 가져온 ANSI 코드 페이지로 설정됩니다. [_getmbcp](../c-runtime-library/reference/getmbcp.md)를 사용하여 사용 중인 멀티바이트 코드 페이지를 쿼리하거나 [_setmbcp](../c-runtime-library/reference/setmbcp.md)를 사용하여 변경합니다.

출력 값은 로캘의 `LC_CTYPE` 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 로캘 종속 동작에 현재 로캘을 사용하고 **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용한다는 점을 제외하고는 동일합니다.

`_ismbb` 패밀리의 루틴은 지정된 정수 `c` 를 다음과 같이 테스트합니다.

|루틴에서 반환된 값|바이트 테스트 조건|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|`_ismbbprint`와 같지만 `_ismbbgraph` 에는 공백 문자(0x20)가 포함되지 않습니다.|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|문장 부호 이외에 ASCII가 아닌 텍스트 기호. 예를 들어 코드 페이지 932에 한해 `_ismbbkalnum` 은 가타카나 영숫자를 테스트합니다.|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|가타카나(0xA1 – 0xDF). 코드 페이지 932에만 해당합니다.|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|ASCII가 아닌 텍스트 또는 ASCII가 아닌 문장 부호 기호. 예를 들어 코드 페이지 932에 한해 `_ismbbkprint`는 가타카나 영숫자 또는 가타카나 문장 부호를 테스트합니다(범위: 0xA1 – 0xDF).|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|ASCII가 아닌 문장 부호. 예를 들어 코드 페이지 932에 한해 `_ismbbkpunct` 는 가타카나 문장 부호를 테스트합니다.|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|멀티바이트 문자의 첫 번째 바이트. 예를 들어 코드 페이지 932에 한해 유효한 범위는 0x81 ~ 0x9F, 0xE0 ~ 0xFC입니다.|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** 에는 공백 문자(0x20)가 포함됩니다.|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|멀티바이트 문자의 두 번째 바이트. 예를 들어 코드 페이지 932에 한해 유효한 범위는 0x40 ~ 0x7E, 0x80 ~ 0xEC입니다.|

다음 표에서는 이들 루틴에 대한 테스트 조건을 구성하는 ORed 값을 보여 줍니다. 매니페스트 상수 `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`및 `_UPPER` 은 Ctype.h에서 정의됩니다.

|루틴|_BLANK|_DIGIT|LOWER|_PUNCT|UPPER|Non-<br /><br /> ASCII<br /><br /> 텍스트|Non-<br /><br /> ASCII<br /><br /> punct|
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|
|`_ismbbalnum`|—|x|x|—|x|x|—|
|`_ismbbalpha`|—|—|x|—|x|x|—|
|`_ismbbblank`|x|—|—|—|—|—|—|
|`_ismbbgraph`|—|x|x|x|x|x|x|
|`_ismbbkalnum`|—|—|—|—|—|x|—|
|`_ismbbkprint`|—|—|—|—|—|x|x|
|`_ismbbkpunct`|—|—|—|—|—|—|x|
|`_ismbbprint`|x|x|x|x|x|x|x|
|`_ismbbpunct`|—|—|—|x|—|—|x|

`_ismbb` 루틴은 함수 및 매크로로 구현됩니다. 구현을 선택하는 방법에 대한 자세한 내용은 [함수와 매크로 중 선택에 대한 권장 사항](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[바이트 분류](../c-runtime-library/byte-classification.md)<br/>
[is, isw 루틴](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)