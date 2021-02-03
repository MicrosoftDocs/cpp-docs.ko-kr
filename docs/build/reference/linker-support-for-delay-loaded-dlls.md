---
description: '자세히 알아보기: 지연 로드 된 Dll에 대 한 링커 지원'
title: 링커의 지연 로드된 DLL 지원
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.openlocfilehash: 02991d6ac409ef301e326eea63ece8c5c7775010
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522419"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>링커의 지연 로드된 DLL 지원

MSVC 링커는 Dll의 지연 로드를 지원 합니다. 이 기능을 사용 하면 Windows SDK 함수를 사용 하 [`LoadLibrary`](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 고 [`GetProcAddress`](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) DLL 지연 로드를 구현할 필요가 없습니다.

지연 로드 없이 런타임에 DLL을 로드 하는 유일한 방법은 및를 사용 하는 것 `LoadLibrary` 입니다 `GetProcAddress` . 운영 체제는 dll을 사용 하는 실행 파일이 나 dll이 로드 될 때 dll을 로드 합니다.

지연 로드를 사용 하는 경우 DLL을 암시적으로 연결할 때 링커에서는 프로그램에서 해당 DLL의 함수를 호출할 때까지 DLL 로드를 지연 하는 옵션을 제공 합니다.

응용 프로그램은 도우미 함수를 사용 하 여 [ `/DELAYLOAD` 로드 지연 가져오기)](delayload-delay-load-import.md) 링커 옵션을 사용 하 여 DLL 로드를 지연 시킬 수 있습니다. (기본 도우미 함수 구현은 Microsoft에서 제공 합니다.) 도우미 함수는 런타임에 및를 호출 하 여 런타임에 필요할 때 DLL을 로드 합니다 `LoadLibrary` `GetProcAddress` .

다음과 같은 경우 DLL 로드를 지연 하는 것이 좋습니다.

- 프로그램이 DLL에서 함수를 호출 하지 않을 수 있습니다.

- DLL의 함수는 프로그램의 실행이 지연 될 때까지 호출 되지 않을 수 있습니다.

DLL의 지연 된 로드는 EXE 또는 DLL 프로젝트를 빌드하는 동안 지정할 수 있습니다. 하나 이상의 Dll 자체 로드를 지연 하는 DLL 프로젝트는에서 지연 로드 된 진입점을 호출 해서는 안 `DllMain` 됩니다.

## <a name="specify-dlls-to-delay-load"></a><a name="specify-dlls-to-delay-load"></a> 로드를 지연할 Dll 지정

링커 옵션을 사용 하 여 로드를 지연할 Dll을 지정할 수 있습니다 [`/delayload:`*`dllname`*](delayload-delay-load-import.md) . 자체 버전의 도우미 함수를 사용 하지 않으려는 경우 프로그램을 *`delayimp.lib`* (데스크톱 응용 프로그램의 경우) 또는 *`dloadhelper.lib`* (UWP 앱의 경우)와 연결 해야 합니다.

다음은 DLL을 지연 로드 하는 간단한 예입니다.

```cpp
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

프로젝트의 디버그 버전을 빌드합니다. 디버거를 사용 하 여 코드를 단계별로 실행 하면 *`user32.dll`* 가 호출 될 때만 로드 됩니다 `MessageBox` .

## <a name="explicitly-unload-a-delay-loaded-dll"></a><a name="explicitly-unload-a-delay-loaded-dll"></a> 지연 로드 된 DLL을 명시적으로 언로드

[`/delay:unload`](delay-delay-load-import-settings.md)링커 옵션을 사용 하면 코드에서 지연 로드 된 DLL을 명시적으로 언로드할 수 있습니다. 기본적으로 지연 로드 된 가져오기는 IAT (가져오기 주소 테이블)에 남아 있습니다. 그러나 링커 명령줄에서를 사용 하는 경우 **`/delay:unload`** 도우미 함수는 호출을 통해 DLL의 명시적 언로드를 지원 `__FUnloadDelayLoadedDLL2` 하 고 IAT를 원래 형식으로 다시 설정 합니다. 지금은 잘못 된 포인터를 덮어씁니다. IAT는 [`ImgDelayDescr`](understanding-the-helper-function.md#calling-conventions-parameters-and-return-type) 원래 iat의 복사본 주소 (있는 경우)가 포함 된 구조의 필드입니다.

### <a name="example-of-unloading-a-delay-loaded-dll"></a>지연 로드 된 DLL 언로드 예제

이 예제에서는 함수를 포함 하는 DLL을 명시적으로 언로드하는 방법을 보여 줍니다 *`MyDll.dll`* `fnMyDll` .

```C
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

지연 로드 된 DLL 언로드에 대 한 중요 정보:

- `__FUnloadDelayLoadedDLL2`MSVC 디렉터리에서 파일의 함수 구현을 찾을 수 있습니다 *`delayhlp.cpp`* *`include`* . 자세한 내용은 [지연 로드 도우미 함수 이해](understanding-the-helper-function.md)를 참조 하세요.

- *`name`* 함수의 매개 변수는 `__FUnloadDelayLoadedDLL2` 가져오기 라이브러리에 포함 된 것과 정확히 일치 해야 합니다 (대/소문자 포함). 이 문자열은 이미지의 가져오기 테이블에도 있습니다. 를 사용 하 여 가져오기 라이브러리의 내용을 볼 수 있습니다 [`DUMPBIN /DEPENDENTS`](dependents.md) . 대/소문자를 구분 하지 않는 문자열 일치를 선호 하는 경우 `__FUnloadDelayLoadedDLL2` 대/소문자를 구분 하지 않는 CRT 문자열 함수 또는 WINDOWS API 호출 중 하나를 사용 하도록를 업데이트할 수 있습니다.

## <a name="bind-delay-loaded-imports"></a><a name="bind-delay-loaded-imports"></a> 바인딩 지연 로드 된 가져오기

기본 링커 동작은 지연 로드 된 DLL에 대해 바인딩 가능한 IAT (가져오기 주소 테이블)를 만드는 것입니다. DLL이 바인딩된 경우 도우미 함수는 `GetProcAddress` 참조 되는 각 가져오기에 대해를 호출 하는 대신 바인딩된 정보를 사용 하려고 합니다. 타임 스탬프 또는 기본 설정 주소가 로드 된 DLL의 타임 스탬프 또는 기본 설정 주소와 일치 하지 않는 경우 도우미 함수는 바인딩된 가져오기 주소 테이블이 최신이 아닌 것으로 가정 합니다. 이는 IAT가 없는 것 처럼 진행 됩니다.

DLL의 지연 로드 된 가져오기를 바인딩하지 않으려는 경우 [`/delay:nobind`](delay-delay-load-import-settings.md) 링커 명령줄에를 지정 합니다. 링커에서는 바인딩된 가져오기 주소 테이블을 생성 하지 않으므로 이미지 파일의 공간이 절약 됩니다.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a><a name="load-all-imports-for-a-delay-loaded-dll"></a> 지연 로드 된 DLL에 대 한 모든 가져오기 로드

`__HrLoadAllImportsForDll`에 정의 된 함수는 링커 *`delayhlp.cpp`* 옵션으로 지정 된 DLL에서 모든 가져오기를 로드 하도록 링커에 지시 합니다 [`/delayload`](delayload-delay-load-import.md) .

모든 가져오기를 한 번에 로드 하면 한 곳에서 오류 처리를 중앙 집중화할 수 있습니다. 가져오기에 대 한 모든 실제 호출에 대해 구조적 예외 처리를 방지할 수 있습니다. 또한 프로세스를 통해 응용 프로그램이 부분 방식으로 실패 하는 상황을 방지할 수 있습니다. 예를 들어 도우미 코드에서 가져오기를 로드 하는 데 실패 한 경우에는 다른 사용자를 성공적으로 로드 한 후에 발생 합니다.

호출은 `__HrLoadAllImportsForDll` 후크 및 오류 처리 동작을 변경 하지 않습니다. 자세한 내용은 [오류 처리 및 알림](error-handling-and-notification.md)을 참조 하세요.

`__HrLoadAllImportsForDll` DLL 자체에 저장 된 이름에 대 한 대/소문자를 구분 하는 비교를 수행 합니다.

이라는 함수에서를 사용 하 여 `__HrLoadAllImportsForDll` `TryDelayLoadAllImports` 명명 된 DLL을 로드 하는 예제는 다음과 같습니다. 이 함수는 함수를 사용 하 여 `CheckDelayException` 예외 동작을 결정 합니다.

```C
int CheckDelayException(int exception_value)
{
    if (exception_value == VcppException(ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) ||
        exception_value == VcppException(ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND))
    {
        // This example just executes the handler.
        return EXCEPTION_EXECUTE_HANDLER;
    }
    // Don't attempt to handle other errors
    return EXCEPTION_CONTINUE_SEARCH;
}

bool TryDelayLoadAllImports(LPCSTR szDll)
{
    __try
    {
        HRESULT hr = __HrLoadAllImportsForDll(szDll);
        if (FAILED(hr))
        {
            // printf_s("Failed to delay load functions from %s\n", szDll);
            return false;
        }
    }
    __except (CheckDelayException(GetExceptionCode()))
    {
        // printf_s("Delay load exception for %s\n", szDll);
        return false;
    }
    // printf_s("Delay load completed for %s\n", szDll);
    return true;
}
```

의 결과를 사용 하 여 `TryDelayLoadAllImports` 가져오기 함수를 호출 하는지 여부를 제어할 수 있습니다.

## <a name="error-handling-and-notification"></a>오류 처리 및 알림

프로그램에서 지연 로드 된 Dll을 사용 하는 경우 오류를 강력 하 게 처리 해야 합니다. 프로그램이 실행 되는 동안 발생 하는 오류는 처리 되지 않은 예외가 발생 합니다. DLL 지연 로드 오류 처리 및 알림에 대 한 자세한 내용은 [오류 처리 및 알림](error-handling-and-notification.md)을 참조 하세요.

## <a name="dump-delay-loaded-imports"></a><a name="dump-delay-loaded-imports"></a> 덤프 지연 로드 된 가져오기

지연 로드 된 가져오기는를 사용 하 여 덤프할 수 있습니다 [`DUMPBIN /IMPORTS`](imports-dumpbin.md) . 이러한 가져오기는 표준 가져오기와 약간 다른 정보를 표시 합니다. 이러한 항목은 목록의 고유한 섹션으로 분리 `/imports` 되며 명시적으로 지연 로드 된 가져오기로 레이블이 지정 됩니다. 이미지에 언로드 정보가 있는 경우 해당 정보가 표시 됩니다. 바인딩 정보가 있는 경우 대상 DLL의 시간 및 날짜 스탬프가 가져오기의 바인딩된 주소와 함께 표시 됩니다.

## <a name="constraints-on-delay-load-dlls"></a><a name="constraints-on-delay-load-dlls"></a> Dll 지연 로드에 대 한 제약 조건

DLL 가져오기의 지연 로드에 대 한 몇 가지 제약 조건이 있습니다.

- 데이터 가져오기는 지원 되지 않습니다. 해결 방법은를 사용 하 여 데이터 가져오기를 직접 처리 하거나, `LoadLibrary` [`GetModuleHandle`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlew) 지연 로드 도우미가 DLL을 로드 한 후를 사용 하 여 데이터 가져오기를 명시적으로 처리 하는 것입니다 `GetProcAddress` .

- 지연 로드는 *`Kernel32.dll`* 지원 되지 않습니다. 지연 로드 도우미 루틴이 작동 하려면이 DLL을 로드 해야 합니다.

- 전달 된 진입점의 [바인딩은](#bind-delay-loaded-imports) 지원 되지 않습니다.

- DLL이 시작 시 로드 되지 않고 지연 로드 되는 경우 프로세스는 다른 동작을 가질 수 있습니다. 지연 로드 된 DLL의 진입점에서 발생 하는 프로세스별 초기화가 있는 경우 볼 수 있습니다. 다른 경우에는를 사용 하 여 선언 된 정적 TLS (스레드 로컬 저장소)가 [`__declspec(thread)`](../../cpp/thread.md) 있습니다 .이는를 통해 DLL이 로드 될 때 처리 되지 않습니다 `LoadLibrary` . 동적 TLS는,, 및를 사용 하 여 [`TlsAlloc`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) [`TlsFree`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsfree) [`TlsGetValue`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) [`TlsSetValue`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlssetvalue) 정적 또는 지연 로드 된 dll에서 계속 사용할 수 있습니다.

- 각 함수를 처음 호출 하 고 나면 가져온 함수에 대 한 정적 전역 함수 포인터를 다시 초기화 합니다. 함수 포인터를 처음 사용 하는 것은 로드 된 함수가 아닌 썽크를 가리키기 때문에 필요 합니다.

- 현재 일반 가져오기 메커니즘을 사용 하는 동안에는 DLL에서 특정 프로시저의 로드를 지연할 수 있는 방법이 없습니다.

- 사용자 지정 호출 규칙 (예: x86 아키텍처의 조건 코드 사용)은 지원 되지 않습니다. 또한 부동 소수점 레지스터는 플랫폼에 저장 되지 않습니다. 사용자 지정 도우미 루틴 또는 후크 루틴이 부동 소수점 형식을 사용 하는 경우 주의 해야 합니다. 루틴은 부동 소수점 매개 변수와 함께 등록 호출 규칙을 사용 하는 컴퓨터에서 전체 부동 소수점 상태를 저장 하 고 복원 해야 합니다. 특히 help 함수의 NDP (숫자 데이터 프로세서) 스택에서 부동 소수점 매개 변수를 사용 하는 CRT 함수를 호출 하는 경우 CRT DLL을 지연 로드 하는 데 주의 해야 합니다.

## <a name="understand-the-delay-load-helper-function"></a>지연 로드 도우미 함수 이해

링커 지원 지연 로드에 대 한 도우미 함수는 런타임에 실제로 DLL을 로드 하는 것입니다. 도우미 함수를 수정 하 여 동작을 사용자 지정할 수 있습니다. 에서 제공 된 도우미 함수를 사용 하는 대신 *`delayimp.lib`* 고유한 함수를 작성 하 고 프로그램에 연결 합니다. 하나의 도우미 함수는 모든 지연 로드 된 Dll을 사용 합니다. 자세한 내용은 [지연 로드 도우미 함수 이해](understanding-the-helper-function.md) 및 사용자 [고유의 도우미 함수 개발](understanding-the-helper-function.md#develop-your-own-helper-function)을 참조 하세요.

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](../dlls-in-visual-cpp.md)<br/>
[MSVC 링커 참조](linking.md)
