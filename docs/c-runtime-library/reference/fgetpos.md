---
description: '자세히 알아보기: fgetpos'
title: fgetpos
ms.date: 4/2/2020
api_name:
- fgetpos
- _o_fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 72ee6e683d568de1650d5a046050230fa86dee24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151764"
---
# <a name="fgetpos"></a>fgetpos

스트림의 파일 위치 표시기를 가져옵니다.

## <a name="syntax"></a>구문

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
대상 스트림입니다.

*pos*<br/>
위치 표시기 스토리지입니다.

## <a name="return-value"></a>반환 값

성공 하면 **fgetpos** 는 0을 반환 합니다. 오류가 발생 하면 0이 아닌 값을 반환 하 고 **errno** 를 stdio.h에 정의 된 다음 매니페스트 상수 중 하나로 설정 합니다. H): **Ebadf**, 지정 된 스트림이 유효한 파일 포인터가 아니거나 액세스할 수 없음을 의미 하는 또는 **EINVAL** 가 null 포인터인 경우와 같이 *스트림* 값 또는 *pos* 의 값이 잘못 되었음을 의미 합니다. *Stream* 또는 *pos* 가 **NULL** 포인터인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다.

## <a name="remarks"></a>설명

**Fgetpos** 함수는 *스트림* 인수의 파일 위치 표시기의 현재 값을 가져와 *pos* 가 가리키는 개체에 저장 합니다. **Fsetpos** 함수는 나중에 *pos* 에 저장 된 정보를 사용 하 여 **fgetpos** 가 호출 된 시간에 *스트림* 인수의 포인터를 해당 위치로 다시 설정할 수 있습니다. *Pos* 값은 내부 형식으로 저장 되며 **fgetpos** 및 **fsetpos** 에 의해서만 사용 됩니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetpostxt"></a>입력: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>출력 crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
