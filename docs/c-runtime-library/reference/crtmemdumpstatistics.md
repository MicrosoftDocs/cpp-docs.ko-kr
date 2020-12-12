---
description: '다음에 대 한 자세한 정보: _CrtMemDumpStatistics'
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
api_name:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 2f02c35ff61dc2bc5ac7e8dfbe921fa48731c2b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319616"
---
# <a name="_crtmemdumpstatistics"></a>_CrtMemDumpStatistics

지정된 힙 상태에 대한 디버그 헤더 정보를 사용자가 읽을 수 있는 형식으로 덤프합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>매개 변수

*state*<br/>
덤프할 힙 상태에 대한 포인터입니다.

## <a name="remarks"></a>설명

**_CrtMemDumpStatistics** 함수는 지정 된 힙 상태에 대 한 디버그 헤더 정보를 사용자가 읽을 수 있는 형식으로 덤프 합니다. 덤프 통계는 애플리케이션에서 할당을 추적하고 메모리 문제를 감지하는 데 사용할 수 있습니다. 메모리 상태에는 특정 힙 상태나 두 상태 간의 차이가 포함될 수 있습니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtMemDumpStatistics** 대 한 호출이 제거 됩니다.

*State* 매개 변수는 **_CrtMemDumpStatistics** 를 호출 하기 전에 [_CrtMemCheckpoint](crtmemcheckpoint.md) 에 의해 입력 되거나 [_CrtMemDifference](crtmemdifference.md) 에서 반환 된 **_CrtMemState** 구조체에 대 한 포인터 여야 합니다. *State* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우에는 **errno** 가 **EINVAL** 로 설정 되 고 아무 동작도 수행 되지 않습니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

힙 상태 함수 및 **_CrtMemState** 구조에 대 한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조 하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)만 해당합니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
