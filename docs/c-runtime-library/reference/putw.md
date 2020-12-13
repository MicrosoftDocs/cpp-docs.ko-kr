---
description: '다음에 대 한 자세한 정보: _putw'
title: _putw
ms.date: 4/2/2020
api_name:
- _putw
- _o__putw
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
- _putw
helpviewer_keywords:
- integers, writing to streams
- putw function
- streams, writing integers to
- _putw function
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
ms.openlocfilehash: e49240d7410f47042f515f310ba79f9a9eb38398
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146395"
---
# <a name="_putw"></a>_putw

정수를 스트림에 씁니다.

## <a name="syntax"></a>구문

```C
int _putw(
   int binint,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*binint*<br/>
출력할 이진 정수입니다.

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

작성된 값을 반환합니다. **EOF** 의 반환 값은 오류를 나타낼 수 있습니다. **EOF** 도 올바른 정수 값 이므로 **ferror** 를 사용 하 여 오류를 확인 합니다. *Stream* 이 null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EOF** 를 반환 합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**_Putw** 함수는 **`int`** 스트림의 현재 위치에 형식의 이진 값을 씁니다 *.* **_putw** 은 스트림의 항목 맞춤에 영향을 주지 않으며 특수 한 맞춤을 가정 하지도 않습니다. **_putw** 는 주로 이전 라이브러리와의 호환성을 위해 사용 됩니다. 의 크기  **`int`** 와 내의 바이트 순서가 **`int`** 시스템 마다 다르기 때문에 _putw에서 이식성 문제가 발생할 수 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_putw**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_putw.c
/* This program uses _putw to write a
* word to a stream, then performs an error check.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   unsigned u;
   if( fopen_s( &stream, "data.out", "wb" ) )
      exit( 1 );
   for( u = 0; u < 10; u++ )
   {
      _putw( u + 0x2132, stream );   /* Write word to stream. */
      if( ferror( stream ) )         /* Make error check. */
      {
         printf( "_putw failed" );
         clearerr_s( stream );
         exit( 1 );
      }
   }
   printf( "Wrote ten words\n" );
   fclose( stream );
}
```

### <a name="output"></a>출력

```Output
Wrote ten words
```

## <a name="see-also"></a>참조

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getw](getw.md)<br/>
