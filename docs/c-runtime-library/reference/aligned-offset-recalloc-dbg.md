---
title: _aligned_offset_recalloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_recalloc_dbg
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
apitype: DLLExport
f1_keywords:
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
ms.openlocfilehash: 0b314b4aca080877b4e41723a8d2010fd8e835ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627970"
---
# <a name="alignedoffsetrecallocdbg"></a>_aligned_offset_recalloc_dbg

[_aligned_malloc](aligned-malloc.md) 또는 [_aligned_offset_malloc](aligned-offset-malloc.md)를 사용하여 할당된 메모리 블록의 크기를 변경하고 메모리를 0으로 초기화합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void * _aligned_offset_recalloc_dbg(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
현재 메모리 블록 포인터입니다.

*수*<br/>
요소의 수입니다.

*size*<br/>
각 요소의 길이입니다(바이트).

*alignment*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

*offset*<br/>
맞춤을 강제하는 메모리 할당으로의 오프셋입니다.

*filename*<br/>
Realloc 작업을 요청한 소스 파일의 이름에 대 한 포인터 또는 **NULL**합니다.

*linenumber*<br/>
여기서 realloc 작업이 요청 된 소스 파일의 줄 번호 또는 **NULL**합니다.

## <a name="return-value"></a>반환 값

**_aligned_offset_recalloc_dbg** 다시 할당 (그리고 이동 되었을 수 있는) 메모리 블록에 대 한 void 포인터를 반환 합니다. 반환 값은 **NULL** 는 크기가 0이 고 버퍼 인수가 아닙니다 **NULL**, 충분 한 사용 가능한 메모리 블록을 지정 된 크기로 확장할 수 없는 경우 또는 합니다. 첫 번째 경우 원래 블록이 해제됩니다. 두 번째 경우 원래 블록은 변경되지 않습니다. 반환 값은 모든 형식의 개체 저장을 위해 적절하게 맞도록 보장되어 있는 저장소 공간을 가리킵니다. void가 아닌 형식의 포인터를 얻으려면 반환 값에 형식 캐스팅을 사용합니다.

## <a name="remarks"></a>설명

**_aligned_offset_realloc_dbg** 의 디버그 버전이 합니다 [_aligned_offset_recalloc](aligned-offset-recalloc.md) 함수입니다. 때 [_DEBUG](../../c-runtime-library/debug.md) 를 정의 하지 않은를 호출할 때마다 **_aligned_offset_recalloc_dbg** 대 한 호출으로 줄어듭니다 **_aligned_offset_recalloc**합니다. 둘 다 **_aligned_offset_recalloc** 하 고 **_aligned_offset_recalloc_dbg** 기본 힙에서 메모리 블록 다시 할당 하지만 **_aligned_offset_recalloc_dbg** 수용 몇 가지 디버깅 기능: 누수 테스트, 블록 형식 매개 변수로 특정 할당 형식 추적 블록의 사용자 부분 양쪽에서 버퍼와 *filename*/*linenumber*  정보로 할당 요청의 원점을 확인 하 합니다.

**_aligned_offset_realloc_dbg** 는 요청 된 것 보다 약간 더 많은 공간을 사용 하 여 지정 된 메모리 블록 다시 할당 *newSize*합니다. *newSize* 원래 할당 된 메모리 블록의 크기 보다 작거나 클 수 있습니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 응용 프로그램에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 다시 할당하면 원래 메모리 블록이 힙의 다른 위치로 이동하고 메모리 블록의 크기가 변할 수 있습니다. 메모리 블록이 이동하면 원래 블록의 내용을 덮어씁니다.

이 함수를 설정 합니다 **errno** 하 **ENOMEM** 메모리 할당에 실패 하거나 요청된 된 크기 (*번호* * *크기* ) 보다 큰 **_HEAP_MAXREQ**합니다. 에 대 한 자세한 내용은 **errno**를 참조 하십시오 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)합니다. 또한 **_aligned_offset_recalloc_dbg** 해당 매개 변수 유효성을 검사 합니다. 하는 경우 *맞춤* 2의 거듭제곱이 아닌 경우 *오프셋* 보다 큰 또는 요청 된 크기를 크거나 같고 0이 아닌 경우이 함수에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 하도록 허용 된 경우이 함수를 반환 합니다 **NULL** 집합과 **errno** 하 **EINVAL**합니다.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요. 응용 프로그램의 디버그 빌드에서 표준 힙 함수와 이 함수의 디버그 버전을 호출하는 경우의 차이점에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_aligned_offset_recalloc_dbg**|\<malloc.h>|

## <a name="see-also"></a>참고자료

[데이터 맞춤](../../c-runtime-library/data-alignment.md)<br/>
