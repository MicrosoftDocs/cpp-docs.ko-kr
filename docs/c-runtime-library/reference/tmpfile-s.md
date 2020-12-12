---
description: '다음에 대 한 자세한 정보: tmpfile_s'
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 1b5830375644cdcdd3d0c400d00735319b3af671
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326142"
---
# <a name="tmpfile_s"></a>tmpfile_s

임시 파일을 만듭니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [tmpfile](tmpfile.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>매개 변수

*pFilePtr*<br/>
생성된 스트림에 대한 포인터의 주소를 저장할 포인터의 주소입니다.

## <a name="return-value"></a>반환 값

정상적으로 실행되는 경우 0을 반환하고 오류 시에는 오류 코드를 반환합니다.

### <a name="error-conditions"></a>오류 조건

|*pFilePtr*|**반환 값**|*PFilePtr* **의 내용**  |
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|변경되지 않음|

위의 매개 변수 유효성 검사 오류가 발생하는 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 는 **EINVAL** 로 설정 되 고 반환 값은 **EINVAL** 입니다.

## <a name="remarks"></a>설명

**Tmpfile_s** 함수는 임시 파일을 만들고 해당 스트림에 대 한 포인터를 *pFilePtr* 인수에 배치 합니다. 임시 파일은 루트 디렉터리에 만들어집니다. 루트가 아닌 디렉터리에 임시 파일을 만들려면 [fopen](fopen-wfopen.md)과 함께 [tmpnam_s](tmpnam-s-wtmpnam-s.md) 또는 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)을 사용합니다.

파일을 열 수 없는 경우 **Tmpfile_s** *PFilePtr* 매개 변수에 **NULL** 을 씁니다. 이 임시 파일은 파일이 닫힐 때, 프로그램이 정상적으로 종료 될 때 또는 현재 작업 디렉터리가 변경 되지 않는다고 가정할 때 **_rmtmp** 가 호출 될 때 자동으로 삭제 됩니다. 임시 파일은 **w + b** (이진 읽기/쓰기) 모드에서 열립니다.

**TMP_MAX_S** 이상 시도 하면 오류가 발생할 수 있습니다 (stdio.h 참조). H) **tmpfile_s** 를 사용 하 여를 호출 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

> [!NOTE]
> 이 예에서는 Windows에서 실행 하기 위해 관리자 권한이 필요할 수 있습니다.

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
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
