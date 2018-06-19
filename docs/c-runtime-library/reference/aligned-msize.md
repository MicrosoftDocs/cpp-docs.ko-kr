---
title: _aligned_msize | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2375ec8f61a95ec018ea55cc1f891ad8049748c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393107"
---
# <a name="alignedmsize"></a>_aligned_msize

힙에 할당된 메모리 블록의 크기를 반환합니다.

## <a name="syntax"></a>구문

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
메모리 블록에 대한 포인터입니다.

*alignment*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

*offset*<br/>
맞춤을 강제하는 메모리 할당으로의 오프셋입니다.

## <a name="return-value"></a>반환 값

크기(바이트)를 부호 없는 정수로 반환합니다.

## <a name="remarks"></a>설명

**_aligned_msize** 함수를 호출 하 여 할당 된 메모리 블록의 바이트 단위로 크기 반환 [_aligned_malloc](aligned-malloc.md) 또는 [_aligned_realloc](aligned-realloc.md)합니다. *맞춤* 및 *오프셋* 값 블록을 할당 하는 함수에 전달 된 값과 동일 해야 합니다.

응용 프로그램은 C 런타임 라이브러리의 디버그 버전과 연결 되어 있으면 **_aligned_msize** 확인 [_aligned_msize_dbg](aligned-msize-dbg.md)합니다. 디버깅 프로세스 동안 힙을 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

이 함수는 해당 매개 변수의 유효성을 검사합니다. 경우 *memblock* 가 null 포인터 또는 *맞춤* 가 2의 거듭제곱이 **_msize** 의 설명 대로 잘못 된 매개 변수 처리기를 호출 [매개 변수 유효성 검사 ](../../c-runtime-library/parameter-validation.md). 함수를 설정 하는 오류 처리 되는 경우 **errno** 를 **EINVAL** 하 고-1을 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고자료

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
