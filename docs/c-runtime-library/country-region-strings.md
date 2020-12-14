---
description: 국가/지역 문자열에 대해 자세히 알아보세요.
title: 국가-지역 문자열
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: d865c3a6a8f505eea7878df379db30224511d51c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195699"
---
# <a name="countryregion-strings"></a>Country/Region Strings

국가 및 지역 문자열을 언어 문자열과 결합하여 `setlocale`, `_wsetlocale`, `_create_locale`및 `_wcreate_locale` 함수에 대한 로캘 사양을 만들 수 있습니다. 다양 한 Windows 운영 체제 버전에서 지원 되는 국가 및 지역 이름 목록은 [부록 a:](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) MS lcid의 제품 동작 : Windows Lcid (언어 코드 식별자) 참조에서 표의 언어, 위치 및 **언어 태그** 열을 참조 \[ 하세요. 사용 가능한 로캘 이름 및 관련 값을 열거하는 코드 예제는 [NLS: 이름 기반 API 샘플](/windows/win32/intl/nls--name-based-apis-sample)을 참조하세요.

## <a name="additional-supported-country-and-region-strings"></a>지원되는 추가 국가 및 지역 문자열

또한 Microsoft C 런타임 라이브러리 구현은 다음과 같은 국가/지역 문자열과 약어를 추가로 지원합니다.

|국가/지역 문자열|약어|해당 로캘 이름|
|----------------------------|------------------|----------------------------|
|america|미국|ko-KR|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|체코|CZE|cs-CZ|
|england|GBR|en-GB|
|great britain|GBR|en-GB|
|holland|NLD|nl-NL|
|hong-kong|HKG|zh-HK|
|new-zealand|NZL|en-NZ|
|nz|NZL|en-NZ|
|pr china|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|슬로바키아|SVK|sk-SK|
|south africa|ZAF|af-ZA|
|south korea|KOR|ko-KR|
|south-africa|ZAF|af-ZA|
|south-korea|KOR|ko-KR|
|trinidad & tobago|TTO|en-TT|
|uk|GBR|en-GB|
|united-kingdom|GBR|en-GB|
|united-states|미국|ko-KR|
|us|미국|ko-KR|

## <a name="see-also"></a>참고 항목

[로캘 이름, 언어 및 국가/지역 문자열](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[언어 문자열](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
