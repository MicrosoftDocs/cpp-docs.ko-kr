---
description: '다음에 대 한 자세한 정보: _aligned_offset_malloc_dbg'
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 1d8ae12e62ec1ea335a8bca554e07a0b64a3c3a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336552"
---
# <a name="_aligned_offset_malloc_dbg"></a>_aligned_offset_malloc_dbg

지정된 맞춤 경계에 메모리를 할당합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
요청된 메모리 할당 크기입니다.

*할당*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

*offset*<br/>
맞춤을 강제하는 메모리 할당으로의 오프셋입니다.

*filename*<br/>
할당 작업 또는 **NULL** 을 요청한 소스 파일의 이름에 대 한 포인터입니다.

*linenumber*<br/>
할당 작업이 요청 되었거나 **NULL 인** 소스 파일의 줄 번호입니다.

## <a name="return-value"></a>반환 값

할당 된 메모리 블록에 대 한 포인터 이거나, 작업에 실패 한 경우 **NULL** 입니다.

## <a name="remarks"></a>설명

**_aligned_offset_malloc_dbg** 은 [_aligned_offset_malloc](aligned-offset-malloc.md) 함수의 디버그 버전입니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 **_aligned_offset_malloc_dbg** 에 대 한 각 호출은 **_aligned_offset_malloc** 호출로 줄어듭니다. **_Aligned_offset_malloc** 와 **_aligned_offset_malloc_dbg** 모두 기본 힙에서 메모리 블록을 할당 하지만 **_aligned_offset_malloc_dbg** 는 여러 디버깅 기능을 제공 합니다. 블록의 사용자 부분 양쪽에 있는 버퍼는 누수를 테스트 하 고, *파일 이름* / *linenumber* 정보는 할당 요청의 출처를 결정 합니다. 블록 형식 매개 변수를 사용 하 여 특정 할당 형식을 추적 하는 것은 정렬 된 할당에 대해 지원 되는 디버그 기능이 아닙니다. 정렬 된 할당은 _NORMAL_BLOCK 블록 형식으로 표시 됩니다.

**_aligned_offset_malloc_dbg** 는 요청한 *크기* 보다 약간 더 많은 공간을 사용 하 여 메모리 블록을 할당 합니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 애플리케이션에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 블록이 할당되면 블록의 사용자 부분은 값 0xCD로 채워지고 각 덮어쓰기 버퍼는 0xFD로 채워집니다.

**_aligned_offset_malloc_dbg** 는 중첩 된 요소에 맞춤이 필요한 경우에 유용 합니다. 예를 들어 중첩 된 클래스에 맞춤이 필요한 경우입니다.

**_aligned_offset_malloc_dbg** 는 **malloc** 를 기반으로 합니다. 자세한 내용은 [malloc](malloc.md)를 참조 하세요.

이 함수는 메모리 할당에 실패 한 경우 또는 요청 된 크기가 **_HEAP_MAXREQ** 보다 큰 경우 **Errno** 를 **enomem** 으로 설정 합니다. **Errno** 에 대 한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요. 또한 **_aligned_offset_malloc** 은 해당 매개 변수의 유효성을 검사 합니다. *Alignment* 가 2의 거듭제곱이 아니거나 *오프셋이* *size* 보다 크거나 같고 0이 아닌 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
