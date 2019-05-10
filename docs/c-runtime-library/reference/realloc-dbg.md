---
title: _realloc_dbg
ms.date: 11/04/2016
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 9b30dfd6fbae9a4831ff53e7896aeb995657da03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357748"
---
# <a name="reallocdbg"></a>_realloc_dbg

블록을 이동하거나 크기를 조정하여 힙에서 지정된 메모리 블록을 재할당합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void *_realloc_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*userData*<br/>
이전에 할당된 메모리 블록에 대한 포인터입니다.

*newSize*<br/>
재할당된 블록에 대해 요청된 크기(바이트)입니다.

*blockType*<br/>
재할당된 된 블록의 요청 된 형식: **_CLIENT_BLOCK** 하거나 **_NORMAL_BLOCK**합니다.

*filename*<br/>
요청한 소스 파일의 이름에 대 한 포인터를 **realloc** 작업이 나 **NULL**합니다.

*linenumber*<br/>
소스 파일의 줄 번호 위치는 **realloc** 작업이 요청 또는 **NULL**합니다.

*filename* 하 고 *linenumber* 매개 변수에 하면 볼 수 있습니다 **_realloc_dbg** 명시적으로 호출 된 또는 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 전처리기 상수가 정의 되었습니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면이 함수는 다시 할당된 된 메모리 블록의 사용자 부분에 대 한 포인터를 반환, 새 처리기 함수를 호출 또는 반환 **NULL**합니다. 반환 동작에 대한 자세한 설명은 다음 설명 섹션을 참조하세요. 새 처리기 함수를 사용하는 방법에 대한 자세한 내용은 [realloc](realloc.md) 함수를 참조하세요.

## <a name="remarks"></a>설명

**_realloc_dbg** 의 디버그 버전이 합니다 [realloc](realloc.md) 함수입니다. 때 [_DEBUG](../../c-runtime-library/debug.md) 를 정의 하지 않은를 호출할 때마다 **_realloc_dbg** 대 한 호출으로 줄어듭니다 **realloc**합니다. 둘 다 **realloc** 하 고 **_realloc_dbg** 기본 힙에서 메모리 블록 다시 할당 하지만 **_realloc_dbg** 몇 가지 디버깅 기능을 수용:의 양쪽에서 버퍼를 누수 테스트, 블록 형식 매개 변수로 특정 할당 형식 추적 블록의 사용자 부분 한 *filename*/*linenumber* 의 출처를 확인 하는 정보 할당 요청 수입니다.

**_realloc_dbg** 는 요청 된 것 보다 약간 더 많은 공간을 사용 하 여 지정 된 메모리 블록 다시 할당 *newSize*합니다. *newSize* 원래 할당 된 메모리 블록의 크기 보다 작거나 클 수 있습니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 애플리케이션에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 다시 할당하면 원래 메모리 블록이 힙의 다른 위치로 이동하고 메모리 블록의 크기가 변할 수 있습니다. 메모리 블록이 이동하면 원래 블록의 내용을 덮어씁니다.

**_realloc_dbg** 설정 **errno** 하려면 **ENOMEM** 메모리 할당이 실패 하는 경우 또는 (앞에서 언급 한 오버 헤드 포함)는 데 필요한 메모리 양을 초과 **_HEAP_ MAXREQ**합니다. 이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요. 애플리케이션의 디버그 빌드에서 표준 힙 함수와 이 함수의 디버그 버전을 호출하는 경우의 차이점에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

[_msize_dbg](msize-dbg.md) 항목의 예제를 참조하세요.

## <a name="see-also"></a>참고자료

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
