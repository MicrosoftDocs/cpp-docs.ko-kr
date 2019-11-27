---
title: calloc
description: C 런타임 라이브러리 함수 calloc는 0으로 초기화 된 메모리를 할당 합니다.
ms.date: 09/27/2019
api_name:
- calloc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 228ec6d01a6f57ff98a9030f5a6d82e4c57388cd
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685365"
---
# <a name="calloc"></a>calloc

0으로 초기화된 요소가 있는 메모리에 배열을 할당합니다.

## <a name="syntax"></a>구문

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>매개 변수

*number*<br/>
요소의 수입니다.

*size*<br/>
각 요소의 길이입니다(바이트).

## <a name="return-value"></a>반환 값

**calloc** 은 할당 된 공간에 대 한 포인터를 반환 합니다. 반환 값이 가리킨 스토리지 공간은 모든 형식의 개체 스토리지를 위해 적절하게 정렬되도록 보장됩니다. **Void**이외의 형식에 대 한 포인터를 가져오려면 반환 값에 형식 캐스팅을 사용 합니다.

## <a name="remarks"></a>주의

**Calloc** 함수는 각각 길이 *크기* 바이트의 *숫자* 요소 배열에 대 한 저장소 공간을 할당 합니다. 각 요소는 0으로 초기화됩니다.

**calloc** 는 메모리 할당이 실패 하거나 요청 된 메모리 양이 **_HEAP_MAXREQ**을 초과 하는 경우 **errno** 을 **enomem** 으로 설정 합니다. 이 오류 코드 및 기타 오류 코드에 대한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

Microsoft 구현에서 *number* 또는 *size* 가 0 인 경우 **calloc** 는 크기가 0이 아닌 할당 된 블록에 대 한 포인터를 반환 합니다. 반환 된 포인터를 통해 읽거나 쓰려고 하면 정의 되지 않은 동작이 발생 합니다.

**calloc** 는 C++ [_set_new_mode](set-new-mode.md) 함수를 사용 하 여 *새 처리기 모드*를 설정 합니다. 새 처리기 모드는 실패 시 **calloc** 가 [_set_new_handler](set-new-handler.md)설정 된 대로 새 처리기 루틴을 호출 하는지 여부를 나타냅니다. 기본적으로 **calloc** 는 메모리 할당 실패 시 새 처리기 루틴을 호출 하지 않습니다. 이 기본 동작을 재정의 하 여 **calloc** 에서 메모리를 할당 하지 못할 때 **새** 연산자가 같은 이유로 실패 했을 때와 동일한 방식으로 새 처리기 루틴을 호출 하도록 할 수 있습니다. 기본값을 재정의하려면 다음을

```C
_set_new_mode(1);
```

프로그램의 초기에 사용 하거나 Newmode를 사용 하 여 연결 *합니다. OBJ* ( [링크 옵션](../../c-runtime-library/link-options.md)참조).

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **calloc** 은 [_calloc_dbg](calloc-dbg.md)를 확인 합니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

**calloc** 는 `__declspec(noalias)` 및 `__declspec(restrict)`으로 표시 되어 있습니다. 즉, 함수가 전역 변수를 수정 하지 않도록 보장 하 고 반환 된 포인터에 별칭이 지정 되지 않습니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**calloc**|\<stdlib.h> 및 \<malloc.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
