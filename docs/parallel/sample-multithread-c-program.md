---
title: 샘플 다중 스레드 C 프로그램
ms.date: 08/09/2019
ms.assetid: 4706f6cd-ff9c-4dbf-99a2-1c999b568f17
ms.openlocfilehash: 355024b995dc638b89a335983bd2e0f2cb0d96ce
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924770"
---
# <a name="sample-multithread-c-program"></a>샘플 다중 스레드 C 프로그램

바운스. c는 문자 `a` 또는 형식이 지정 될 때마다 새 스레드를 만드는 샘플 다중 스레드 프로그램입니다. `A` 각 스레드는 화면 주위에 다른 색의 문자를 바운스 합니다. 최대 32 스레드를 만들 수 있습니다. 프로그램의 정상적인 종료는 `q` 또는가 입력 될 때 발생 합니다 `Q` .

## <a name="compile-and-link-a-multithread-program"></a>다중 스레드 프로그램 컴파일 및 연결

프로그램은 기본적으로 다중 스레드로 컴파일됩니다.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>개발 환경 내에서 다중 스레드 프로그램을 컴파일 및 연결 하려면

::: moniker range=">=msvc-160"

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트 만들기** 대화 상자에서 **c + +** , **Windows** 및 **콘솔** 태그를 포함 하는 **콘솔 응용 프로그램** 템플릿을 선택 합니다. 계속 진행하려면 **다음** 을 선택합니다.

1. **새 프로젝트 구성** 대화 상자에서 프로젝트 이름 (예: "바운스")을 입력 합니다. **만들기** 를 선택 하 여 계속 합니다.

1. **솔루션 탐색기** 창에서 프로젝트 아래의 **소스 파일** 폴더를 열고 확장명이 .c 인 소스 파일의 이름을 변경 합니다.

1. 편집 창에서 기존 소스 코드를 삭제 하 고 샘플 코드로 바꿉니다.

1. **빌드** 메뉴에서 **솔루션 빌드** 를 선택합니다.

1. **F5** 키를 눌러 디버거에서 프로그램을 시작 합니다.

::: moniker-end

::: moniker range="<=msvc-150"

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C++** 을 선택한 다음 가운데 창에서 **빈 프로젝트** 를 선택 합니다.

1. **이름** 입력란에 프로젝트 이름 (예: "바운스")을 입력 합니다. **확인** 을 선택 하 여 빈 프로젝트를 만듭니다.

1. **솔루션 탐색기** 창에서 프로젝트 아래의 **소스 파일** 폴더를 열고 C 소스 코드가 포함 된 파일을 프로젝트에 추가 합니다.

1. **빌드** 메뉴에서 **솔루션 빌드** 명령을 선택 하 여 프로젝트를 빌드합니다.

1. **F5** 키를 눌러 디버거에서 프로그램을 시작 합니다.

::: moniker-end

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>명령줄에서 다중 스레드 프로그램을 컴파일 및 연결 하려면

1. 프로그램을 컴파일하고 연결 합니다.

    ```cmd
    cl bounce.c
    ```

## <a name="example"></a>예제

명령줄에서 빌드하려면 확장명이 .c 인 소스 파일에이 샘플을 복사 하 여 저장 합니다. IDE에서 템플릿에서 만든 소스 코드를이 샘플로 바꿉니다.

```C
// sample_multithread_c_program.c
// compile with: /c
//
//  Bounce - Creates a new thread each time the letter 'a' is typed.
//  Each thread bounces a character of a different color around
//  the screen. All threads are terminated when the letter 'Q' is
//  entered.
//

#include <windows.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>
#include <process.h>

#define MAX_THREADS  32

// The function getrandom returns a random number between
// min and max, which must be in integer range.
#define getrandom( min, max ) (SHORT)((rand() % (int)(((max) + 1) - \
                               (min))) + (min))

int main(void);                    // Thread 1: main
void KbdFunc(void);                // Keyboard input, thread dispatch
void BounceProc(void* MyID);       // Threads 2 to n: display
void ClearScreen(void);            // Screen clear
void ShutDown(void);               // Program shutdown
void WriteTitle(int ThreadNum);    // Display title bar information

HANDLE  hConsoleOut;                 // Handle to the console
HANDLE  hRunMutex;                   // "Keep Running" mutex
HANDLE  hScreenMutex;                // "Screen update" mutex
int     ThreadNr;                    // Number of threads started
CONSOLE_SCREEN_BUFFER_INFO csbiInfo; // Console information
COORD   consoleSize;
BOOL    bTrails;

int main() // Thread One
{
    // Get display screen information & clear the screen.
    hConsoleOut = GetStdHandle(STD_OUTPUT_HANDLE);
    GetConsoleScreenBufferInfo(hConsoleOut, &csbiInfo);
    consoleSize.X = csbiInfo.srWindow.Right;
    consoleSize.Y = csbiInfo.srWindow.Bottom;
    ClearScreen();
    WriteTitle(0);

    // Create the mutexes and reset thread count.
    hScreenMutex = CreateMutexW(NULL, FALSE, NULL);  // Cleared
    hRunMutex = CreateMutexW(NULL, TRUE, NULL);      // Set
    ThreadNr = 0;
    bTrails = FALSE;

    // Start waiting for keyboard input to dispatch threads or exit.
    KbdFunc();

    // All threads done. Clean up handles.
    if (hScreenMutex) CloseHandle(hScreenMutex);
    if (hRunMutex) CloseHandle(hRunMutex);
    if (hConsoleOut) CloseHandle(hConsoleOut);
}

void ShutDown(void) // Shut down threads
{
    while (ThreadNr > 0)
    {
        // Tell thread to die and record its death.
        ReleaseMutex(hRunMutex);
        ThreadNr--;
    }

    // Clean up display when done
    WaitForSingleObject(hScreenMutex, INFINITE);
    ClearScreen();
}

void KbdFunc(void) // Dispatch and count threads.
{
    int         KeyInfo;

    do
    {
        KeyInfo = _getch();
        if (tolower(KeyInfo) == 'a' &&
            ThreadNr < MAX_THREADS)
        {
            ThreadNr++;
            _beginthread(BounceProc, 0, &ThreadNr);
            WriteTitle(ThreadNr);
        }
        if (tolower(KeyInfo) == 't')
        {
            bTrails = !bTrails;
        }
    } while (tolower(KeyInfo) != 'q');

    ShutDown();
}

void BounceProc(void* pMyID)
{
    wchar_t MyCell, OldCell;
    WORD    MyAttrib, OldAttrib = 0;
    wchar_t BlankCell = 0x20;
    COORD   Coords, Delta;
    COORD   Old = { 0,0 };
    DWORD   Dummy;
    char* MyID = (char*)pMyID;

    // Generate update increments and initial
    // display coordinates.
    srand((unsigned int)* MyID * 3);

    Coords.X = getrandom(0, consoleSize.X - 1);
    Coords.Y = getrandom(0, consoleSize.Y - 1);
    Delta.X = getrandom(-3, 3);
    Delta.Y = getrandom(-3, 3);

    // Set up character & generate color
    // attribute from thread number.
    if (*MyID > 16)
        MyCell = 0x60 + *MyID - 16; // lower case
    else
        MyCell = 0x40 + *MyID;      // upper case
    MyAttrib = *MyID & 0x0f;   // force black background

    do
    {
        // Wait for display to be available, then lock it.
        WaitForSingleObject(hScreenMutex, INFINITE);

        if (!bTrails)
        {
            // If we still occupy the old screen position, blank it out.
            ReadConsoleOutputCharacterW(hConsoleOut, &OldCell, 1,
                Old, &Dummy);
            ReadConsoleOutputAttribute(hConsoleOut, &OldAttrib, 1,
                Old, &Dummy);
            if ((OldCell == MyCell) && (OldAttrib == MyAttrib))
                WriteConsoleOutputCharacterW(hConsoleOut, &BlankCell, 1,
                    Old, &Dummy);
        }

        // Draw new character, then clear screen lock
        WriteConsoleOutputCharacterW(hConsoleOut, &MyCell, 1,
            Coords, &Dummy);
        WriteConsoleOutputAttribute(hConsoleOut, &MyAttrib, 1,
            Coords, &Dummy);
        ReleaseMutex(hScreenMutex);

        // Increment the coordinates for next placement of the block.
        Old.X = Coords.X;
        Old.Y = Coords.Y;
        Coords.X += Delta.X;
        Coords.Y += Delta.Y;

        // If we are about to go off the screen, reverse direction
        if (Coords.X < 0 || Coords.X >= consoleSize.X)
        {
            Delta.X = -Delta.X;
            Beep(400, 50);
        }
        if (Coords.Y < 0 || Coords.Y > consoleSize.Y)
        {
            Delta.Y = -Delta.Y;
            Beep(600, 50);
        }
    }
    // Repeat while RunMutex is still taken.
    while (WaitForSingleObject(hRunMutex, 75L) == WAIT_TIMEOUT);
}

void WriteTitle(int ThreadNum)
{
    enum
    {
        sizeOfNThreadMsg = 120
    };
    wchar_t    NThreadMsg[sizeOfNThreadMsg] = { L"" };

    swprintf_s(NThreadMsg, sizeOfNThreadMsg,
        L"Threads running: %02d.  Press 'A' "
        L"to start a thread, 'T' to toggle "
        L"trails, 'Q' to quit.", ThreadNum);
    SetConsoleTitleW(NThreadMsg);
}

void ClearScreen(void)
{
    DWORD    dummy = 0;
    COORD    Home = { 0, 0 };
    FillConsoleOutputCharacterW(hConsoleOut, L' ',
        consoleSize.X * consoleSize.Y,
        Home, &dummy);
}
```

## <a name="see-also"></a>참고 항목

[C 및 Wind32를 사용한 다중 스레딩](multithreading-with-c-and-win32.md)
