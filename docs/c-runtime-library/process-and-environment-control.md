---
description: '자세히 알아보기: 프로세스 및 환경 제어'
title: 프로세스 및 환경 제어
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
ms.openlocfilehash: 7ba9c81aff87f6cfdf253da6a5d4504bcc59dce5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284566"
---
# <a name="process-and-environment-control"></a>프로세스 및 환경 제어

프로세스 제어 루틴을 사용하여 프로그램 내에서 프로세스를 시작, 중지 및 관리합니다. 환경 제어 루틴을 사용하여 운영 체제 환경에 대한 정보를 가져오고 변경합니다.

## <a name="process-and-environment-control-functions"></a>프로세스 및 환경 제어 함수

|루틴에서 반환된 값|기능|
|-------------|---------|
|[중단이](../c-runtime-library/reference/abort.md)|**atexit** 및 **_onexit** 에서 등록한 버퍼를 플러시하거나 함수를 호출하지 않고 프로세스를 중단합니다.|
|[어설션하](../c-runtime-library/reference/assert-macro-assert-wassert.md)|논리 오류를 테스트합니다.|
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 매크로|**assert** 와 비슷하지만 런타임 라이브러리의 디버그 버전에서만 사용할 수 있습니다.|
|[atexit](../c-runtime-library/reference/atexit.md)|프로그램 종료 시 실행 루틴을 예약합니다.|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Windows 운영 체제 프로세스에서 새 스레드를 만듭니다.|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|**exit** 종료 프로시저(예: 버퍼 플러시)를 수행한 다음, 프로세스를 종료하지 않고 호출 프로그램에 제어를 반환합니다.|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|**_exit** 종료 프로시저를 수행한 다음, 프로세스를 종료하지 않고 호출 프로그램에 제어를 반환합니다.|
|[_cwait](../c-runtime-library/reference/cwait.md)|다른 프로세스가 종료될 때까지 기다립니다.|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Windows 운영 체제 스레드를 종료합니다.|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|인수 목록을 사용하여 새 프로세스를 실행합니다.|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|인수 목록 및 지정된 환경을 사용하여 새 프로세스를 실행합니다.|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|**PATH** 변수 및 인수 목록을 사용하여 새 프로세스를 실행합니다.|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|**PATH** 변수, 지정된 환경 및 인수 목록을 사용하여 새 프로세스를 실행합니다.|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|인수 배열을 사용하여 새 프로세스를 실행합니다.|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|인수 배열 및 지정된 환경을 사용하여 새 프로세스를 실행합니다.|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|**PATH** 변수 및 인수 배열을 사용하여 새 프로세스를 실행합니다.|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|**PATH** 변수, 지정된 환경 및 인수 배열을 사용하여 새 프로세스를 실행합니다.|
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|**atexit** 및 **_onexit** 에서 등록한 함수를 호출하고, 모든 버퍼를 플러시하고, 열려 있는 모든 파일을 닫고, 프로세스를 종료합니다.|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|**atexit** 또는 **_onexit** 를 호출하거나 버퍼를 플러시하지 않고 프로세스를 즉시 종료합니다.|
|[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|환경 변수 값을 가져옵니다.|
|[_getpid](../c-runtime-library/reference/getpid.md)|프로세스 ID 번호를 가져옵니다.|
|[longjmp](../c-runtime-library/reference/longjmp.md)|저장 된 스택 환경 복원 비로컬를 실행 하는 데 사용 **`goto`**|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|프로그램 종료 시 실행 루틴을 예약합니다. Microsoft C/C++ 버전 7.0 및 이전 버전과의 호환성을 위해 사용합니다.|
|[_pclose](../c-runtime-library/reference/pclose.md)|새 명령 프로세서가 실행될 때까지 기다렸다가 연결된 파이프에서 스트림을 닫습니다.|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|오류 메시지를 출력합니다.|
|[_pipe](../c-runtime-library/reference/pipe.md)|읽기 및 쓰기용 파이프를 만듭니다.|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|파이프를 만들고 명령을 실행합니다.|
|[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|환경 변수의 값을 추가하거나 변경합니다.|
|[raise](../c-runtime-library/reference/raise.md)|호출 프로세스로 신호를 보냅니다.|
|[setjmp](../c-runtime-library/reference/setjmp.md)|스택 환경 저장 로컬이 아닌를 실행 하는 데 사용 **`goto`**|
|[signal](../c-runtime-library/reference/signal.md)|인터럽트 신호를 처리합니다.|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|새 프로세스를 만들고 지정된 인수 목록을 사용하여 실행합니다.|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|새 프로세스를 만들고 지정된 인수 목록 및 환경을 사용하여 실행합니다.|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|**PATH** 변수 및 지정된 인수 목록을 사용하여 새 프로세스를 만들고 실행합니다.|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|**PATH** 변수, 지정된 환경 및 인수 목록을 사용하여 새 프로세스를 만들고 실행합니다.|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|새 프로세스를 만들고 지정된 인수 배열을 사용하여 실행합니다.|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|새 프로세스를 만들고 지정된 환경 및 인수 배열을 사용하여 실행합니다.|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|**PATH** 변수 및 지정된 인수 배열을 사용하여 새 프로세스를 만들고 실행합니다.|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|**PATH** 변수, 지정된 환경 및 인수 배열을 사용하여 새 프로세스를 만들고 실행합니다.|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|운영 체제 명령을 실행합니다.|

Windows 운영 체제에서 생성된 프로세스는 생성하는 프로세스와 동급입니다. 모든 프로세스에서 **_cwait** 를 사용하여 프로세스 ID가 알려진 다른 모든 프로세스를 기다릴 수 있습니다.

**_exec** 및 **_spawn** 패밀리 간의 차이는 **_spawn** 함수가 새 프로세스에서 호출 프로세스로 제어를 반환할 수 있다는 것입니다. **_spawn** 함수에서 **_P_OVERLAY** 가 지정되지 않으면 호출 프로세스 및 새 프로세스는 모두 메모리에 있습니다. **_exec** 함수에서 새 프로세스는 호출 프로세스를 오버레이하므로, 새 프로세스의 실행을 시작하려고 할 때 오류가 발생하지 않으면 호출 프로세스에 제어를 반환할 수 없습니다.

다음 표에서 보여 주듯이 **_exec** 패밀리 함수 간 및 **_spawn** 패밀리 함수 간의 차이는 새 프로세스로 실행될 파일을 찾는 방법, 인수가 새 프로세스에 전달되는 형식 및 환경을 설정하는 방법과 관련이 있습니다. 인수 개수가 일정하거나 컴파일 타임에 알려질 경우 인수 목록을 전달하는 함수를 사용합니다. 인수 개수가 런타임에 결정될 경우에는 인수를 포함하는 배열에 대한 포인터를 전달하는 함수를 사용합니다. 다음 표의 정보는 **_spawn** 및 **_exec** 함수의 와이드 문자 대응에도 적용됩니다.

### <a name="_spawn-and-_exec-function-families"></a>_spawn 및 _exec 함수 패밀리

|함수|PATH 변수를 사용하여 파일 찾기|인수 전달 규칙|환경 설정|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl**, **_spawnl**|아니요|목록|호출하는 프로세스에서 상속됨|
|**_execle**, **_spawnle**|아니요|목록|마지막 인수로 전달되는 새 프로세스의 환경 테이블에 대한 포인터|
|**_execlp**, **_spawnlp**|예|목록|호출하는 프로세스에서 상속됨|
|**_execvpe**, **_spawnvpe**|예|Array|마지막 인수로 전달되는 새 프로세스의 환경 테이블에 대한 포인터|
|**_execlpe**, **_spawnlpe**|예|목록|마지막 인수로 전달되는 새 프로세스의 환경 테이블에 대한 포인터|
|**_execv**, **_spawnv**|아니요|배열|호출하는 프로세스에서 상속됨|
|**_execve**, **_spawnve**|아니요|배열|마지막 인수로 전달되는 새 프로세스의 환경 테이블에 대한 포인터|
|**_execvp**, **_spawnvp**|예|Array|호출하는 프로세스에서 상속됨|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
