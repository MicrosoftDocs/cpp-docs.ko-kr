---
description: '다음에 대 한 자세한 정보: _locking'
title: _locking
ms.date: 4/2/2020
api_name:
- _locking
- _o__locking
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 087fc65edbb30bdb6e36b7410f29cf165b119d38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198806"
---
# <a name="_locking"></a>_locking

파일의 바이트를 잠그거나 잠금 해제합니다.

## <a name="syntax"></a>구문

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
파일 설명자입니다.

*mode*<br/>
수행할 잠금 작업입니다.

*nbytes*<br/>
잠글 바이트 수입니다.

## <a name="return-value"></a>반환 값

성공 하면 **_locking** 0을 반환 합니다. 반환 값-1은 오류를 나타내며,이 경우 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 는 다음 값 중 하나로 설정 됩니다.

|errno 값|조건|
|-|-|
| **EACCES** | 잠금 위반(파일이 이미 잠겨 있거나 잠금 해제됨)입니다. |
| **EBADF** | 잘못된 파일 설명자입니다. |
| **EDEADLOCK** | 잠금 위반입니다. **_LK_LOCK** 또는 **_LK_RLCK** 플래그가 지정 되 고 10 번의 시도 후 파일을 잠글 수 없는 경우 반환 됩니다. |
| **EINVAL** | **_Locking** 에 잘못 된 인수가 제공 되었습니다. |

잘못된 파일 설명자와 같이 잘못된 매개 변수로 인해 오류가 발생한 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다.

## <a name="remarks"></a>설명

**_Locking** 함수는 *fd* 에서 지정 된 파일의 *nbytes* 바이트를 잠그거나 잠금 해제 합니다. 파일의 바이트를 잠그면 다른 프로세스에서 해당 바이트에 액세스할 수 없습니다. 모든 잠금 또는 잠금 해제는 파일 포인터의 현재 위치에서 시작되며 다음 *nbytes* 바이트로 진행됩니다. 파일의 끝을 지난 바이트를 잠글 수 있습니다.

*mode* 는 Locking.h에 정의된 다음 매니페스트 상수 중 하나여야 합니다.

|*모드* 값|효과|
|-|-|
| **_LK_LOCK** | 지정된 바이트를 잠급니다. 바이트를 잠글 수 없는 경우 프로그램에서 1초 후 바로 다시 시도합니다. 10번 시도 후에도 바이트를 잠글 수 없으면 상수에서 오류가 반환됩니다. |
| **_LK_NBLCK** | 지정된 바이트를 잠급니다. 바이트를 잠글 수 없으면 상수에서 오류가 반환됩니다. |
| **_LK_NBRLCK** | **_LK_NBLCK** 와 동일 합니다. |
| **_LK_RLCK** | **_LK_LOCK** 와 동일 합니다. |
| **_LK_UNLCK** | 지정된 바이트를 잠금 해제합니다. 이러한 바이트는 이미 잠겨 있어야 합니다. |

파일에서 겹치지 않는 여러 영역을 잠글 수 있습니다. 잠금 해제할 영역은 이미 잠겨 있어야 합니다. **_locking** 인접 한 영역을 병합 하지 않습니다. 잠긴 두 지역이 인접해 있는 경우 각 지역은 별도로 잠금 해제 되어야 합니다. 영역은 일시적으로만 잠가야 하며 파일을 닫거나 프로그램을 종료하기 전에 잠금을 해제해야 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h> 및 \<sys/locking.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crt_lockingtxt"></a>입력: crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>샘플 출력

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
