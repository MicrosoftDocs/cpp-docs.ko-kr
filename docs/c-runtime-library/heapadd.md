---
description: '다음에 대 한 자세한 정보: _heapadd'
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: 0270f84de2c543e37f089418b833011c2d83230d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120684"
---
# <a name="_heapadd"></a>_heapadd

힙에 메모리를 추가합니다.

> [!IMPORTANT]
> 이 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>매개 변수

*memblock*<br/>
힙 메모리에 대한 포인터입니다.

*size*<br/>
추가할 메모리 크기(바이트)입니다.

## <a name="return-value"></a>반환 값

성공하면 `_heapadd`에서 0을 반환합니다. 그렇지 않으면 함수에서 –1을 반환하고 `errno`를 `ENOSYS`로 설정합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하십시오.

## <a name="remarks"></a>설명

Visual C++ 버전 4.0부터 새 디버깅 기능을 지원하기 위해 기본 힙 구조가 C 런타임 라이브러리로 이동되었습니다. 따라서 `_heapadd` 는 Win32 API를 기반으로 하는 플랫폼에서 더 이상 지원되지 않습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

호환성에 대한 자세한 내용은 소개 단원의 [호환성](../c-runtime-library/compatibility.md) 부분을 참조하세요.

## <a name="see-also"></a>참고 항목

[메모리 할당](../c-runtime-library/memory-allocation.md)<br/>
[free](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
