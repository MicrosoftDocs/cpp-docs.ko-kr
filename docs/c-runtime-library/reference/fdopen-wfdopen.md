---
title: _fdopen, _wfdopen
ms.date: 12/12/2017
api_name:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 5202c84cd1a9038faf68587f9207d376ed8c0af1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941251"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

하위 수준 I/O를 위해 이전에 연 파일에 스트림을 연결합니다.

## <a name="syntax"></a>구문

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
열린 파일의 파일 설명자입니다.

*mode*<br/>
파일 액세스의 유형입니다.

## <a name="return-value"></a>반환 값

각 함수는 열린 스트림에 대한 포인터를 반환합니다. null 포인터 값은 오류를 나타냅니다. 오류가 발생하는 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **ebadf**로 설정 됩니다 .이는 잘못 된 파일 설명자를 나타내는 **EINVAL**이 고, 해당 *모드가* null 포인터 임을 나타내는입니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Fdopen** 함수는 *fd*로 식별 되는 파일과 i/o 스트림을 연결 하 여 하위 수준 i/o에 대해 열려 있는 파일을 버퍼링 하 고 형식을 지정할 수 있도록 합니다. **_wfdopen** 는 **_fdopen**의 와이드 문자 버전입니다. **_wfdopen** 에 대 한 *mode* 인수는 와이드 문자열입니다. 그렇지 않으면 **_wfdopen** 및 **_fdopen** 이 동일 하 게 작동 합니다.

**_Fdopen** 에 전달 된 파일 설명자는 반환 된 **파일 &#42;**  스트림이 소유 합니다. **_Fdopen** 이 성공 하면 파일 설명자에서 [ \_close](close.md) 를 호출 하지 마세요. 반환 된  **&#42; 파일** 에서 [fclose](fclose-fcloseall.md) 를 호출 하면 파일 설명자도 닫힙니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑

|Tchar.h 루틴|\_유니코드 및 \_MBCS가 정의 되지 않음|\_MBCS 정의|\_유니코드 정의|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*모드* 문자열은 파일에 대해 요청 되는 파일 액세스의 유형을 지정 합니다.

| *mode* | 액세스 |
|--------|--------|
| **"r"** | 읽기 위해 엽니다. 파일이 없거나 찾을 수 없는 경우 **fopen** 호출이 실패 합니다. |
| **"w"** | 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **"a"** | 파일의 끝에서 쓰기 위해 엽니다 (추가). 파일이 없는 경우 파일을 만듭니다. |
| **"r+"** | 읽고 쓰기 위해 엽니다. 파일이 있어야 합니다. |
| **"w+"** | 읽고 쓰기 위해 빈 파일을 엽니다. 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **"a+"** | 읽고 추가하기 위해 엽니다. 파일이 없는 경우 파일을 만듭니다. |

파일이 **"a"** 또는 **"a +"** 액세스 형식으로 열리면 모든 쓰기 작업이 파일 끝에서 발생 합니다. [Fseek](fseek-fseeki64.md) 또는 [되감기](rewind.md)를 사용 하 여 파일 포인터의 위치를 변경할 수 있지만 쓰기 작업을 수행 하기 전에 항상 파일 끝으로 다시 이동 합니다. 따라서 기존 데이터를 덮어쓸 수 없습니다. **"R +"** , **"w +"** 또는 **"a +"** 액세스 형식을 지정한 경우 읽기와 쓰기가 모두 허용 됩니다. 즉, 파일이 "업데이트" 용으로 열립니다. 그러나 읽기와 쓰기를 전환할 때는 중간에 [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)또는 [되감기](rewind.md) 작업이 있어야 합니다. 원하는 경우 [fsetpos](fsetpos.md) 또는 [fseek](fseek-fseeki64.md) 작업의 현재 위치를 지정할 수 있습니다.

위의 값 외에도 다음 문자를 *모드* 에 포함 하 여 줄 바꿈 문자에 대 한 변환 모드를 지정할 수 있습니다.

| *모드* 한정자 | 동작 |
|-----------------|----------|
| **t** | 텍스트(변환됨) 모드에서 엽니다. 이 모드에서는 CR-LF(캐리지 리턴 줄 바꿈) 조합은 입력 시 단일 LF(줄 바꿈)로 변환되고, LF 문자는 출력 시 CR-LF 조합으로 변환됩니다. 또한 CTRL+Z는 입력 시 파일 끝 문자로 변환됩니다. |
| **b** | 이진(변환되지 않음) 모드에서 엽니다. **T** 모드에서의 모든 변환은 표시 되지 않습니다. |
| **c** | 연결 된 *파일 이름* 에 대해 커밋 플래그를 사용 하도록 설정 하 여 **fflush** 또는 **_flushall** 이 호출 되 면 파일 버퍼의 내용이 디스크에 직접 기록 되도록 합니다. |
| **n** | 관련 *파일 이름* 에 대 한 커밋 플래그를 "커밋 안 함"으로 다시 설정 합니다. 기본값입니다. 또한 프로그램을 Commode.obj와 연결할 경우 전역 커밋 플래그를 재정의합니다. 프로그램을 Commode.obj와 명시적으로 연결하지 않을 경우 전역 커밋 플래그 기본값은 "커밋 안 함"입니다. |

**T**, **c**및 **n** *모드* 옵션은 **fopen** 및 **_cff**용 Microsoft 확장입니다. ANSI 이식성을 유지하려는 경우에는 사용하지 마세요.

*모드*에서 **t** 또는 **b** 를 지정 하지 않은 경우 기본 변환 모드는 전역 변수 [ \_fmode](../../c-runtime-library/fmode.md)에 의해 정의 됩니다. **T** 또는 **b** 가 인수 앞에 있으면 함수가 실패 하 고 NULL을 반환 합니다. 텍스트 모드와 이진 모드에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)를 참조하세요.

**Fopen** 및 **_fdopen** 에 사용 되는 *모드* 문자열의 유효한 문자는 다음 표에 나와 있는 것 [ \_처럼 open](open-wopen.md) 및 [ \_sopen](sopen-wsopen.md)에 사용 되는 *oflag* 인수에 해당 합니다.

|*모드* 문자열의 문자|**_Open** 및 **_sopen** 에 대 한 해당 *oflag* 값|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_ &#124; WRONLYoAPPEND\_(일반적으로 o WRONLY o 만들기 o) \_**  **&#124; \_\_ \_ &#124; \_\_\_ 추가**)|
|**a+**|**\_&#124; O\_ rdwr\_o\_append** (일반적 **으로\_o &#124; &#124; rdwro\_추가o)\_ \_\_ \_** )|
|**r**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (일반적  **\_으로o\_WRONLY &#124; o &#124; 만들기 oTRUNC\_) \_\_ \_**|
|**w+**|**\_O\_rdwr** (일반적  **\_으로\_ &#124; \_\_ &#124; o rdwr o\_TRUNC)\_**|
|**b**|**\_O\_BINARY**|
|**t**|**\_O\_TEXT**|
|**c**|없음|
|**n**|없음|

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>입력: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>출력

```Output
Lines in file: 2
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_open, \_wopen](open-wopen.md)<br/>
