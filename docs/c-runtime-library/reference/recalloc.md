---
description: '다음에 대 한 자세한 정보: _recalloc'
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 09cecc0b7fe006ca5f52340254534fcc67b70e84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205176"
---
# <a name="_recalloc"></a>_recalloc

**Realloc** 와 **calloc** 의 조합입니다. 메모리에 배열을 다시 할당하고 해당 요소를 0으로 초기화합니다.

## <a name="syntax"></a>구문

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
이전에 할당된 메모리 블록에 대한 포인터입니다.

*number*<br/>
요소의 수입니다.

*size*<br/>
각 요소의 길이입니다(바이트).

## <a name="return-value"></a>반환 값

**_recalloc** **`void`** 는 다시 할당 된 (그리고 이동 가능한) 메모리 블록에 대 한 포인터를 반환 합니다.

블록을 지정 된 크기로 확장 하는 데 사용할 수 있는 메모리가 충분 하지 않은 경우 원래 블록은 변경 되지 않은 상태로 유지 되 고 **NULL** 이 반환 됩니다.

요청 된 크기가 0 이면 *memblock* 이 가리키는 블록이 해제 됩니다. 반환 값은 **NULL** 이 고 *memblock* 은 해제 된 블록을 가리키는 상태로 유지 됩니다.

반환 값은 모든 형식의 개체 스토리지를 위해 적절하게 맞도록 보장되어 있는 스토리지 공간을 가리킵니다. 이외의 형식에 대 한 포인터를 가져오려면 **`void`** 반환 값에 형식 캐스팅을 사용 합니다.

## <a name="remarks"></a>설명

**_Recalloc** 함수는 할당 된 메모리 블록의 크기를 변경 합니다. *Memblock* 인수는 메모리 블록의 시작 부분을 가리킵니다. *Memblock* 이 **NULL** 인 경우 **_recalloc** 는 [calloc](calloc.md) 와 같은 방식으로 동작 하 고 새 블록 바이트 *수* 를 할당  *   합니다. 각 요소는 0으로 초기화됩니다. *Memblock* 이 **NULL** 이 아닌 경우 **calloc**, [malloc](malloc.md)또는 [realloc](realloc.md)에 대 한 이전 호출에서 반환 된 포인터 여야 합니다.

새 블록은 새 메모리 위치에 있을 수 있으므로 **_recalloc** 에 의해 반환 되는 포인터는 *memblock* 인수를 통해 전달 되는 포인터가 보장 되지 않습니다.

**_recalloc** 는 메모리 할당이 실패 하거나 요청 된 메모리 양이 **_HEAP_MAXREQ** 을 초과 하는 경우 **errno** 을 **enomem** 으로 설정 합니다. 이러한 오류 코드 및 기타 오류 코드에 대한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

**realloc** 는 c + + [_set_new_mode](set-new-mode.md) 함수를 사용 하 여 새 처리기 모드를 설정 하기 **위해 호출 합니다** . 새 처리기 모드는 실패 시 **realloc** 가 [_set_new_handler](set-new-handler.md)설정 된 대로 새 처리기 루틴을 호출 하는지 여부를 나타냅니다. 기본적으로 **realloc** 는 메모리 할당 실패 시 새 처리기 루틴을 호출 하지 않습니다. 이 기본 동작을 재정의 하 여 **_recalloc** 에서 메모리를 할당 하지 못할 때 **realloc** 가 **`new`** 동일한 이유로 실패 했을 때와 동일한 방식으로 새 처리기 루틴을 호출 하도록 할 수 있습니다. 기본값을 재정의하려면 다음 코드를

```C
_set_new_mode(1);
```

프로그램에서 초기에 호출하거나, NEWMODE.OBJ를 사용하여 연결합니다.

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **_recalloc** 은 [_recalloc_dbg](recalloc-dbg.md)으로 확인 됩니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

**_recalloc** 는 및로 표시 됩니다 `__declspec(noalias)` `__declspec(restrict)` . 즉, 함수가 전역 변수를 수정 하지 않도록 보장 하 고 반환 된 포인터에 별칭이 지정 되지 않음을 의미 합니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 및 \<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[링크 옵션](../../c-runtime-library/link-options.md)<br/>
