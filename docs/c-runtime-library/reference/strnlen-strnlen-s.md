---
description: '다음에 대 한 자세한 정보: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l'
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: 2f38ba18647b232e19e2ecda94519a8a0e55a444
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336456"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

현재 로캘이나 전달된 로캘을 사용하여 문자열 길이를 가져옵니다. 이러한 함수는 [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)의 더 안전한 버전입니다.

> [!IMPORTANT]
> **_mbsnlen**, **_mbsnlen_l**, **_mbstrnlen** 및 **_mbstrnlen_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
Null 종료 문자열입니다.

*이면 numberofelements 이벤트가*<br/>
문자열 버퍼의 크기입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

이러한 함수는 null 종결 문자를 제외하고 문자열에 있는 문자의 수를 반환합니다. 문자열의 첫 번째 *numberofelements* 바이트 (또는 **wcsnlen** 의 와이드 문자) 내에 null 종결자가 없는 경우에는 오류 조건을 나타내기 위해 *numberofelements* 가 반환 됩니다. null로 끝나는 문자열의 길이는 *Numberofelements* 보다 작아야 합니다.

문자열에 잘못 된 멀티 바이트 문자가 포함 된 경우 **_mbstrnlen** 와 **_mbstrnlen_l** 는-1을 반환 합니다.

## <a name="remarks"></a>설명

> [!NOTE]
> **strnlen** 은 **strlen** 을 대체 하지 않습니다. **strnlen** 은 알려진 크기의 버퍼에서 들어오는 신뢰할 수 없는 데이터의 크기 (예: 네트워크 패킷)를 계산 하는 용도로만 사용 됩니다. **strnlen** 은 길이를 계산 하지만 문자열이 종결 되지 않은 경우 버퍼의 끝을 지나서 이동 하지 않습니다. 다른 경우에는 **strlen** 을 사용 합니다. **Wcsnlen**, **_mbsnlen** 및 **_mbstrnlen** 에도 동일 하 게 적용 됩니다.

이러한 각 함수는 null 종결 문자를 포함 하지 않고 *str* 의 문자 수를 반환 합니다. 그러나 **strnlen** 및 **strnlen_s** 는 문자열을 싱글바이트 문자열로 해석 하므로 문자열에 멀티 바이트 문자가 포함 되어 있더라도 반환 값은 항상 바이트 수와 동일 합니다. **wcsnlen** 및 **wcsnlen_s** 는 각각 **strnlen** 및 **strnlen_s** 의 와이드 문자 버전입니다. **wcsnlen** 및 **wcsnlen_s** 에 대 한 인수는 와이드 문자열이 고 문자 수는 와이드 문자 단위입니다. 그렇지 않으면 **strnlen_s** 와 **wcsnlen_s** 같이 **wcsnlen** 및 **strnlen** 이 동일 하 게 작동 합니다.

**strnlen**, **wcsnlen** 및 **_mbsnlen** 는 해당 매개 변수의 유효성을 검사 하지 않습니다. *Str* 이 **NULL** 이면 액세스 위반이 발생 합니다.

**strnlen_s** 하 고 **wcsnlen_s** 매개 변수의 유효성을 검사 합니다. *Str* 이 **NULL** 인 경우 함수는 0을 반환 합니다.

또한 **_mbstrnlen** 은 해당 매개 변수의 유효성을 검사 합니다. *Str* 이 **NULL** 이거나 *numberofelements* 가 **INT_MAX** 보다 큰 경우에는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 **_mbstrnlen** 에서 잘못 된 매개 변수 예외를 생성 합니다. 계속 해 서 실행 하도록 허용한 경우 **_mbstrnlen** 는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** 및 **_mbstrnlen** 는 멀티 바이트 문자열의 멀티 바이트 문자 수를 반환 합니다. **_mbsnlen** 는 현재 사용 중인 멀티 바이트 코드 페이지 또는 전달 된 로캘에 따라 멀티 바이트 문자 시퀀스를 인식 합니다. 멀티 바이트 문자의 유효성을 테스트 하지는 않습니다. **_mbstrnlen** 멀티 바이트 문자의 유효성을 테스트 하 고 멀티 바이트 문자 시퀀스를 인식 합니다. **_Mbstrnlen** 전달 되는 문자열에 잘못 된 멀티 바이트 문자가 포함 된 경우 **Errno** 는 **eilseq** 로 설정 됩니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따라 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale를](setlocale-wsetlocale.md) 참조 하세요. **_L** 접미사가 없는 함수는이 로캘 종속 동작에 현재 로캘을 사용 하 고 **_l** 접미사가 있는 버전은 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고 이러한 함수의 버전은 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> 또는 \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll 함수](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
