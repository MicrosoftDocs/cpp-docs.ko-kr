---
description: '자세한 정보: fopen, _wfopen'
title: fopen, _wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: a11bf5ab387ac3436a488f77bea4c5c130836790
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164928"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

파일을 엽니다. 추가 매개 변수 유효성 검사를 수행하고 오류 코드를 반환하는 이 함수의 더 안전한 버전을 사용할 수 있습니다. [fopen_s, _wfopen_s](fopen-s-wfopen-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
파일 이름.

*mode*<br/>
사용할 수 있는 액세스 종류입니다.

## <a name="return-value"></a>반환 값

각 함수는 열린 파일에 대한 포인터를 반환합니다. null 포인터 값은 오류를 나타냅니다. *파일 이름* 또는 *모드가* **NULL** 이거나 빈 문자열인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 트리거합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**Fopen** 함수는 *filename* 으로 지정 된 파일을 엽니다. 기본적으로 좁은 *파일 이름* 문자열은 ANSI 코드 페이지 (CP_ACP)를 사용 하 여 해석 됩니다. Windows 데스크톱 애플리케이션에서 이 페이지를 [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) 함수를 사용하여 OEM 코드 페이지(CP_OEMCP)로 변경할 수 있습니다. [Arefileapisansi](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) 함수를 사용 하 여 ANSI 또는 시스템 기본 OEM 코드 페이지를 사용 하 여 *파일 이름을* 해석할지 여부를 결정할 수 있습니다. **_wfopen** 는 **fopen** 의 와이드 문자 버전입니다. **_wfopen** 인수는 와이드 문자 문자열입니다. 그렇지 않으면 **_wfopen** 와 **fopen** 이 동일 하 게 작동 합니다. **_Wfopen** 사용 하는 경우에만 파일 스트림에 사용 되는 코딩 된 문자 집합에 영향을 주지 않습니다.

**fopen** 은 실행 시점에 파일 시스템에 유효한 경로를 허용 합니다. **fopen** 은 코드를 실행 하는 시스템에서 실행 시점에 공유 또는 매핑된 드라이브에 액세스할 수 있는 한, 매핑된 네트워크 드라이브를 포함 하는 UNC 경로 및 경로를 허용 합니다. **Fopen** 에 대 한 경로를 생성할 때 드라이브, 경로 또는 네트워크 공유를 실행 환경에서 사용할 수 있는지 확인 합니다. 슬래시(/) 또는 백슬래시(\\)를 경로의 디렉터리 구분 기호로 사용할 수 있습니다.

파일에서 추가 작업을 수행하기 전에 항상 반환 값을 검사하여 포인터가 NULL인지 여부를 확인하세요. 오류가 발생 하면 전역 변수 **errno** 가 설정 되어 특정 오류 정보를 가져오는 데 사용할 수 있습니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="unicode-support"></a>유니코드 지원

**fopen** 은 유니코드 파일 스트림을 지원 합니다. 유니코드 파일을 열려면 다음과 같이 **fopen** 에 원하는 인코딩을 지정 하는 **ccs** 플래그를 전달 합니다.

> **FILE \* fp = fopen ("newfile.txt", "rt +, ccs =**_encoding_**");**

*Encoding* 의 허용 되는 값은 **UNICODE**, **utf-8** 및 **u t f-utf-16le** 입니다.

파일이 유니코드 모드에서 열리면 입력 함수는 파일에서 읽은 데이터를 형식으로 저장 된 UTF-16 데이터로 변환 합니다 **`wchar_t`** . 유니코드 모드에서 연 파일에 쓰는 함수는 UTF-16 데이터가 포함 된 버퍼가 형식으로 저장 되어야 **`wchar_t`** 합니다. 이 파일이 UTF-8로 인코딩되면 UTF-16 데이터는 쓸 때 UTF-8로 변환되고 이 파일의 UTF-8로 인코딩된 내용은 읽을 때 UTF-16으로 변환됩니다. 유니코드 모드에서 홀수 바이트를 읽거나 쓰려고 하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md) 오류가 발생 합니다. 프로그램에 UTF-8로 저장된 데이터를 읽거나 쓰려는 경우 유니코드 모드 대신 텍스트 또는 이진 파일 모드를 사용합니다. 필수 인코딩은 사용자가 변환해야 합니다.

파일이 이미 있고 읽기 또는 추가용으로 열려 있는 경우 BOM(바이트 순서 표시)(파일에 있는 경우)에 따라 인코딩이 결정됩니다. BOM 인코딩은 **ccs** 플래그에 의해 지정 되는 인코딩과 우선적으로 적용 됩니다. **Ccs** 인코딩은 BOM이 없거나 파일이 새 파일인 경우에만 사용 됩니다.

> [!NOTE]
> BOM 검색은 유니코드 모드에서 연 파일 (즉, **ccs** 플래그를 전달 하 여)에만 적용 됩니다.

다음 표에는 파일의 **fopen** 및 바이트 순서 표시에 제공 되는 다양 한 **ccs** 플래그에 사용 되는 모드가 요약 되어 있습니다.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>ccs 플래그 및 BOM을 기반으로 사용되는 인코딩

|ccs 플래그|BOM이 없거나 새 파일|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

유니코드 모드에서 쓰도록 파일을 열면 BOM이 파일에 자동으로 기록됩니다.

*Mode* 가 **"a, ccs =**_encoding_**"** 이면 **fopen** 은 읽기 및 쓰기 권한을 모두 사용 하 여 파일을 열려고 시도 합니다. 성공하면 BOM을 읽고 파일에 대한 인코딩을 결정하고, 실패하면 파일에 대한 기본 인코딩을 사용합니다. 두 경우 모두 **fopen** 은 쓰기 전용 액세스를 사용 하 여 파일을 다시 엽니다. 이는 "a **"** 모드에만 적용 되 고 **"a +"** 모드에는 적용 되지 않습니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

문자열 *모드* 는 다음과 같이 파일에 대해 요청 되는 액세스의 종류를 지정 합니다.

|*mode*|Access|
|-|-|
| **&** | 읽기 위해 엽니다. 파일이 없거나 찾을 수 없는 경우 **fopen** 호출이 실패 합니다. |
| **w** | 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **은** | 새 데이터를 파일에 쓰기 전에 EOF(파일 끝) 표식을 제거하지 않고 파일의 끝에 쓰기(추가)하기 위해 엽니다. 파일이 없는 경우 파일을 만듭니다. |
| **"r +"** | 읽고 쓰기 위해 엽니다. 파일이 있어야 합니다. |
| **"w +"** | 읽고 쓰기 위해 빈 파일을 엽니다. 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **"a +"** | 읽고 추가하기 위해 엽니다. 추가 작업에는 새 데이터를 파일에 쓰기 전에 EOF 표식을 제거하는 작업이 포함됩니다. 쓰기 완료 후 EOF 표식이 복원되지 않습니다. 파일이 없는 경우 파일을 만듭니다. |

**"A"** 액세스 형식 또는 **"a +"** 액세스 형식을 사용 하 여 파일을 열면 모든 쓰기 작업이 파일 끝에서 발생 합니다. [Fseek](fseek-fseeki64.md) 또는 [되감기](rewind.md)를 사용 하 여 파일 포인터의 위치를 변경할 수 있지만 쓰기 작업을 수행 하기 전에 항상 파일 끝으로 다시 이동 합니다. 따라서 기존 데이터를 덮어쓸 수 없습니다.

**"A"** 모드에서는 파일에 추가 하기 전에 EOF 표식을 제거 하지 않습니다. 추가 작업이 수행된 이후에는 MS-DOS TYPE 명령은 원래 EOF 표식까지만 데이터를 표시하고 파일에 추가된 데이터는 표시하지 않습니다. 파일에 추가 하기 전에 **"a +"** 모드에서는 EOF 표식을 제거 합니다. 추가 후에는 MS-DOS TYPE 명령으로 파일의 모든 데이터를 표시합니다. **"A +"** 모드는 CTRL + Z EOF 표식으로 종료 되는 스트림 파일에 추가 하는 데 필요 합니다.

**"R +"**, **"w +"** 또는 **"a +"** 액세스 형식을 지정한 경우 읽기와 쓰기를 모두 사용할 수 있습니다. 즉, 파일이 "업데이트" 용으로 열립니다. 하지만 읽기에서 쓰기로 전환할 경우 입력 작업 시 EOF 표식이 필요합니다. EOF가 없는 경우 사이에 파일 위치 지정 함수를 호출해야 합니다. 파일 위치 지정 함수는 **fsetpos**, [fseek](fseek-fseeki64.md)및 [되감기](rewind.md)입니다. 쓰기에서 읽기로 전환 하는 경우 **fflush** 또는 파일 위치 지정 함수에 대 한 중간 호출을 사용 해야 합니다.

이전 값 이외에 다음 문자를 *모드* 에 추가 하 여 줄 바꿈 문자에 대 한 변환 모드를 지정할 수 있습니다.

|*모드* 한정자|변환 모드|
|-|-|
| **t** | 텍스트(변환됨) 모드에서 엽니다. |
| **b** | 이진 (변환 되지 않음) 모드에서 열기 캐리지 리턴 및 줄 바꿈 문자를 포함 하는 변환은 표시 되지 않습니다. |

텍스트 모드에서 CTRL + Z는 입력에서 EOF 문자로 해석 됩니다. **"A +"** 를 사용 하 여 읽기/쓰기용으로 열려 있는 파일에서 **fopen** 은 파일 끝에 CTRL + Z가 있는지 확인 하 고 가능한 경우이를 제거 합니다. 이 작업은 [fseek](fseek-fseeki64.md) 및 **fseek** 를 사용 하 여 CTRL + Z로 끝나는 파일 내에서 이동 하면 파일의 끝 부분에서 [fseek](fseek-fseeki64.md) 가 제대로 동작 하지 않을 수 있기 때문입니다.

텍스트 모드에서 캐리지 리턴-줄 바꿈 조합은 입력 시 단일 줄 바꿈으로 변환 되 고, 줄 바꿈 문자는 출력에서 캐리지 리턴-줄 바꿈 조합으로 변환 됩니다. 유니코드 스트림 I/O 함수가 텍스트 모드에서 작동할 경우(기본값) 소스 또는 대상 스트림은 멀티바이트 문자 시퀀스로 간주됩니다. 따라서 유니코드 스트림 입력 함수는 **mbtowc** 함수 호출과 마찬가지로 멀티바이트 문자를 와이드 문자로 변환합니다. 동일한 이유로 유니코드 스트림 출력 함수는 **wctomb** 함수 호출과 마찬가지로 와이드 문자를 멀티바이트 문자로 변환합니다.

*모드* 에서 **t** 또는 **b** 를 지정 하지 않은 경우 기본 변환 모드는 [_fmode](../../c-runtime-library/fmode.md)전역 변수에 의해 정의 됩니다. **T** 또는 **b** 가 인수 앞에 있으면 함수가 실패 하 고 **NULL** 을 반환 합니다.

유니코드 및 멀티바이트 스트림 I/O에서 텍스트 모드 및 이진 모드를 사용하는 방법에 대한 자세한 내용은 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 및 [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)를 참조하세요.

다음 옵션을 *모드* 에 추가 하 여 추가 동작을 지정할 수 있습니다.

|*모드* 한정자|동작|
|-|-|
| **x** | *Filename* 이 이미 있는 경우 함수를 강제로 실행 하지 않습니다. 는 "w" 또는 "w +" 지정자와만 사용할 수 있습니다. |
| **c** | **Fflush** 또는 **_flushall** 가 호출 되는 경우 파일 버퍼의 내용이 디스크에 직접 기록 되도록 연결 된 *파일 이름* 에 대 한 커밋 플래그를 사용 하도록 설정 합니다. |
| **n** | 관련 *파일 이름* 에 대 한 커밋 플래그를 "커밋 안 함"으로 다시 설정 합니다. 이것이 기본값입니다. 또한 프로그램을 COMMODE.OBJ와 연결할 경우 전역 커밋 플래그를 재정의합니다. 프로그램을 COMMODE.OBJ와 명시적으로 연결하지 않을 경우 전역 커밋 플래그 기본값은 "커밋 안 함"입니다( [Link Options](../../c-runtime-library/link-options.md)참조). |
| **N** | 자식 프로세스에서 파일을 상속하지 않도록 지정합니다. |
| **S** | 캐싱이 디스크에서 순차적 액세스를 위해 최적화되며 이에 제한되지 않습니다. |
| **R** | 캐싱이 디스크에서 임의 액세스를 위해 최적화되며 이에 제한되지 않습니다. |
| **T** | 파일을 임시 파일로 지정합니다. 가능하면 디스크에 플러시되지 않습니다. |
| **D** | 파일을 임시 파일로 지정합니다. 마지막 파일 포인터를 닫을 때 삭제됩니다. |
| **ccs =**_인코딩_ | 이 파일에 사용할 인코딩된 문자 집합 ( **utf-8**, **utf-16le** 또는 **유니코드** 중 하나)을 지정 합니다. ANSI 인코딩을 원할 경우 지정되지 않은 상태로 둡니다. |

**Fopen** 및 **_fdopen** 에 사용 되는 *모드* 문자열의 유효한 문자는 다음과 같이 [_open](open-wopen.md) 및 [_sopen](sopen-wsopen.md)에서 사용 되는 *oflag* 인수에 해당 합니다.

|*모드* 문자열의 문자|Open/sopen에 대 한 해당 *oflag* 값 \_ \_|
|-------------------------------|----------------------------------------------------|
|**은**|**\_ O \_ WRONLY** &#124; **\_ o \_ append** (일반적으로 **\_ o \_ WRONLY** &#124; **\_ o \_** 만들기 &#124; **\_ o \_ 추가**)|
|**a +**|**\_ O \_ rdwr** &#124; **\_ o \_ append** (일반적으로 **\_ o \_ rdwr** &#124; **\_ o \_ 추가** &#124; **\_ o \_** )|
|**r**|**\_O \_ RDONLY**|
|**r +**|**\_O \_ RDWR**|
|**w**|**\_ O \_ WRONLY** (일반적으로 **\_ o \_ WRONLY** &#124; **\_ o \_** &#124; o **\_ \_ TRUNC**)|
|**w +**|**\_ O \_ rdwr** (일반적으로 **\_ o \_ rdwr** &#124; **\_ o \_** &#124; o **\_ \_ TRUNC**)|
|**b**|**\_O \_ 이진**|
|**t**|**\_O \_ 텍스트**|
|**x**|**\_O \_ EXCL**|
|**c**|없음|
|**n**|없음|
|**S**|**\_O \_ 순차**|
|**R**|**\_O \_ 임의**|
|**T**|**\_O \_ SHORTLIVED**|
|**D**|**\_O \_ 임시**|
|**ccs = 유니코드**|**\_O \_ WTEXT**|
|**ccs = UTF-8**|**\_O \_ UTF8**|
|**ccs = UTF-UTF-16LE**|**\_O \_ UTF16**|

**Rb** 모드를 사용 하는 경우 코드를 이식할 필요가 없으며, 큰 파일의 대부분을 읽어야 하거나 네트워크 성능이 염려 하지 않을 경우 메모리 매핑된 Win32 파일을 옵션으로 사용할지 여부를 고려할 수도 있습니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> 또는 \<wchar.h>|

**_wfopen** 는 Microsoft 확장입니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**C**, **n**, **t**, **S**, **R**, **t** 및 **D** *모드* 옵션은 **fopen** 및 **_fdopen** 에 대 한 Microsoft 확장 이며 ANSI 이식성이 필요한 곳에서 사용 하면 안 됩니다.

## <a name="example-1"></a>예 1

다음 프로그램은 두 파일을 엽니다.  **Fclose** 를 사용 하 여 첫 번째 파일을 닫고 **_fcloseall** 하 여 나머지 파일을 모두 닫습니다.

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>예제 2

다음 프로그램은 텍스트 모드에서 유니코드 인코딩을 포함하는 파일을 만들거나 덮어씁니다(파일이 있는 경우).  그런 다음 파일에 두 문자열을 쓰고 파일을 닫습니다. 출력 파일은 _wfopen_test.xml이며, 출력 섹션의 데이터를 포함합니다.

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[Multibyte-Character 시퀀스의 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
