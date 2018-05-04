---
title: _lseek, _lseeki64 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lseeki64
- _lseek
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lseeki64
- _lseek
- lseeki64
dev_langs:
- C++
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb47214ac2de3c3e217bf41387ba206b94caf906
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="lseek-lseeki64"></a>_lseek, _lseeki64

지정된 위치로 파일 포인터를 이동합니다.

## <a name="syntax"></a>구문

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
열려 있는 파일을 참조하는 파일 설명자입니다.

*offset*<br/>
*origin*부터의 바이트 수입니다.

*origin*<br/>
초기 위치입니다.

## <a name="return-value"></a>반환 값

**_lseek** 파일의 시작 부분에서 새 위치로의 바이트 오프셋을 반환 합니다. **_lseeki64** 64 비트 정수에서 오프셋을 반환 합니다. 함수는 오류를 나타내기 위해-1l로 반환 합니다. 잘못된 파일 설명자와 같이 잘못된 매개 변수를 전달했거나, *origin*에 대한 값이 잘못되었거나, *offset*에 지정된 위치가 파일의 시작 이전인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 실행을 계속 허용 된, 이러한 함수 설정 **errno** 를 **EBADF** 고-1l을 반환 합니다. 검색을 수행할 수 없는 장치(예: 터미널 및 프린터)에서는 반환 값이 정의되지 않습니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_lseek** 와 관련 된 파일 포인터를 이동 하는 함수 *fd* 중인 새 위치에 *오프셋* 바이트 *원점*합니다. 파일에 대한 다음 작업은 새 위치에서 수행됩니다. *origin* 인수는 Stdio.h에 정의된 다음 상수 중 하나여야 합니다.

|*origin* 값||
|-|-|
**SEEK_SET**|파일 시작
**SEEK_CUR**|파일 포인터의 현재 위치
**SEEK_END**|파일 끝

사용할 수 있습니다 **_lseek** 파일 또는 파일의 끝을 넘어 아무 곳 이나 마우스 포인터 위치입니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crtlseekcinput"></a>입력: crt_lseek.c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>출력

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>참고자료

[하위 수준 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
