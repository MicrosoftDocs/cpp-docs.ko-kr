---
description: '자세한 정보: 다중 스레딩 및 로캘'
title: 다중 스레딩 및 로캘
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
ms.openlocfilehash: 246eb6c9be7046a77770de701d15754579b66055
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149983"
---
# <a name="multithreading-and-locales"></a>다중 스레딩 및 로캘

C 런타임 라이브러리와 c + + 표준 라이브러리 모두 프로그램의 로캘 변경에 대 한 지원을 제공 합니다. 이 항목에서는 다중 스레드 응용 프로그램에서 두 라이브러리의 로캘 기능을 사용할 때 발생 하는 문제에 대해 설명 합니다.

## <a name="remarks"></a>설명

C 런타임 라이브러리를 사용 하면 및 함수를 사용 하 여 다중 스레드 응용 프로그램을 만들 수 있습니다 `_beginthread` `_beginthreadex` . 이 항목에서는 이러한 함수를 사용 하 여 만든 다중 스레드 응용 프로그램에 대해서만 다룹니다. 자세한 내용은 [_beginthread, _beginthreadex을](../c-runtime-library/reference/beginthread-beginthreadex.md)참조 하세요.

C 런타임 라이브러리를 사용 하 여 로캘을 변경 하려면 [setlocale](../preprocessor/setlocale.md) 함수를 사용 합니다. 이전 버전의 Visual C++에서이 함수는 항상 전체 응용 프로그램 전체에서 로캘을 수정 합니다. 이제는 스레드 단위로 로캘을 설정 하는 기능이 지원 됩니다. [_Configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 함수를 사용 하 여이 작업을 수행 합니다. [Setlocale](../preprocessor/setlocale.md) 이 현재 스레드의 로캘을 변경 하도록 지정 하려면 해당 스레드에서를 호출 합니다 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . 반대로를 호출 하면 `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` 해당 스레드가 전역 로캘을 사용 하 고 해당 스레드에서 [setlocale](../preprocessor/setlocale.md) 을 호출 하면 스레드 단위 로캘을 명시적으로 사용 하도록 설정 하지 않은 모든 스레드의 로캘이 변경 됩니다.

C + + 런타임 라이브러리를 사용 하 여 로캘을 변경 하려면 [로캘 클래스](../standard-library/locale-class.md)를 사용 합니다. [Locale:: global](../standard-library/locale-class.md#global) 메서드를 호출 하 여 스레드 단위 로캘을 명시적으로 사용 하도록 설정 하지 않은 모든 스레드에서 로캘을 변경 합니다. 단일 스레드나 응용 프로그램의 일부에서 로캘을 변경 하려면 `locale` 해당 스레드나 코드 부분에 개체의 인스턴스를 만들면 됩니다.

> [!NOTE]
> [Locale:: global](../standard-library/locale-class.md#global) 을 호출 하면 c + + 표준 라이브러리 및 c 런타임 라이브러리의 로캘이 모두 변경 됩니다. 그러나 [setlocale](../preprocessor/setlocale.md) 을 호출 하면 C 런타임 라이브러리에 대 한 로캘만 변경 됩니다. c + + 표준 라이브러리는 영향을 받지 않습니다.

다음 예제에서는 [setlocale](../preprocessor/setlocale.md) 함수, [로캘 클래스](../standard-library/locale-class.md)및 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 함수를 사용 하 여 여러 가지 시나리오에서 응용 프로그램의 로캘을 변경 하는 방법을 보여 줍니다.

## <a name="example-change-locale-with-per-thread-locale-enabled"></a>예: 스레드별 로캘로 설정 된 로캘 변경

이 예제에서 주 스레드는 두 개의 자식 스레드를 생성 합니다. 첫 번째 스레드인 스레드 A는를 호출 하 여 스레드별 로캘을 사용 하도록 설정 합니다 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . 주 스레드는 물론 두 번째 스레드는 스레드 단위 로캘을 사용 하지 않습니다. 그런 다음 스레드 A는 C 런타임 라이브러리의 [setlocale](../preprocessor/setlocale.md) 함수를 사용 하 여 로캘을 변경 합니다.

스레드 A에 스레드 단위 로캘을 사용 하도록 설정 되어 있으므로 스레드 A의 C 런타임 라이브러리 함수만 "프랑스어" 로캘을 사용 하 여 시작 합니다. 스레드 B 및 주 스레드의 C 런타임 라이브러리 함수는 계속 해 서 "C" 로캘을 사용 합니다. 또한 [setlocale](../preprocessor/setlocale.md) 은 c + + 표준 라이브러리 로캘에 영향을 주지 않으므로 모든 c + + 표준 라이브러리 개체는 계속 해 서 "c" 로캘을 사용 합니다.

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example-change-global-locale-with-per-thread-locale-enabled"></a>예: 스레드 단위 로캘을 사용 하도록 설정 된 전역 로캘 변경

이 예제에서 주 스레드는 두 개의 자식 스레드를 생성 합니다. 첫 번째 스레드인 스레드 A는를 호출 하 여 스레드별 로캘을 사용 하도록 설정 합니다 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . 주 스레드는 물론 두 번째 스레드는 스레드 단위 로캘을 사용 하지 않습니다. 그런 다음 스레드 A는 c + + 표준 라이브러리의 [locale:: global](../standard-library/locale-class.md#global) 메서드를 사용 하 여 로캘을 변경 합니다.

스레드 A에 스레드 단위 로캘을 사용 하도록 설정 되어 있으므로 스레드 A의 C 런타임 라이브러리 함수만 "프랑스어" 로캘을 사용 하 여 시작 합니다. 스레드 B 및 주 스레드의 C 런타임 라이브러리 함수는 계속 해 서 "C" 로캘을 사용 합니다. 그러나 [locale:: global](../standard-library/locale-class.md#global) 메서드가 로캘 "전역"을 변경 하므로 모든 스레드의 모든 c + + 표준 라이브러리 개체는 "프랑스어" 로캘을 사용 하기 시작 합니다.

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example-change-locale-without-per-thread-locale-enabled"></a>예: 스레드 단위 로캘을 사용 하지 않고 로캘 변경

이 예제에서 주 스레드는 두 개의 자식 스레드를 생성 합니다. 첫 번째 스레드인 스레드 A는를 호출 하 여 스레드별 로캘을 사용 하도록 설정 합니다 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . 주 스레드는 물론 두 번째 스레드는 스레드 단위 로캘을 사용 하지 않습니다. 그런 다음 스레드 B는 C 런타임 라이브러리의 [setlocale](../preprocessor/setlocale.md) 함수를 사용 하 여 로캘을 변경 합니다.

스레드 B는 스레드 단위 로캘을 사용 하도록 설정 되어 있지 않으므로 스레드 B의 C 런타임 라이브러리와 주 스레드의 함수는 "프랑스어" 로캘을 사용 하 여 시작 합니다. 스레드 a에서 스레드 단위 로캘을 사용할 수 있으므로 스레드 A의 C 런타임 라이브러리 함수는 "C" 로캘을 계속 사용 합니다. 또한 [setlocale](../preprocessor/setlocale.md) 은 c + + 표준 라이브러리 로캘에 영향을 주지 않으므로 모든 c + + 표준 라이브러리 개체는 계속 해 서 "c" 로캘을 사용 합니다.

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example-change-global-locale-without-per-thread-locale-enabled"></a>예: 스레드 단위 로캘을 사용 하지 않는 전역 로캘 변경

이 예제에서 주 스레드는 두 개의 자식 스레드를 생성 합니다. 첫 번째 스레드인 스레드 A는를 호출 하 여 스레드별 로캘을 사용 하도록 설정 합니다 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . 주 스레드는 물론 두 번째 스레드는 스레드 단위 로캘을 사용 하지 않습니다. 그런 다음 스레드 B는 c + + 표준 라이브러리의 [locale:: global](../standard-library/locale-class.md#global) 메서드를 사용 하 여 로캘을 변경 합니다.

스레드 B는 스레드 단위 로캘을 사용 하도록 설정 되어 있지 않으므로 스레드 B의 C 런타임 라이브러리와 주 스레드의 함수는 "프랑스어" 로캘을 사용 하 여 시작 합니다. 스레드 a에서 스레드 단위 로캘을 사용할 수 있으므로 스레드 A의 C 런타임 라이브러리 함수는 "C" 로캘을 계속 사용 합니다. 그러나 [locale:: global](../standard-library/locale-class.md#global) 메서드가 로캘 "전역"을 변경 하므로 모든 스레드의 모든 c + + 표준 라이브러리 개체는 "프랑스어" 로캘을 사용 하기 시작 합니다.

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>참고 항목

[이전 코드에 대 한 다중 스레딩 지원 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[국제화](../c-runtime-library/internationalization.md)<br/>
[로캘](../c-runtime-library/locale.md)<br/>
[\<clocale>](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[locale 클래스](../standard-library/locale-class.md)
