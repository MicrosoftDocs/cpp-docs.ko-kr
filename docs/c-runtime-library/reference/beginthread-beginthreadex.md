---
description: '자세히 알아보기: _beginthread, _beginthreadex'
title: _beginthread, _beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
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
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: f4357186a970914e70116650bd1c218521327f99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171909"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread, _beginthreadex

스레드를 만듭니다.

## <a name="syntax"></a>구문

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>매개 변수

*start_address*<br/>
새 스레드의 실행을 시작하는 루틴의 시작 주소입니다. **_Beginthread** 의 경우 호출 규칙은 [__cdecl](../../cpp/cdecl.md) (네이티브 코드의 경우) 또는 [__clrcall](../../cpp/clrcall.md) (관리 코드의 경우)입니다. **_beginthreadex** 의 경우 [__stdcall](../../cpp/stdcall.md) (네이티브 코드의 경우) 또는 [__clrcall](../../cpp/clrcall.md) (관리 코드의 경우)입니다.

*stack_size*<br/>
새 스레드의 스택 크기 또는 0입니다.

*arglist*<br/>
새 스레드에 전달할 인수 목록 또는 **NULL** 입니다.

*Security*<br/>
반환된 핸들이 자식 프로세스에 의해 상속되는지 여부를 결정하는 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 구조에 대한 포인터입니다. *보안이* **NULL** 이면 핸들을 상속할 수 없습니다. Windows 95 응용 프로그램의 경우 **NULL** 이어야 합니다.

*initflag*<br/>
새 스레드의 초기 상태를 제어하는 플래그입니다. *Initflag* 를 0으로 설정 하 여 즉시 실행 하거나, **CREATE_SUSPENDED** 하 여 일시 중단 된 상태에서 스레드를 만듭니다. [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) 를 사용 하 여 스레드를 실행 합니다. *Initflag* 를 **STACK_SIZE_PARAM_IS_A_RESERVATION** 플래그를 설정 하 여 스택의 초기 예약 크기인 바이트 단위로 *stack_size* 를 사용 합니다. 이 플래그를 지정 하지 않으면 *stack_size* 는 커밋 크기를 지정 합니다.

*thrdaddr*<br/>
스레드 식별자를 수신하는 32비트 변수를 가리킵니다. **NULL** 인 경우에는 사용 되지 않습니다.

## <a name="return-value"></a>반환 값

성공 하는 경우 이러한 각 함수는 새로 만든 스레드에 대 한 핸들을 반환 합니다. 그러나 새로 만든 스레드가 너무 빨리 종료 되는 경우 **_beginthread** 올바른 핸들을 반환 하지 않을 수 있습니다. 설명 섹션의 설명을 참조 하세요. 오류가 발생 하면 **_beginthread** -1l을 반환 하 고, 너무 많은 스레드가 **있는 경우** EINVAL, 인수가 잘못 되었거나 스택 크기가 잘못 된 경우에는  , 리소스 (예: 메모리)가 **부족 한 경우** 에는 **eagain** 로 설정 됩니다. 오류가 발생 하면 **_beginthreadex** 가 0을 반환 하 고 **errno** 및 **_doserrno** 가 설정 됩니다.

*Start_address* **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

**Uintptr_t** 에 대 한 자세한 내용은 [표준 형식](../../c-runtime-library/standard-types.md)을 참조 하세요.

## <a name="remarks"></a>설명

**_Beginthread** 함수는 *start_address* 에서 루틴 실행을 시작 하는 스레드를 만듭니다. *Start_address* 의 루틴은 **`__cdecl`** (네이티브 코드) 또는 **__clrcall** (관리 코드) 호출 규칙을 사용 해야 하 고 반환 값이 없어야 합니다. 스레드가 루틴에서 반환되면 자동으로 종료됩니다. 스레드에 대한 자세한 내용은 [이전 코드를 위한 다중 스레드 지원(Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조하세요.

**_beginthreadex** 는 **_beginthread** 보다 더 가깝게 Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API와 비슷합니다. **_beginthreadex** 는 다음과 같은 방식으로 **_beginthread** 와 다릅니다.

- **_beginthreadex** 에는 *initflag*, *Security* 및 **threadaddr** 의 세 가지 추가 매개 변수가 있습니다. 새 스레드는 지정 된 보안을 사용 하 여 일시 중단 된 상태로 만들 수 있으며, 스레드 식별자 인 *thrdaddr* 를 사용 하 여 액세스할 수 있습니다.

- **_Beginthreadex** 에 전달 된 *start_address* 루틴은 **`__stdcall`** (네이티브 코드의 경우) 또는 **__clrcall** (관리 코드) 호출 규칙을 사용 해야 하며, 스레드 종료 코드를 반환 해야 합니다.

- **_beginthreadex** 는-1l이 아닌 실패 시 0을 반환 합니다.

- **_Beginthreadex** 를 사용 하 여 만든 스레드는 [_endthreadex](endthread-endthreadex.md)에 대 한 호출로 종료 됩니다.

**_Beginthreadex** 함수를 사용 하면 **_beginthread** 에서 수행 하는 것 보다 스레드를 만드는 방법을 보다 강력 하 게 제어할 수 있습니다. **_Endthreadex** 함수는 더 유연 하기도 합니다. 예를 들어 **_beginthreadex** 를 사용 하 여 보안 정보를 사용 하 고 스레드의 초기 상태 (실행 중 또는 일시 중단 됨)를 설정 하 고 새로 만든 스레드의 스레드 식별자를 가져올 수 있습니다. **_Beginthread** 에서 수행할 수 없는 동기화 api를 사용 하 여 **_beginthreadex** 에서 반환 된 스레드 핸들을 사용할 수도 있습니다.

**_Beginthread** 보다 **_beginthreadex** 를 사용 하는 것이 더 안전 합니다. **_Beginthread** 에서 생성 된 스레드가 빨리 종료 되는 경우 **_beginthread** 호출자에 게 반환 되는 핸들이 잘못 되었거나 다른 스레드를 가리킬 수 있습니다. 그러나 **_beginthreadex** 에서 반환 하는 핸들은 **_beginthreadex** 호출자가 닫아야 하므로 **_beginthreadex** 에서 오류를 반환 하지 않은 경우 유효한 핸들 이어야 합니다.

[_Endthread](endthread-endthreadex.md) 또는 **_endthreadex** 를 명시적으로 호출 하 여 스레드를 종료할 수 있습니다. 그러나 **_endthread** 또는 **_endthreadex** 는 스레드가 매개 변수로 전달 된 루틴에서 반환 될 때 자동으로 호출 됩니다. **_Endthread** 또는 **_endthreadex** 에 대 한 호출로 스레드를 종료 하면 스레드에 할당 된 리소스의 올바른 복구를 보장 하는 데 도움이 됩니다.

**_endthread** 는 스레드 핸들을 자동으로 닫지만 **_endthreadex** 는 그렇지 않습니다. 따라서 **_beginthread** 및 **_endthread** 를 사용 하는 경우 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API를 호출 하 여 스레드 핸들을 명시적으로 닫지 마세요. 이 동작은 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API와 다릅니다.

> [!NOTE]
> Libcmt.lib로 연결 된 실행 파일의 경우 런타임 시스템이 할당 된 리소스를 회수 하지 않도록 Win32 **Exitthread** API를 호출 하지 마세요. 할당 된 스레드 리소스를 **_endthread** 및 **_endthreadex** 회수 한 다음 **exitthread** 를 호출 합니다.

**_Beginthread** 또는 **_beginthreadex** 를 호출 하면 운영 체제에서 스택 할당을 처리 합니다. 스레드 스택의 주소를 이러한 함수 중 하나에 전달할 필요가 없습니다. 또한 *stack_size* 인수는 0 일 수 있습니다 .이 경우 운영 체제는 주 스레드에 지정 된 스택과 동일한 값을 사용 합니다.

*arglist* 는 새로 만든 스레드에 전달 되는 매개 변수입니다. 일반적으로 문자열과 같은 데이터 항목의 주소입니다. *arglist* 는 필요 하지 않은 경우 **NULL** 일 수 있지만 **_beginthread** 및 **_beginthreadex** 에는 새 스레드에 전달할 값이 지정 되어야 합니다. 스레드가 [abort](abort.md), **exit**, **_exit** 또는 **exitprocess** 를 호출 하면 모든 스레드가 종료 됩니다.

새 스레드의 로캘은 프로세스별 전역 현재 로캘 정보를 사용 하 여 초기화 됩니다. [_Configthreadlocale](configthreadlocale.md) 호출 (전역적으로 또는 새 스레드에만 해당)에 대 한 호출을 통해 스레드별 로캘을 사용 하도록 설정한 경우에는 스레드는 **setlocale** 또는 **_wsetlocale** 를 호출 하 여 다른 스레드와 독립적으로 로캘을 변경할 수 있습니다. 스레드별 로캘 플래그가 설정 되지 않은 스레드는 스레드 단위 로캘 플래그를 설정 하지 않은 다른 모든 스레드의 로캘 정보 뿐만 아니라 새로 만든 모든 스레드도 영향을 받을 수 있습니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

**/Clr** 코드의 경우 **_beginthread** 및 **_beginthreadex** 에는 두 개의 오버 로드가 있습니다. 하나는 네이티브 호출 규칙 함수 포인터를 사용 하 고 다른 하나는 **__clrcall** 함수 포인터를 사용 합니다. 첫 번째 오버로드는 애플리케이션 도메인에 안전하지 않고 어떤 방법으로도 안전할 수 없습니다. **/Clr** 코드를 작성 하는 경우 새 스레드가 관리 되는 리소스에 액세스 하기 전에 올바른 응용 프로그램 도메인에 입력 되도록 해야 합니다. 이 작업은 예를 들어 [call_in_appdomain 함수](../../dotnet/call-in-appdomain-function.md)를 사용하여 수행할 수 있습니다. 두 번째 오버 로드는 응용 프로그램 도메인에 안전 합니다. 새로 만든 스레드는 항상 **_beginthread** 또는 **_beginthreadex** 호출자의 응용 프로그램 도메인에서 종료 됩니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

다중 스레드 버전의 유일한 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md) 입니다.

**_Beginthread** 또는 **_beginthreadex** 를 사용 하려면 응용 프로그램이 다중 스레드 C 런타임 라이브러리 중 하 나와 연결 해야 합니다.

## <a name="examples"></a>예제

다음 예에서는 **_beginthread** 와 **_endthread** 를 사용 합니다.

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

아무 키나 눌러 샘플 애플리케이션을 종료합니다.

다음 샘플 코드는 동기화 API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)를 사용 하 여 **_beginthreadex** 에서 반환 된 스레드 핸들을 사용할 수 있는 방법을 보여 줍니다. 주 스레드는 두 번째 스레드가 종료할 때까지 기다린 다음 계속합니다. 두 번째 스레드가 **_endthreadex** 를 호출 하면 스레드 개체가 신호를 받은 상태로 전환 됩니다. 그러면 기본 스레드를 계속 실행할 수 있습니다. **_Endthread** 가 신호 된 상태로 설정 되기 전에 스레드 개체를 소멸 시키는 **CloseHandle** 을 호출 하기 때문에이 작업은 **_beginthread** 및 **_endthread** 에서 수행할 수 없습니다.

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>참고 항목

- [프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [중단이](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
