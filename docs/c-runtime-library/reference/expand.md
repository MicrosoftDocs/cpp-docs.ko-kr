---
description: '다음에 대 한 자세한 정보: _expand'
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 31558bb67266430cc028e37a1e23dff2fa411356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235967"
---
# <a name="_expand"></a>_expand

메모리 블록의 크기를 변경합니다.

## <a name="syntax"></a>구문

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
이전에 할당된 메모리 블록에 대한 포인터입니다.

*size*<br/>
새 크기(바이트)입니다.

## <a name="return-value"></a>반환 값

**_expand** 는 다시 할당 된 메모리 블록에 대 한 void 포인터를 반환 합니다. **realloc** 와 달리 **_expand** 은 블록을 이동 하 여 크기를 변경할 수 없습니다. 따라서 이동 하지 않고 블록을 확장 하는 데 사용할 수 있는 메모리가 충분 한 경우 **_expand** 에 대 한 *memblock* 매개 변수가 반환 값과 동일 합니다.

작업을 수행 하는 동안 오류가 검색 되 면 **_Expand** **NULL** 을 반환 합니다. 예를 들어 **_expand** 를 사용 하 여 메모리 블록을 축소 하는 경우 작은 블록 힙 또는 잘못 된 블록 포인터의 손상이 감지 되 고 **NULL** 이 반환 될 수 있습니다.

블록을 이동 하지 않고 지정 된 크기로 확장 하는 데 사용할 수 있는 메모리가 충분 하지 않은 경우 함수는 **NULL** 을 반환 합니다. **_expand** 는 요청한 것 보다 작은 크기로 확장 된 블록을 반환 하지 않습니다. 오류가 발생 하는 경우 **errno** 는 오류의 특성을 나타냅니다. **Errno** 에 대 한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요.

반환 값은 모든 형식의 개체 스토리지를 위해 적절하게 맞도록 보장되어 있는 스토리지 공간을 가리킵니다. 항목의 새 크기를 확인 하려면 **_msize** 을 사용 합니다. 이외의 형식에 대 한 포인터를 가져오려면 **`void`** 반환 값에 형식 캐스팅을 사용 합니다.

## <a name="remarks"></a>설명

**_Expand** 함수는 힙에서 위치를 이동 하지 않고 블록을 확장 하거나 축소 하 여 이전에 할당 된 메모리 블록의 크기를 변경 합니다. *Memblock* 매개 변수는 블록의 시작 부분을 가리킵니다. *Size* 매개 변수는 블록의 새 크기 (바이트)를 제공 합니다. 블록의 콘텐츠는 새 크기와 이전 크기 중 더 짧은 크기까지 변경 사항이 없습니다. *memblock* 은 해제 된 블록 일 수 없습니다.

> [!NOTE]
> 64 비트 플랫폼에서는 새 크기가 현재 크기 보다 작은 경우 **_expand** 블록을 차단 하지 않을 수 있습니다. 특히 블록 크기가 16K 미만 이어서 낮은 조각화 힙에서 할당 된 경우 **_expand** 는 블록을 변경 하지 않고 *memblock* 을 반환 합니다.

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **_expand** 은 [_expand_dbg](expand-dbg.md)으로 확인 됩니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Memblock* 이 null 포인터인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 **NULL** 을 반환 합니다. *Size* 가 **_HEAP_MAXREQ** 보다 크면 **errno** 가 **enomem** 으로 설정 되 고 함수는 **NULL** 을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
