---
title: localeconv | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c5f66975d8d9904d1a4a8f2d26d4fe98ecfdd40
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223027"
---
# <a name="localeconv"></a>localeconv

로캘 설정에 대한 자세한 정보를 가져옵니다.

## <a name="syntax"></a>구문

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>반환 값

**localeconv** 형식의 채워진 개체에 대 한 포인터를 반환 [struct lconv](../../c-runtime-library/standard-types.md)합니다. 개체에 포함 된 값은 스레드 로컬 저장소의 로캘 설정에서 복사 되 고 후속 호출을 덮어쓸 수 있습니다 **localeconv**합니다. 이 개체의 값 변경의 로캘 설정을 수정 하지 마십시오. 에 대 한 호출 [setlocale](setlocale-wsetlocale.md) 사용 하 여 *범주* 의 값 **LC_ALL**를 **LC_MONETARY**, 또는 **LC_NUMERIC** 구조체의 내용을 덮어씁니다.

## <a name="remarks"></a>설명

합니다 **localeconv** 함수는 현재 로캘의 숫자 형식에 대 한 자세한 정보를 가져옵니다. 이 정보는 **lconv** 형식의 구조체에 저장됩니다. LOCALE.H에 저장된 **lconv** 구조체에는 다음 멤버가 포함됩니다.

|필드|의미|
|-|-|
decimal_point,<br/>_W_decimal_point|소수점 문자 비 통화 수량에 대 한 포인터입니다.
thousands_sep,<br/>_W_thousands_sep|비 통화 수량에 대 한 소수점 왼쪽의 숫자 그룹 구분 하는 문자에 대 한 포인터입니다.
그룹화|에 대 한 포인터를 **char**-자릿수 비 통화 수량에서 각 그룹의 크기를 포함 하는 정수 크기입니다.
int_curr_symbol,<br/>_W_int_curr_symbol|현재 로캘에 대 한 국제 통화 기호에 대 한 포인터입니다. 처음 세 문자는 *ISO 4217 Codes for the Representation of Currency and Funds* 표준에 정의된 대로 영문자 국제 통화 기호를 지정합니다. 네 번째 문자(null 문자 바로 앞)는 통화 수량에서 국제 통화 기호를 구분합니다.
currency_symbol,<br/>_W_currency_symbol|현재 로캘에 대 한 현지 통화 기호에 대 한 포인터입니다.
mon_decimal_point,<br/>_W_mon_decimal_point|소수점 문자 통화 수량에 대 한 포인터입니다.
mon_thousands_sep,<br/>_W_mon_thousands_sep|통화 수량에서 소수점 자리 왼쪽의 숫자 그룹 구분 기호에 대 한 포인터입니다.
mon_grouping|에 대 한 포인터를 **char**-자릿수 통화 수량에서 각 그룹의 크기를 포함 하는 정수 크기입니다.
positive_sign,<br/>_W_positive_sign|음수가 아닌 통화 수량에 대한 부호를 나타내는 문자열입니다.
negative_sign,<br/>_W_negative_sign|음수 통화 수량에 대한 부호를 나타내는 문자열입니다.
int_frac_digits|국제적으로 서식이 지정된 통화 수량에서 소수점 오른쪽의 자릿수입니다.
frac_digits|서식이 지정된 통화 수량에서 소수점 오른쪽의 자릿수입니다.
p_cs_precedes|통화 기호가 음수가 아닌 서식이 지정된 통화 수량에 대한 값보다 앞에 오면 1로 설정합니다. 기호가 값 다음에 오면 0으로 설정합니다.
p_sep_by_space|통화 기호가 음수가 아닌 서식이 지정된 통화 수량에 대한 값에서 공백으로 구분되면 1로 설정합니다. 공백으로 구분되지 않으면 0으로 설정합니다.
n_cs_precedes|통화 기호가 음수 서식이 지정된 통화 수량에 대한 값보다 앞에 오면 1로 설정합니다. 기호가 값 다음에 오면 0으로 설정합니다.
n_sep_by_space|통화 기호가 음수 서식이 지정된 통화 수량에 대한 값에서 공백으로 구분되면 1로 설정합니다. 공백으로 구분되지 않으면 0으로 설정합니다.
p_sign_posn|음수가 아닌 서식이 지정된 통화 수량에서 양수 부호의 위치입니다.
n_sign_posn|음수 서식이 지정된 통화 수량에서 양수 부호의 위치입니다.

지정 된 멤버를 제외 하 고는 **lconv** 있는 구조 `char *` 고 `wchar_t *` 버전은 문자열에 대 한 포인터입니다. 해당 하는 이러한 **""** (또는 **L ""** 에 대 한 **wchar_t** <strong>\*</strong>)은 길이가 0 또는 현재에서 지원 되지 않습니다 로캘입니다. 사실은 **decimal_point** 하 고 **_W_decimal_point** 는 항상 지원 되며 0이 아닌 길이의 합니다.

합니다 **char** 구조체의 멤버는 음수가 아닌 작은 숫자 이며 문자가 아닙니다. **CHAR_MAX**와 동일한 이러한 멤버는 현재 로캘에서 지원되지 않습니다.

값 **그룹화** 하 고 **mon_grouping** 다음 규칙에 따라 해석 됩니다.

- **CHAR_MAX** -그룹화를 더 이상 수행 하지 않습니다.

- 0-나머지 각 숫자에 대 한 이전 요소를 사용 합니다.

- *n* -현재 그룹을 구성 하는 자릿수입니다. 다음 요소를 검사하여 현재 그룹 앞 다음 숫자 그룹의 크기를 확인합니다.

**int_curr_symbol**에 대한 값은 다음 규칙에 따라 해석됩니다.

- 처음 세 문자는 *ISO 4217 Codes for the Representation of Currency and Funds* 표준에 정의된 대로 영문자 국제 통화 기호를 지정합니다.

- 네 번째 문자(null 문자 바로 앞)는 통화 수량에서 국제 통화 기호를 구분합니다.

**p_cs_precedes** 및 **n_cs_precedes**에 대한 값은 다음 규칙에 따라 해석됩니다. **n_cs_precedes** 규칙은 괄호 안에 표시됩니다.

- 0-통화 기호가 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 값을 따릅니다.

- 1-통화 기호는 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 값 앞에 옵니다.

**p_sep_by_space** 및 **n_sep_by_space**에 대한 값은 다음 규칙에 따라 해석됩니다. **n_sep_by_space** 규칙은 괄호 안에 표시됩니다.

- 0-통화 기호가 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 공백으로 값에서 구분 됩니다.

- 1-통화 기호가 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 값 사이의 공간 분리 되지 않습니다.

**p_sign_posn** 및 **n_sign_posn**에 대한 값은 다음 규칙에 따라 해석됩니다.

- 0-괄호 수량 및 통화 기호를 묶습니다.

- 1-부호 문자열이 수량 및 통화 기호를 앞에 옵니다.

- 2-부호 문자열이 수량 및 통화 기호를 따릅니다.

- 3-부호 문자열이 통화 기호에 바로 앞에 옵니다.

- 4-기호 바로 다음과 같이 통화 기호는 문자열입니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고자료

[로캘](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
