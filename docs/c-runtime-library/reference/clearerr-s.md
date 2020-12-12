---
description: '다음에 대 한 자세한 정보: clearerr_s'
title: clearerr_s
ms.date: 4/2/2020
api_name:
- clearerr_s
- _o_clearerr_s
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
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: cbc9ac5122b5754b43f6fb93c4301afd6e449568
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171532"
---
# <a name="clearerr_s"></a>clearerr_s

스트림에 대한 오류 표시기를 다시 설정합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [clearerr](clearerr.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**파일** 구조에 대 한 포인터

## <a name="return-value"></a>반환 값

성공 하면 0입니다. **EINVAL** 가 **NULL** *인 경우* .

## <a name="remarks"></a>설명

**Clearerr_s** 함수는 *스트림에* 대 한 오류 표시기와 파일 끝 표시기를 다시 설정 합니다. 오류 표시기는 자동으로 지워지지 않습니다. 지정 된 스트림에 대 한 오류 표시기가 설정 되 면 해당 스트림의 연산은 **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos** 또는 [되감기](rewind.md) 가 호출 될 때까지 오류 값을 계속 반환 합니다.

*Stream* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **EINVAL** 를 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>입력

```Input
n
```

### <a name="output"></a>출력

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>참조

[오류 처리](../../c-runtime-library/error-handling-crt.md)<br/>
[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
