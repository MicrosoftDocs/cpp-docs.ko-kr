---
title: tmpfile
ms.date: 11/04/2016
apiname:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 98afcb7a3e04a96a1b08bc1b975634153e550839
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155565"
---
# <a name="tmpfile"></a>tmpfile

임시 파일을 만듭니다. 더 안전한 버전을 사용할 수 있으므로 이 함수는 더 이상 사용되지 않습니다. [tmpfile_s](tmpfile-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>반환 값

성공 하면 **tmpfile** 스트림 포인터를 반환 합니다. 그러지 않으면 반환 된 **NULL** 포인터.

## <a name="remarks"></a>설명

합니다 **tmpfile** 함수는 임시 파일을 만들고 해당 스트림에 대 한 포인터를 반환 합니다. 임시 파일은 루트 디렉터리에 만들어집니다. 루트가 아닌 디렉터리에 임시 파일을 만들려면 [fopen](fopen-wfopen.md)과 함께 [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 또는 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)을 사용합니다.

파일을 열 수 없는 경우 **tmpfile** 반환 된 **NULL** 포인터입니다. 이 임시 파일은 때나 일반적으로 프로그램을 종료 하면 파일을 닫을 때 자동으로 삭제 됩니다 **_rmtmp** 현재 작업 디렉터리를 변경 하지 않습니다 가정 라고 합니다. 임시 파일에 열려 **w + b** (이진 읽기/쓰기) 모드입니다.

TMP_MAX 보다 더 시도 하면 오류가 발생할 수 있습니다 (STDIO 참조 합니다. H) 사용 하 여 호출 **tmpfile**합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

> [!NOTE]
> 이 예제를 Windows Vista에서 실행하려면 관리 권한이 필요합니다.

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
