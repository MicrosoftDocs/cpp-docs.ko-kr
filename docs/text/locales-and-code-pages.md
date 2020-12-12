---
description: '자세한 정보: 로캘 및 코드 페이지'
title: 로캘 및 코드 페이지
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: f8b5310d7712617b1397bc42ef6ec58e5b3297ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207204"
---
# <a name="locales-and-code-pages"></a>로캘 및 코드 페이지

로캘 ID는 특정 지역에 대 한 로컬 규칙 및 언어를 반영 합니다. 지정된 언어는 여러 국가/지역에서 통용될 수 있습니다. 예를 들어 포르투갈어는 브라질과 포르투갈에서 통용됩니다. 반대로 한 국가/지역에 여러 개의 공식 언어가 있을 수 있습니다. 예를 들어 캐나다에는 영어와 프랑스어 라는 두 가지 언어가 있습니다. 따라서 캐나다에는 Canadian-English와 캐나다 프랑스어 라는 두 개의 고유 로캘이 있습니다. 일부 로캘 종속 범주에는 날짜 형식 지정 및 통화 값의 형식 표시가 포함됩니다.

언어에 따라 텍스트 및 데이터 형식 지정 규칙이 결정되고 국가/지역에 따라 지역 규칙이 결정됩니다. 모든 언어에는 코드 페이지로 표시 되는 고유한 매핑이 있습니다. 여기에는 영문자 이외의 문자 (예: 문장 부호 및 숫자)가 포함 됩니다. 코드 페이지는 문자 집합이 며 언어와 관련 되어 있습니다. 따라서 [로캘은](../c-runtime-library/locale.md) 언어, 국가/지역 및 코드 페이지의 고유한 조합입니다. 로캘 및 코드 페이지 설정은 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 함수를 호출 하 여 런타임에 변경할 수 있습니다.

언어 마다 다른 코드 페이지를 사용할 수 있습니다. 예를 들어, ANSI 코드 페이지 1252는 영어와 대부분의 유럽 언어에 사용 되 고 ANSI 코드 페이지 932는 일본어 간지에 사용 됩니다. 거의 모든 코드 페이지는 가장 낮은 128 문자 (0x00에서 0x7F)의 ASCII 문자 집합을 공유 합니다.

단일 바이트 코드 페이지는 문자 (숫자 및 문장 부호 포함) 또는 문자 모양에 대 한 바이트 값의 매핑으로 (256 항목 포함) 테이블에 표시 될 수 있습니다. 모든 멀티 바이트 코드 페이지는 문자에 대 한 더블 바이트 값의 매우 큰 테이블 (64K 항목 포함)로 표시 될 수도 있습니다. 실제로이 값은 일반적으로 처음 256 (싱글바이트) 문자 및 더블 바이트 값의 범위로 표시 됩니다.

코드 페이지에 대한 자세한 내용은 [Code Pages](../c-runtime-library/code-pages.md)를 참조하세요.

C 런타임 라이브러리에는 두 가지 유형의 내부 코드 페이지 (로캘 및 멀티 바이트)가 있습니다. 프로그램 실행 중에 현재 코드 페이지를 변경할 수 있습니다 ( [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 및 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 함수에 대 한 설명서 참조). 또한 런타임 라이브러리는 프로그램 실행 기간 동안 상수인 운영 체제 코드 페이지의 값을 가져오고 사용할 수 있습니다.

로캘 코드 페이지를 변경 하면 로캘 종속 함수 집합의 동작이 선택한 코드 페이지에 의해 결정 된 대로 변경 됩니다. 기본적으로 모든 로캘 종속 함수는 "C" 로캘에 고유한 로캘 코드 페이지를 사용 하 여 실행을 시작 합니다. 함수를 호출 하 여 내부 로캘 코드 페이지 및 기타 로캘별 속성을 변경할 수 있습니다 `setlocale` . `setlocale`(LC_ALL, "")에 대 한 호출은 운영 체제 사용자 로캘이 나타내는 로캘을 설정 합니다.

마찬가지로 멀티 바이트 코드 페이지가 변경 되 면 멀티 바이트 함수의 동작이 선택한 코드 페이지에 의해 결정 된 대로 변경 됩니다. 기본적으로 모든 멀티 바이트 함수는 운영 체제의 기본 코드 페이지에 해당 하는 멀티 바이트 코드 페이지를 사용 하 여 실행을 시작 합니다. 함수를 호출 하 여 내부 멀티 바이트 코드 페이지를 변경할 수 있습니다 `_setmbcp` .

C 런타임 함수는 `setlocale` 현재 프로그램 로캘 정보의 일부 또는 전부를 설정, 변경 또는 쿼리 합니다. [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 루틴은의 와이드 문자 버전 이며 `setlocale` ,의 인수 및 반환 값은 `_wsetlocale` 와이드 문자 문자열입니다.

## <a name="see-also"></a>참고 항목

[유니코드 및 멀티바이트 문자 집합(MBCS)](../text/unicode-and-mbcs.md)<br/>
[문자 집합 이식성의 이점](../text/benefits-of-character-set-portability.md)
