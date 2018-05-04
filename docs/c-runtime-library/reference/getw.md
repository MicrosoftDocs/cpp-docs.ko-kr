---
title: _getw | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getw
apilocation:
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
apitype: DLLExport
f1_keywords:
- _getw
dev_langs:
- C++
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3caffb90252780b833b80e3e5d1cd6d5ef6b0fcb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getw"></a>_getw

스트림에서 정수를 가져옵니다.

## <a name="syntax"></a>구문

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

**_getw** 읽은 정수 값을 반환 합니다. 반환 값이 **EOF** 오류 또는 파일의 끝을 나타냅니다. 그러나 때문에 **EOF** 값은 또한 유효한 정수 값을 사용 하 여 **feof** 또는 **ferror** 파일 끝 또는 오류 조건을 확인 합니다. 경우 *스트림* 은 **NULL**에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 하도록 허용 된 경우 **errno** 로 설정 된 **EINVAL** 함수가 반환 하 고 **EOF**합니다.

## <a name="remarks"></a>설명

**_getw** 함수 형식의 다음 이진 값을 읽습니다 **int** 연결 된 파일에서 *스트림* 을 가리키도록 연결 된 파일 포인터 (있는 경우) 증가 읽지 않은 문자입니다. **_getw** 스트림의 항목의 특수 정렬도 간주 하지 않습니다. 이식 관련 문제가 발생할 수 있습니다 **_getw** 때문에 크기는 **int** 유형과 내의 바이트 순서가 **int** 형식은 시스템에서 다를 합니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crtgetwtxt"></a>입력: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>출력

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
