---
description: '다음에 대 한 자세한 정보: _malloc_dbg'
title: _malloc_dbg
ms.date: 11/04/2016
api_name:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: 56b39ecbbe5f90d9eee378d4ce42016e5960ff63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299815"
---
# <a name="_malloc_dbg"></a>_malloc_dbg

디버깅 헤더에 대한 추가 공간이 있는 힙에서 메모리 블록을 할당하고 버퍼를 덮어씁니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
요청된 메모리 블록의 크기입니다(바이트).

*blockType*<br/>
메모리 블록의 요청 된 형식: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**.

*filename*<br/>
할당 작업 또는 **NULL** 을 요청한 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
할당 작업이 요청 되었거나 **NULL 인** 소스 파일의 줄 번호입니다.

*Filename* 및 *linenumber* 매개 변수는 **_malloc_dbg** 명시적으로 호출 되었거나 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 전처리기 상수가 정의 된 경우에만 사용할 수 있습니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면이 함수는 할당 된 메모리 블록의 사용자 부분에 대 한 포인터를 반환 하거나 새 처리기 함수를 호출 하거나 **NULL** 을 반환 합니다. 반환 동작에 대한 자세한 설명은 다음 설명 섹션을 참조하세요. 새 처리기 함수를 사용하는 방법에 대한 자세한 내용은 [malloc](malloc.md) 함수를 참조하세요.

## <a name="remarks"></a>설명

**_malloc_dbg** 는 [malloc](malloc.md) 함수의 디버그 버전입니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우에는 **_malloc_dbg** 에 대 한 각 호출이 **malloc** 에 대 한 호출로 줄어듭니다. **Malloc** 및 **_malloc_dbg** 는 모두 기본 힙에서 메모리 블록을 할당 하지만 **_malloc_dbg** 는 여러 디버깅 기능을 제공 합니다 .이는 블록의 사용자 부분 양쪽에 있는 버퍼, 특정 할당 형식을 추적 하는 블록 형식 매개 *변수 및* / 할당 요청의 출처를 결정 하는 *linenumber* 정보를 제공 합니다.

**_malloc_dbg** 는 요청한 *크기* 보다 약간 더 많은 공간을 사용 하 여 메모리 블록을 할당 합니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 애플리케이션에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 블록이 할당되면 블록의 사용자 부분은 값 0xCD로 채워지고 각 덮어쓰기 버퍼는 0xFD로 채워집니다.

**_malloc_dbg** 는 메모리 할당이 실패 하거나 필요한 메모리 양 (앞에서 언급 한 오버 헤드 포함)이 **_HEAP_MAXREQ** 을 초과 하는 경우 **errno** 를 **enomem** 으로 설정 합니다. 이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요. 애플리케이션의 디버그 빌드에서 표준 힙 함수를 호출하는 것과 해당 함수의 디버그 버전을 호출하는 것의 차이에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

**_Malloc_dbg** 사용 방법에 대 한 샘플은 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
