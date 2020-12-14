---
description: '다음에 대 한 자세한 정보: _getw'
title: _getw
ms.date: 4/2/2020
api_name:
- _getw
- _o__getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 2f951305351b4693b9787b6eac926c719afd3f3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296539"
---
# <a name="_getw"></a>_getw

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

**_getw** 읽은 정수 값을 반환 합니다. **EOF** 의 반환 값은 오류 또는 파일 끝을 나타냅니다. 그러나 **EOF** 값도 올바른 정수 값 이므로 **feof** **ferror** 를 사용 하 여 파일 끝 또는 오류 조건을 확인 합니다. *Stream* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 는 **EINVAL** 로 설정 되 고 함수는 **EOF** 를 반환 합니다.

## <a name="remarks"></a>설명

**_Getw** 함수는 스트림과 연결 된 파일에서 형식의 다음 이진 값을 읽고 **`int`** 읽지  않은 다음 문자를 가리키도록 연결 된 파일 포인터 (있는 경우)를 증가 시킵니다. **_getw** 는 스트림의 항목에 대 한 특별 한 맞춤을 가정 하지 않습니다.  **`int`** 형식의 크기와 형식 내 바이트의 순서가 시스템 마다 다르기 때문에 _getw를 사용 하는 데 문제가 발생할 수 있습니다 **`int`** .

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

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

### <a name="input-crt_getwtxt"></a>입력: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>출력

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>참조

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
