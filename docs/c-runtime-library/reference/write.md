---
description: '다음에 대 한 자세한 정보: _write'
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 15988f803b37f9ce128a49662c2311a4aa6ca8fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117161"
---
# <a name="_write"></a>_write

파일에 데이터를 씁니다.

## <a name="syntax"></a>구문

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
데이터를 쓸 파일의 파일 설명자입니다.

*버퍼*<br/>
쓸 데이터입니다.

*count*<br/>
바이트 수입니다.

## <a name="return-value"></a>반환 값

성공 하면 **_write** 은 쓴 바이트 수를 반환 합니다. 디스크에 남아 있는 실제 공간이 함수가 디스크에 쓰려고 하는 버퍼의 크기 보다 적으면 **_write** 는 실패 하 고 버퍼의 내용을 디스크에 플러시하지 않습니다. 반환 값-1은 오류를 나타냅니다. 잘못된 매개 변수가 전달되면 이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속 해 서 실행 하도록 허용한 경우 함수는-1을 반환 하 고 **errno** 는 **ebadf** 의 세 값 중 하나로 설정 됩니다. 즉, 파일 설명자가 잘못 되었거나 파일이 쓰기용으로 열리지 않습니다. **ENOSPC** 는 작업을 위해 장치에 남아 있는 공간이 부족 함을 의미 합니다. 또는 **EINVAL** 는 *버퍼가* null 포인터 이거나 유니코드 모드 *에서 홀수 바이트 수가 파일* 에 기록 되도록 전달 되었음을 의미 합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

파일이 텍스트 모드에서 열리면 각 줄 바꿈 문자는 출력에서 캐리지 리턴-줄 바꿈 쌍으로 바뀝니다. 대체는 반환 값에 영향을 주지 않습니다.

파일이 유니코드 변환 모드에서 열리는 경우 (예: **_open** 또는 **_sopen** 를 사용 하 여 *fd* 를 연 경우와 **_O_WTEXT** 포함 된 모드 매개 변수를 사용 하는 경우 **_O_U16TEXT** 또는 **_O_U8TEXT** 하거나, **fopen** 을 사용 하 여 연 경우 또는 ccs = **Unicode**, **ccs = utf-16le** 또는 **ccs = u s f-8** 을 포함 하는 모드 매개 변수를 사용 하 여 연 경우 또는 **_setmode** 를 사용 하 여 모드를 유니코드 변환 모드로 변경한 경우 *버퍼* 는 **`wchar_t`** **utf-16** 데이터가 포함 된의 배열에 대 한 포인터로 해석 됩니다. 이 모드에서 홀수 바이트를 쓰려고 하면 매개 변수 유효성 검사 오류가 발생합니다.

## <a name="remarks"></a>설명

**_Write** 함수는 *버퍼* 의 *카운트* 바이트를 *fd* 와 연결 된 파일에 씁니다. 쓰기 작업은 지정된 파일과 연결된 파일 포인터(있는 경우)의 현재 위치에서 시작됩니다. 추가의 목적으로 파일을 연 경우 쓰기 작업은 파일의 현재 끝에서 시작됩니다. 쓰기 작업 후 파일 포인터는 쓴 바이트 수 만큼 증가 합니다.

텍스트 모드로 연 파일에 쓰는 경우 **_write** 는 CTRL + Z 문자를 파일의 논리적 끝으로 처리 합니다. 장치에 쓰는 경우 **_write** 는 버퍼의 CTRL + Z 문자를 출력 종결자로 처리 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_write**|\<io.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occurred
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>참고 항목

[하위 수준 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
