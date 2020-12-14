---
description: _Ismbc 루틴에 대 한 자세한 정보
title: _ismbc 루틴
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 319e077d839cacb6faf0c9095d403f99a1677975
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246593"
---
# <a name="_ismbc-routines"></a>_ismbc 루틴

각 **_ismbc** 루틴은 특정 조건에 대해 지정된 멀티바이트 문자 `c`를 테스트합니다.

:::row:::
   :::column span="":::
      [_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)\
      [_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)\
      [_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)\
      [_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)\
      [_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)\
      [_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)
   :::column-end:::
:::row-end:::

## <a name="remarks"></a>설명

각 **_ismbc** 루틴의 테스트 결과는 적용되는 멀티바이트 코드 페이지에 따라 다릅니다. 멀티바이트 코드 페이지는 싱글바이트 알파벳 문자를 포함합니다. 기본적으로 멀티바이트 코드 페이지는 프로그램 시작 시 운영 체제에서 가져온 system-default ANSI 코드 페이지로 설정됩니다. [_getmbcp](../c-runtime-library/reference/getmbcp.md) 또는 [_setmbcp](../c-runtime-library/reference/setmbcp.md)를 각각 사용하여 사용 중인 멀티바이트 코드 페이지를 변경하거나 쿼리할 수 있습니다.

출력값은 로캘의 `LC_CTYPE` 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다.

|루틴에서 반환된 값|테스트 조건|932 코드 페이지 예제|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|영숫자|`c`가 ASCII 영어 문자의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다. `_ismbcdigit` 및 `_ismbcalpha`의 예제를 참조하십시오.|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|사전순|`c`가 ASCII 영어 문자(`_ismbcupper` 및 `_ismbclower`에 대한 예 참조) 또는 가타카나 문자(0xA6<=`c`<=0xDF)의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|숫자|`c`가 ASCII 숫자(0x30<=`c`<=0x39)의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Graphic|`c`가 공백 ( )을 제외하고 모든 ASCII 또는 가타카나 인쇄 가능한 문자의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다. `_ismbcdigit`, `_ismbcalpha` 및 `_ismbcpunct`에 대한 예를 참조하세요.|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|유효한 멀티바이트 문자|`c`의 첫 번째 바이트는 0x81 – 0x9F 또는 0xE0 – 0xFC 범위 내에 있고 두 번째 바이트는 0x40 - 0x7E 또는 0x80 - FC 범위 내에 있는 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|소문자 영문자|`c`가 ASCII 영어 소문자(0x61<=`c`<=0x7A)의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|인쇄 가능|`c`가 공백 ( )을 포함하여 모든 ASCII 또는 가타카나 인쇄 가능한 문자의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다. `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha` 및 `_ismbcpunct`에 대한 예를 참조하세요.|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|문장 부호|`c`가 모든 ASCII 또는 가타카나 문장 부호 문자의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|공백 또는 가로 탭|`c`가 공백 문자 또는 가로 탭 문자의 싱글바이트 표현인 경우(`c`=0x20 또는 `c`=0x09)에만 0이 아닌 값을 반환합니다.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|공백|`c`가 공백 문자(`c`=0x20 또는 0x09<=`c`<=0x0D)인 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|멀티바이트 기호|0x8141<=`c`<=0x81AC인 경우에만 0이 아닌 값을 반환합니다.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|대문자 영문자|`c`가 ASCII 영어 대문자(0x41<=`c`<=0x5A)의 싱글바이트 표현인 경우에만 0이 아닌 값을 반환합니다.|

**코드 페이지 932 관련**

다음 루틴은 코드 페이지 932에만 해당합니다.

|루틴에서 반환된 값|테스트 조건(코드 페이지 932만 해당)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|더블바이트 히라가나: 0x829F<=`c`<=0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|더블바이트 가타카나: 0x8340<=`c`<=0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 비간지: 0x8140<=`c`<=0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 수준 1: 0x889F<=`c`<=0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 수준 2: 0x989F<=`c`<=0xEA9E.|

`_ismbcl0`, `_ismbcl1` 및 `_ismbcl2`는 지정된 값 `c`가 이전 테이블에 설명된 테스트 조건과 일치하는지 확인하지만 `c`가 유효한 멀티바이트 문자인지는 확인하지 않습니다. 하위 바이트 범위가 0x00 – 0x3F, 0x7F 또는 0xFD – 0xFF인 경우 이러한 함수는 0이 아닌 값을 반환하여 문자가 테스트 조건을 충족함을 나타냅니다. [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)을 사용하여 멀티바이트 문자가 정의되었는지 여부를 테스트합니다.

**최종 코드 페이지 932 관련**

## <a name="see-also"></a>참고 항목

[문자 분류](../c-runtime-library/character-classification.md)<br/>
[is, isw 루틴](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 루틴](../c-runtime-library/ismbb-routines.md)
