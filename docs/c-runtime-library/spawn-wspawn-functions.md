---
description: _Spawn, _wspawn 함수에 대해 자세히 알아보세요.
title: _spawn, _wspawn 함수
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
ms.openlocfilehash: 4b5fe1b386358095880c69fbf956c7c0a4a08ba9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276909"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn, _wspawn 함수

각 `_spawn` 함수는 새로운 프로세스를 만들고 실행합니다.

:::row:::
   :::column span="":::
      [_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)\
      [_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)\
      [_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)\
      [_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)\
   :::column-end:::
   :::column span="":::
      [_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)\
      [_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)\
      [_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)\
      [_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)\
   :::column-end:::
:::row-end:::

함수 이름 끝에 있는 문자에 따라 변형이 결정됩니다.

|Letter|변형|
|-|-|
| `e`  | 환경 설정에 대한 포인터 배열인 `envp`가 새로운 프로세스에 전달됩니다.  |
| `l`  | 명령줄 인수는 `_spawn` 함수로 개별적으로 전달됩니다. 이 접미사는 일반적으로 새로운 프로세스에 대한 여러 매개 변수를 미리 알고 있을 때 사용됩니다.  |
| `p`  | `PATH` 환경 변수는 실행할 파일을 찾는 데 사용됩니다.  |
| `v`  | 명령줄 인수에 대한 포인터 배열인 `argv`가 `_spawn` 함수에 전달됩니다. 이 접미사는 일반적으로 새로운 프로세스에 대한 여러 매개 변수가 가변적일 때 사용됩니다.  |

## <a name="remarks"></a>설명

`_spawn` 함수는 각각 새로운 프로세스를 만들고 실행합니다. 이러한 함수는 현재 사용 중인 멀티바이트 코드 페이지에 따라 멀티바이트 문자 시퀀스를 인식하며 멀티바이트 문자열 인수를 자동으로 적절하게 처리합니다. `_wspawn` 함수는 `_spawn` 함수의 와이드 문자 버전으로, 멀티바이트 문자열을 처리하지 않습니다. 그 외에는 `_wspawn` 함수가 `_spawn`의 상응 함수와 동일하게 동작합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|

새로운 프로세스를 로드 및 실행하려면 사용할 수 있는 메모리가 충분해야 합니다. `mode` 인수는 `_spawn`을 실행하기 전과 실행하는 중에 호출 프로세스에 의해 수행되는 작업을 결정합니다. `mode`의 다음 값은 Process.h에서 정의됩니다.

|값|설명|
|-|-|
| `_P_OVERLAY`  | 호출 프로세스를 제거하며 호출 프로세스를 새로운 프로세스와 겹쳐서 표시합니다(`_exec` 호출과 효과가 같음).  |
| `_P_WAIT`  | 새로운 프로세스의 실행이 완료될 때까지 호출 스레드를 일시 중단합니다(동기적 `_spawn`).  |
| `_P_NOWAIT` 또는 `_P_NOWAITO`  | 호출 프로세스를 계속 새로운 프로세스와 동시에 실행합니다(비동기적 `_spawn`).  |
| `_P_DETACH`  | 호출 프로세스를 계속 실행합니다. 새로운 프로세스는 콘솔 또는 키보드에 대한 액세스 없이 백그라운드에서 실행됩니다. 새로운 프로세스에 대해 `_cwait`를 호출하는 작업은 실패합니다(비동기적 `_spawn`).  |

`cmdname` 인수는 새로운 프로세스로 실행되는 파일을 지정하며, 전체 경로(루트부터) 또는 부분 경로(현재 작업 디렉터리부터)를 지정하거나 파일 이름만 지정할 수도 있습니다. `cmdname`은 파일 이름 확장명을 가지지 않거나 마침표(.)로 끝나지 않으며, `_spawn` 함수는 먼저 .com 파일 이름 확장명을 시도한 다음 .exe 파일 이름 확장명, .bat 파일 이름 확장명을 시도하고 마지막으로 .cmd 파일 이름 확장명을 시도합니다.

`cmdname`에 파일 이름 확장명이 있으면 해당 확장명만 사용됩니다. `cmdname`이 마침표로 끝나면 `_spawn` 호출이 파일 이름 확장명이 없는 `cmdname`을 검색합니다. `_spawnlp`, `_spawnlpe`, `_spawnvp` 및 `_spawnvpe` 함수는 동일한 절차를 사용하여 `PATH` 환경 변수로 지정된 디렉터리에서 `cmdname`을 검색합니다.

`cmdname`에 드라이브 지정자 또는 슬래시가 포함되어 있으면(상대 경로) `_spawn` 호출이 지정된 파일만 검색하며, 경로 검색이 수행되지 않습니다.

이전에는 이러한 함수 중 일부가 성공 시 `errno`를 0으로 설정했지만 현재는 C 표준에 지정된 대로 성공 시 `errno`를 그대로 유지합니다. 이전 동작을 에뮬레이트해야 하는 경우에는 이러한 함수를 호출하기 직전에 `errno`를 0으로 설정하십시오.

> [!NOTE]
> 적절한 오버레이 초기화 및 종료가 보장되도록 `setjmp` 또는 `longjmp` 함수를 사용하여 오버레이 루틴에 출입하지 마십시오.

## <a name="arguments-for-the-spawned-process"></a>생성된 프로세스에 대한 인수

새로운 프로세스에 인수를 전달하려면 `_spawn` 호출에서 문자열에 대한 하나 이상의 포인터를 인수로 제공합니다. 이러한 문자열은 생성된 프로세스에 대한 인수 목록을 형성합니다. 새로운 프로세스에 대한 인수 목록을 형성하는 문자열을 합친 길이는 1024바이트를 초과할 수 없습니다. 각 문자열에 대한 종결 null 문자('\0')는 개수에 포함되지 않지만 공백 문자(인수를 구분하기 위해 자동으로 삽입됨)는 포함됩니다.

> [!NOTE]
> 문자열에 포함된 공백으로 인해 예기치 않은 동작이 발생할 수 있습니다. 예를 들어 `_spawn`를 전달하면 문자열 `"hi there"`는 두 개의 인수 `"hi"` 및 `"there"`를 가져오는 새 프로세스가 됩니다. 새 프로세스에서 "hi there"라는 파일을 열도록 의도한 것이라면 이 프로세스는 실패한 것입니다. `"\"hi there\""`처럼 문자열을 따옴표로 묶으면 이러한 문제를 피할 수 있습니다.

> [!IMPORTANT]
> 내용을 명시적으로 확인하지 않고 사용자 입력을 `_spawn`에 전달하지 마세요. `_spawn`은 [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)를 호출합니다. 따라서 정규화되지 않은 경로 이름을 사용하는 경우 보안 취약성이 발생할 수 있음을 기억해야 합니다.

인수 포인터를 별도의 인수(`_spawnl`, `_spawnle`, `_spawnlp` 및 `_spawnlpe`) 또는 포인터 배열(`_spawnv`, `_spawnve`, `_spawnvp` 및 `_spawnvpe`)로 전달할 수 있습니다. 생성된 프로세스에 `arg0` 또는 `argv`[0] 중 하나 이상의 인수를 전달해야 합니다. 규칙에 따라 이 인수는 명령줄에 입력하는 것과 같은 프로그램의 이름입니다. 다른 값은 오류를 발생시키지 않습니다.

인수의 개수를 미리 알고 있는 경우에는 `_spawnl`, `_spawnle`, `_spawnlp` 및 `_spawnlpe` 호출이 일반적으로 사용됩니다. `arg0` 인수는 일반적으로 `cmdname`에 대한 포인터입니다. `arg1` - `argn` 인수는 새 인수 목록을 구성하는 문자열에 대한 포인터입니다. `argn` 다음에는 인수 목록의 끝을 표시하는 **NULL** 포인터가 와야 합니다.

새로운 프로세스에 대한 인수 개수가 가변적인 경우에는 `_spawnv`, `_spawnve`, `_spawnvp` 및 `_spawnvpe` 호출이 유용합니다. 인수에 대한 포인터는 `argv`*배열로 전달됩니다.* 인수 `argv`[0]은 일반적으로 리얼 모드에서 경로를 가리키는 포인터이거나 보호 모드에서 프로그램 이름을 가리키는 포인터입니다. `argv`[1]부터 `argv`[`n`]은 새로운 인수 목록을 구성하는 문자열을 가리키는 포인터입니다. 인수 `argv`[`n` +1]은 인수 목록의 끝을 표시하는 **NULL** 포인터여야 합니다.

## <a name="environment-of-the-spawned-process"></a>생성된 프로세스의 환경

`_spawn` 호출 실행 시 열려 있는 파일은 새로운 프로세스에서 열린 채로 유지됩니다. `_spawnl`, `_spawnlp`, `_spawnv` 및 `_spawnvp` 호출에서 새로운 프로세스는 호출 프로세스의 환경을 상속 받습니다. `_spawnle`, `_spawnlpe`, `_spawnve` 및 `_spawnvpe` 호출을 사용하면 `envp` 인수를 통해 환경 설정 목록을 전달하여 새로운 프로세스에 대한 환경을 변경할 수 있습니다. `envp` 인수는 문자 포인터 배열이며, 마지막 요소를 제외한 각 요소는 환경 변수를 정의하고 null로 종료되는 문자열을 가리킵니다. 이러한 문자열의 형식은 일반적으로 `NAME`=`value`입니다. 여기서 `NAME`은 환경 변수의 이름이고, `value`는 해당 변수가 설정된 문자열 값입니다. 는 큰따옴표로 `value` 묶지 않습니다. 배열의 마지막 요소는 NULL 이어야 합니다 `envp` .  `envp` 자체가 **NULL** 이면 생성된 프로세스가 부모 프로세스의 환경 설정을 상속 받습니다.

`_spawn` 함수는 변환 모드를 포함하여 열려 있는 파일에 대한 모든 정보를 새로운 프로세스에 전달할 수 있습니다. 이 정보는 환경의 `C_FILE_INFO` 항목을 통해 리얼 모드에서 전달됩니다. 시작 코드는 일반적으로 이 항목을 처리한 다음 환경에서 삭제합니다. 그러나 `_spawn` 함수가 C 프로세스가 아닌 프로세스를 생성하면 이 항목이 환경에 남아 있습니다. 환경을 인쇄하면 이 항목에 대한 정의 문자열에 그래픽 문자가 표시됩니다. 이는 환경 정보가 리얼 모드에서 이진 형식으로 전달되기 때문입니다. 일반 작업에서는 다른 효과가 없습니다. 보호 모드에서는 환경 정보가 텍스트 형식으로 전달되므로 그래픽 문자를 포함하지 않습니다.

`fflush` 또는 `_flushall`을 사용하여 명시적으로 플러시하거나 `_spawn` 함수를 호출하기 전에 모든 스트림을 닫아야 합니다.

`_spawn` 루틴에 대한 호출을 통해 생성된 새로운 프로세스는 신호 설정을 유지하지 않습니다. 대신 생성된 프로세스는 신호 설정을 기본값으로 다시 설정합니다.

## <a name="redirecting-output"></a>출력 리디렉션

DLL 또는 GUI 애플리케이션에서 `_spawn`을 호출하며 출력을 파이프로 리디렉션하려는 경우 두 가지 옵션이 있습니다.

- Win32 API를 사용하여 파이프를 만든 다음 [AllocConsole](/windows/console/allocconsole)을 호출하고, 시작 구조에서 핸들 값을 설정하고, [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)를 호출합니다.

- 그런 다음 [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)을 호출합니다. 이 함수는 **cmd.exe /c** 또는 **command.exe /c** 를 사용하여 파이프를 만들고 앱을 호출합니다.

## <a name="example"></a>예제

```c
// crt_spawn.c
// This program accepts a number in the range
// 1-8 from the command line. Based on the number it receives,
// it executes one of the eight different procedures that
// spawn the process named child. For some of these procedures,
// the CHILD.EXE file must be in the same directory; for
// others, it only has to be in the same path.
//

#include <stdio.h>
#include <process.h>

char *my_env[] =
{
   "THIS=environment will be",
   "PASSED=to child.exe by the",
   "_SPAWNLE=and",
   "_SPAWNLPE=and",
   "_SPAWNVE=and",
   "_SPAWNVPE=functions",
   NULL
};

int main( int argc, char *argv[] )
{
   char *args[4];

   // Set up parameters to be sent:
   args[0] = "child";
   args[1] = "spawn??";
   args[2] = "two";
   args[3] = NULL;

   if (argc <= 2)
   {
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }

   switch (argv[1][0])   // Based on first letter of argument
   {
   case '1':
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );
      break;
   case '2':
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",
               NULL, my_env );
      break;
   case '3':
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );
      break;
   case '4':
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",
                NULL, my_env );
      break;
   case '5':
      _spawnv( _P_OVERLAY, argv[2], args );
      break;
   case '6':
      _spawnve( _P_OVERLAY, argv[2], args, my_env );
      break;
   case '7':
      _spawnvp( _P_OVERLAY, argv[2], args );
      break;
   case '8':
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );
      break;
   default:
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }
   printf( "from SPAWN!\n" );
}
```

```Output
child process output
from SPAWN!
```

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../c-runtime-library/process-and-environment-control.md)<br/>
[중단이](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, _wexec 함수](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
