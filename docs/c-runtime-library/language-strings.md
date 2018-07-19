---
title: 언어 문자열 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92ad129a5703f509cfd9543497cceffae3a6e7b3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391365"
---
# <a name="language-strings"></a>Language Strings
`setlocale` 및 `_create_locale` 함수는 유니코드 코드 페이지를 사용하지 않는 운영 체제에서 Windows NLS API를 지원하는 언어를 사용할 수 있습니다. 운영 체제 버전에서 지원되는 언어 목록은 [NLS(국가별 언어 지원) API 참조](https://www.microsoft.com/resources/msdn/goglobal/default.mspx)를 참조하세요. 언어 문자열은 지원되는 언어 목록의 **언어** 및 **언어 이름 약어** 열에 있는 임의의 값일 수 있습니다. 운영 체제 버전별 언어 지원에 대한 자세한 내용은 [MS-LCID]: Windows LCID(언어 코드 식별자) 참조의 [부록 A: 제품 동작(영문)](http://msdn.microsoft.com/goglobal/bb896001.aspx)을 참조하세요.   
  
C 런타임 라이브러리 구현은 다음 언어 문자열도 지원합니다.  
  
|언어 문자열|해당 로캘 이름|  
|---------------------|----------------------------|  
|american|ko-KR|  
|american english|ko-KR|  
|american-english|ko-KR|  
|australian|en-AU|  
|belgian|nl-BE|  
|canadian|en-CA|  
|chh|zh-HK|  
|chi|zh-SG|  
|chinese|zh|  
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
|norwegian|no|  
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
|swiss|de-CH|  
|uk|en-GB|  
|us|ko-KR|  
|usa|ko-KR|  
  
## <a name="see-also"></a>참고 항목  
 [로캘 이름, 언어 및 국가/지역 문자열](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [국가/지역 문자열](../c-runtime-library/country-region-strings.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)