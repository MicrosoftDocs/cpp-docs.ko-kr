---
description: '자세히 알아보기: _memicmp, _memicmp_l'
title: _memicmp, _memicmp_l
ms.date: 4/2/2020
api_name:
- _memicmp_l
- _memicmp
- _o__memicmp
- _o__memicmp_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
ms.openlocfilehash: 261c7b64cc7da58c201515697addc587c575a9ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171415"
---
# <a name="_memicmp-_memicmp_l"></a>_memicmp, _memicmp_l

두 개의 버퍼에서 문자를 비교합니다(소문자).

## <a name="syntax"></a>구문

```C
int _memicmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int _memicmp_l(
   const void *buffer1,
   const void *buffer2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*buffer1*<br/>
첫 번째 버퍼입니다.

*buffer2*<br/>
두 번째 버퍼입니다.

*count*<br/>
문자 수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

반환 값은 부분 문자열 간의 관계를 나타냅니다.

|반환 값|buf1 및 buf2의 첫 번째 count 바이트의 관계|
|------------------|--------------------------------------------------------|
|< 0|*buffer1* 보다 작음 *buffer2*.|
|0|*buffer1* 는 *buffer2* 와 동일 합니다.|
|> 0|*buffer1* *buffer2* 보다 큽니다.|
|**_NLSCMPERROR**|오류가 발생했습니다.|

## <a name="remarks"></a>설명

**_Memicmp** 함수는 두 버퍼 *buffer1* 및 *buffer2* 바이트의 첫 번째 *count* 문자를 바이트 단위로 비교 합니다. 대/소문자를 구분하지 않고 비교합니다.

*Buffer1* 또는 *buffer2* 가 null 포인터인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 함수는 **_NLSCMPERROR** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

**_memicmp** 은 로캘 종속 동작에 현재 로캘을 사용 합니다. **_memicmp_l** 은 전달 된 로캘을 대신 사용 한다는 점을 제외 하 고 동일 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_memicmp**|\<memory.h> 또는 \<string.h>|
|**_memicmp_l**|\<memory.h> 또는 \<string.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_memicmp.c
// This program uses _memicmp to compare
// the first 29 letters of the strings named first and
// second without regard to the case of the letters.

#include <memory.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   int result;
   char first[] = "Those Who Will Not Learn from History";
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";
   // Note that the 29th character is right here ^

   printf( "Compare '%.29s' to '%.29s'\n", first, second );
   result = _memicmp( first, second, 29 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else if( result > 0 )
      printf( "First is greater than second.\n" );
}
```

```Output
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'
First is equal to second.
```

## <a name="see-also"></a>참고 항목

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
