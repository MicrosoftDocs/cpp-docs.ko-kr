---
title: _cwait
description: Microsoft Visual C 런타임 함수에 대 한 API 참조 `_cwait()` 입니다.
ms.date: 10/23/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: 5b4c4db3c40645b947583b722d345c2e80dcaa8e
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639109"
---
# <a name="_cwait"></a>_cwait

다른 프로세스가 종료될 때까지 기다립니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>매개 변수

*`termstat`*\
지정 된 프로세스의 결과 코드가 저장 되는 버퍼에 대 한 포인터 **`NULL`** 입니다. 또는입니다.

*`procHandle`*\
대기 중인 프로세스에 대 한 핸들입니다 (즉, **_cwait** 를 반환 하기 전에 종료 되어야 하는 프로세스).

*`action`*\
**`NULL`** : Windows 운영 체제 응용 프로그램에서 무시 됩니다. 기타 응용 프로그램:에 대해 수행할 작업 코드 *`procHandle`* 입니다.

## <a name="return-value"></a>반환 값

지정 된 프로세스가 성공적으로 완료 되 면는 지정 된 프로세스의 핸들을 반환 하 고을 *`termstat`* 지정 된 프로세스에서 반환 된 결과 코드로 설정 합니다. 그렇지 않으면-1을 반환 하 고를 **`errno`** 다음과 같이 설정 합니다.

|값|Description|
|-----------|-----------------|
|**`ECHILD`**|지정 된 프로세스가 없거나, *`procHandle`* 잘못 되었거나, 또는 API에 대 한 [`GetExitCodeProcess`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) 호출이 [`WaitForSingleObject`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) 실패 했습니다.|
|**`EINVAL`**|*`action`* 잘못 되었습니다.|

이러한 반환 코드 및 기타 반환 코드에 대 한 자세한 내용은을 참조 하십시오 [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>설명

**`_cwait`** 함수는에서 제공 하는 지정 된 프로세스의 프로세스 ID가 종료 될 때까지 기다립니다 *`procHandle`* . *`procHandle`* 에 전달 되는의 값은 **`_cwait`** 지정 된 프로세스를 만든 함수 호출에서 반환 되는 값 이어야 합니다 [`_spawn`](../../c-runtime-library/spawn-wspawn-functions.md) . 가 호출 되기 전에 프로세스 ID가 종료 되 면가 **`_cwait`** **`_cwait`** 즉시 반환 됩니다. **`_cwait`** 모든 프로세스에서 유효한 핸들 ()이 있는 다른 모든 알려진 프로세스를 기다리는 데 사용할 수 있습니다 *`procHandle`* .

*`termstat`* 지정 된 프로세스의 반환 코드가 저장 될 버퍼를 가리킵니다. 값은 *`termstat`* 지정 된 프로세스가 Windows API를 호출 하 여 정상적으로 종료 되었는지 여부를 나타냅니다 [`ExitProcess`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) . **`ExitProcess`** 지정 된 프로세스가 또는를 호출 하거나, **`exit`** **`_exit`** 에서 반환 **`main`** 되거나,의 끝에 도달 하면가 내부적으로 호출 됩니다 **`main`** . 를 통해 다시 전달 되는 값에 대 한 자세한 내용은 *`termstat`* [Getexitcodeprocess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)를 참조 하세요. **`_cwait`** 에 대 한 값을 사용 하 여를 호출 하면 **`NULL`** *`termstat`* 지정 된 프로세스의 반환 코드가 저장 되지 않습니다.

*`action`* 이러한 환경에서는 부모-자식 관계가 구현 되지 않으므로 Windows 운영 체제에서는 매개 변수를 무시 합니다.

*`procHandle`* 이-1 또는-2 (현재 프로세스 또는 스레드에 대 한 핸들)가 아닌 경우 핸들이 닫힙니다. 이 경우 반환 된 핸들을 사용 하지 마세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**`_cwait`**|\<process.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
    intptr_t hProcess;
    char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main(int argc, char* argv[])
{
    int termstat, c;
    unsigned int number;

    srand((unsigned)time(NULL));    // Seed randomizer

    // If no arguments, this is the calling process
    if (argc == 1)
    {
        // Spawn processes in numeric order
        for (c = 0; c < 4; c++) {
            _flushall();
            process[c].hProcess = _spawnl(_P_NOWAIT, argv[0], argv[0],
                process[c].name, NULL);
        }

        // Wait for randomly specified process, and respond when done
        c = getrandom(0, 3);
        printf("Come here, %s.\n", process[c].name);
        _cwait(&termstat, process[c].hProcess, _WAIT_CHILD);
        printf("Thank you, %s.\n", process[c].name);

    }
    // If there are arguments, this must be a spawned process
    else
    {
        // Delay for a period that's determined by process number
        Sleep((argv[1][0] - 'A' + 1) * 1000L);
        printf("Hi, Dad. It's %s.\n", argv[1]);
    }
}
```

출력 순서는 실행에 따라 달라 집니다.

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)\
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)
