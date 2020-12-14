---
description: '다음에 대 한 자세한 정보: _expand_dbg'
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 6ebdce3a22c4e5b4b63b8301570effed888fe66f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235968"
---
# <a name="_expand_dbg"></a>_expand_dbg

블록을 확장하거나 축소하여 힙에서 지정된 메모리 블록의 크기를 조정합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*Data*<br/>
이전에 할당된 메모리 블록에 대한 포인터입니다.

*newSize*<br/>
요청된 블록의 새 크기(바이트)입니다.

*blockType*<br/>
크기 조정 된 블록의 요청 된 형식: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**.

*filename*<br/>
확장 작업 또는 **NULL** 을 요청한 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
확장 작업이 요청 되었거나 **NULL 인** 소스 파일의 줄 번호입니다.

*Filename* 및 *linenumber* 매개 변수는 **_expand_dbg** 명시적으로 호출 되었거나 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 전처리기 상수가 정의 된 경우에만 사용할 수 있습니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면 **_expand_dbg** 는 크기 조정 된 메모리 블록에 대 한 포인터를 반환 합니다. 메모리가 이동되지 않으므로 주소는 userData와 같습니다. 오류가 발생 했거나 블록을 요청 된 크기로 확장할 수 없는 경우 **NULL** 을 반환 합니다. 오류가 발생 하는 경우 **errno** 은 운영 체제에서 오류 특성에 대 한 정보를 포함 합니다. **Errno** 에 대 한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요.

## <a name="remarks"></a>설명

**_Expand_dbg** 함수는 _ [expand](expand.md) 함수의 디버그 버전입니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 **_expand_dbg** 에 대 한 각 호출은 **_expand** 호출로 줄어듭니다. **_Expand** 및 **_expand_dbg** 둘 다 기본 힙에서 메모리 블록 크기를 조정 하지만, **_expand_dbg** 는 블록의 사용자 부분 양쪽에 있는 버퍼, 특정 할당 형식을 추적 하는 블록 형식 매개 변수, 할당 요청의 출처를 확인 하는 *파일 이름* / *linenumber* 정보 등 여러 가지 디버깅 기능을 사용할 수 있습니다.

**_expand_dbg** 지정 된 메모리 블록의 크기를 요청 된 *newSize* 보다 약간 더 많이 사용 하 여 크기를 조정 합니다. *newSize* 는 원래 할당 된 메모리 블록의 크기 보다 크거나 적을 수 있습니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 애플리케이션에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 크기를 조정하려면 원래 메모리 블록을 확장하거나 축소합니다. [_realloc_dbg](realloc-dbg.md) 함수와 마찬가지로 **_expand_dbg** 는 메모리 블록을 이동 하지 않습니다.

*NewSize* 가 원래 블록 크기 보다 크면 메모리 블록이 확장 됩니다. 확장 하는 동안 메모리 블록을 요청 된 크기에 맞게 확장할 수 없는 경우 **NULL** 이 반환 됩니다. *NewSize* 가 원래 블록 크기 보다 작은 경우 새 크기를 얻을 때까지 메모리 블록이 축소 됩니다.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요. 애플리케이션의 디버그 빌드에서 표준 힙 함수를 호출하는 것과 해당 함수의 디버그 버전을 호출하는 것의 차이에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Memblock* 이 null 포인터 이거나 크기가 **_HEAP_MAXREQ** 보다 큰 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 **NULL** 을 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>의견

이 프로그램의 출력은 모든 섹션을 확장하는 컴퓨터 기능에 따라 달라집니다. 모든 섹션이 확장되면 출력이 출력 섹션에 반영됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
