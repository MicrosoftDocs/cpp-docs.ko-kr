---
description: '다음에 대 한 자세한 정보: _CrtMemDifference'
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 076cead5f60df457171bbcdf2fd8690f0361870b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319653"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

두 메모리 상태를 비교하고 해당 차이점을 반환합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>매개 변수

*stateDiff*<br/>
두 메모리 상태 (반환 됨)의 차이를 저장 하는 데 사용 되는 **_CrtMemState** 구조체에 대 한 포인터입니다.

*oldState*<br/>
이전 메모리 상태 (**_CrtMemState** 구조)에 대 한 포인터입니다.

*newState*<br/>
이후 메모리 상태 (**_CrtMemState** 구조)에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

메모리 상태가 현저 하 게 다른 경우 **_CRTMEMDIFFERENCE** TRUE를 반환 합니다. 그렇지 않은 경우 이 함수는 FALSE를 반환합니다.

## <a name="remarks"></a>설명

**_CrtMemDifference** 함수는 *oldState* 와 *newState* 를 비교 하 여 해당 차이를 *statediff* 에 저장 합니다 .이는 응용 프로그램에서 메모리 누수 및 기타 메모리 문제를 감지 하는 데 사용할 수 있습니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtMemDifference** 대 한 호출이 제거 됩니다.

*newState* 및 *oldState* 는 crtdbg.h에 정의 되어 있고 **_CrtMemDifference** 를 호출 하기 전에 [_CrtMemCheckpoint](crtmemcheckpoint.md) 에 의해 채워진 **_CrtMemState** 구조체에 대 한 유효한 포인터 여야 합니다. *Statediff* 는 **_CrtMemState** 구조체의 이전에 할당 된 인스턴스에 대 한 포인터 여야 합니다. *Statediff*, *newState* 또는 *OldState* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용 된 경우 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 가 **EINVAL** 로 설정 되 고 함수는 FALSE를 반환 합니다.

**_CrtMemDifference** *oldState* 에 있는 블록의 **_CrtMemState** 필드 값을 *newState* 의 값과 비교 하 고 결과를 *statediff* 에 저장 합니다. 할당된 블록 형식의 수 또는 각 형식에 대해 할당된 총 블록 수가 두 메모리 상태 간에 다를 경우 상태가 현저하게 다르다고 합니다. 두 상태에 대해 한 번에 할당 된 최대 크기와 두 상태에 대 한 총 할당 간의 차이는 *Statediff* 에도 저장 됩니다.

기본적으로 내부 C 런타임 블록 (**_CRT_BLOCK**)은 메모리 상태 작업에 포함 되지 않습니다. [_CrtSetDbgFlag](crtsetdbgflag.md) 함수를 사용 하 여 이러한 블록을 누수 감지 및 기타 메모리 상태 작업에 포함 하는 **_crtDbgFlag** **_CRTDBG_CHECK_CRT_DF** 비트를 설정할 수 있습니다. 해제 한 메모리 블록 (**_FREE_BLOCK**)은 **_CrtMemDifference** TRUE를 반환 하지 않습니다.

힙 상태 함수 및 **_CrtMemState** 구조에 대 한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조 하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)만 해당합니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
