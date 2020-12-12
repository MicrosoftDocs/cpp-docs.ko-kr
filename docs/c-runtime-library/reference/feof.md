---
description: '다음에 대 한 자세한 정보: feof'
title: feof
ms.date: 4/2/2020
api_name:
- feof
- _o_feof
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
- feof
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
ms.openlocfilehash: 6bfa0382878cef2843f3a6a6e2ba6e6d8c5bed8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322539"
---
# <a name="feof"></a>feof

스트림의 파일 끝을 테스트합니다.

## <a name="syntax"></a>구문

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

파일의 끝을 지나서 읽기 작업을 읽으려고 시도 하는 경우 **feof** 함수는 0이 아닌 값을 반환 합니다. 그렇지 않으면 0을 반환 합니다. 스트림 포인터가 **NULL** 인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용 된 경우 **errno** 가 **EINVAL** 로 설정 되 고 **feof** 0을 반환 합니다.

이러한 오류 코드 및 기타 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

루틴 (함수와 매크로 모두로 구현 됨) **의 feof** *스트림의* 끝이 전달 되었는지 여부를 확인 합니다. 파일의 끝이 전달 되 면 읽기 작업은 스트림이 닫힐 때까지 또는 [되감기](rewind.md), **fsetpos**, [fseek](fseek-fseeki64.md)또는 **clearerr** 이 호출 될 때까지 파일의 끝 표시기를 반환 합니다.

예를 들어 파일이 10 바이트를 포함 하 고 파일에서 10 바이트를 읽은 경우 **feof** 는 파일 포인터가 파일의 끝에 있더라도 끝을 넘어 읽으려고 시도 하지 않았으므로 0을 반환 합니다. 11 번째 바이트를 읽으려고 시도한 후에만에서 0이 아닌 값 **을 반환 합니다** .

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**feof**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crt_feoftxt"></a>입력: crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>출력

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>참조

[오류 처리](../../c-runtime-library/error-handling-crt.md)<br/>
[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
