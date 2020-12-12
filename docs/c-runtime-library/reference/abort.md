---
description: '자세히 알아보기: abort'
title: abort
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: a1733cb99fca332a97f59540833d5c48eb258a4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303915"
---
# <a name="abort"></a>abort

현재 프로세스를 중단하고 오류 코드를 반환합니다.

> [!NOTE]
> 테스트 또는 디버깅 시나리오를 제외 하 고이 메서드를 사용 하 여 Microsoft Store 앱 또는 유니버설 Windows 플랫폼 (UWP) 앱을 종료 하지 마세요. 프로그래밍 또는 UI 방식으로 스토어 앱을 닫는 것은 [Microsoft Store 정책](/legal/windows/agreements/store-policies)에 따라 허용 되지 않습니다. 자세한 내용은 [UWP 앱 수명 주기](/windows/uwp/launch-resume/app-lifecycle)를 참조 하세요.

## <a name="syntax"></a>구문

```C
void abort( void );
```

## <a name="return-value"></a>Return Value

**abort** 는 호출 프로세스에 대 한 제어를 반환 하지 않습니다. 기본적으로 중단 신호 처리기를 확인하고, 설정된 경우 `SIGABRT`를 표시합니다. 그런 다음 **abort** 는 현재 프로세스를 종료 하 고 부모 프로세스에 종료 코드를 반환 합니다.

## <a name="remarks"></a>설명

**Microsoft 전용**

기본적으로 디버그 런타임 라이브러리를 사용 하 여 앱을 빌드할 때 **abort** 루틴은가 발생 하기 전에 오류 메시지를 표시 합니다 `SIGABRT` . 콘솔 모드에서 실행되는 콘솔 앱에 대해서는 메시지가 `STDERR`로 전송됩니다. 창 모드에서 실행되는 Windows 데스크톱 앱 및 콘솔 앱은 메시지 상자에 메시지를 표시합니다. 메시지를 표시하지 않으려면 [_set_abort_behavior](set-abort-behavior.md)를 사용하여 `_WRITE_ABORT_MSG` 플래그를 지웁니다. 표시되는 메시지는 사용 중인 런타임 환경 버전에 따라 달라집니다. 최신 버전의 Visual C++를 사용 하 여 빌드한 응용 프로그램의 경우 메시지는 다음과 유사 합니다.

> R6010 ()이 호출 되었습니다.

C 런타임 라이브러리의 이전 버전에서는 다음과 같은 메시지가 표시됐습니다.

> 이 애플리케이션에서 비정상적인 종료를 런타임에 요청했습니다. 자세한 내용은 해당 애플리케이션의 지원 팀에 문의하십시오.

디버그 모드에서 프로그램을 컴파일하면 메시지 상자에 **중단**, **다시 시도** 또는 **무시** 옵션이 표시됩니다. 사용자가 **중단** 을 선택하면 프로그램이 즉시 종료되고 종료 코드 3이 반환됩니다. 사용자가 **다시 시도** 를 선택하면 사용 가능한 경우 Just-In-Time 디버깅을 위해 디버거가 호출됩니다. 사용자가 **무시** 를 선택 하면 **abort** 는 정상적인 처리를 계속 합니다.

일반 정품 빌드와 디버그 빌드 모두에서 **abort** 는 중단 신호 처리기가 설정 되었는지 여부를 확인 합니다. 기본이 아닌 신호 처리기가 설정 된 경우 **abort** 는를 호출 `raise(SIGABRT)` 합니다. 중단 신호 처리기 함수를 `SIGABRT` 신호와 연결하려면 [signal](signal.md) 함수를 사용합니다. 사용자 지정 작업(예: 리소스 정리 또는 정보 기록)을 수행하고 처리기 함수에서 자체 오류 코드로 앱을 종료할 수 있습니다. 사용자 지정 신호 처리기가 정의 되지 않은 경우 **abort** 는 신호를 발생 시 키 지 않습니다 `SIGABRT` .

기본적으로 데스크톱 또는 콘솔 앱의 디버그가 아닌 빌드에서는 **중단** 한 다음 Windows 오류 보고 서비스 메커니즘 (이전의 dr. Watson)을 호출 하 여 오류를 Microsoft에 보고 합니다. `_set_abort_behavior`를 호출하고 `_CALL_REPORTFAULT` 플래그를 설정하거나 마스킹하여 이 동작을 활성화 또는 비활성화할 수 있습니다. 플래그가 설정되면 "문제로 인해 프로그램이 정상 작동을 중지합니다."와 같은 내용의 메시지 상자가 표시됩니다. 사용자는 **디버그** 단추를 사용하여 디버거를 호출하는 방법 또는 **프로그램 닫기** 단추를 사용하여 운영 체제에 의해 정의된 오류 코드와 함께 앱을 종료하는 방법을 선택할 수 있습니다.

Windows 오류 보고 처리기가 호출 되지 않으면 **abort** 를 호출 하 여 프로세스를 종료 코드 3으로 종료 하 고 부모 프로세스 또는 운영 체제에 대 한 제어를 반환 [_exit](exit-exit-exit.md) 합니다. `_exit`는 스트림 버퍼를 플러시하지 않거나 `atexit`/`_onexit` 프로세싱을 수행합니다.

CRT 디버깅에 대한 자세한 내용은 [CRT 디버깅 기술](/visualstudio/debugger/crt-debugging-techniques)을 참조하세요.

**Microsoft 전용 종료**

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**중단이**|\<process.h> 또는 \<stdlib.h>|

## <a name="example"></a>예제

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

[abort 사용](../../cpp/using-abort.md)<br/>
[abort 함수](../../c-language/abort-function-c.md)<br/>
[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec 함수](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_spawn, _wspawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
