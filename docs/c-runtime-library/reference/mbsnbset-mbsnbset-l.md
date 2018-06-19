---
title: _mbsnbset, _mbsnbset_l | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbset
- _mbsnbset_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
dev_langs:
- C++
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316580b0c5f1f46ffa9f4a49ef759b347032fc09
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404651"
---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset, _mbsnbset_l

설정 하는 첫 번째 **n** 바이트의 지정 된 문자를 멀티 바이트 문자 문자열입니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [_mbsnbset_s, _mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md)을 참조하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
변경할 문자열입니다.

*c*<br/>
단일 바이트나 멀티바이트 문자 설정입니다.

*count*<br/>
설정할 바이트 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**_mbsnbset** 변경된 된 문자열에 대 한 포인터를 반환 합니다.

## <a name="remarks"></a>설명

**_mbsnbset** 및 **_mbsnbset_l** 기능 설정, 최대, 첫 번째 *count* 바이트의 *str* 를 *c*. 경우 *개수* 의 길이 보다 크면 *str*, 길이의 *str* 대신 사용 됩니다 *count*합니다. 경우 *c* 는 멀티 바이트 문자가 고로 지정 된 마지막 바이트에 전체가 들어 맞지 설정할 수 없습니다 *count*, 마지막 바이트 빈 문자로 채워집니다. **_mbsnbset** 및 **_mbsnbset_l** 종료 두지 않는의 끝에 null *str*합니다.

**_mbsnbset** 및 **_mbsnbset_l** 비슷합니다 **_mbsnset**설정 한다는 점을 제외 하 고, *count* 바이트 보다는 *count* 문자 *c*합니다.

경우 *str* 은 **NULL** 또는 *count* 0 이면이 함수에 설명 된 대로 잘못 된 매개 변수 예외를 생성 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md). 실행을 계속 하도록 허용 된 경우 **errno** 로 설정 된 **EINVAL** 함수가 반환 하 고 **NULL**합니다. 또한 경우 *c* 은 유효한 멀티 바이트 문자가 아닙니다 **errno** 로 설정 된 **EINVAL** 공백을 대신 사용 됩니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따른 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. **_mbsnbset** 이 함수의 버전은이 로캘 종속 동작에 대 한 현재 로캘을 사용는 **_mbsnbset_l** 버전은 전달 된 로캘 매개 변수를 사용 하 여 제외 하 고 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

**보안 정보** 이 API는 버퍼 오버런 문제로 인해 발생하는 잠재적인 위협을 일으킵니다. 버퍼 오버런 문제는 자주 사용되는 시스템 공격 방법으로, 불필요한 권한 상승을 초래합니다. 자세한 내용은 [버퍼 오버런 방지](http://msdn.microsoft.com/library/windows/desktop/ms717795)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>출력

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>참고자료

[문자열 조작](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
