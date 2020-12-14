---
description: '자세한 정보: 언어 문자열'
title: Language Strings
ms.date: 11/04/2016
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 077a440981c9e39e87356310c40ae9b249d4662e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246580"
---
# <a name="language-strings"></a>Language Strings

[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 및 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 함수는 유니코드 코드 페이지를 사용하지 않는 운영 체제에서 Windows NLS API를 지원하는 언어를 사용할 수 있습니다. 운영 체제 버전에서 지원 되는 언어 목록은 [부록 a:](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) MS Lcid의 제품 동작 \[ : Windows 언어 코드 식별자 (lcid) 참조를 참조 하세요. 언어 문자열은 지원되는 언어 목록의 **언어** 및 **언어 태그** 열에 있는 임의의 값일 수 있습니다. 사용 가능한 로캘 이름 및 관련 값을 열거하는 코드 예제는 [NLS: 이름 기반 API 샘플](/windows/win32/intl/nls--name-based-apis-sample)을 참조하세요.

## <a name="additional-supported-language-strings"></a>지원되는 추가 언어 문자열

Microsoft C 런타임 라이브러리 구현은 다음 언어 문자열도 지원합니다.

|언어 문자열|해당 로캘 이름|
|---------------------|----------------------------|
|아메리카|ko-KR|
|american english|ko-KR|
|american-english|ko-KR|
|오스트레일리아|en-AU|
|벨기에|nl-BE|
|캐나다|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|중국|zh|
|chinese-hongkong|zh-HK|
|chinese-simplified|zh-CN|
|chinese-singapore|zh-SG|
|chinese-traditional|zh-TW|
|dutch-belgian|nl-BE|
|english-american|ko-KR|
|english-aus|en-AU|
|english-belize|en-BZ|
|english-can|en-CA|
|english-caribbean|en-029|
|english-ire|en-IE|
|english-jamaica|en-JM|
|english-nz|en-NZ|
|english-south africa|en-ZA|
|english-trinidad y tobago|en-TT|
|english-uk|en-GB|
|english-us|ko-KR|
|english-usa|ko-KR|
|french-belgian|fr-BE|
|french-canadian|fr-CA|
|french-luxembourg|fr-LU|
|french-swiss|fr-CH|
|german-austrian|de-AT|
|german-lichtenstein|de-LI|
|german-luxembourg|de-LU|
|german-swiss|de-CH|
|irish-english|en-IE|
|italian-swiss|it-CH|
|노르웨이어|no|
|norwegian-bokmal|nb-NO|
|norwegian-nynorsk|nn-NO|
|portuguese-brazilian|pt-BR|
|spanish-argentina|es-AR|
|spanish-bolivia|es-BO|
|spanish-chile|es-CL|
|spanish-colombia|es-CO|
|spanish-costa rica|es-CR|
|spanish-dominican republic|es-DO|
|spanish-ecuador|es-EC|
|spanish-el salvador|es-SV|
|spanish-guatemala|es-GT|
|spanish-honduras|es-HN|
|spanish-mexican|es-MX|
|spanish-modern|es-ES|
|spanish-nicaragua|es-NI|
|spanish-panama|es-PA|
|spanish-paraguay|es-PY|
|spanish-peru|es-PE|
|spanish-puerto rico|es-PR|
|spanish-uruguay|es-UY|
|spanish-venezuela|es-VE|
|swedish-finland|sv-FI|
|스위스|de-CH|
|uk|en-GB|
|us|ko-KR|
|usa|ko-KR|

## <a name="see-also"></a>참고 항목

[로캘 이름, 언어 및 국가/지역 문자열](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[국가/지역 문자열](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
