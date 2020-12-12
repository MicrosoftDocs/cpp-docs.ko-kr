---
description: '자세한 정보: fseek, _fseeki64'
title: fseek, _fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: 7e15bd7cd273da2f73a58c2bd012670216c1938c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114327"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

파일 포인터를 지정된 위치로 이동합니다.

## <a name="syntax"></a>구문

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

*offset*<br/>
*origin* 부터의 바이트 수입니다.

*원본*<br/>
초기 위치입니다.

## <a name="return-value"></a>반환 값

성공 하면 **fseek** 및 **_fseeki64** 가 0을 반환 합니다. 그렇지 않으면 0이 아닌 값을 반환합니다. 검색을 수행할 수 없는 디바이스에서는 반환 값이 정의되지 않습니다. *Stream* 이 null 포인터 이거나 *원본이* 아래에서 설명 하는 허용 되는 값 중 하나가 아닌 경우 **Fseek** 및 **_fseeki64** 는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

## <a name="remarks"></a>설명

**Fseek** 및 **_fseeki64** 함수는 *스트림과* 연결 된 파일 포인터 (있는 경우)를 *원점* 에서 *오프셋* 된 바이트의 새 위치로 이동 합니다. 스트림에 대한 다음 작업은 새 위치에서 수행됩니다. 업데이트를 위해 열린 스트림에 대한 다음 작업은 읽기 또는 쓰기일 수 있습니다. 인수 *원본은* stdio.h에 정의 된 다음 상수 중 하나 여야 합니다. 넣기

|원점 값|의미|
|-|-|
| **SEEK_CUR** | 파일 포인터의 현재 위치 |
| **SEEK_END** | 파일 끝 |
| **SEEK_SET** | 파일 시작 |

**Fseek** 및 **_fseeki64** 를 사용 하 여 파일에서 포인터의 위치를 변경할 수 있습니다. 포인터는 파일 끝을 지나서 배치될 수도 있습니다. **fseek** 및 **_fseeki64** 는 파일의 끝 표시기를 지우고 *스트림에* 대 한 이전 [ungetc](ungetc-ungetwc.md) 호출의 영향을 부정 합니다.

데이터를 추가하기 위해 파일이 열리면 현재 파일 위치는 다음 쓰기가 수행되는 위치가 아니라 마지막 I/O 작업에 의해 결정됩니다. 추가를 위해 열린 파일에서 I/O 작업이 아직 수행되지 않은 경우 파일 위치는 파일의 시작입니다.

텍스트 모드에서 열린 스트림의 경우 캐리지 리턴-줄 바꿈 번역으로 인해 **fseek** 및 **_fseeki64** 에서 예기치 않은 결과가 생성 될 수 있으므로 **fseek** 및 **_fseeki64** 는 제한적으로 사용 됩니다. 텍스트 모드에서 연 스트림에 대해 작동 하도록 보장 되는 **fseek** 및 **_fseeki64** 작업은 다음과 같습니다.

- 원점 값을 기준으로 한 0 오프셋을 사용하여 검색

- **_Fseeki64** 를 사용 하는 경우 **ftell** 또는 [_ftelli64](ftell-ftelli64.md) 을 사용할 때 [ftell](ftell-ftelli64.md) 에서 반환 된 오프셋 값을 사용 하 여 파일의 시작 부분에서 검색 합니다.

또한 텍스트 모드에서 Ctrl+Z는 입력 시 파일 끝 문자로 해석됩니다. 읽기/쓰기용으로 열려 있는 파일에서 [fopen](fopen-wfopen.md) 및 모든 관련 루틴은 파일 끝에 CTRL + Z가 있는지 확인 하 고 가능 하면 제거 합니다. 이 작업은 **fseek** 와 [fseek](ftell-ftelli64.md) **_fseeki64** 및 [_ftelli64](ftell-ftelli64.md)의 조합을 사용 하 여 CTRL + Z로 끝나는 파일 내에서 이동 하면 파일의 끝 부분에서 **fseek** 또는 **_fseeki64** 가 제대로 동작 하지 않을 수 있기 때문에 수행 됩니다.

CRT가 BOM(바이트 순서 표시)으로 시작되는 파일을 열면 파일 포인터는 BOM 뒤(파일 실제 콘텐츠의 시작)에 배치됩니다. 파일의 시작 부분을 **검색** 해야 하는 경우 [fseek](ftell-ftelli64.md) 을 사용 하 여 위치 0이 아닌 초기 위치와 **fseek** 를 가져옵니다.

이 함수는 실행 중에 다른 스레드를 잠그므로 스레드로부터 안전합니다. 잠기지 않는 버전의 경우 [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[되감습니다](rewind.md)<br/>
