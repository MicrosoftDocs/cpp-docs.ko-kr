---
description: '다음에 대 한 자세한 정보: strftime, wcsftime, _strftime_l, _wcsftime_l'
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: f6297af6ad7c0f6f9a0280cc47ea7a0caa6440af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299568"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

시간 문자열 서식을 지정합니다.

## <a name="syntax"></a>구문

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*strDest*<br/>
출력 문자열입니다.

*크기*<br/>
*Strdest* 버퍼의 크기 ( **`char`** 또는 **`wchar_t`** )입니다.

*format*<br/>
형식 컨트롤 문자열입니다.

*timeptr*<br/>
**tm** 데이터 구조.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**strftime** 은 *strdest* 에 배치 된 문자 수를 반환 하 고 **wcsftime** 은 해당 하는 와이드 문자 수를 반환 합니다.

종료 null을 포함 한 총 문자 수가 *maxsize* 보다 많은 경우 **strftime** 및 **wcsftime** 은 모두 0을 반환 하 고 *strdest* 의 내용은 결정 되지 않습니다.

*Strdest* 의 문자 수는 형식 지정 코드를 통해 *형식* 에 추가 될 수 있는 문자 뿐만 아니라 *형식* 의 리터럴 문자 수와 같습니다. 문자열의 종료 null은 반환 값 계산에 포함되지 않습니다.

## <a name="remarks"></a>설명

**Strftime** 및 **wcsftime** 함수는 제공 된 *형식* 인수에 따라 *timeptr* 의 **tm** 시간 값을 지정 하 고 그 결과를 버퍼 *strdest* 에 저장 합니다. 최대 *maxsize* 문자는 문자열에 배치 됩니다. *Timeptr* 구조체의 필드에 대 한 설명은 [asctime](asctime-wasctime.md)를 참조 하세요. **wcsftime** 은 **strftime** 에 해당 하는 와이드 문자입니다. 해당 문자열 포인터 인수는 와이드 문자열을 가리킵니다. 그 외의 경우에는 이들 함수가 동일하게 작동합니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Strdest*, *format* 또는 *timeptr* 이 null 포인터인 경우 또는 *timeptr* 에서 주소가 지정 **된 tm** 데이터 구조가 잘못 된 경우 (예: 시간 또는 날짜에 대 한 범위를 벗어난 값을 포함 하는 경우), *형식* 문자열에 잘못 된 형식 지정 코드가 포함 된 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는 0을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*Format* 인수는 하나 이상의 코드로 구성 됩니다. **printf** 와 마찬가지로 형식 지정 코드 앞에 백분율 기호 ( **%** )가 있습니다. 로 시작 하지 않는 문자 **%** 는 변경 되지 않은 상태로 *strdest* 로 복사 됩니다. 현재 로캘의 **LC_TIME** 범주는 **strftime** 의 출력 형식에 영향을 줍니다. **LC_TIME** 에 대 한 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조 하세요. **Strftime** 및 **wcsftime** 함수는 현재 설정 된 로캘을 사용 합니다. 이러한 함수의 **_strftime_l** 및 **_wcsftime_l** 버전은 로캘을 매개 변수로 사용 하 고 현재 설정 된 로캘 대신 사용 한다는 점을 제외 하 고는 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

**Strftime** 함수는 다음과 같은 서식 지정 코드를 지원 합니다.

|코드|바꾸기 문자열|
|-|-|
|**% a**|로캘의 축약 된 요일 이름|
|**% A**|로캘의 전체 요일 이름|
|**% b**|로캘의 약식 월 이름|
|**% B**|로캘의 전체 월 이름|
|**% c**|로캘에 적합한 날짜 및 시간 표현|
|**% C**|100로 나누고 정수로 잘린 연도 (00-99)|
|**% d**|월의 일자 (10 진수) (01-31)|
|**% D**|**% M/% d/% y** 와 동일 합니다.|
|**% e**|10 진수 (1-31)로 서, 단일 숫자 앞에 공백이 있는 날짜|
|**% F**|**% Y-% m-% d** 과 (와) 동일 합니다.|
|**% g**|ISO 8601 주 기반 연도의 마지막 두 자리 (00-99)|
|**% G**|ISO 8601 주 기반 연도 (10 진수)입니다.|
|**% h**|약식 월 이름 ( **% b** 에 해당)|
|**% H**|24 시간 형식의 시간 (00-23)|
|**% I**|12 시간 형식의 시간 (01-12)|
|**% j**|10 진수의 일자 (001-366)|
|**% m**|월을 10 진수로 표시 합니다 (01-12).|
|**% M**|10 진수로 분 (00-59)|
|**% n**|줄 바꿈 문자 (**\n**)|
|**% p**|로캘의 오전 오전 12시간제 표시기|
|**% r**|로캘의 12 시간 시계 시간|
|**% R**|**% H:%M** 와 동일 합니다.|
|**% S**|10 진수 (00-59)입니다.|
|**% t**|가로 탭 문자 (**\t**)|
|**% T**|**% H:%M:% S**, ISO 8601 시간 형식에 해당 합니다.|
|**% u**|ISO 8601 평일 (1-7;) 월요일은 1)|
|**% U**|10 진수 (00-53)로 된 연간 주 번호입니다. 첫 번째 일요일은 1 주의 첫 번째 요일입니다.|
|**% V**|ISO 8601 주 번호 (00-53)|
|**% w**|10 진수로 평일 (0-6; 일요일은 0)|
|**% W**|10 진수 (00-53)로 된 연간 주 번호입니다. 첫 번째 월요일은 1 주의 첫 번째 요일입니다.|
|**% x**|로캘의 날짜 표시|
|**% X**|로캘에 대 한 시간 표현|
|**% y**|세기 없는 연도 (10 진수) (00-99)|
|**% Y**|세기 포함 10진수 연도|
|**% z**|ISO 8601 형식으로 된 UTC의 오프셋입니다. 표준 시간대를 알 수 없는 경우 문자 없음|
|**% Z**|레지스트리 설정에 따라 로캘의 표준 시간대 이름 또는 표준 시간대 약어 중 하나입니다. 표준 시간대를 알 수 없는 경우 문자 없음|
|**%%**|퍼센트 기호|

**Printf** 함수와 마찬가지로 **#** 플래그는 서식 지정 코드에 접두사를 지정할 수 있습니다. 이 경우의 서식 코드 의미는 다음과 같이 변경됩니다.

|코드 형식|의미|
|-----------------|-------------|
|**% #a**, **% #A**,% **#b**,% **#B**, **% #g**, **% #G**, **% #h**, **% #n**, **% #p**, **% #t**, **% #u**, **% #w**, **% #X**, **% #z**, **% #Z**, **%#%**|**#** 플래그는 무시 됩니다.|
|**% #c**|로캘에 적합 한 긴 날짜 및 시간 표현입니다. 예를 들면 "1995년 3월 14일 화요일 12:41:29"와 같습니다.|
|**% #x**|로캘에 적합 한 긴 날짜 표현입니다. 예를 들면 "1995년 3월 14일 화요일"과 같습니다.|
|**% #d**, **% #D**,% **#e**,% **#F**, **% #H**, **% #I**, **% #j**,% **#m**, **% #M**, **% #r**, **% #R,%**#S,% #T,% **#U**, **% #V**, **% #W**, **% #y**, **% #Y**  |앞에 오는 0 또는 공백을 제거 합니다 (있는 경우).|

**% V**, **% g**, **% g** 에 의해 생성 되는 ISO 8601 주 및 주 기반 연도는 월요일에 시작 하는 주를 사용 합니다. 여기서 week 1은 1 월 4 일을 포함 하는 주입니다. 여기서 1은 연도를 4 일 이상 포함 하는 첫 번째 주입니다. 해당 연도의 첫 번째 월요일이 두 번째, 세 번째 또는 네 번째 이면 이전 일은 작년의 마지막 주에 포함 됩니다. 이러한 일의 경우 **% V** 은 (는) 53로 바뀌고 **% g** 와 **% g** 는 모두 이전 연도의 숫자로 대체 됩니다.

> [!NOTE]
> 에서 반환 된 포인터가 있는 함수 중 하나를 사용 하는 경우 `strftime` `tm` `gmtime` 및 지정자를 통해 인쇄 된 값 `%Z` `%z` 이 정확 하지 않습니다. 이는 `tm` C 표준에 지정 된 구조체에 표준 시간대 이름 또는 오프셋에 대 한 정보가 포함 되지 않기 때문입니다. 대신 표준 시간대 정보는 전역 변수 [ `_timezone` 및 `_dstbias` ](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)를 통해 채워집니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 또는 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 또는 \<wchar.h>|

**_Strftime_l** 및 **_Wcsftime_l** 함수는 Microsoft 전용입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[time](time-time32-time64.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[로캘](../../c-runtime-library/locale.md) <br/>
[시간 관리](../../c-runtime-library/time-management.md) <br/>
[문자열 조작](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
