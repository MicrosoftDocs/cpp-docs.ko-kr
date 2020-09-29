---
title: _aligned_msize
ms.date: 4/2/2020
api_name:
- _aligned_msize
- _o__aligned_msize
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
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 1037c63af17a844959bc72e42da2c33267b43004
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414037"
---
# <a name="_aligned_msize"></a>_aligned_msize

힙에 할당된 메모리 블록의 크기를 반환합니다.

## <a name="syntax"></a>구문

```C
size_t _aligned_msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
메모리 블록에 대한 포인터입니다.

*할당*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

*offset*<br/>
맞춤을 강제하는 메모리 할당으로의 오프셋입니다.

## <a name="return-value"></a>반환 값

크기(바이트)를 부호 없는 정수로 반환합니다.

## <a name="remarks"></a>설명

**_Aligned_msize** 함수는 [_aligned_malloc](aligned-malloc.md) 또는 [_aligned_realloc](aligned-realloc.md)에 대 한 호출에 의해 할당 된 메모리 블록의 크기 (바이트)를 반환 합니다. *맞춤* 및 *오프셋* 값은 블록을 할당 한 함수에 전달 된 값과 같아야 합니다.

응용 프로그램이 C 런타임 라이브러리의 디버그 버전에 연결 된 경우 **_aligned_msize** 은 [_aligned_msize_dbg](aligned-msize-dbg.md)으로 확인 됩니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Memblock* 이 null 포인터 이거나 *맞춤이* 2의 거듭제곱이 아닌 경우 **_Aligned_msize** 는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 오류가 처리 되 면 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_aligned_msize**|\<malloc.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
