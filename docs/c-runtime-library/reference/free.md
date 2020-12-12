---
description: '자세히 알아보기: 무료'
title: free
ms.date: 4/2/2020
api_name:
- free
- _o_free
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
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: 731bd1ea6cf3bfe56bf71ee762fb3477346ddf13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314024"
---
# <a name="free"></a>free

메모리 블록을 할당 해제하거나 해제합니다.

## <a name="syntax"></a>구문

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
해제할 이전에 할당된 메모리 블록입니다.

## <a name="remarks"></a>설명

**Free** 함수는 **calloc**, **malloc** 또는 **realloc** 에 대 한 호출에 의해 이전에 할당 된 메모리 블록 (*memblock*)의 할당을 취소 합니다. 해제 된 바이트 수는 블록이 할당 되거나 ( **realloc** 의 경우 다시 할당) 요청 된 바이트 수와 동일 합니다. *Memblock* 이 **NULL** 인 경우 포인터는 무시 되 고 **free** 는 즉시 반환 됩니다. 잘못 된 포인터 ( **calloc**, **malloc** 또는 **realloc** 에 의해 할당 되지 않은 메모리 블록에 대 한 포인터)를 해제 하려고 하면 후속 할당 요청에 영향을 줄 수 있으며 오류가 발생할 수 있습니다.

메모리를 확보 하는 동안 오류가 발생 하는 경우 **errno** 는 오류 특성에 따라 운영 체제의 정보로 설정 됩니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

메모리 블록이 해제된 후 [_heapmin](heapmin.md)은 사용되지 않은 영역을 결합하고 다시 운영 체제로 릴리스하여 힙에 있는 사용 가능한 메모리 양을 최소화합니다. 운영 체제로 릴리스되지 않은 해제된 메모리는 사용 가능한 풀로 복원되고 다시 할당할 수 있습니다.

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **사용 가능한** [_free_dbg](free-dbg.md)으로 확인 됩니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

**free** 는로 표시 됩니다 `__declspec(noalias)` . 즉, 함수가 전역 변수를 수정 하지 않도록 보장 됩니다. 자세한 내용은 [noalias](../../cpp/noalias.md)를 참조하세요.

[_malloca](malloca.md)를 사용하여 할당된 메모리를 해제하려면 [_freea](freea.md)를 사용합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**free**|\<stdlib.h> 및 \<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[malloc](malloc.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
