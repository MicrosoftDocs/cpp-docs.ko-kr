---
description: '자세히 알아보기: strcoll 함수'
title: strcoll 함수
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcoll
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
ms.openlocfilehash: 8a0b146bff2eab8927733923367b0ae49ecea4c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235686"
---
# <a name="strcoll-functions"></a>strcoll 함수

각 `strcoll` 및 `wcscoll` 함수는 현재 사용 중인 로캘 코드 페이지의 `LC_COLLATE` 범주 설정에 따라 두 개의 문자열을 비교합니다. 각 `_mbscoll` 함수는 현재 사용 중인 멀티바이트 코드 페이지에 따라 두 개의 문자열을 비교합니다. `coll` 함수는 현재 코드 페이지에서 문자 집합 순서와 사전적 문자 순서가 다르며 이러한 차이가 비교 시 중요한 경우의 문자열 비교에 사용합니다. 문자열 일치만 테스트하려면 해당 `cmp` 함수를 사용합니다.

### <a name="strcoll-functions"></a>strcoll 함수

|SBCS|유니코드(Unicode)|MBCS|설명|
|----------|-------------|----------|-----------------|
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|두 문자열을 비교합니다.|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|두 문자열을 비교합니다(대/소문자 구분).|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|두 문자열의 처음 `count`자를 비교합니다.|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|두 문자열의 처음 `count`자를 비교합니다(대/소문자 구분 없음).|

## <a name="remarks"></a>설명

이러한 함수(`strcoll`, `stricoll`, `_strncoll` 및 `_strnicoll`)의 SBCS(싱글바이트 문자) 버전은 현재 로캘의 `LC_COLLATE` 범주 설정에 따라 `string1` 및 `string2`를 비교합니다. 이러한 함수는 `strcoll` 함수가 데이터 정렬 시퀀스를 제공하는 로캘 코드 페이지 정보를 사용한다는 측면에서 해당 `strcmp` 함수와 다릅니다. 문자 집합 순서와 사전적 문자 순서가 다른 로캘에서 문자열을 비교하는 경우 해당 `strcmp` 함수가 아닌 `strcoll` 함수를 사용해야 합니다. `LC_COLLATE`에 대한 자세한 내용은 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요.

일부 코드 페이지와 해당 문자 집합의 경우 문자 집합의 문자 순서가 사전적 문자 순서와 다를 수 있습니다. "C" 로캘에서는 해당되지 않습니다. 즉, ASCII 문자 집합에서 문자의 순서는 문자의 사전적 순서와 동일합니다. 예를 들어 특정 유럽 코드 페이지의 문자 집합에서 문자 'a'(값 0x61)는 문자 'ä'(값 0xE4) 앞에 오지만 사전적으로는 문자 'ä'가 'a' 앞에 옵니다. 이러한 인스턴스에서 사전적 비교를 수행하려면 `strcmp` 대신 `strcoll`을 사용합니다. 또는 원본 문자열에 `strxfrm`를 사용한 다음 결과 문자열에 `strcmp`을 사용할 수 있습니다.

`strcoll``stricoll`, `_strncoll` 및 `_strnicoll`은 해당 와이드 문자(유니코드) 요소와 마찬가지로 현재 사용 중인 로캘 코드 페이지에 따라 멀티바이트 문자열을 자동으로 처리합니다. 그러나 이러한 함수의 MBCS(멀티 바이트 문자) 버전은 현재 사용 중인 멀티바이트 코드 페이지에 따라 문자 단위로 문자열을 비교합니다.

`coll` 함수는 문자열을 비교하기 위해 사전적으로 대조하는 반면 `cmp` 함수는 문자열이 같은지 여부만 테스트하므로 `coll` 함수는 해당 `cmp` 버전보다 훨씬 더 느립니다. 따라서 `coll` 함수는 현재 코드 페이지에서 문자 집합 순서와 사전적 문자 순서가 다르며 이러한 차이가 문자열 비교 시 중요한 경우에만 사용해야 합니다.

## <a name="see-also"></a>참고 항목

[로캘](../c-runtime-library/locale.md)<br/>
[문자열 조작](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)
