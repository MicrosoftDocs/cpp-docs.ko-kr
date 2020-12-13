---
description: '자세한 정보: 숫자 값에 대 한 문자열 함수'
title: 문자열을 숫자 값으로 변환하는 함수
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: f560c83c8ae8d510b70804540e5360982770773c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339568"
---
# <a name="string-to-numeric-value-functions"></a>문자열을 숫자 값으로 변환하는 함수

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>설명

**strtod** 패밀리의 각 함수는 null로 끝나는 문자열을 숫자 값으로 변환합니다. 사용할 수 있는 함수는 다음 표에 나와 있습니다.

|함수|설명|
|--------------|-----------------|
|`strtod`|문자열을 배정밀도 부동 소수점 값으로 변환|
|`strtol`|문자열을 long 정수로 변환|
|`strtoul`|문자열을 부호 없는 long 정수로 변환|
|`_strtoi64`|문자열을 64 비트 정수로 변환 합니다. **`__int64`**|
|`_strtoui64`|문자열을 부호 없는 64 비트 정수로 변환 합니다. **`__int64`**|

`wcstod`, `wcstol`, `wcstoul`, 및 `_wcstoi64`는 각각 `strtod`, `strtol`, `strtoul` 및 `_strtoi64`의 와이드 문자 버전입니다. 이러한 각 와이드 문자 함수에 대한 문자열 인수는 와이드 문자 문자열이고, 각 함수는 싱글바이트 문자 문자열과 동일하게 동작합니다.

`strtod` 함수는 두 개의 인수를 사용합니다. 첫 번째 인수는 입력 문자열이고 두 번째 인수는 변환 프로세스를 종료하는 문자에 대한 포인터입니다. `strtol`, `strtoul`, **_strtoi64** 및 **_strtoui64** 는 세 번째 인수를 기수로 사용하여 변환 프로세스에 사용합니다.

입력 문자열은 지정된 형식의 숫자 값으로 해석될 수 있는 문자 시퀀스입니다. 각 함수는 숫자의 일부분으로 인식할 수 없는 첫 문자에서 문자열 읽기를 중지합니다. 이 문자는 종료 null 문자일 수 있습니다. `strtol`, `strtoul`, `_strtoi64`, 및 `_strtoui64`의 경우 이 종결 문자는 사용자가 제공한 기수보다 크거나 같은 첫 번째 숫자도 될 수 있습니다.

호출 시 변환 종료 문자에 대해 사용자가 제공한 포인터가 **NULL** 로 설정되어 있지 않은 경우 검색을 중지한 문자에 대한 포인터가 대신 거기에 저장됩니다. 올바른 숫자를 찾을 수 없거나 잘못된 밑을 지정하여 변환을 수행할 수 없는 경우에는 문자열 포인터의 값이 해당 주소에 저장됩니다.

`strtod`는 다음 형식의 문자열이 필요합니다.

[*공백*] [*sign*] [`digits`] [**.**`digits`] [{**d** &#124; **d** &#124; **e** &#124; **e**} [*sign*] `digits` ]

*whitespace* 는 공백 또는 탭 문자(무시됨)로 구성될 수 있습니다. *sign* 은 더하기 기호(**+**) 또는 빼기 기호(**-**)이고 `digits`는 하나 이상의 10진수입니다. 기수 문자 앞에 숫자가 없는 경우 기수 문자 뒤에는 숫자가 하나 이상 있어야 합니다. 10진수 뒤에 지수가 올 수 있습니다. 지수는 소개 문자(**d**, **D**, **e** 또는 **E**) 및 부호 있는 정수(선택 사항)로 구성됩니다. 지수 부분과 기수 문자가 모두 없으면 기수 문자는 문자열의 마지막 숫자를 따르는 것으로 간주합니다. 이 형식에 맞지 않는 첫 번째 문자가 발견되면 검색이 중지됩니다.

`strtol`, `strtoul`, `_strtoi64`, 및 `_strtoui64` 함수는 다음과 같은 형식의 문자열을 필요로 합니다.

[*공백*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [ `digits` ]

기본 인수는 2와 36 사이인 경우 숫자의 밑으로 사용됩니다. 0인 경우 변환 종료 포인터에서 참조하는 시작 문자가 밑을 결정하는 데 사용됩니다. 첫 번째 문자가 0이고 두 번째 문자가 'x' 또는 'X'가 아니면 문자열은 8진수 정수로 해석됩니다. 그렇지 않은 경우 10진수로 해석됩니다. 첫 번째 문자가 '0'이고 두 번째 문자가 'x' 또는 'X'이면 문자열은 16진수 정수로 해석됩니다. 첫 번째 문자가 '1'~'9' 이면 문자열은 10진수 정수로 해석됩니다. 문자 'a'~'z' 또는 'A'~'Z'에는 값 10~35가 할당됩니다. 할당된 값이 *밑* 보다 작은 문자만 사용할 수 있습니다. `strtoul``_strtoui64`더하기 ( **+** ) 또는 빼기 기호 ()를 허용 **-** 합니다. 앞에 빼기 기호는 반환 값이 부정 됨을 나타냅니다.

출력 값은 로캘의 `LC_NUMERIC` 범주 설정에 영향을 받습니다. 자세한 내용은 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 참조하세요. **_l** 접미사가 없는 이러한 함수 버전은 이 로캘 종속 동작에 현재 로캘을 사용하며, **_l** 접미사가 있는 버전은 전달된 로캘 매개 변수를 대신 사용하는 경우를 제외하고는 동일합니다.

이러한 함수에서 반환하는 값이 오버플로 또는 언더플로의 원인이 되거나 변환이 불가능한 경우 특수한 경우 값이 다음과 같이 반환됩니다.

|함수|조건|반환 값|
|--------------|---------------|--------------------|
|`strtod`|오버플로|+/- `HUGE_VAL`|
|`strtod`|언더플로 또는 변환 없음|0|
|`strtol`|+ 오버플로|**LONG_MAX**|
|`strtol`|- 오버플로|**LONG_MIN**|
|`strtol`|언더플로 또는 변환 없음|0|
|`_strtoi64`|+ 오버플로|**_I64_MAX**|
|`_strtoi64`|- 오버플로|**_I64_MIN**|
|`_strtoi64`|변환 없음|0|
|`_strtoui64`|오버플로|**_UI64_MAX**|
|`_strtoui64`|변환 없음|0|

**_I64_MAX**, _ **I64_MIN** 및 **_UI64_MAX** 는 LIMITS.H에 정의됩니다.

`wcstod`, `wcstol`, `wcstoul`, `_wcstoi64` 및 `_wcstoui64`는 각각 `strtod`, `strtol`, `strtoul`, `_strtoi64` 및 `_strtoui64`의 와이드 문자 버전이며, 이러한 각 와이드 문자 함수의 변환 종료 인수에 대한 포인터는 와이드 문자열입니다. 그렇지 않은 경우 이러한 각 와이드 문자 함수는 싱글바이트 문자 함수와 동일하게 동작합니다.

## <a name="see-also"></a>참고 항목

[데이터 변환](../c-runtime-library/data-conversion.md)<br/>
[로캘](../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[부동 소수점 지원](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
