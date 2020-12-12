---
description: '다음에 대 한 자세한 정보: _CrtSetDbgFlag'
title: _CrtSetDbgFlag
ms.date: 11/04/2016
api_name:
- _CrtSetDbgFlag
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
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
ms.openlocfilehash: cbeda5cdd3434e753f873533f4d362243d5aa64a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319588"
---
# <a name="_crtsetdbgflag"></a>_CrtSetDbgFlag

**_crtDbgFlag** 플래그의 상태를 검색하거나 수정하여 디버그 힙 관리자의 할당 동작을 제어합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>매개 변수

*newFlag*<br/>
**_crtDbgFlag** 의 새로운 상태입니다.

## <a name="return-value"></a>반환 값

**_crtDbgFlag** 의 이전 상태를 반환합니다.

## <a name="remarks"></a>설명

응용 프로그램은 **_CrtSetDbgFlag** 함수를 사용 하 여 디버그 힙 관리자가 **_crtDbgFlag** 플래그의 비트 필드를 수정 하 여 메모리 할당을 추적 하는 방법을 제어할 수 있습니다. 애플리케이션에서는 비트를 설정하여(켜기) 디버그 힙 관리자에 특수 디버깅 작업을 수행하도록 지시합니다. 이러한 작업에는 애플리케이션 종료 시 메모리 누수 확인 후 메모리 누수가 발견되면 보고, 힙의 연결된 목록에 확보한 메모리 블록이 남아 있도록 지정하여 메모리 부족 조건을 시뮬레이션 및 모든 할당 요청 시 각 메모리 블록을 조사하여 힙의 무결성을 확인하는 작업 등이 있습니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtSetDbgFlag** 대 한 호출이 제거 됩니다.

다음 표에서는 **_crtDbgFlag** 의 비트 필드를 보여 주고 이러한 필드의 동작에 대해 설명합니다. 비트를 설정하면 진단 출력이 늘어나고 프로그램 실행 속도가 줄어들기 때문에 비트는 기본적으로 설정되지 않습니다(꺼짐). 이러한 비트 필드에 대한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

|비트 필드|기본값|설명|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|켜기|ON: 디버그 힙 할당과 메모리 블록 형식 식별자 (예: **_CLIENT_BLOCK**) 사용을 사용 하도록 설정 합니다. OFF: 힙의 연결된 목록에 새 할당을 추가하지만 블록 형식을 **_IGNORE_BLOCK** 으로 설정합니다.<br /><br /> 또한 힙 빈도 확인 매크로 중 하나와 함께 사용할 수도 있습니다.|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|ON: 모든 할당 및 할당 해제 요청 시 [_CrtCheckMemory](crtcheckmemory.md)를 호출합니다. OFF: **_CrtCheckMemory** 을 명시적으로 호출 해야 합니다.<br /><br /> 이 플래그가 설정되어 있으면 힙 빈도 확인 매크로는 효과가 없습니다.|
|**_CRTDBG_CHECK_CRT_DF**|OFF|ON: 누수 검색 및 메모리 상태 차이 작업에 **_CRT_BLOCK** 유형을 포함 합니다. OFF: 런타임 라이브러리에서 내부적으로 사용되는 메모리는 이러한 작업에서 무시됩니다.<br /><br /> 또한 힙 빈도 확인 매크로 중 하나와 함께 사용할 수도 있습니다.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|ON: 확보한 메모리 블록을 힙의 연결된 목록에서 유지하고 **_FREE_BLOCK** 형식에 할당하고 바이트 값 0xDD로 채웁니다. OFF: 확보한 블록을 힙의 연결된 목록에 유지하지 않습니다.<br /><br /> 또한 힙 빈도 확인 매크로 중 하나와 함께 사용할 수도 있습니다.|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|ON: [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)에 대한 호출을 통해 프로그램 종료 시 자동 누수 검사를 수행하고 애플리케이션이 직접 할당한 모든 메모리 확보에 실패한 경우 오류 보고서를 생성합니다. OFF: 프로그램 종료 시 누수 검사를 자동으로 수행하지 않습니다.<br /><br /> 또한 힙 빈도 확인 매크로 중 하나와 함께 사용할 수도 있습니다.|

**힙 검사 빈도 매크로**

**Malloc**, **realloc**, **free** 및 **_msize** 에 대 한 호출 수를 기반으로 C 런타임 라이브러리가 디버그 힙 (**_CrtCheckMemory**)의 유효성 검사를 수행 하는 빈도를 지정할 수 있습니다.

그런 다음 **_CrtSetDbgFlag** 는 *newflag* 매개 변수의 상위 16 비트를 검사 하 여 값을 검사 합니다. 지정 된 값은 **_CrtCheckMemory** 호출 사이의 **malloc**, **realloc**, **free** 및 **_msize** 호출 수입니다. 이러한 용도로 미리 정의된 매크로 4개가 제공됩니다.

|매크로|_CrtCheckMemory 호출 사이의 malloc, realloc, free 및 _msize 호출 횟수|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0(기본값, 힙 검사 안 함)|

기본적으로 **_CrtCheckMemory** 는 **malloc**, **realloc**, **free** 및 **_msize** 를 호출 하는 1024 회 마다 한 번씩 호출 됩니다.

예를 들어 다음 코드를 사용 하 여 16 개의 **malloc**, **realloc**, **free** 및 **_msize** 작업 마다 힙 검사를 지정할 수 있습니다.

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired frequency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

_CRTDBG_CHECK_ALWAYS_DF 지정 된 경우 *Newflag* 매개 변수의 상위 16 비트는 무시 됩니다. 이 경우 **malloc**, **realloc**, **free** 및 **_msize** 를 호출할 때마다 **_CrtCheckMemory** 가 호출 됩니다.

*Newflag* 는 **_crtDbgFlag** 에 적용할 새 상태 이며 각 비트 필드에 대 한 값의 조합입니다.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>이러한 비트 필드를 하나 이상 변경하고 플래그에 새로운 상태를 만들려면

1. 현재 **_crtDbgFlag** 상태를 가져오고 반환 된 값을 임시 변수에 저장 하려면 **_CRTDBG_REPORT_FLAG** 와 같은 *newflag* 를 사용 하 여 **_CrtSetDbgFlag** 를 호출 합니다.

1. 해당 비트 마스크 (응용 프로그램 코드에서 매니페스트 상수로 표시)로 임시 변수의 비트 **or** 를 사용 하 여 모든 비트를 설정 합니다.

1. 적절한 비트 마스크의 비트 **NOT** 연산자를 사용하여 변수를 **AND** 연산하여 다른 비트를 해제합니다.

1. **_CrtDbgFlag** 에 대 한 새 상태를 설정 하기 위해 임시 변수에 저장 된 값과 같은 *newflag* 를 사용 하 여 **_CrtSetDbgFlag** 를 호출 합니다.

다음 코드에서는 메모리 블록을 힙의 연결 된 목록에 유지 하 여 메모리 부족 상태를 시뮬레이션 하는 방법을 보여 줍니다. 그러면 모든 할당 요청 시 **_CrtCheckMemory** 호출 되지 않습니다.

```C
// Get the current state of the flag
// and store it in a temporary variable
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn On (OR) - Keep freed memory blocks in the
// heap's linked list and mark them as freed
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;

// Turn Off (AND) - prevent _CrtCheckMemory from
// being called at every allocation request
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;

// Set the new state for the flag
_CrtSetDbgFlag( tmpFlag );
```

메모리 관리 및 디버그 힙의 개요는 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

**_CrtSetDbgFlag** 함수를 사용 하 여 플래그를 사용 하지 않도록 설정 하려면 비트 마스크의 비트 **not** 비트를 사용 하 여 **변수를 사용 해야 합니다** .

*Newflag* 가 유효한 값이 아닌 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **errno** 를 **EINVAL** 로 설정 하 고 **_crtDbgFlag** 의 이전 상태를 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
