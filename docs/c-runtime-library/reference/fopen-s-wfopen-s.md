---
title: fopen_s, _wfopen_s
description: 및 용 API에 대해 설명 합니다. `fopen_s``_wfopen_s`
ms.date: 11/20/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: 1d6d0b739db1177b903c0e8aa8e6f55e49c1df16
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483167"
---
# <a name="fopen_s-_wfopen_s"></a>`fopen_s`, `_wfopen_s`

파일을 엽니다. 이러한 버전의에는 [`fopen, _wfopen`](fopen-wfopen.md) [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명 된 대로 향상 된 보안 기능이 포함 되어 있습니다.

## <a name="syntax"></a>구문

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>매개 변수

*`pFile`*\
열린 파일에 대한 포인터를 수신할 파일 포인터에 대한 포인터입니다.

*`filename`*\
파일 이름입니다.

*`mode`*\
허용되는 액세스 형식입니다.

## <a name="return-value"></a>반환 값

성공 시 0이고, 실패 시 오류 코드입니다. 이러한 오류 코드에 대 한 자세한 내용은을 참조 하십시오 [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

### <a name="error-conditions"></a>오류 조건

|*`pFile`*|*`filename`*|*`mode`*|반환 값|내용 *`pFile`*|
|-------------|----------------|------------|------------------|------------------------|
|**`NULL`**|any|any|**`EINVAL`**|변경 안 됨|
|any|**`NULL`**|any|**`EINVAL`**|변경 안 됨|
|any|any|**`NULL`**|**`EINVAL`**|변경 안 됨|

## <a name="remarks"></a>설명

에서 열 수 있는 파일 **`fopen_s`** 은 **`_wfopen_s`** 공유할 수 없습니다. 파일을 공유할 수 있어야 하는 경우 [`_fsopen, _wfsopen`](fsopen-wfsopen.md) **`_SH_DENYNO`** 읽기/쓰기 공유의 경우와 같이 적절 한 공유 모드 상수와 함께를 사용 합니다.

**`fopen_s`** 함수는 *filename* 으로 지정 된 파일을 엽니다. **`_wfopen_s`** 는의 와이드 문자 버전 이며 **`fopen_s`** ,에 대 한 인수는 **`_wfopen_s`** 와이드 문자 문자열입니다. **`_wfopen_s`** 및는 동일 하 게 **`fopen_s`** 동작 합니다.

**`fopen_s`** 는 실행 시점에 파일 시스템에 유효한 경로를 허용 합니다. 매핑된 네트워크 드라이브를 포함 하는 UNC 경로 및 경로는 **`fopen_s`** 실행 시 코드를 실행 하는 시스템에서 공유 또는 매핑된 네트워크 드라이브에 액세스할 수 있는 한에만 허용 됩니다. 에 대 한 경로를 생성할 때 **`fopen_s`** 실행 환경에서 드라이브, 경로 또는 네트워크 공유의 가용성을 가정 하지 마세요. 슬래시(/) 또는 백슬래시(\\)를 경로의 디렉터리 구분 기호로 사용할 수 있습니다.

이러한 함수는 해당 함수 매개 변수의 유효성을 검사합니다. *`pFile`*, *`filename`* 또는 *`mode`* 가 null 포인터인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 예외를 생성 합니다.

파일에서 추가 작업을 수행 하기 전에 항상 반환 값을 확인 하 여 함수가 성공 했는지 확인 합니다. 오류가 발생 하면 오류 코드가 반환 되 고 전역 변수가 **`errno`** 설정 됩니다. 자세한 내용은 [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을(를) 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="unicode-support"></a>유니코드 지원

**`fopen_s`** 는 유니코드 파일 스트림을 지원 합니다. 새 유니코드 파일이 나 기존 유니코드 파일을 열려면 원하는 인코딩을 지정 하는 *ccs* 플래그를 **`fopen_s`** 다음과 같이 전달 합니다.

**`fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");`**

*Encoding* 의 허용 되는 값은 **`UNICODE`** , **`UTF-8`** 및 **`UTF-16LE`** 입니다. 에 대해 지정 된 값이 없는 경우는 *`encoding`* **`fopen_s`** ANSI 인코딩을 사용 합니다.

파일이 이미 있고 읽기 또는 추가용으로 열려 있는 경우 BOM(바이트 순서 표시)(파일에 있는 경우)에 따라 인코딩이 결정됩니다. BOM 인코딩은 플래그에 지정 된 인코딩에 우선 합니다 *`ccs`* . *`ccs`* 인코딩은 BOM이 없거나 파일이 새 파일인 경우에만 사용 됩니다.

> [!NOTE]
> BOM 검색은 유니코드 모드로 열려 있는 파일에만 적용 됩니다. 즉, 플래그를 전달 *`ccs`* 합니다.

다음 표에서는 *`ccs`* **`fopen_s`** 파일에서 및 바이트 순서 표시에 제공 되는 다양 한 플래그에 대 한 모드를 요약 합니다.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>ccs 플래그 및 BOM을 기반으로 사용되는 인코딩

|ccs 플래그|BOM이 없거나 새 파일|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**`UNICODE`**|**`UTF-16LE`**|**`UTF-8`**|**`UTF-16LE`**|
|**`UTF-8`**|**`UTF-8`**|**`UTF-8`**|**`UTF-16LE`**|
|**`UTF-16LE`**|**`UTF-16LE`**|**`UTF-8`**|**`UTF-16LE`**|

유니코드 모드에서 쓰도록 파일을 열면 BOM이 파일에 자동으로 기록됩니다.

*`mode`* 가 **`"a, ccs=` _encoding_ encoding `"`** 인 경우는 **`fopen_s`** 먼저 읽기 액세스와 쓰기 권한을 모두 사용 하 여 파일을 열려고 시도 합니다. 성공하면 함수가 BOM을 읽어서 파일에 대한 인코딩을 결정하고, 실패하면 함수가 파일에 대한 기본 인코딩을 사용합니다. 두 경우 모두 **`fopen_s`** 쓰기 전용 액세스 권한으로 파일을 다시 열립니다. 이 **`a`** 는 모드에만 적용 되 고는 적용 되지 않습니다 **`a+`** .

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tfopen_s`**|**`fopen_s`**|**`fopen_s`**|**`_wfopen_s`**|

문자열은 *`mode`* 다음과 같이 파일에 대해 요청 되는 액세스의 종류를 지정 합니다.

|*`mode`*|Access|
|-|-|
| **`"r"`** | 읽기 위해 엽니다. 파일이 없거나 찾을 수 없는 경우 **`fopen_s`** 호출이 실패 합니다. |
| **`"w"`** | 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **`"a"`** | 새 데이터를 파일에 쓰기 전에 EOF(파일 끝) 표식을 제거하지 않고 파일의 끝에 쓰기(추가)하기 위해 엽니다. 파일이 없는 경우 파일을 만듭니다. |
| **`"r+"`** | 읽고 쓰기 위해 엽니다. 파일이 있어야 합니다. |
| **"w +"** | 읽고 쓰기 위해 빈 파일을 엽니다. 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **`"a+"`** | 읽고 추가하기 위해 엽니다. 추가 작업에는 새 데이터를 파일에 쓰기 전에 EOF 표식을 제거하는 작업이 포함됩니다. 쓰기가 완료 된 후 EOF 표식이 복원 되지 않습니다. 파일이 없는 경우 파일을 만듭니다. |

파일이 또는 액세스 형식을 사용 하 여 열리면 **`"a"`** **`"a+"`** 모든 쓰기 작업이 파일 끝에서 발생 합니다. 또는를 사용 하 여 파일 포인터의 위치를 변경할 수 [`fseek`](fseek-fseeki64.md) [`rewind`](rewind.md) 있지만, 기존 데이터를 덮어쓸 수 없도록 쓰기 작업을 수행 하기 전에 항상 파일 끝으로 다시 이동 합니다.

**`"a"`** 모드는 파일에 추가 하기 전에 EOF 표식을 제거 하지 않습니다. 추가가 발생 하면 MS-DOS `TYPE` 명령은 원본 EOF 표식 까지만 데이터를 표시 하 고 파일에 추가 된 데이터는 표시 하지 않습니다. **`"a+"`** 모드는 파일에 추가 하기 전에 EOF 표식을 제거 합니다. 추가 후에는 MS-DOS `TYPE` 명령이 파일의 모든 데이터를 표시 합니다. **`"a+"`** 이 모드는 EOF 표식으로 종료 되는 스트림 파일에 추가 하는 데 필요 `CTRL+Z` 합니다.

**`"r+"`**, **`"w+"`** 또는 **`"a+"`** 액세스 형식을 지정한 경우 읽기와 쓰기가 모두 허용 됩니다. 파일은 "업데이트" 용으로 열립니다. 그러나 읽기에서 쓰기로 전환 하는 경우 입력 작업은 EOF 표식에서 가져와야 합니다. EOF 표식이 없는 경우 파일 위치 지정 함수에 대 한 중간 호출을 사용 해야 합니다. 파일 위치 지정 함수는 **`fsetpos`** , [`fseek`](fseek-fseeki64.md) 및 [`rewind`](rewind.md) 입니다. 쓰기에서 읽기로 전환 하는 경우 **`fflush`** 또는 파일 위치 지정 함수에 대 한 중간 호출을 사용 해야 합니다.

위의 값 이외에 다음 문자를에 포함 *`mode`* 하 여 줄 바꿈 문자에 대 한 변환 모드를 지정할 수 있습니다.

|*`mode`* modifier|변환 모드|
|-|-|
| **`t`** | 텍스트(변환됨) 모드에서 엽니다. |
| **`b`** | 이진 (변환 되지 않음) 모드에서 열기 캐리지 리턴 및 줄 바꿈 문자를 포함 하는 변환은 표시 되지 않습니다. |

텍스트 (변환 됨) 모드에서 `CTRL+Z` 는 입력 시 파일 끝 문자로 해석 됩니다. 를 사용 하 여 읽기/쓰기용으로 열려 있는 파일에서 **`"a+"`** **`fopen_s`** 는 파일 끝에 있는을 확인 `CTRL+Z` 하 고 가능 하면 제거 합니다. 이 작업은 및를 사용 하 여 [`fseek`](fseek-fseeki64.md) **`ftell`** 로 끝나는 파일 내에서 이동 하면가 `CTRL+Z` [`fseek`](fseek-fseeki64.md) 파일 끝 부분에서 제대로 동작 하지 않을 수 있기 때문에 수행 됩니다.

또한 텍스트 모드에서 캐리지 리턴/줄 바꿈 조합은 입력 시 단일 줄 바꿈으로 변환 되 고, 줄 바꿈 문자는 출력에서 캐리지 리턴-줄 바꿈 조합으로 변환 됩니다. 유니코드 스트림 I/O 함수가 텍스트 모드에서 작동할 경우(기본값) 소스 또는 대상 스트림은 멀티바이트 문자 시퀀스로 간주됩니다. 유니코드 스트림 입력 함수는 멀티 바이트 문자를 와이드 문자로 변환 합니다 (함수를 호출한 것 처럼 **`mbtowc`** ). 이와 같은 이유로 유니코드 스트림 출력 함수는 와이드 문자를 멀티 바이트 문자로 변환 합니다 (함수를 호출한 것 처럼 **`wctomb`** ).

**`t`** 에 또는가 **`b`** 지정 되지 않은 경우 *`mode`* 기본 변환 모드는 [_fmode](../../c-runtime-library/fmode.md)전역 변수에 의해 정의 됩니다. **`t`** 또는 **`b`** 가 인수 앞에 붙는 경우 함수는 실패 하 고을 반환 **`NULL`** 합니다.

텍스트 및 이진 모드를 유니코드 및 멀티바이트 스트림 I/O에서 사용하는 방법에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 및 [텍스트 및 이진 모드의 유니코드 스트림 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)를 참조하세요.

|*`mode`* modifier|동작|
|-|-|
| **`c`** | 또는가 호출 될 때 파일 버퍼의 내용이 디스크에 직접 기록 되도록 연결 된 *파일 이름* 에 대 한 커밋 플래그를 사용 하도록 설정 합니다 **`fflush`** **`_flushall`** . |
| **`n`** | 관련 *파일 이름* 에 대 한 커밋 플래그를 "커밋 안 함"으로 다시 설정 합니다. 이것이 기본값입니다. 또한 프로그램을 COMMODE.OBJ와 연결할 경우 전역 커밋 플래그를 재정의합니다. 프로그램을 COMMODE.OBJ와 명시적으로 연결하지 않을 경우 전역 커밋 플래그 기본값은 "커밋 안 함"입니다( [Link Options](../../c-runtime-library/link-options.md)참조). |
| **`n`** | 자식 프로세스에서 파일을 상속 하지 않도록 지정 합니다. |
| **`S`** | 캐싱이 디스크에서 순차적 액세스를 위해 최적화되며 이에 제한되지 않습니다. |
| **`R`** | 캐싱이 디스크에서 임의 액세스를 위해 최적화되며 이에 제한되지 않습니다. |
| **`t`** | 파일을 임시 파일로 지정합니다. 가능 하면 디스크에 플러시되지 않습니다. |
| **`D`** | 파일을 임시 파일로 지정합니다. 마지막 파일 포인터를 닫을 때 삭제 됩니다. |
| **`ccs=**`_인코딩이_ | **`UTF-8`** **`UTF-16LE`** 이 파일에 사용할 인코딩된 문자 집합 (, 또는 중 하나)을 지정 합니다 **`UNICODE`** . ANSI 인코딩을 원할 경우 지정되지 않은 상태로 둡니다. |

및에서 사용 되는 문자열에 유효한 문자는 *`mode`* **`fopen_s`** [`_fdopen`](fdopen-wfdopen.md) *`oflag`* 다음과 같이 및에 사용 되는 인수와 일치 [`_open`](open-wopen.md) [`_sopen`](sopen-wsopen.md) 합니다.

|문자열의 문자 *`mode`*|에 해당 하는 *`oflag`* 값 `_open`/`_sopen`|
|-------------------------------|----------------------------------------------------|
|**`a`**|**`_O_WRONLY`** &#124; **`_O_APPEND`** (일반적으로 **`_O_WRONLY`** &#124; **`_O_CREAT`** &#124; **`_O_APPEND`** )|
|**`a+`**|**`_O_RDWR`** &#124; **`_O_APPEND`** (일반적으로 **`_O_RDWR`** &#124; **`_O_APPEND`** &#124; **`_O_CREAT`** )|
|**`R`**|**`_O_RDONLY`**|
|**`r+`**|**`_O_RDWR`**|
|**`w`**|**`_O_WRONLY`** (일반적으로 **`_O_WRONLY`** &#124; **`_O_CREAT`** &#124; **_O_TRUNC**)|
|**`w+`**|**`_O_RDWR`** (일반적으로 **`_O_RDWR`** &#124; **`_O_CREAT`** &#124; **_O_TRUNC**)|
|**`b`**|**`_O_BINARY`**|
|**`t`**|**`_O_TEXT`**|
|**`c`**|없음|
|**`n`**|없음|
|**`S`**|**`_O_SEQUENTIAL`**|
|**`R`**|**`_O_RANDOM`**|
|**`t`**|**`_O_SHORTLIVED`**|
|**`D`**|**`_O_TEMPORARY`**|
|**`ccs=UNICODE`**|**`_O_WTEXT`**|
|**`ccs=UTF-8`**|**`_O_UTF8`**|
|**`ccs=UTF-16LE`**|**`_O_UTF16`**|

모드를 사용 하는 경우 **`rb`** 코드를 이식할 필요가 없거나, 파일의 대부분을 읽거나, 네트워크 성능이 중요 하지 않은 경우에도 메모리 매핑된 Win32 파일을 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**`fopen_s`**|`<stdio.h>`|
|**`_wfopen_s`**|`<stdio.h>` 또는 `<wchar.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

**`c`**, **`n`** 및 옵션은 **`t`** *`mode`* 및에 대 한 Microsoft **`fopen_s`** 확장 [`_fdopen`](fdopen-wfdopen.md) 이며 ANSI 이식성이 필요한 경우에는 사용할 수 없습니다.

## <a name="example"></a>예제

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" doesn't exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it isn't NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>참조

[스트림 i/o](../../c-runtime-library/stream-i-o.md)\
[`fclose, _fcloseall`](fclose-fcloseall.md)\
[`_fdopen, _wfdopen`](fdopen-wfdopen.md)\
[`ferror`](ferror.md)\
[`_fileno`](fileno.md)\
[`freopen, _wfreopen`](freopen-wfreopen.md)\
[`_open, _wopen`](open-wopen.md)\
[`_setmode`](setmode.md)
