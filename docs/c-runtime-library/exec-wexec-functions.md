---
description: _Exec, _wexec 함수에 대해 자세히 알아보세요.
title: _exec, _wexec 함수
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
ms.openlocfilehash: 0a28c7bdc192e2e72c751e953987509c07611934
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300101"
---
# <a name="_exec-_wexec-functions"></a>_exec, _wexec 함수

이 패밀리의 다음 각 함수는 새 프로세스를 로드하고 실행합니다.

:::row:::
   :::column span="":::
      [_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)\
      [_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)\
      [_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)
   :::column-end:::
   :::column span="":::
      [_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)\
      [_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)\
      [_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)
   :::column-end:::
   :::column span="":::
      [_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)\
      [_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)
   :::column-end:::
:::row-end:::

함수 이름 끝에 있는 문자는 변형을 확인합니다.

|_exec 함수 접미사|설명|
|----------------------------|-----------------|
|`e`|환경 설정에 대한 포인터의 배열인 `envp`가 새 프로세스로 전달됩니다.|
|`l`|명령줄 인수는 `_exec` 함수로 개별적으로 전달됩니다. 새 프로세스의 매개 변수 개수가 미리 알려진 경우 일반적으로 사용됩니다.|
|`p`|`PATH` 환경 변수는 실행할 파일을 찾는 데 사용됩니다.|
|`v`|명령줄 인수에 대한 포인터의 배열인 `argv`가 `_exec`로 전달됩니다. 새 프로세스의 매개 변수 개수가 가변적인 경우 일반적으로 사용됩니다.|

## <a name="remarks"></a>설명

`_exec` 함수는 새 프로세스를 로드하고 실행합니다. 모든 `_exec` 함수는 동일한 운영 체제 함수([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw))를 사용합니다. `_exec` 함수는 멀티바이트 문자열 인수를 적절하게 자동으로 처리하여 현재 사용 중인 멀티바이트 코드 페이지에 따라 멀티바이트 문자 시퀀스를 인식합니다. `_wexec` 함수는 `_exec` 함수의 와이드 문자 버전입니다. `_wexec` 함수는 멀티바이트 문자열을 처리하지 않는다는 점만 제외하면 자신의 `_exec` 패밀리 대응 함수와 동일하게 작동합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_texecl`|`_execl`|`_execl`|`_wexecl`|
|`_texecle`|`_execle`|`_execle`|`_wexecle`|
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|
|`_texecv`|`_execv`|`_execv`|`_wexecv`|
|`_texecve`|`_execve`|`_execve`|`_wexecve`|
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|

`cmdname` 매개변수는 새 프로세스로 실행할 파일을 지정합니다. 이 매개 변수는 루트부터 시작하는 전체 경로, 현재 작업 디렉터리부터 시작하는 부분 경로 또는 파일 이름을 지정할 수 있습니다. `cmdname` 매개 변수에 확장명이 없거나 이 매개 변수가 마침표(.)로 끝나지 않은 경우에도 `_exec` 함수는 명명된 파일을 검색합니다. 검색에 실패하면 이 매개 변수는 기본 이름은 동일하고 확장명이 .com인 파일을 검색한 다음, 확장명이 .exe, .bat 및 .cmd인 파일을 차례대로 검색합니다. `cmdname`에 파일 확장명이 포함되어 있으면 검색에서는 해당 확장명만 사용됩니다. `cmdname`이 마침표로 끝나는 경우 `_exec` 함수는 파일 확장명이 없는 `cmdname`을 검색합니다. `_execlp`, `_execlpe`, `_execvp` 및 `_execvpe`는 `cmdname` 환경 변수가 지정한 디렉터리에서 동일한 절차에 따라 `PATH`을 검색합니다. `cmdname`에 드라이브 지정자 또는 슬래시(즉, 상대 경로인 경우)가 포함된 경우 `_exec` 호출은 지정된 파일만 검색하고 경로는 검색하지 않습니다.

매개 변수는 `_exec` 호출 시 문자열에 대한 한 개 이상의 포인터를 매개 변수로 제공하여 매개 변수를 새 프로세스에 전달합니다. 이러한 문자열은 새 프로세스에 대한 매개 변수 목록을 구성합니다. 상속된 환경 설정과 새 프로세스의 매개 변수 목록을 구성하는 문자열의 결합된 길이는 32KB를 초과하지 않아야 합니다. 각 문자열의 null 종결 문자('\0')는 계산되지 않지만 매개 변수를 구분하기 위해 자동으로 삽입된 공백 문자는 계산됩니다.

> [!NOTE]
> 문자열에 포함된 공백으로 인해 예기치 않은 동작이 발생할 수 있습니다. 예를 들어 `_exec`를 전달하면 문자열 `"hi there"`는 두 개의 인수 `"hi"` 및 `"there"`를 가져오는 새 프로세스가 됩니다. 새 프로세스에서 "hi there"라는 파일을 열도록 의도한 것이라면 이 프로세스는 실패한 것입니다. `"\"hi there\""`처럼 문자열을 따옴표로 묶으면 이러한 문제를 피할 수 있습니다.

> [!IMPORTANT]
> 내용을 명시적으로 확인하지 않고 사용자 입력을 `_exec`에 전달하지 마세요. `_exec`은 [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)를 호출합니다. 따라서 정규화되지 않은 경로 이름을 사용하는 경우 보안 취약성이 발생할 수 있음을 기억해야 합니다.

`_exec` 함수는 자신의 매개 변수에 대한 유효성을 검사합니다. 예상 매개 변수가 null 포인터이거나 빈 문자열이거나 생략된 경우 `_exec` 함수는 [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용한 경우 이러한 함수는 `errno` 를 `EINVAL` 로 설정하고 -1을 반환합니다. 새로운 프로세스가 실행되지 않습니다.

인수 포인터는 개별 매개 변수(`_execl`, `_execle`, `_execlp` 및 `_execlpe`) 또는 포인터의 배열(`_execv`, `_execve`, `_execvp` 및 `_execvpe`)로 전달될 수 있습니다. 하나 이상의 `arg0` 매개 변수를 새 프로세스로 전달해야 합니다. 이 매개 변수는 새 프로세스의 `argv`[0]입니다. 일반적으로 이 매개 변수는 `cmdname`의 복사본입니다. 다른 값은 오류를 일으키지 않습니다.

`_execl`, `_execle`, `_execlp` 및 `_execlpe` 호출은 일반적으로 매개 변수의 개수가 미리 알려진 경우 사용됩니다. 일반적으로 매개 변수 `arg0`은 `cmdname`에 대한 포인터입니다. 매개 변수 `arg1`~`argn`은 새 매개 변수 목록을 구성하는 문자열을 가리킵니다. null 포인터는 `argn`에 따라 매개변수 목록의 끝을 표시합니다.

`_execv`, `_execve`, `_execvp` 및 `_execvpe` 호출은 새 프로세스에 대한 매개 변수 개수가 가변적인 경우 유용합니다. 매개변수에 대한 포인터는 배열 `argv`로 전달됩니다. 일반적으로 매개 변수 `argv`[0]은 `cmdname`에 대한 포인터입니다. 매개 변수 `argv`[1]~`argv`[`n`]는 새 매개 변수 목록을 구성하는 문자열을 가리킵니다. 매개 변수 `argv`[`n`+1]는 매개 변수 목록의 끝을 표시하는 **NULL** 포인터여야 합니다.

`_exec` 호출 시 열린 파일은 새 프로세스에서도 열린 채 남아 있습니다. `_execl`, `_execlp`, `_execv` 및 `_execvp` 호출 시 새 프로세스는 호출 프로세스의 환경을 상속합니다. `_execle`, `_execlpe`, `_execve` 및 `_execvpe` 호출은 `envp` 매개 변수를 통해 환경 설정 목록을 전달함으로써 새 프로세스의 환경을 변경합니다. `envp`는 문자 포인터의 배열로, 마지막 요소를 제외한 각 요소는 환경 변수를 정의하는 null로 끝나는 문자열을 가리킵니다. 이러한 문자열의 형식은 일반적으로 `NAME`=`value`입니다. 여기서 `NAME`은 환경 변수의 이름이고, `value`는 해당 변수가 설정된 문자열 값입니다. 는 큰따옴표로 `value` 묶지 않습니다. 배열의 마지막 요소는 NULL 이어야 합니다 `envp` .  `envp` 자체가 **NULL** 이면 새 프로세스는 호출 프로세스의 환경을 상속합니다.

`_exec` 함수 중 하나를 사용하여 실행된 프로그램은 마치 프로그램의 .exe 파일 헤더에 있는 최대 할당 필드가 기본값인 0xFFFFH로 설정된 것처럼 항상 메모리로 로드됩니다 .

`_exec` 호출은 열린 파일의 변환 모드를 유지하지 않습니다. 새 프로세스가 호출 프로세스에서 상속된 파일을 사용해야 하는 경우 [_setmode](../c-runtime-library/reference/setmode.md) 루틴을 사용하여 이러한 파일의 변환 모드를 원하는 모드로 설정합니다. `fflush` 함수 호출 전에 모든 스트림을 명시적으로 플러시하거나(`_flushall` 또는 `_exec` 사용) 닫아야 합니다. `_exec` 루틴에 대한 호출로 생성된 새 프로세스에서 신호 설정은 유지되지 않습니다. 신호 설정은 새 프로세스에서 기본값으로 다시 설정됩니다.

## <a name="example"></a>예제

```c
// crt_args.c
// Illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
// This program will be executed by crt_exec which follows.

#include <stdio.h>

int main( int argc,  // Number of strings in array argv
char *argv[],       // Array of command-line argument strings
char **envp )       // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf( "  %s\n", *(envp++) );

    return;
}
```

다음 프로그램을 실행하여 Crt_args.exe를 실행합니다.

```c
// crt_exec.c
// Illustrates the different versions of exec, including
//      _execl          _execle          _execlp          _execlpe
//      _execv          _execve          _execvp          _execvpe
//
// Although CRT_EXEC.C can exec any program, you can verify how
// different versions handle arguments and environment by
// compiling and specifying the sample program CRT_ARGS.C. See
// "_spawn, _wspawn Functions" for examples of the similar spawn
// functions.

#include <stdio.h>
#include <conio.h>
#include <process.h>

char *my_env[] =     // Environment for exec?e
{
   "THIS=environment will be",
   "PASSED=to new process by",
   "the EXEC=functions",
   NULL
};

int main( int ac, char* av[] )
{
   char *args[4];
   int ch;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );
      return;
   }

   // Arguments for _execv?
   args[0] = av[1];
   args[1] = "exec??";
   args[2] = "two";
   args[3] = NULL;

   switch( atoi( av[2] ) )
   {
   case 1:
      _execl( av[1], av[1], "_execl", "two", NULL );
      break;
   case 2:
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );
      break;
   case 3:
      _execlp( av[1], av[1], "_execlp", "two", NULL );
      break;
   case 4:
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );
      break;
   case 5:
      _execv( av[1], args );
      break;
   case 6:
      _execve( av[1], args, my_env );
      break;
   case 7:
      _execvp( av[1], args );
      break;
   case 8:
      _execvpe( av[1], args, my_env );
      break;
   default:
      break;
   }

   // This point is reached only if exec fails.
   printf( "\nProcess was not execed." );
   exit( 0 );
}
```

## <a name="requirements"></a>요구 사항

**헤더:** process.h

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../c-runtime-library/process-and-environment-control.md)<br/>
[중단이](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn 함수](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
