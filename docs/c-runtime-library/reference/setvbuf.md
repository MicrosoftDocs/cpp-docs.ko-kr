---
description: '자세히 알아보기: setvbuf'
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 8010bdea7a2542e8797ea8c352d9221cdb4cc0b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303494"
---
# <a name="setvbuf"></a>setvbuf

스트림 버퍼링 및 버퍼 크기를 제어합니다.

## <a name="syntax"></a>구문

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

*버퍼*<br/>
사용자가 할당한 버퍼입니다.

*mode*<br/>
버퍼링 모드입니다.

*size*<br/>
버퍼 크기(바이트)입니다. 허용 범위: 2 <= *size* <= INT_MAX (2147483647). 내부적으로 *크기* 에 대해 제공 되는 값은 가장 가까운 2의 배수로 반올림 됩니다.

## <a name="return-value"></a>반환 값

정상적으로 실행되는 경우 0을 반환합니다.

*Stream* 이 **NULL** 이거나 *모드나* *크기가* 유효한 변경 범위에 포함 되지 않은 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속해서 실행하도록 허용된 경우 이 함수는 -1을 반환하고 **errno** 를 **EINVAL** 로 설정합니다.

이러한 오류 코드 및 기타 오류 코드에 대한 내용은 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**Setvbuf** 함수를 사용 하면 프로그램에서 *스트림의* 버퍼링 및 버퍼 크기를 모두 제어할 수 있습니다. *스트림이* 열려 있었기 때문에 i/o 작업이 수행 되지 않은 열려 있는 파일을 참조 해야 합니다. *버퍼* 에서 가리키는 배열이 **NULL** 이 아닌 경우 버퍼로 사용 됩니다 .이 경우 **setvbuf** 는 자동으로 할당 된 바이트 *크기*/2 바이트의 버퍼를 사용 \* 합니다.

모드는 **_IOFBF**, **_IOLBF** 또는 **_IONBF** 이어야 합니다. *Mode* 가 **_IOFBF** 또는 **_IOLBF** 이면 *크기가* 버퍼의 크기로 사용 됩니다. *Mode* 가 **_IONBF** 이면 스트림은 버퍼링 되지 않으며 *크기* 는 무시 되 고 *버퍼* 는 무시 됩니다. *모드* 의 값과 해당 의미는 다음과 같습니다.

|*모드* 값|의미|
|-|-|
| **_IOFBF** | 전체 버퍼링 즉, 버퍼는 버퍼로 *사용 되 고* *크기* 는 버퍼 크기로 사용 됩니다. *버퍼가* **NULL** 이면 자동으로 할당 된 버퍼 *크기* (바이트)가 사용 됩니다. |
| **_IOLBF** | 이 값을 사용하는 경우 라인 버퍼링이 제공되는 시스템도 있습니다. 그러나 Win32의 경우 동작은 **_IOFBF** 전체 버퍼링과 동일 합니다. |
| **_IONBF** | *버퍼 또는* *크기* 에 관계 없이 버퍼가 사용 되지 않습니다. |

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
