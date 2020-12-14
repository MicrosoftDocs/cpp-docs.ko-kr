---
description: '다음에 대 한 자세한 정보: _recalloc_dbg'
title: _recalloc_dbg
ms.date: 11/04/2016
api_name:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: abad8ff877a78bc589a48da689766322ad8438de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254263"
---
# <a name="_recalloc_dbg"></a>_recalloc_dbg

배열을 다시 할당하고 배열의 요소를 0으로 초기화합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*Data*<br/>
이전에 할당된 메모리 블록에 대한 포인터입니다.

*number*<br/>
요청된 메모리 블록 수입니다.

*size*<br/>
요청된 각 메모리 블록 크기입니다(바이트).

*blockType*<br/>
요청 된 메모리 블록 형식: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**.

할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

*filename*<br/>
할당 작업 또는 **NULL** 을 요청한 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
할당 작업이 요청 되었거나 **NULL 인** 소스 파일의 줄 번호입니다.

*Filename* 및 *linenumber* 매개 변수는 **_recalloc_dbg** 명시적으로 호출 되었거나 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 전처리기 상수가 정의 된 경우에만 사용할 수 있습니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면이 함수는 다시 할당 된 메모리 블록의 사용자 부분에 대 한 포인터를 반환 하거나 새 처리기 함수를 호출 하거나 **NULL** 을 반환 합니다. 반환 동작에 대한 자세한 설명은 다음 설명 섹션을 참조하세요. 새 처리기 함수를 사용하는 방법에 대한 자세한 내용은 [_recalloc](recalloc.md) 함수를 참조하세요.

## <a name="remarks"></a>설명

**_recalloc_dbg** 은 [_recalloc](recalloc.md) 함수의 디버그 버전입니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 **_recalloc_dbg** 에 대 한 각 호출은 **_recalloc** 호출로 줄어듭니다. **_Recalloc** 및 **_recalloc_dbg** 둘 다 기본 힙에서 메모리 블록을 다시 할당 하지만, **_recalloc_dbg** 는 블록의 사용자 부분 양쪽에 있는 버퍼, 특정 할당 형식을 추적 하는 블록 형식 매개 변수, 할당 요청의 출처를 확인 하는 *파일 이름* / *linenumber* 정보 등 여러 가지 디버깅 기능을 사용할 수 있습니다.

**_recalloc_dbg** 지정 된 메모리 블록을  *  원래 할당 된 메모리 블록의 크기 보다 크거나 적을 수 있는 요청 된 크기 (숫자 *크기*) 보다 약간 더 많은 공간으로 다시 할당 합니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 애플리케이션에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 다시 할당하면 원래 메모리 블록이 힙의 다른 위치로 이동하고 메모리 블록의 크기가 변할 수 있습니다. 블록의 사용자 부분은 값 0xCD로 채워지고 각 덮어쓰기 버퍼는 0xFD로 채워집니다.

메모리 할당이 실패 하는 경우 **errno** 을 **enomem** 으로 설정 **_recalloc_dbg** . **EINVAL** 는 필요한 메모리 양 (앞에서 언급 한 오버 헤드 포함)이 **_HEAP_MAXREQ** 을 초과 하는 경우 반환 됩니다. 이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 애플리케이션의 디버그 빌드에서 표준 힙 함수를 호출하는 것과 해당 함수의 디버그 버전을 호출하는 것의 차이에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
