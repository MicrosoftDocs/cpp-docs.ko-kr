---
description: '자세히 알아보기: tmpfile'
title: tmpfile
ms.date: 11/04/2016
api_name:
- tmpfile
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 27760a7d1369a0292c6719667b8cb182ce7df815
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299516"
---
# <a name="tmpfile"></a>tmpfile

임시 파일을 만듭니다. 더 안전한 버전을 사용할 수 있으므로 이 함수는 더 이상 사용되지 않습니다. [tmpfile_s](tmpfile-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Return Value

성공 하면 **tmpfile** 는 스트림 포인터를 반환 합니다. 그렇지 않으면 **NULL** 포인터를 반환 합니다.

## <a name="remarks"></a>설명

**Tmpfile** 함수는 임시 파일을 만들고 해당 스트림에 대 한 포인터를 반환 합니다. 임시 파일은 루트 디렉터리에 만들어집니다. 루트가 아닌 디렉터리에 임시 파일을 만들려면 [fopen](fopen-wfopen.md)과 함께 [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 또는 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)을 사용합니다.

파일을 열 수 없는 경우 **tmpfile** 는 **NULL** 포인터를 반환 합니다. 이 임시 파일은 파일이 닫힐 때, 프로그램이 정상적으로 종료 될 때 또는 현재 작업 디렉터리가 변경 되지 않는다고 가정할 때 **_rmtmp** 가 호출 될 때 자동으로 삭제 됩니다. 임시 파일은 **w + b** (이진 읽기/쓰기) 모드에서 열립니다.

TMP_MAX 이상 시도 하면 오류가 발생할 수 있습니다 (STDIO.H 참조). H)를 사용 하 여 **tmpfile** 를 호출 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

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

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
