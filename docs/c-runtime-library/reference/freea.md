---
description: '다음에 대 한 자세한 정보: _freea'
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
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
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: 6d6f57117265e62e7d3c822110b52f69cb65ffac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282967"
---
# <a name="_freea"></a>_freea

메모리 블록을 할당 해제하거나 해제합니다.

## <a name="syntax"></a>구문

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
해제할 이전에 할당된 메모리 블록입니다.

## <a name="return-value"></a>반환 값

없음

## <a name="remarks"></a>설명

**_Freea** 함수는 [_malloca](malloca.md)를 호출 하 여 이전에 할당 된 메모리 블록 (*memblock*)의 할당을 취소 합니다. **_freea** 는 메모리가 힙과 스택에 할당 되었는지 확인 합니다. 스택에서 할당 된 경우 **_freea** 아무 작업도 수행 하지 않습니다. 힙에서 할당된 경우 해제된 바이트 수는 블록이 할당될 때 요청된 바이트 수와 일치합니다. *Memblock* 이 **NULL** 인 경우 포인터는 무시 되 고 **_freea** 즉시 반환 됩니다. 잘못 된 포인터를 해제 하려고 시도 하는 경우 ( **_malloca** 에 의해 할당 되지 않은 메모리 블록에 대 한 포인터) 후속 할당 요청에 영향을 주거나 오류가 발생할 수 있습니다.

메모리가 힙에 할당 되는 것을 발견 하면 **_freea** 는 내부적으로 **free** 를 호출 합니다. 메모리가 힙 또는 스택에 있는지 여부는 할당된 메모리 바로 앞 주소의 메모리에 배치된 표식에 의해 결정됩니다.

메모리를 확보 하는 동안 오류가 발생 하는 경우 **errno** 는 오류 특성에 따라 운영 체제의 정보로 설정 됩니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

메모리 블록이 해제된 후 [_heapmin](heapmin.md)은 사용되지 않은 영역을 결합하고 다시 운영 체제로 릴리스하여 힙에 있는 사용 가능한 메모리 양을 최소화합니다. 운영 체제로 릴리스되지 않은 해제된 메모리는 사용 가능한 풀로 복원되고 다시 할당할 수 있습니다.

**_Freea** 에 대 한 호출은 **_malloca** 에 대 한 모든 호출과 함께 제공 되어야 합니다. 동일한 메모리에서 **_freea** 를 두 번 호출 하는 것도 오류입니다. 응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우, 특히 **_CRTDBG_MAP_ALLOC** 을 정의 하 여 사용 하도록 설정 된 [_malloc_dbg](malloc-dbg.md) 기능을 사용 하는 경우 **_freea** 에 대 한 누락 되거나 중복 된 호출을 찾는 것이 더 쉽습니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

**_freea** 표시 됩니다 `__declspec(noalias)` . 즉, 함수가 전역 변수를 수정 하지 않도록 보장 합니다. 자세한 내용은 [noalias](../../cpp/noalias.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_freea**|\<stdlib.h> 및 \<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_malloca](malloca.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
