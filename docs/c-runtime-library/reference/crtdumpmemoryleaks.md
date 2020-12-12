---
description: '다음에 대 한 자세한 정보: _CrtDumpMemoryLeaks'
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
api_name:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: 83b3effdc4f3e8afdad24057ab55123aee924d60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319780"
---
# <a name="_crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

메모리 누수가 발생한 경우 디버그 힙의 모든 메모리 블록을 덤프합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Return Value

메모리 누수가 발견 되 면 **_CRTDUMPMEMORYLEAKS** TRUE를 반환 합니다. 그렇지 않은 경우 이 함수는 FALSE를 반환합니다.

## <a name="remarks"></a>설명

**_CrtDumpMemoryLeaks** 함수는 프로그램 실행이 시작 된 이후 메모리 누수가 발생 했는지 여부를 확인 합니다. 누수를 발견하면 힙에 있는 모든 개체에 대한 디버그 헤더 정보를 사용자가 읽을 수 있는 형식으로 덤프합니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtDumpMemoryLeaks** 대 한 호출이 제거 됩니다.

**_CrtDumpMemoryLeaks** 는 응용 프로그램에서 할당 한 모든 메모리가 해제 되었는지 확인 하기 위해 프로그램 실행이 끝날 때 자주 호출 됩니다. [_CrtSetDbgFlag](crtsetdbgflag.md) 함수를 사용 하 여 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 플래그의 **_CRTDBG_LEAK_CHECK_DF** 비트 필드를 켜면 프로그램 종료 시 자동으로 함수를 호출할 수 있습니다.

**_CrtDumpMemoryLeaks** 는 [_CrtMemCheckpoint](crtmemcheckpoint.md) 를 호출 하 여 힙의 현재 상태를 가져온 다음 해제 되지 않은 블록에 대 한 상태를 검색 합니다. 해제 된 블록이 발견 되 면 **_CrtDumpMemoryLeaks** 를 [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) 호출 하 여 프로그램 실행 시작부터 힙에 할당 된 모든 개체에 대 한 정보를 덤프 합니다.

기본적으로 내부 C 런타임 블록 (**_CRT_BLOCK**)은 메모리 덤프 작업에 포함 되지 않습니다. [_CrtSetDbgFlag](crtsetdbgflag.md) 함수를 사용 하면 **_crtDbgFlag** 의 **_CRTDBG_CHECK_CRT_DF** 비트를 설정 하 여 이러한 블록을 누수 검색 프로세스에 포함할 수 있습니다.

힙 상태 함수 및 **_CrtMemState** 구조에 대 한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조 하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

**_CrtDumpMemoryLeaks** 사용 방법에 대 한 샘플은 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
