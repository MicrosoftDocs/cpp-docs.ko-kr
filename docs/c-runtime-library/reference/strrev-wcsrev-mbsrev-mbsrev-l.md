---
description: '자세한 정보: _strrev, _wcsrev, _mbsrev, _mbsrev_l'
title: _strrev, _wcsrev, _mbsrev, _mbsrev_l
ms.date: 4/2/2020
api_name:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
- _o__mbsrev
- _o__mbsrev_l
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
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
ms.openlocfilehash: c3e1e0483220daca9182f6ee8a312dfc6589caf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296175"
---
# <a name="_strrev-_wcsrev-_mbsrev-_mbsrev_l"></a>_strrev, _wcsrev, _mbsrev, _mbsrev_l

문자열의 문자 순서를 반대로 바꿉니다.

> [!IMPORTANT]
> **_mbsrev** 및 **_mbsrev_l** 는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
순서를 반대로 바꿀 Null 종료 문자열입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

변경된 문자열에 대한 포인터를 반환합니다. 반환 값 없음은 오류를 나타내는 데 예약되어 있습니다.

## <a name="remarks"></a>설명

**_Strrev** 함수는 *str* 의 문자 순서를 반대로 바꿉니다. 종료 null 문자는 현재 위치에 유지됩니다. **_wcsrev** 및 **_mbsrev** 는 **_strrev** 의 와이드 문자 및 멀티 바이트 문자 버전입니다. **_Wcsrev** 의 인수 및 반환 값은 와이드 문자 문자열입니다. **_mbsrev** 의 이러한 문자열은 멀티 바이트 문자열입니다. **_Mbsrev** 의 경우 *str* 의 각 멀티 바이트 문자의 바이트 순서는 변경 되지 않습니다. 그렇지 않으면 이들 세 함수는 동일하게 작동합니다.

**_mbsrev** 은 해당 매개 변수의 유효성을 검사 합니다. *String1* 또는 *문자열* 하나가 Null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **_Mbsrev** **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다. **_strrev** 및 **_wcsrev** 는 매개 변수의 유효성을 검사 하지 않습니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따라 영향을 받습니다. 자세한 내용은 [setlocale, _wsetlocale를](setlocale-wsetlocale.md) 참조 하세요. **_L** 접미사가 없는 함수는 현재 로캘을 사용 하 고 **_l** 접미사가 있는 함수는 전달 된 로캘 매개 변수를 대신 사용 한다는 점을 제외 하 고 이러한 함수의 버전은 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

> [!IMPORTANT]
> 이러한 함수는 버퍼 오버런 위협에 노출될 수 있습니다. 버퍼 오버런은 불필요한 권한 상승을 발생시킬 수 있으므로 시스템 공격에 사용될 수 있습니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**해당 없음**|**해당 없음**|**_mbsrev_l**|**해당 없음**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_strrev**|\<string.h>|
|**_wcsrev**|\<string.h> 또는 \<wchar.h>|
|**_mbsrev**, **_mbsrev_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>참고 항목

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[로캘](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
