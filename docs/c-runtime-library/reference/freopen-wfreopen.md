---
description: '자세히 알아보기: freopen, _wfreopen'
title: freopen, _wfreopen
ms.date: 2/23/2021
api_name:
- freopen
- _wfreopen
- _o__wfreopen
- _o_freopen
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
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.openlocfilehash: 7b90be37154e2ceb951623e130cb1a45ae0a71bf
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236662"
---
# <a name="freopen-_wfreopen"></a>`freopen`, `_wfreopen`

파일 포인터를 다시 할당합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [`freopen_s, _wfreopen_s`](freopen-s-wfreopen-s.md)을 참조 하세요.

## <a name="syntax"></a>구문

```C
FILE *freopen(
   const char *path,
   const char *mode,
   FILE *stream
);
FILE *_wfreopen(
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*`path`*\
새 파일의 경로입니다.

*`mode`*\
허용되는 액세스 형식입니다.

*`stream`*\
구조체에 대 한 포인터 **`FILE`** 입니다.

## <a name="return-value"></a>반환 값

각 함수는 새로 열린 파일에 대한 포인터를 반환합니다. 오류가 발생 하면 원래 파일이 닫히고 함수에서 **`NULL`** 포인터 값을 반환 합니다. *`path`*, *`mode`* 또는 *`stream`* 가 null 포인터인 경우 또는 *filename* 이 빈 문자열인 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **`errno`** 를로 설정 하 **`EINVAL`** 고를 반환 **`NULL`** 합니다.

이러한 오류 코드 및 기타 오류 코드에 대 한 자세한 내용은를 참조 하십시오 [`_doserrno, errno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) . 

## <a name="remarks"></a>설명

이러한 함수의 더 안전한 버전은를 참조 [`freopen_s, _wfreopen_s`](freopen-s-wfreopen-s.md) 하세요.

**`freopen`** 함수는 현재와 연결 된 파일을 닫고 *`stream`* *`stream`* 에서 지정 된 파일에 다시 할당 *`path`* 합니다. **`_wfreopen`** 는의 와이드 문자 버전 이며 **`_freopen`** , *`path`* *`mode`* 에 대 한 및 인수는 **`_wfreopen`** 와이드 문자 문자열입니다. **`_wfreopen`** 및는 동일 하 게 **`_freopen`** 동작 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|`TCHAR.H `일반|_ `UNICODE & _MBCS` 정의 되지 않음|`_MBCS` 지정|`_UNICODE` 지정|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tfreopen`**|**`freopen`**|**`freopen`**|**`_wfreopen`**|

**`freopen`** 는 일반적으로 미리 열린 파일, **`stdin`** **`stdout`** 및를 **`stderr`** 사용자가 지정한 파일로 리디렉션하는 데 사용 됩니다. 와 연결 된 새 파일은 다음과 *`stream`* *`mode`* 같이 파일에 대해 요청 된 액세스 형식을 지정 하는 문자열을 사용 하 여 열립니다.

|*`mode`*|Access|
|-|-|
| **`"r"`** | 읽기 위해 엽니다. 파일이 없거나 찾을 수 없는 경우 **`freopen`** 호출이 실패 합니다. |
| **`"w"`** | 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **`"a"`** | 새 데이터를 파일에 쓰기 전에 EOF(파일 끝) 표식을 제거하지 않고 파일의 끝에 쓰기(추가)하기 위해 엽니다. 파일이 없는 경우 파일을 만듭니다. |
| **`"r+"`** | 읽고 쓰기 위해 엽니다. 파일이 있어야 합니다. |
| **`"w+"`** | 읽고 쓰기 위해 빈 파일을 엽니다. 파일이 있으면 이 파일의 내용은 삭제됩니다. |
| **`"a+"`** | 읽고 추가하기 위해 엽니다. 추가 작업에는 새 데이터를 파일에 쓰기 전에 EOF 표식을 제거하는 작업이 포함됩니다. 쓰기가 완료 된 후 EOF 표식이 복원 되지 않습니다. 파일이 없는 경우 파일을 만듭니다. |

**`"w"`** 및 **`"w+"`** 형식은 기존 파일을 삭제할 수 있으므로 주의 해 서 사용 합니다. C11부터 또는에 추가 하 여 **`"x"`** **`"w"`** **`"w+"`** 파일이 있는 경우 덮어쓰지 않고 함수가 실패할 수 있습니다.

파일이 또는 액세스 형식으로 열려 있으면 **`"a"`** **`"a+"`** 모든 쓰기 작업이 파일의 끝에서 수행 됩니다. 또는를 사용 하 여 파일 포인터의 위치를 변경할 수 있지만 [`fseek`](fseek-fseeki64.md) [`rewind`](rewind.md) , 파일 포인터는 쓰기 작업을 수행 하기 전에 항상 파일 끝으로 다시 이동 합니다. 따라서 기존 데이터를 덮어쓸 수 없습니다.

**`"a"`** 모드는 파일에 추가 하기 전에 EOF 표식을 제거 하지 않습니다. 추가 작업이 수행된 이후에는 MS-DOS TYPE 명령은 원래 EOF 표식까지만 데이터를 표시하고 파일에 추가된 데이터는 표시하지 않습니다. **`"a+"`** 모드는 파일에 추가 하기 전에 EOF 표식을 제거 합니다. 추가 후에는 MS-DOS TYPE 명령으로 파일의 모든 데이터를 표시합니다. **`"a+"`** 이 모드는 CTRL + Z EOF 표식으로 종료 되는 스트림 파일에 추가 하는 데 필요 합니다.

**`"r+"`**, **`"w+"`** 또는 **`"a+"`** 액세스 형식을 지정한 경우 읽기와 쓰기가 모두 허용 됩니다. 즉, 파일이 "업데이트" 용으로 열립니다. 그러나 읽기와 쓰기를 전환할 때는 중간 [`fsetpos`](fsetpos.md) , [`fseek`](fseek-fseeki64.md) 또는 작업이 있어야 합니다 [`rewind`](rewind.md) . [`fsetpos`](fsetpos.md)원하는 경우 또는 작업에 대해 현재 위치를 지정할 수 있습니다 [`fseek`](fseek-fseeki64.md) . 위의 값 외에도 다음 문자 중 하나를 문자열에 포함 *`mode`* 하 여 새 줄에 대해 변환 모드를 지정할 수 있습니다.

|*`mode`* modifier|변환 모드|
|-|-|
| **`t`** | 텍스트(변환됨) 모드에서 엽니다. |
| **`b`** | 이진 (변환 되지 않음) 모드에서 열기 캐리지 리턴 및 줄 바꿈 문자를 포함 하는 변환은 표시 되지 않습니다. |

텍스트 (변환 됨) 모드에서 캐리지 리턴-줄 바꿈 (CR-LF) 조합은 입력 시 LF (단일 줄 바꿈) 문자로 변환 됩니다. LF 문자는 출력에서 CR-LF 조합으로 변환 됩니다. 또한 CTRL+Z는 입력 시 파일 끝 문자로 변환됩니다. 를 사용 하 여 읽거나 읽고 쓰기 위해 열린 파일에서 **`"a+"`** 런타임 라이브러리는 파일 끝에 CTRL + Z가 있는지 확인 하 고 가능한 경우이를 제거 합니다. 이는를 사용 하 [`fseek`](fseek-fseeki64.md) 여 [](ftell-ftelli64.md) 파일 내에서 이동 하면 [`fseek`](fseek-fseeki64.md) 파일의 끝 부분에서가 제대로 동작 하지 않을 수 있기 때문입니다. **`t`** Microsoft 확장 이므로 ANSI 이식성을 원하는 경우 옵션을 사용 하지 마세요.

**`t`** 에 또는가 **`b`** 지정 되지 않은 경우 *`mode`* 기본 변환 모드는 전역 변수에 의해 정의 됩니다 [`_fmode`](../../c-runtime-library/fmode.md) . **`t`** 또는 **`b`** 가 인수 앞에 붙는 경우 함수는 실패 하 고을 반환 **`NULL`** 합니다.

텍스트 모드와 이진 모드에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**`freopen`**|`<stdio.h>`|
|**`_wfreopen`**|`<stdio.h>` 또는 `<wchar.h>`|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔,, 및에 연결 된 표준 스트림 핸들은 **`stdin`** **`stdout`** **`stderr`** C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_freopen.c
// compile with: /W3
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.
#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   // Reassign "stderr" to "freopen.out":
   stream = freopen( "freopen.out", "w", stderr ); // C4996
   // Note: freopen is deprecated; consider using freopen_s instead

   if( stream == NULL )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>참고 항목

[스트림 i/o](../../c-runtime-library/stream-i-o.md)\
[`fclose, _fcloseall`](fclose-fcloseall.md)\
[`_fdopen, _wfdopen`](fdopen-wfdopen.md)\
[`_fileno`](fileno.md)\
[`fopen, _wfopen`](fopen-wfopen.md)\
[`_open, _wopen`](open-wopen.md)\
[`_setmode`](setmode.md)\
