---
description: '자세한 정보: strtol ,, wcstol _strtol_l , _wcstol_l'
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: 8dd175929335533f8ade91450608db7f39bc0cc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288674"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

문자열을 **`long`** 정수 값으로 변환 합니다.

## <a name="syntax"></a>구문

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*문자열*\
변환할 Null 종료 문자열입니다.

*end_ptr*\
출력 매개 변수는 마지막 해석 문자 뒤의 문자를 가리키도록 설정 합니다. **NULL** 인 경우 무시 됩니다.

*하단*\
사용할 기수입니다.

*로캘을*\
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**strtol**, **wcstol** , **_strtol_l** 및 **_wcstol_l** 는 *문자열* 에 표시 된 값을 반환 합니다. 변환할 수 없는 경우 0을 반환 합니다. 표현이 오버플로를 발생 시키는 경우 또는를 반환 **LONG_MAX** **LONG_MIN** 합니다.

**errno****ERANGE** 오버플로 또는 언더플로가 발생 하면가로 설정 됩니다. **EINVAL** *문자열이* **NULL** 인 경우로 설정 됩니다. 또는 *base* 가 0이 아니고 2 보다 작거나 36 보다 큰 경우입니다. **ERANGE**, 및 기타 반환 코드에 대 한 자세한 내용은 **EINVAL** [_dos errno , errno , _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요.

## <a name="remarks"></a>설명

**strtol**,, **wcstol** 및 함수는 문자열을으로 **_strtol_l** **_wcstol_l** 변환  **`long`** 합니다. 숫자의 일부로 인식 되지 않는 첫 번째 문자에서 *문자열* 읽기를 중지 합니다. 이 문자는 종료 null 문자 이거나 *base* 보다 크거나 같은 첫 번째 영숫자 문자일 수 있습니다.

**wcstol** 및 **_wcstol_l** 는 및의 와이드 문자 버전 **strtol** 입니다 **_strtol_l** . *문자열* 인수는 와이드 문자열입니다. 이러한 함수는와 동일 하 게 작동 **strtol** **_strtol_l** 합니다. 로캘의 **LC_NUMERIC** 범주 설정에 따라 *문자열* 의 기 개수 문자 (분수 표식 또는 소수점) 인식이 결정 됩니다. 함수 **strtol** 및는 **wcstol** 현재 로캘을 사용 합니다. **_strtol_l****_wcstol_l** 대신 전달 된 로캘을 사용 합니다. 자세한 내용은 [ setlocale ] 및 [로캘](../../c-runtime-library/locale.md)을 참조 하세요.

*End_ptr* **NULL** 인 경우에는 무시 됩니다. 그렇지 않은 경우 검색을 중지 한 문자에 대 한 포인터는 *end_ptr* 가 가리키는 위치에 저장 됩니다. 올바른 숫자를 찾을 수 없거나 잘못 된 기본이 지정 된 경우 변환이 가능 하지 않습니다. 그런 다음 *문자열* 의 값은 *end_ptr* 가 가리키는 위치에 저장 됩니다.

**strtol***문자열* 은 다음 형식의 문자열을 가리키도록 합니다.

> [*공백*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*영숫자*]

대괄호 ( `[ ]` )는 선택적 요소를 둘러쌉니다. 단일 요소를 대체 하는 중괄호와 세로 막대 ( `{ | }` )를 둘러쌉니다. *공백은 무시* 되는 공백과 탭 문자로 구성 될 수 있습니다. *영숫자* 는 10 진수 또는 ' a ' ~ ' z ' (또는 ' a ' ~ ' z ')입니다. 이 폼에 맞지 않는 첫 번째 문자는 검색을 중지 합니다. *Base* 가 2에서 36 사이인 경우 숫자의 밑으로 사용 됩니다. *Base* 가 0 인 경우 *문자열* 에서 가리키는 문자열의 초기 문자를 사용 하 여 기본를 확인 합니다. 첫 번째 문자가 0이 고 두 번째 문자가 ' x ' 또는 ' X '가 아니면 문자열은 8 진수 정수로 해석 됩니다. 첫 번째 문자가 '0'이고 두 번째 문자가 'x' 또는 'X'이면 문자열은 16진수 정수로 해석됩니다. 첫 번째 문자가 '1'~'9' 이면 문자열은 10진수 정수로 해석됩니다. 문자 ' a ' ~ ' z ' (또는 ' A ' ~ ' Z ')에는 값 10 ~ 35이 할당 됩니다. 검색에서는 값이 *base* 보다 작은 문자만 사용할 수 있습니다. 밑의 범위를 벗어난 첫 번째 문자가 발견되면 검색이 중지됩니다. 예를 들어 *문자열* 은 "01"로 시작 한다고 가정 합니다. *Base* 가 0 인 경우 스캐너는 8 진수 정수인 것으로 가정 합니다. ' 8 ' 또는 ' 9 ' 문자는 검색을 중지 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> 또는 \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> 또는 \<wchar.h>|

**_strtol_l** 및 **_wcstol_l** 함수는 Microsoft 전용 이며 표준 C 라이브러리의 일부가 아닙니다. 호환성에 대한 자세한 내용은 [Compatibility](../compatibility.md)을 참조하세요.

## <a name="example"></a>예제

의 예제를 참조 하세요 [strtod](strtod-strtod-l-wcstod-wcstod-l.md) .

## <a name="see-also"></a>참고 항목

[데이터 변환](../data-conversion.md)\
[로캘을](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[문자열-숫자 값 함수](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
