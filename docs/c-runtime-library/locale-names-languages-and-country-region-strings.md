---
title: 로캘 이름, 언어 및 국가-지역 문자열 | Microsoft Docs
ms.custom: ''
ms.date: 08/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2622702cd19dab3cad2613aa3df28b5cef464853
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076010"
---
# <a name="locale-names-languages-and-countryregion-strings"></a>로캘 이름, 언어 및 국가/지역 문자열

`setlocale` 및 `_create_locale` 함수에 대한 *locale* 인수는 Windows NLS API에서 지원하는 로캘 이름, 언어, 국가/지역 코드 및 코드 페이지를 사용하여 설정할 수 있습니다. *locale* 인수 형식은 다음과 같습니다.

> *locale* :: "*locale_name*" &nbsp;&nbsp;&nbsp;&nbsp;| "*language*\[\_*country-region*]\[.*code_page*]]" &nbsp;&nbsp;&nbsp;&nbsp;| ".*code_page*" &nbsp;&nbsp;&nbsp;&nbsp;| "C" &nbsp;&nbsp;&nbsp;&nbsp;| "" &nbsp;&nbsp;&nbsp;&nbsp;| NULL

로캘 이름 형식(예: 영어(미국)의 경우 `en-US` 또는 보스니아어(키릴 자모, 보스니아 헤르체고비나)의 경우 `bs-Cyrl-BA`)을 사용하는 것이 좋습니다. 로캘 이름 집합은 [Locale Names(로캘 이름)](/windows/desktop/Intl/locale-names)에 설명되어 있습니다. Windows 운영 체제 버전별 지원되는 로캘 이름 목록은 [MS-LCID]: Windows LCID(언어 코드 식별자) 참조의 [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx)(부록 A: 제품 동작)에 있는 표의 **언어 태그** 열을 참조하세요. 이 리소스는 로캘 이름의 지원되는 언어, 스크립트 및 영역 부분을 나열합니다. 비-기본 정렬 순서를 사용하는 지원되는 로캘 이름에 대한 정보는 **Sort Order Identifiers(정렬 순서 식별자)** 에서 [로캘 이름](/windows/desktop/Intl/sort-order-identifiers)열을 참조하세요. Windows 10 이상에서는 유효한 BCP-47 언어 태그에 해당하는 로캘 이름을 사용할 수 있습니다. 예를 들어 `jp-US`는 유효한 BCP-47 태그이지만 로캘 기능의 경우 `US`만 유효합니다.

*language*[*_country_region*[.*code_page*]] 양식은 언어 문자열 또는 언어 문자열과 국가/지역 문자열이 로캘을 만드는 데 사용되는 경우 범주에 대한 로캘 설정에 저장됩니다. 지원되는 언어 문자열 집합은 [Language Strings](../c-runtime-library/language-strings.md)에 설명되어 있고, 지원되는 국가/지역 문자열은 [Country/Region Strings](../c-runtime-library/country-region-strings.md)에 나열되어 있습니다. 지정된 언어가 국가/지역과 연결되어 있지 않으면 지정된 국가/지역에 대한 기본 언어가 로캘 설정에 저장됩니다. 이러한 문자열은 로캘 이름 형식보다 운영 체제 업데이트에 의해 변경될 가능성이 높기 때문에 코드에 포함되거나 저장소로 직렬화된 로캘 문자열에는 이 양식을 사용하지 않는 것이 좋습니다.

코드 페이지는 로캘과 연관된 ANSI/OEM 코드 페이지입니다. 언어 또는 언어와 국가/지역만으로 로캘을 지정하면 코드 페이지가 결정됩니다. 특수 값 `.ACP` 가 국가/지역에 대한 ANSI 코드 페이지를 지정합니다. 특수 값 `.OCP` 가 국가/지역에 대한 OEM 코드 페이지를 지정합니다. 예를 들어, `"Greek_Greece.ACP"` 를 로캘로 지정하는 경우 로캘이 `Greek_Greece.1253` (그리스어의 ANSI 코드 페이지)으로 저장되고, `"Greek_Greece.OCP"` 를 로캘로 지정하는 경우 로캘이 `Greek_Greece.737` (그리스어의 OEM 코드 페이지)로 저장됩니다. 코드 페이지에 대한 자세한 내용은 [Code Pages](../c-runtime-library/code-pages.md)를 참조하세요. Windows에서 지원되는 코드 페이지 목록을 보려면 [Code Page Identifiers(코드 페이지 식별자)](/windows/desktop/Intl/code-page-identifiers)를 참조하세요.

로캘을 지정하는 데 코드 페이지만 사용하는 경우 [GetUserDefaultLocaleName](/windows/desktop/api/winnls/nf-winnls-getuserdefaultlocalename)에서 보고한 대로 사용자의 기본 언어 및 국가/지역이 사용됩니다. 예를 들어, 영어(미국)로 구성된 사용자에게 `".1254"`(ANSI 터키어)를 로캘로 지정하는 경우 저장되는 로캘은 `English_United States.1254`입니다. 일관되지 않은 동작이 발생할 수 있으므로 이 양식을 사용하지 않는 것이 좋습니다.

`C`의 *locale* 인수 값은 C 번역에 대한 최소 ANSI 표준에 맞는 환경을 지정합니다. `C` 로캘은 모든 **char** 데이터 형식이 1바이트이고, 해당 값이 항상 256보다 작은 것으로 간주합니다. *locale*에서 빈 문자열을 가리키면 로캘은 구현에서 정의된 네이티브 환경입니다.

`setlocale` 범주를 사용하여 `_wsetlocale` 및 `LC_ALL` 함수에 대해 동시에 모든 로캘 범주를 지정할 수 있습니다. 범주를 모두 동일한 로캘로 설정하거나 이 양식을 사용하는 로캘 인수를 사용하여 범주를 각각 설정할 수 있습니다.

> LC_ALL_specifier :: locale &nbsp;&nbsp;&nbsp;&nbsp;| [LC_COLLATE=locale][;LC_CTYPE=locale][;LC_MONETARY=locale][;LC_NUMERIC=locale][;LC_TIME=locale]

세미콜론으로 구분된 여러 범주 형식을 지정할 수 있습니다. 지정되지 않은 범주 형식에서 현재 로캘 설정을 사용합니다. 예를 들어 이 코드 조각에서는 모든 범주에 대한 현재 로캘을 `de-DE`로 설정한 다음, `LC_MONETARY` 범주를 `en-GB`로, `LC_TIME` 범주를 `es-ES`로 설정합니다.

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>참고 항목

[C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[언어 문자열](../c-runtime-library/language-strings.md)<br/>
[국가/지역 문자열](../c-runtime-library/country-region-strings.md)
