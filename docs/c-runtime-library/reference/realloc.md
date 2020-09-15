---
title: realloc
description: Realloc ();에 대 한 API 참조 는 메모리 블록을 다시 할당 합니다.
ms.date: 9/11/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: c68909b2f5d73959465d63af522ceeb00c8ce23e
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075818"
---
# <a name="realloc"></a>realloc

메모리 블록을 다시 할당합니다.

## <a name="syntax"></a>구문

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>매개 변수

*`memblock`*\
이전에 할당된 메모리 블록에 대한 포인터입니다.

*`size`*\
새 크기(바이트)입니다.

## <a name="return-value"></a>반환 값

**`realloc`****`void`** 다시 할당 된 (그리고 이동 가능한) 메모리 블록에 대 한 포인터를 반환 합니다.

블록을 지정 된 크기로 확장 하는 데 사용할 수 있는 메모리가 충분 하지 않은 경우 원래 블록은 변경 되지 않고 그대로 유지 되 고 **`NULL`** 이 반환 됩니다.

*`size`* 가 0 이면에서 가리키는 블록이 *`memblock`* 해제 됩니다. 반환 값은 이며 **`NULL`** , *`memblock`* 은 해제 된 블록을 가리키는 상태로 유지 됩니다.

반환 값은 모든 형식의 개체 저장을 위해 적절 하 게 정렬 된 저장소 공간을 가리킵니다. 이외의 형식에 대 한 포인터를 가져오려면 **`void`** 반환 값에 형식 캐스팅을 사용 합니다.

## <a name="remarks"></a>설명

> [!NOTE]
> **`realloc`** 새 동작이 Windows 운영 체제와 호환 되지 않기 때문에 C17 동작을 구현 하도록 업데이트 되지 않았습니다.

**`realloc`** 함수는 할당 된 메모리 블록의 크기를 변경 합니다. *`memblock`* 인수는 메모리 블록의 시작 부분을 가리킵니다. 가 이면는와 *`memblock`* **`NULL`** **`realloc`** 동일한 방식으로 동작 **`malloc`** 하 고 새 바이트 블록을 할당 *`size`* 합니다. *`memblock`* 가이 아니면, **`NULL`** 또는에 대 한 이전 호출에서 반환 된 포인터 여야 **`calloc`** 합니다 **`malloc`** **`realloc`** .

*`size`* 인수는 블록의 새 크기 (바이트)를 제공 합니다. 블록의 내용은 새 크기와 이전 크기 중 더 짧은 쪽까지는 변경되지 않습니다. 그러나 새 블록은 다른 위치에 있을 수 있습니다. 새 블록은 새 메모리 위치에 있을 수 있으므로에서 반환 되는 포인터는 **`realloc`** 인수를 통해 전달 되는 포인터가 아닙니다 *`memblock`* . **`realloc`** 버퍼 증가 시 새로 할당 된 메모리는 0이 아닙니다.

**`realloc`****`errno`** **`ENOMEM`** 메모리 할당이 실패 하거나 요청 된 메모리의 양이를 초과 하는 경우를로 설정 **`_HEAP_MAXREQ`** 합니다. 이러한 오류 코드 및 기타 오류 코드에 대한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

**`realloc`****`malloc`** 는 c + + [_set_new_mode](set-new-mode.md) 함수를 사용 하 여 새 처리기 모드를 설정 하기 위해를 호출 합니다. 새 처리기 모드는 실패 시 **`malloc`** [_set_new_handler](set-new-handler.md)에 의해 설정 된 대로 새 처리기 루틴을 호출 하는지 여부를 나타냅니다. 기본적으로에서는 **`malloc`** 오류 발생 시 새 처리기 루틴을 호출 하 여 메모리를 할당 하지 않습니다. 가 **`realloc`** 메모리 할당에 실패 하는 경우 **`malloc`** 연산자가 **`new`** 같은 이유로 실패 했을 때 수행 하는 것과 동일한 방식으로 새 처리기 루틴을 호출 하도록이 기본 동작을 재정의할 수 있습니다. 기본값을 재정의하려면 다음 코드를

```C
_set_new_mode(1);
```

프로그램에서 초기에 호출하거나, NEWMODE.OBJ를 사용하여 연결합니다([링크 옵션](../../c-runtime-library/link-options.md) 참조).

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **`realloc`** [_realloc_dbg](realloc-dbg.md)으로 확인 됩니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

**`realloc`** 는로 표시 되며,이는 `__declspec(noalias)` `__declspec(restrict)` 함수가 전역 변수를 수정 하지 않도록 보장 하 고 반환 된 포인터에 별칭이 지정 되지 않음을 의미 합니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`realloc`**|\<stdlib.h> 및 \<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)\
[calloc](calloc.md)\
[늘릴](free.md)\
[malloc](malloc.md)
