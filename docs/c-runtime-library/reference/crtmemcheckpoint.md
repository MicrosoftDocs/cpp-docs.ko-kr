---
description: '다음에 대 한 자세한 정보: _CrtMemCheckpoint'
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: f7a88e63c99c063999f3de0d01e019fecd10496f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319679"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

디버그 힙의 현재 상태를 가져오고 응용 프로그램에서 제공 하는 **_CrtMemState** 구조에 저장 합니다 (디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>매개 변수

*state*<br/>
메모리 검사점으로 채울 **_CrtMemState** 구조에 대 한 포인터입니다.

## <a name="remarks"></a>설명

**_CrtMemCheckpoint** 함수는 지정 된 순간에 디버그 힙의 현재 상태에 대 한 스냅숏을 만듭니다. 이 스냅샷은 메모리 누수를 비롯한 여러 문제를 손쉽게 감지하도록 [_CrtMemDifference](crtmemdifference.md) 같은 기타 힙 상태 함수에 사용할 수 있습니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtMemState** 대 한 호출이 제거 됩니다.

응용 프로그램은 Crtdbg.h에 정의 된 **_CrtMemState** 구조의 이전에 할당 된 인스턴스에 대 한 포인터를 *state* 매개 변수에 전달 해야 합니다. 검사점을 만드는 동안 **_CrtMemCheckpoint** 오류가 발생 하면 함수는 문제를 설명 하는 **_CRT_WARN** 디버그 보고서를 생성 합니다.

힙 상태 함수 및 **_CrtMemState** 구조에 대 한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조 하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

*State* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용 된 경우 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 가 **EINVAL** 로 설정 되 고 함수는을 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 UCRT만 해당합니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
