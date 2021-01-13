---
title: Language Strings
description: '자세한 정보: 언어 문자열'
ms.date: 1/12/2021
helpviewer_keywords:
- language strings
ms.openlocfilehash: ec82bb8b9efb9c366c287c79b71b60a3c6bc6ab2
ms.sourcegitcommit: b51f79b5394e12cd90cb65c85cc01716f90bfc90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98167023"
---
# <a name="language-strings"></a>Language Strings

[`setlocale`](../c-runtime-library/reference/setlocale-wsetlocale.md)및 [`_create_locale`](../c-runtime-library/reference/create-locale-wcreate-locale.md) 함수는 유니코드 코드 페이지를 사용 하지 않는 운영 체제에서 지원 되는 Windows NLS API 언어를 사용할 수 있습니다. 운영 체제 버전에서 지원 되는 언어 목록은 [부록 a:](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) MS Lcid의 제품 동작 \[ : Windows 언어 코드 식별자 (lcid) 참조를 참조 하세요. 언어 문자열은 지원되는 언어 목록의 **언어** 및 **언어 태그** 열에 있는 임의의 값일 수 있습니다. 사용 가능한 로캘 이름 및 관련 값을 열거 하는 예제 코드는 [NLS: 이름 기반 Api 샘플](/windows/win32/intl/nls--name-based-apis-sample)을 참조 하세요.

## <a name="supported-language-strings"></a>지원 되는 언어 문자열

Microsoft C 런타임 라이브러리 구현은 다음 언어 문자열도 지원합니다.

|언어 문자열|해당 로캘 이름|
|---------------------|----------------------------|
|`american`|`en-US`|
|`american english`|`en-US`|
|`american-english`|`en-US`|
|`australian`|`en-AU`|
|`belgian`|`nl-BE`|
|`canadian`|`en-CA`|
|`chh`|`zh-HK`|
|`chi`|`zh-SG`|
|`chinese`|`zh`|
|`chinese-hongkong`|`zh-HK`|
|`chinese-simplified`|`zh-CN`|
|`chinese-singapore`|`zh-SG`|
|`chinese-traditional`|`zh-TW`|
|`dutch-belgian`|`nl-BE`|
|`english-american`|`en-US`|
|`english-aus`|`en-AU`|
|`english-belize`|`en-BZ`|
|`english-can`|`en-CA`|
|`english-caribbean`|`en-029`|
|`english-ire`|`en-IE`|
|`english-jamaica`|`en-JM`|
|`english-nz`|`en-NZ`|
|`english-south africa`|`en-ZA`|
|`english-trinidad y tobago`|`en-TT`|
|`english-uk`|`en-GB`|
|`english-us`|`en-US`|
|`english-usa`|`en-US`|
|`french-belgian`|`fr-BE`|
|`french-canadian`|`fr-CA`|
|`french-luxembourg`|`fr-LU`|
|`french-swiss`|`fr-CH`|
|`german-austrian`|`de-AT`|
|`german-lichtenstein`|`de-LI`|
|`german-luxembourg`|`de-LU`|
|`german-swiss`|`de-CH`|
|`irish-english`|`en-IE`|
|`italian-swiss`|`it-CH`|
|`norwegian`|`no`|
|`norwegian-bokmal`|`nb-NO`|
|`norwegian-nynorsk`|`nn-NO`|
|`portuguese-brazilian`|`pt-BR`|
|`spanish-argentina`|`es-AR`|
|`spanish-bolivia`|`es-BO`|
|`spanish-chile`|`es-CL`|
|`spanish-colombia`|`es-CO`|
|`spanish-costa rica`|`es-CR`|
|`spanish-dominican republic`|`es-DO`|
|`spanish-ecuador`|`es-EC`|
|`spanish-el salvador`|`es-SV`|
|`spanish-guatemala`|`es-GT`|
|`spanish-honduras`|`es-HN`|
|`spanish-mexican`|`es-MX`|
|`spanish-modern`|`es-ES`|
|`spanish-nicaragua`|`es-NI`|
|`spanish-panama`|`es-PA`|
|`spanish-paraguay`|`es-PY`|
|`spanish-peru`|`es-PE`|
|`spanish-puerto rico`|`es-PR`|
|`spanish-uruguay`|`es-UY`|
|`spanish-venezuela`|`es-VE`|
|`swedish-finland`|`sv-FI`|
|`swiss`|`de-CH`|
|`uk`|`en-GB`|
|`us`|`en-US`|
|`usa`|`en-US`|

## <a name="see-also"></a>참고 항목

- [로캘 이름, 언어 및 국가/지역 문자열](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
- [국가/지역 문자열](../c-runtime-library/country-region-strings.md)\
- [`setlocale`, `_wsetlocale`](../c-runtime-library/reference/setlocale-wsetlocale.md)\
- [`_create_locale`, `_wcreate_locale`](../c-runtime-library/reference/create-locale-wcreate-locale.md)
