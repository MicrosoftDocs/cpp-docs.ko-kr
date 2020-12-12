---
description: '자세히 알아보기: localeconv'
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: 488a6e9dbc913f1102be3a53685dc68b38fb833b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195673"
---
# <a name="localeconv"></a>localeconv

로캘 설정에 대한 자세한 정보를 가져옵니다.

## <a name="syntax"></a>구문

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Return Value

**localeconv** 는 [struct lconv](../../c-runtime-library/standard-types.md)형식의 채워진 개체에 대 한 포인터를 반환 합니다. 개체에 포함 된 값은 스레드 로컬 저장소의 로캘 설정에서 복사 되며 **localeconv** 에 대 한 후속 호출로 덮어쓸 수 있습니다. 이 개체의 값을 변경 해도 로캘 설정은 수정 되지 않습니다. **LC_ALL**, **LC_MONETARY** 또는 **LC_NUMERIC** *범주* 값이 포함 된 [setlocale](setlocale-wsetlocale.md) 호출은 구조체의 내용을 덮어씁니다.

## <a name="remarks"></a>설명

**Localeconv** 함수는 현재 로캘의 숫자 서식에 대 한 자세한 정보를 가져옵니다. 이 정보는 **lconv** 형식의 구조체에 저장됩니다. LOCALE.H에 저장된 **lconv** 구조체에는 다음 멤버가 포함됩니다.

|필드|의미|
|-|-|
decimal_point,<br/>_W_decimal_point|비 통화 수량에 대 한 소수점 문자 포인터입니다.
thousands_sep,<br/>_W_thousands_sep|비 통화 수량에 대 한 소수점 왼쪽의 숫자 그룹을 구분 하는 문자에 대 한 포인터입니다.
그룹화|**`char`** 비 통화 수량에서 각 숫자 그룹의 크기를 포함 하는 크기가 지정 된 정수에 대 한 포인터입니다.
int_curr_symbol,<br/>_W_int_curr_symbol|현재 로캘의 국제 통화 기호에 대 한 포인터입니다. 처음 세 문자는 *ISO 4217 Codes for the Representation of Currency and Funds* 표준에 정의된 대로 영문자 국제 통화 기호를 지정합니다. 네 번째 문자(null 문자 바로 앞)는 통화 수량에서 국제 통화 기호를 구분합니다.
currency_symbol,<br/>_W_currency_symbol|현재 로캘의 현지 통화 기호에 대 한 포인터입니다.
mon_decimal_point,<br/>_W_mon_decimal_point|통화 수량의 소수점 문자에 대 한 포인터입니다.
mon_thousands_sep,<br/>_W_mon_thousands_sep|통화 수량에서 소수점 왼쪽에 있는 숫자 그룹의 구분 기호에 대 한 포인터입니다.
mon_grouping|**`char`** 통화 수량에서 각 숫자 그룹의 크기를 포함 하는 크기 조정 된 정수에 대 한 포인터입니다.
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

지정 된 경우를 제외 하 고 및 버전이 포함 된 **lconv** 구조체의 멤버 `char *` `wchar_t *` 는 문자열에 대 한 포인터입니다. **""** (또는 **L "** 의 경우)와 같은 이러한 **`wchar_t`** <strong>\*</strong> 값은 길이가 0 이거나 현재 로캘에서 지원 되지 않습니다. **Decimal_point** 및 **_W_decimal_point** 는 항상 지원 되며 0이 아닌 길이입니다.

**`char`** 구조체의 멤버는 문자가 아닌 음수가 아닌 작은 숫자입니다. **CHAR_MAX** 와 동일한 이러한 멤버는 현재 로캘에서 지원되지 않습니다.

**그룹화** 및 **mon_grouping** 의 값은 다음 규칙에 따라 해석 됩니다.

- **CHAR_MAX** -추가 그룹화를 수행 하지 않습니다.

- 0-나머지 각 자릿수에 대해 이전 요소를 사용 합니다.

- *n* -현재 그룹을 구성 하는 숫자입니다. 다음 요소를 검사하여 현재 그룹 앞 다음 숫자 그룹의 크기를 확인합니다.

**int_curr_symbol** 에 대한 값은 다음 규칙에 따라 해석됩니다.

- 처음 세 문자는 *ISO 4217 Codes for the Representation of Currency and Funds* 표준에 정의된 대로 영문자 국제 통화 기호를 지정합니다.

- 네 번째 문자(null 문자 바로 앞)는 통화 수량에서 국제 통화 기호를 구분합니다.

**p_cs_precedes** 및 **n_cs_precedes** 에 대한 값은 다음 규칙에 따라 해석됩니다. **n_cs_precedes** 규칙은 괄호 안에 표시됩니다.

- 0-통화 기호가 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 값을 따릅니다.

- 1-통화 기호가 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 값 보다 앞에 옵니다.

**p_sep_by_space** 및 **n_sep_by_space** 에 대한 값은 다음 규칙에 따라 해석됩니다. **n_sep_by_space** 규칙은 괄호 안에 표시됩니다.

- 0-통화 기호가 음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 값에서 공백으로 구분 됩니다.

- 1-음수가 아닌 (음수) 서식이 지정 된 통화 값에 대 한 통화 기호와 값 사이에 공백이 구분 되지 않습니다.

**p_sign_posn** 및 **n_sign_posn** 에 대한 값은 다음 규칙에 따라 해석됩니다.

- 0-괄호는 수량 및 통화 기호를 묶습니다.

- 1-부호 문자열이 수량 및 통화 기호 앞에 옵니다.

- 2-부호 문자열이 수량 및 통화 기호를 따릅니다.

- 3-부호 문자열이 통화 기호 바로 앞에 옵니다.

- 4-부호 문자열이 통화 기호 바로 다음에 옵니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[로캘](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
