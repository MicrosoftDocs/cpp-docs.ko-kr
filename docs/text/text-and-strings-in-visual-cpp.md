---
description: '자세한 정보: Visual C++의 텍스트 및 문자열'
title: Visual C++의 텍스트 및 문자열
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: 3b77df006e095871d11fb3bfbc3d83b081d6052f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335734"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++의 텍스트 및 문자열

국제 시장을 위해 응용 프로그램을 개발 하는 중요 한 측면은 로컬 문자 집합의 적절 한 표현입니다. ASCII 문자 집합은 0x00에서 0x7F 범위의 문자를 정의 합니다. 주로 유럽의 문자 집합은 ASCII 문자 집합과 동일 하 게 0x00에서 0x7F 사이에 있는 문자를 정의 하 고 0x80에서 0xFF로 확장 문자 집합을 정의 합니다. 따라서 8 비트 SBCS (싱글바이트 문자 집합)는 ASCII 문자 집합 뿐만 아니라 많은 유럽 언어의 문자 집합을 나타내는 데 충분 합니다. 그러나 일본어 간지와 같은 일부 비 유럽 문자 집합에는 싱글바이트 코딩 체계에서 표현할 수 있는 것 보다 더 많은 문자가 포함 되므로 MBCS (멀티 바이트 문자 집합) 인코딩이 필요 합니다.

## <a name="in-this-section"></a>섹션 내용

[유니코드 및 멀티바이트 문자 집합(MBCS)](../text/unicode-and-mbcs.md)<br/>
유니코드 및 MBCS 프로그래밍에 대 한 Visual C++ 지원에 대해 설명 합니다.

[유니코드 지원](../text/support-for-unicode.md)<br/>
단일 바이트로 나타낼 수 없는 문자 집합을 포함 하 여 모든 문자 집합을 지 원하는 데 필요한 유니코드에 대해 설명 합니다.

[MBCS (멀티 바이트 문자 집합) 지원](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
단일 바이트로 표현할 수 없는 일본어 및 중국어와 같은 문자 집합을 지 원하는 유니코드에 대 한 대체 인 MBCS에 대해 설명 합니다.

[Tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)<br/>
에서는 다양 한 데이터 형식, 루틴 및 기타 개체에 대해 Microsoft 고유의 일반 텍스트 매핑을 제공 합니다.

[방법: 다양 한 문자열 형식 간 변환](../text/how-to-convert-between-various-string-types.md)<br/>
다양 한 Visual C++ 문자열 형식을 다른 문자열로 변환 하는 방법을 보여 줍니다.

## <a name="related-sections"></a>관련 단원

[국제화](../c-runtime-library/internationalization.md)<br/>
C 런타임 라이브러리의 국가별 지원에 대해 설명 합니다.

[국가별 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International)<br/>
Visual C++에서 국제화를 보여 주는 샘플에 대 한 링크를 제공 합니다.

[언어 및 국가/지역 문자열](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
C 런타임 라이브러리의 언어 및 국가/지역 문자열을 제공 합니다.
