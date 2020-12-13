---
description: '자세한 정보: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32'
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
ms.openlocfilehash: b7c9bd6994506cabd27bfad949bbe7ec3784ffcc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334246"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

열린 파일에 대한 정보를 가져옵니다.

## <a name="syntax"></a>구문

```C
int _fstat(
   int fd,
   struct _stat *buffer
);
int _fstat32(
   int fd,
   struct __stat32 *buffer
);
int _fstat64(
   int fd,
   struct __stat64 *buffer
);
int _fstati64(
   int fd,
   struct _stati64 *buffer
);
int _fstat32i64(
   int fd,
   struct _stat32i64 *buffer
);
int _fstat64i32(
   int fd,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
열린 파일의 파일 설명자입니다.

*버퍼*<br/>
결과를 저장할 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

파일 상태 정보를 가져오는 경우 0을 반환합니다. 반환 값-1은 오류를 나타냅니다. 파일 설명자가 잘못 되었거나 *버퍼가* **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 는 **ebadf** 로 설정 되 고, 잘못 된 파일 설명자의 경우에는 **EINVAL** 로 설정 되 고, *버퍼가* **NULL** 인 경우에는로 설정 됩니다.

## <a name="remarks"></a>설명

**_Fstat** 함수는 *fd* 와 연결 된 열려 있는 파일에 대 한 정보를 가져와 *버퍼* 에 의해 가리키는 구조에 저장 합니다. SYS\Stat.h에 정의 된 **_stat** 구조에는 다음 필드가 포함 됩니다.

|필드|의미|
|-|-|
| **st_atime** | 마지막 파일 액세스 시간입니다. |
| **st_ctime** | 파일 생성 시간입니다. |
| **st_dev** | 장치인 경우 *fd*; 그렇지 않으면 0입니다. |
| **st_mode** | 파일 모드 정보의 비트 마스크입니다. *Fd* 가 장치를 참조 하는 경우 **_S_IFCHR** 비트가 설정 됩니다. *Fd* 가 일반 파일을 참조 하는 경우 **_S_IFREG** 비트가 설정 됩니다. 파일의 사용 권한 모드에 따라 사용자 읽기/쓰기 비트가 설정됩니다. **_S_IFCHR** 및 기타 상수는 Sys\stv\stvhs에 정의 됩니다. |
| **st_mtime** | 파일의 마지막 수정 시간입니다. |
| **st_nlink** | NTFS가 아닌 파일 시스템에서 항상 1입니다. |
| **st_rdev** | 장치인 경우 *fd*; 그렇지 않으면 0입니다. |
| **st_size** | 파일 크기(바이트)입니다. |

*Fd* 가 장치를 참조 하는 경우 **st_atime**, **st_ctime**, **st_mtime** 및 **st_size** 필드는 의미가 없습니다.

Stat.h에서는 Types.h에 정의된 [_dev_t](../../c-runtime-library/standard-types.md) 형식을 사용하므로 코드에서 Stat.h 앞에 Types.h를 포함해야 합니다.

**__stat64** 구조를 사용 하는 **_fstat64** 는 파일 생성 날짜를 23:59:59 년 12 월 31 일, 3000 년 12 월 31 일까 지 표현할 수 있습니다. 반면 다른 함수는 날짜를 23:59:59 년 1 월 18 일 년 1 월 2038 18 일 까지만 나타냅니다. 1970년 1월 1일 자정은 이러한 모든 함수에 대한 날짜 범위의 하한입니다.

이러한 함수의 변형은 32비트 또는 64비트 시간 형식과 32비트 또는 64비트 파일 길이를 지원합니다. 첫 번째 숫자 접미사 (**32** 또는 **64**)는 사용 된 시간 형식의 크기를 나타냅니다. 두 번째 접미사는 **i32** 또는 **i64** 중 하나 이며, 파일 크기가 32 비트 또는 64 비트 정수로 표시 되는지를 나타냅니다.

**_fstat** 은 **_fstat64i32** 와 같으며 **`struct`** **_stat** 에는 64 비트 시간이 포함 됩니다. 이는 **_USE_32BIT_TIME_T** 정의 되지 않는 한 true 이며,이 경우 이전 동작이 적용 됩니다. **_fstat** 는 32 비트 시간을 사용 하 고 **`struct`** **_stat** 는 32 비트 시간을 포함 합니다. **_Fstati64** 에도 마찬가지입니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat의 시간 형식 및 파일 길이 형식 변형

|함수|_USE_32BIT_TIME_T 정의 여부|시간 형식|파일 길이 형식|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|정의되지 않음|64비트|32비트|
|**_fstat**|정의됨|32비트|32비트|
|**_fstat32**|매크로 정의의 영향을 받지 않음|32비트|32비트|
|**_fstat64**|매크로 정의의 영향을 받지 않음|64비트|64비트|
|**_fstati64**|정의되지 않음|64비트|64비트|
|**_fstati64**|정의됨|32비트|64비트|
|**_fstat32i64**|매크로 정의의 영향을 받지 않음|32비트|64비트|
|**_fstat64i32**|매크로 정의의 영향을 받지 않음|64비트|32비트|

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> 및 \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> 및 \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> 및 \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> 및 \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> 및 \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> 및 \<sys/types.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fstat.c
// This program uses _fstat to report
// the size of a file named F_STAT.OUT.

#include <io.h>
#include <fcntl.h>
#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <share.h>

int main( void )
{
   struct _stat buf;
   int fd, result;
   char buffer[] = "A line to output";
   char timebuf[26];
   errno_t err;

   _sopen_s( &fd,
             "f_stat.out",
             _O_CREAT | _O_WRONLY | _O_TRUNC,
             _SH_DENYNO,
             _S_IREAD | _S_IWRITE );
   if( fd != -1 )
      _write( fd, buffer, strlen( buffer ) );

   // Get data associated with "fd":
   result = _fstat( fd, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      if (errno == EBADF)
        printf( "Bad file descriptor.\n" );
      else if (errno == EINVAL)
        printf( "Invalid argument to _fstat.\n" );
   }
   else
   {
      printf( "File size     : %ld\n", buf.st_size );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid argument to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
   _close( fd );
}
```

```Output
File size     : 16
Time modified : Wed May 07 15:25:11 2003
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat 함수](stat-functions.md)<br/>
