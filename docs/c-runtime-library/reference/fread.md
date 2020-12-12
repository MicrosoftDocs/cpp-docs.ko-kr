---
description: '자세한 정보: fread'
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 131dacd296d4e710ea1b91d9a8578ef06b76a341
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314050"
---
# <a name="fread"></a>fread

스트림에서 데이터를 읽습니다.

## <a name="syntax"></a>구문

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
데이터의 스토리지 위치입니다.

*size*<br/>
항목 크기(바이트)입니다.

*count*<br/>
읽힐 항목의 최대 수입니다.

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

**fread** 는 실제로 읽은 전체 항목 수를 반환 합니다. 오류가 발생 하는 경우에는 count 보다 적거나 파일의 끝에 도달 하는 경우에 *는 개수 보다* 적을 *수 있습니다.* **Feof** 또는 **ferror** 함수를 사용 하 여 파일 끝 조건과 읽기 오류를 구분 합니다. *크기* 또는 *개수가* 0 인 경우 **fread** 는 0을 반환 하 고 버퍼 내용은 변경 되지 않습니다. *Stream* 또는 *buffer* 가 null 포인터인 경우 **Fread** 는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 0을 반환 합니다.

이러한 오류 코드에 대 한 자세한 내용은 [ \_ doserrno, errno, \_ sys \_ errlist 및 \_ sys의 \_ r](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 을 참조 하세요.

## <a name="remarks"></a>설명

**Fread** 함수는 입력 *스트림에서* *크기* 바이트의 항목 *수를 계산* 하 여 *버퍼* 에 저장 합니다. *스트림* (있는 경우)과 연결 된 파일 포인터는 실제로 읽은 바이트 수 만큼 증가 합니다. 지정 된 스트림이 [텍스트 모드](../../c-runtime-library/text-and-binary-mode-file-i-o.md)에서 열리면 Windows 스타일 줄바꿈는 Unix 스타일 줄바꿈로 변환 됩니다. 즉, 캐리지 리턴 (캐리지 리턴-줄 바꿈) 쌍은 LF (단일 줄 바꿈) 문자로 대체 됩니다. 이렇게 바뀌더라도 파일 포인터 또는 반환 값에는 영향을 미치지 않습니다. 오류가 발생할 경우 파일 포인터 위치는 비활성화 상태입니다. 부분적으로 읽은 항목의 값은 확인할 수 없습니다.

텍스트 모드 스트림에서 사용 되는 경우 요청 된 데이터 양 (즉, *크기* \* *수*)이 내부 **파일** 버퍼 크기 보다 크거나 같은 경우 \* (기본값은 [setvbuf](../../c-runtime-library/reference/setvbuf.md)를 사용 하 여 구성 가능한 4096 바이트), 스트림 데이터는 사용자가 제공 하는 버퍼로 직접 복사 되 고, 줄 바꿈 변환은 해당 버퍼에서 수행 됩니다. 변환 된 데이터는 버퍼에 복사 된 스트림 데이터 보다 짧을 수 있으므로 *버퍼* \[ *return_value* \* *크기*] ( *return_value* 는 **fread** 의 반환 값) 이면 파일에서 변환 되지 않은 데이터가 포함 될 수 있습니다. 따라서  \[  \* 버퍼의 의도를 C 스타일 문자열로 사용할 경우 버퍼 return_value *size*]에서 문자 데이터를 null로 종료 하는 것이 좋습니다. 텍스트 모드와 이진 모드의 효과에 대 한 자세한 내용은 [fopen](fopen-wfopen.md) 을 참조 하세요.

이 함수는 다른 스레드를 잠급니다. 잠기지 않는 버전이 필요한 경우 **_fread_nolock** 를 사용 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fread**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[텍스트 및 이진 파일 i/o](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
