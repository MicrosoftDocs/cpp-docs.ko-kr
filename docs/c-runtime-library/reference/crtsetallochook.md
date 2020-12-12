---
description: '다음에 대 한 자세한 정보: _CrtSetAllocHook'
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: a60024eff510f457cfc16f4afa3035efef37cca4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319666"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

클라이언트 정의 할당 함수를 C 런타임 디버그 메모리 할당 프로세스에 연결함으로써 설치합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>매개 변수

*allocHook*<br/>
C 런타임 디버그 메모리 할당 프로세스에 연결할 새로운 클라이언트 정의 할당 함수입니다.

## <a name="return-value"></a>반환 값

이전에 정의 된 할당 후크 함수를 반환 하거나 *allocHook* 가 **Null** 인 경우 **null** 을 반환 합니다.

## <a name="remarks"></a>설명

**_CrtSetAllocHook** 를 사용 하면 응용 프로그램에서 해당 할당 함수를 C 런타임 디버그 라이브러리 메모리 할당 프로세스에 연결할 수 있습니다. 결과적으로 메모리 블록을 할당, 재할당 또는 해제하기 위해 디버그 할당 함수를 호출할 때마다 애플리케이션의 후크 함수 호출이 트리거됩니다. **_CrtSetAllocHook** 는 응용 프로그램에서 메모리 부족 상황을 처리 하는 방법, 할당 패턴을 검사 하는 기능 및 나중에 분석할 수 있도록 할당 정보를 기록할 수 있는 방법을 테스트 하는 간단한 방법을 제공 합니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtSetAllocHook** 대 한 호출이 제거 됩니다.

**_CrtSetAllocHook** 함수는 *allocHook* 에 지정 된 새로운 클라이언트 정의 할당 함수를 설치 하 고 이전에 정의 된 후크 함수를 반환 합니다. 다음 예제에서는 클라이언트 정의 할당 후크가 어떻게 프로토타입화되어야 하는지 보여 줍니다.

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**Alloctype** 인수는 할당의 후크 함수에 대 한 호출을 트리거한 할당 작업 (**_HOOK_ALLOC**, **_HOOK_REALLOC** 및 **_HOOK_FREE**)의 유형을 지정 합니다. 트리거 할당 형식이 **_HOOK_FREE** 이면 *userData* 는 해제할 메모리 블록의 사용자 데이터 섹션에 대 한 포인터입니다. 그러나 트리거 할당 형식이 **_HOOK_ALLOC** 또는 **_HOOK_REALLOC** 이면 메모리 블록이 아직 할당 되지 않았기 때문에 *userData* 가 **NULL** 입니다.

*크기* 는 메모리 블록의 크기 (바이트)를 지정 하 고 *blocktype* 은 메모리 블록의 유형을 나타내며, *requestnumber* 는 메모리 블록의 개체 할당 순서 번호이 고, 사용 가능한 경우 *파일* 이름 및 **lineNumber** 는 트리거 할당 작업이 시작 된 소스 파일 이름과 줄 번호를 지정 합니다.

후크 함수에서 프로세스가 완료되면 후크 함수는 부울 값을 반환해야 합니다. 이를 통해 기본 C 런타임 할당 프로세스에 계속 진행하는 방식을 알려 줍니다. 후크 함수가 호출 된 적이 없는 것 처럼 기본 할당 프로세스를 계속 진행 하려는 경우 후크 함수는 **TRUE** 를 반환 해야 합니다. 이렇게 하면 원래 트리거 할당 작업이 실행됩니다. 이 구현을 사용하여, 후크 함수는 현재 할당 작업 또는 디버그 힙의 상태를 방해하지 않고 향후 분석을 위해 할당 정보를 수집하고 저장할 수 있습니다.

후크 함수에서 트리거 할당 작업이 호출 된 것 처럼 주 할당 프로세스를 계속 진행 하려는 경우 후크 함수는 **FALSE** 를 반환 해야 합니다. 이 구현을 사용하여, 후크 함수는 다양한 메모리 조건 및 디버그 힙 상태를 시뮬레이트하여 애플리케이션에서 각 상황을 처리하는 방법을 테스트할 수 있습니다.

후크 함수를 지우려면 **_CrtSetAllocHook** 에 **NULL** 을 전달 합니다.

다른 메모리 관리 함수와 함께 **_CrtSetAllocHook** 를 사용 하는 방법 또는 고유한 클라이언트 정의 후크 함수를 작성 하는 방법에 대 한 자세한 내용은 [디버그 후크 함수 작성](/visualstudio/debugger/debug-hook-function-writing)을 참조 하세요.

> [!NOTE]
> **/Clr: pure** 에서는 **_CrtSetAllocHook** 지원 되지 않습니다. **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서 제거 되었습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

**_CrtSetAllocHook** 사용 방법에 대 한 샘플은 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
