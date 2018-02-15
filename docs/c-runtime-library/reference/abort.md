---
title: "abort | Microsoft 문서"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- abort
apilocation:
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02e8c81ef539dc2f078a3b120ca673a0ef612779
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="abort"></a>abort

현재 프로세스를 중단하고 오류 코드를 반환합니다.

> [!NOTE]
> 테스트 또는 디버깅 시나리오에서 Microsoft 스토어 앱 또는 유니버설 Windows 플랫폼 (UWP) 응용 프로그램을 제외 하 고 종료 하려면이 메서드를 사용 하지 마십시오. 스토어 앱을 닫으려면 프로그래밍 또는 UI 방식으로에 따라 허용 되지 않습니다는 [Microsoft 스토어 정책](/legal/windows/agreements/store-policies)합니다. 자세한 내용은 참조 [UWP 앱 수명 주기](/windows/uwp/launch-resume/app-lifecycle)합니다.

## <a name="syntax"></a>구문

```c
void abort( void );
```

## <a name="return-value"></a>반환 값

`abort`는 호출 프로세스에 대한 제어를 반환하지 않습니다. 기본적으로 중단 신호 처리기를 확인하고, 설정된 경우 `SIGABRT`를 표시합니다. 그런 다음 `abort`는 현재 프로세스를 종료하고 종료 코드를 부모 프로세스에 반환합니다.

## <a name="remarks"></a>설명

**Microsoft 전용**

기본적으로 디버그 런타임 라이브러리를 사용하여 앱을 빌드하면, `SIGABRT`가 표시되기 전에 `abort` 루틴은 오류 메시지를 표시합니다. 콘솔 모드에서 실행되는 콘솔 앱에 대해서는 메시지가 `STDERR`로 전송됩니다. 창 모드에서 실행되는 Windows 데스크톱 앱 및 콘솔 앱은 메시지 상자에 메시지를 표시합니다. 메시지를 표시하지 않으려면 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)를 사용하여 `_WRITE_ABORT_MSG` 플래그를 지웁니다. 표시되는 메시지는 사용 중인 런타임 환경 버전에 따라 달라집니다. Visual c + +의 가장 최신 버전을 사용 하 여 빌드한 응용 프로그램에 대 한 메시지는 다음과 같습니다.

> R6010-abort () 호출 된

C 런타임 라이브러리의 이전 버전에서는 다음과 같은 메시지가 표시됐습니다.

> 이 응용 프로그램에서 비정상적인 종료를 런타임에 요청했습니다. 자세한 내용은 해당 응용 프로그램의 지원 팀에 문의하세요.

디버그 모드에서 프로그램을 컴파일하면 메시지 상자에 **중단**, **다시 시도** 또는 **무시** 옵션이 표시됩니다. 사용자가 **중단**을 선택하면 프로그램이 즉시 종료되고 종료 코드 3이 반환됩니다. 사용자가 **다시 시도**를 선택하면 사용 가능한 경우 Just-In-Time 디버깅을 위해 디버거가 호출됩니다. 사용자가 **무시**를 선택하면 `abort`는 일반적인 처리 작업을 계속 진행합니다.

그런 다음 `abort`는 정품 및 디버그 빌드에서 중단 신호 처리기가 설정되었는지를 확인합니다. 기본이 아닌 신호 처리기가 설정된 경우 `abort`는 `raise(SIGABRT)`를 호출합니다. 중단 신호 처리기 함수를 `SIGABRT` 신호와 연결하려면 [signal](../../c-runtime-library/reference/signal.md) 함수를 사용합니다. 사용자 지정 작업(예: 리소스 정리 또는 정보 기록)을 수행하고 처리기 함수에서 자체 오류 코드로 앱을 종료할 수 있습니다. 사용자 지정 신호 처리기가 정의되지 않은 경우 `abort`는 `SIGABRT` 신호를 표시하지 않습니다.

기본적으로 데스크톱 또는 콘솔 응용 프로그램의 디버그가 아닌 빌드에서 `abort` 다음 (이전의 Dr Windows 오류 보고 서비스 메커니즘을 호출. Watson)을 호출하여 Microsoft에 오류를 보고합니다. `_set_abort_behavior`를 호출하고 `_CALL_REPORTFAULT` 플래그를 설정하거나 마스킹하여 이 동작을 활성화 또는 비활성화할 수 있습니다. 플래그가 설정되면 "문제로 인해 프로그램이 정상 작동을 중지합니다."와 같은 내용의 메시지 상자가 표시됩니다. 사용자는 **디버그** 단추를 사용하여 디버거를 호출하는 방법 또는 **프로그램 닫기** 단추를 사용하여 운영 체제에 의해 정의된 오류 코드와 함께 앱을 종료하는 방법을 선택할 수 있습니다.

Windows 오류 보고 처리기가 호출되지 않는 경우, `abort`는 [_exit](../../c-runtime-library/reference/exit-exit-exit.md)를 호출하여 종료 코드 3과 함께 프로세스를 종료하고 부모 프로세스 또는 운영 체제로 제어를 반환합니다. `_exit`는 스트림 버퍼를 플러시하지 않거나 `atexit`/`_onexit` 프로세싱을 수행합니다.

CRT 디버깅에 대한 자세한 내용은 [CRT 디버깅 기술](/visualstudio/debugger/crt-debugging-techniques)을 참조하세요.

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`abort`|\<process.h> 또는 \<stdlib.h>|

## <a name="example"></a>예

다음 프로그램은 파일을 열려고 시도하고 실패하는 경우 중단합니다.

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>참고 항목

[abort 사용](../../cpp/using-abort.md)  
[abort 함수](../../c-language/abort-function-c.md)  
[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)  
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[raise](../../c-runtime-library/reference/raise.md)  
[signal](../../c-runtime-library/reference/signal.md)  
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)  
[_DEBUG](../../c-runtime-library/debug.md)  
[_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)  

