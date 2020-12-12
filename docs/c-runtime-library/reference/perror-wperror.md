---
description: Perror, _wperror에 대해 자세히 알아보세요.
title: perror, _wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: e63108ac90170d460ee8a2c86e1db773343c1911
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304690"
---
# <a name="perror-_wperror"></a>perror, _wperror

오류 메시지를 인쇄합니다.

## <a name="syntax"></a>구문

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>매개 변수

*message*<br/>
인쇄할 문자열 메시지입니다.

## <a name="remarks"></a>설명

**Perror** 함수는 오류 메시지를 **stderr** 에 출력 합니다. **_wperror** 은 **_perror** 의 와이드 문자 버전입니다. **_wperror** 에 대 한 *메시지* 인수는 와이드 문자열입니다. **_wperror** 와 **_perror** 는 동일 하 게 동작 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*메시지가* 먼저 인쇄 된 후 콜론, 오류를 생성 한 마지막 라이브러리 호출에 대 한 시스템 오류 메시지 및 줄 바꿈 문자가 차례로 인쇄 됩니다. *메시지가* null 포인터 또는 null 문자열에 대 한 포인터인 경우 **perror** 는 시스템 오류 메시지만 인쇄 합니다.

오류 번호는 ERRNO.H에 정의되어 있는 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 변수에 저장됩니다. [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 변수를 통해 시스템 오류 메시지에 액세스합니다. 이 변수는 오류 번호순으로 정렬된 메시지 배열입니다. **perror** 는 **_sys_errlist** 에 대 한 인덱스로 **errno** 값을 사용 하 여 적절 한 오류 메시지를 인쇄 합니다. 변수 [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 의 값은 **_sys_errlist** 배열의 최대 요소 수로 정의 됩니다.

정확한 결과를 위해 라이브러리 루틴이 오류와 함께 반환 되는 즉시 **perror** 를 호출 합니다. 그렇지 않으면 후속 호출에서 **errno** 값을 덮어쓸 수 있습니다.

Windows 운영 체제에서 일부 **errno** 값은 errno에 나열 됩니다. H는 사용 되지 않습니다. 이러한 값은 UNIX 운영 체제에서 사용되도록 예약되어 있습니다. Windows 운영 체제에서 사용 하는 **errno** 값 목록은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 를 참조 하세요. **perror** 는 이러한 플랫폼에서 사용 하지 않는 모든 **errno** 값에 대 한 빈 문자열을 인쇄 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**perror**|\<stdio.h> 또는 \<stdlib.h>|
|**_wperror**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \_ _wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
