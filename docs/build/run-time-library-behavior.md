---
description: '자세한 정보: DLL 및 Visual C++ 런타임 라이브러리 동작'
title: DLL 및 Visual C++ 런타임 라이브러리 동작
ms.date: 08/19/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
ms.openlocfilehash: 5b76ec562b87969350b49d38e24c33ce7a4fabf8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275453"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL 및 Visual C++ 런타임 라이브러리 동작

Visual Studio를 사용하여 DLL(동적 연결 라이브러리)을 빌드하는 경우 기본적으로 링커는 VCRuntime(Visual C++ 런타임 라이브러리)을 포함합니다. VCRuntime에는 C/C++ 실행 파일을 초기화하고 종료하는 데 필요한 코드가 포함되어 있습니다. DLL에 연결된 경우 VCRuntime 코드는 DLL에 대한 Windows OS 메시지를 처리하여 프로세스 또는 스레드에 연결하거나 분리하는 `_DllMainCRTStartup`이라는 내부 DLL 진입점 함수를 제공합니다. `_DllMainCRTStartup` 함수는 스택 버퍼 보안 설정, CRT(C 런타임 라이브러리) 초기화 및 종료, 정적 및 전역 개체에 대한 생성자 및 소멸자 호출과 같은 필수 작업을 수행합니다. `_DllMainCRTStartup`은 WinRT, MFC, ATL 등의 다른 라이브러리에 대해 후크 함수를 호출하여 자체적으로 초기화 및 종료를 수행합니다. 이 초기화가 없으면 CRT 및 기타 라이브러리와 정적 변수는 초기화되지 않은 상태로 유지됩니다. DLL이 정적으로 연결된 CRT 또는 동적으로 연결된 CRT DLL을 사용하는지 관계없이 동일한 VCRuntime 내부 초기화 및 종료 루틴이 호출됩니다.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>기본 DLL 진입점 _DllMainCRTStartup

Windows에서 모든 DLL에는 초기화 및 종료 모두를 위해 호출되는 선택적 진입점 함수(일반적으로 `DllMain`이라고 함)가 포함될 수 있습니다. 이를 통해 필요에 따라 추가 리소스를 할당하거나 해제할 수 있습니다. Windows에서는 프로세스 연결, 프로세스 분리, 스레드 연결 및 스레드 분리의 네 가지 상황에서 진입점 함수를 호출합니다. DLL을 사용하는 애플리케이션이 로드될 때 또는 애플리케이션이 런타임에 DLL을 요청하여 DLL이 프로세스 주소 공간에 로드되면 운영 체제에서 DLL 데이터의 개별 복사본을 만듭니다. 이를  프로세스 연결이라고 합니다.  스레드 연결은 DLL을 로드하는 프로세스가 새 스레드를 만들 때 발생합니다.  스레드 분리는 스레드가 종료될 때 발생하고  프로세스 분리는 DLL이 더 이상 필요하지 않아 애플리케이션에 의해 해제될 때 발생합니다. 운영 체제는 이러한 각 이벤트의 DLL 진입점에 대한 개별 호출을 수행하여 각 이벤트 유형에 대한 *reason* 인수를 전달합니다. 예를 들어 OS는 *reason* 인수로 `DLL_PROCESS_ATTACH`를 보내 프로세스 연결을 알립니다.

VCRuntime 라이브러리는 기본 초기화 및 종료 작업을 처리하는 `_DllMainCRTStartup`이라는 진입점 함수를 제공합니다. 프로세스 연결에서 `_DllMainCRTStartup` 함수는 버퍼 보안 검사를 설정하고, CRT 및 기타 라이브러리를 초기화하고, 런타임 형식 정보를 초기화하고, 정적 및 비 로컬 데이터의 생성자를 초기화 및 호출하고, 스레드 로컬 저장소를 초기화하고, 각 연결에 대한 내부 정적 카운터를 증가시키고, 사용자 또는 라이브러리에서 제공한 `DllMain`을 호출합니다. 프로세스 분리에서는 함수가 이러한 단계를 역순으로 진행합니다. `DllMain`을 호출하고, 내부 카운터를 감소시키고, 소멸자를 호출하고, CRT 종료 함수 및 등록된 `atexit` 함수를 호출하고, 다른 종료 라이브러리에 알립니다. 연결 카운터가 0에 도달하면 함수는 `FALSE`를 반환하여 Windows에 DLL을 언로드할 수 있음을 표시합니다. `_DllMainCRTStartup` 함수는 스레드 연결 및 스레드 분리 시에도 호출됩니다. 이러한 경우 VCRuntime 코드는 자체적으로 추가 초기화 또는 종료를 수행하지 않으며 `DllMain`을 호출하여 메시지를 전달하기만 합니다. `DllMain`이 프로세스 연결에서 `FALSE`를 반환하여 실패를 표시하는 경우, `_DllMainCRTStartup`은 `DllMain`을 다시 호출하고 *reason* 인수로 `DLL_PROCESS_DETACH`를 전달한 다음 나머지 종료 프로세스를 진행합니다.

Visual Studio에서 DLL을 빌드하면 VCRuntime에서 제공하는 기본 진입점 `_DllMainCRTStartup`이 자동으로 연결됩니다. [/ENTRY(진입점 기호)](reference/entry-entry-point-symbol.md) 링커 옵션을 사용하여 DLL에 대한 진입점 함수를 지정할 필요가 없습니다.

> [!NOTE]
> /ENTRY: 링커 옵션을 사용하여 DLL에 대한 다른 진입점 함수를 지정할 수 있지만 진입점 함수는 `_DllMainCRTStartup`이 수행하는 모든 작업을 동일한 순서로 복제해야 하기 때문에 권장하지 않습니다. VCRuntime은 동작을 복제할 수 있는 함수를 제공합니다. 예를 들어 [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)를 [/gs (buffer security check)](reference/gs-buffer-security-check.md) 버퍼 검사 옵션을 지원 하기 위해 프로세스 연결에서 즉시 호출할 수 있습니다. 진입점 함수와 동일한 매개 변수를 전달하여 `_CRT_INIT` 함수를 호출해 나머지 DLL 초기화 또는 종료 기능을 수행할 수 있습니다.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>DLL 초기화

DLL에는 DLL 로드 시 실행되어야 하는 초기화 코드가 있을 수 있습니다. 사용자가 자체 DLL 초기화 및 종료 기능을 수행할 수 있도록 `_DllMainCRTStartup`은 사용자가 제공할 수 있는 `DllMain`이라는 함수를 호출합니다. `DllMain`에는 DLL 진입점에 필요한 서명이 있어야 합니다. 기본 진입점 함수 `_DllMainCRTStartup`은 Windows에서 전달하는 것과 동일한 매개 변수를 사용하여 `DllMain`을 호출합니다. `DllMain` 함수를 제공하지 않는 경우 기본적으로 Visual Studio는 `_DllMainCRTStartup`가 항상 호출할 수 있도록 사용자 대신 함수를 제공하고 연결합니다. 그러므로 DLL을 초기화할 필요가 없는 경우 DLL을 빌드할 때 특별한 작업을 수행할 필요가 없습니다.

다음은 `DllMain`에 사용되는 서명입니다.

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

일부 라이브러리는 `DllMain` 함수를 래핑합니다. 예를 들어 일반 MFC DLL에서 `CWinApp` 개체의 `InitInstance` 및 `ExitInstance` 멤버 함수를 구현하여 DLL에서 요구하는 초기화 및 종료 작업을 수행합니다. 자세한 내용은 [일반 MFC DLL 초기화](#initializing-regular-dlls) 섹션을 참조하세요.

> [!WARNING]
> DLL 진입점에서 안전하게 수행할 수 있는 작업은 상당히 제한적입니다. `DllMain`에서 호출하기에 안전하지 않은 특정 Windows API에 대한 [일반 모범 사례](/windows/win32/Dlls/dynamic-link-library-best-practices)를 참조하세요. 가장 간단한 초기화가 필요한 경우가 아닌 한 DLL에 대한 초기화 함수에서 이를 수행합니다. `DllMain`이 실행되고 DLL의 다른 함수를 호출하기 전에 애플리케이션에서 초기화 함수를 호출하도록 할 수 있습니다.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>일반(비 MFC) DLL 초기화

VCRuntime에서 제공하는 `_DllMainCRTStartup` 진입점을 사용하는 일반(비 MFC) DLL에서 초기화를 수행하려면 DLL 소스 코드에 `DllMain`이라는 함수가 포함되어 있어야 합니다. 다음 코드는 `DllMain` 정의에 대한 기본 구조를 제공합니다.

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason)
    {
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```

> [!NOTE]
> 이전 Windows SDK 설명서에서는 링커 명령줄에서 /ENTRY 옵션을 사용하여 DLL 진입점 함수의 실제 이름을 지정해야 한다고 설명했습니다. Visual Studio에서는 진입점 함수의 이름이 `DllMain`인 경우 /ENTRY 옵션을 사용할 필요가 없습니다. 실제로는 /ENTRY 옵션을 사용하여 진입점 함수 이름을 `DllMain` 이외의 이름으로 지정하는 경우 진입점 함수가 `_DllMainCRTStartup`과 동일하게 초기화 호출을 수행하지 않으면 CRT가 제대로 초기화되지 않습니다.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>일반 MFC DLL 초기화

일반 MFC DLL에는 `CWinApp` 개체가 있으므로 MFC 애플리케이션과 동일한 위치, 즉 DLL의 `CWinApp` 파생 클래스의 `InitInstance` 및 `ExitInstance` 멤버 함수에서 초기화 및 종료 작업을 수행해야 합니다. MFC는 `_DllMainCRTStartup`이 `DLL_PROCESS_ATTACH` 및 `DLL_PROCESS_DETACH`에 대해 호출하는 `DllMain` 함수를 제공하므로 자체 `DllMain` 함수를 작성하면 안됩니다. MFC 제공 `DllMain` 함수는 DLL이 로드될 때 `InitInstance`를 호출하고 DLL이 언로드되기 전에 `ExitInstance`를 호출합니다.

일반 MFC DLL은 `InitInstance` 함수에서 [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) 및 [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)를 호출하여 여러 스레드를 추적할 수 있습니다. 이러한 함수를 사용하면 DLL이 스레드별 데이터를 추적할 수 있습니다.

MFC에 동적으로 연결되는 일반 MFC DLL에서 MFC OLE, MFC 데이터베이스(또는 DAO) 또는 MFC 소켓 지원을 각각 사용하는 경우 디버그 MFC 확장 DLL인 MFCO *version* D.dll, MFCD *version* D.dll 및 MFCN *version* D.dll(여기서 *version* 은 버전 번호)가 자동으로 연결됩니다. 일반 MFC DLL의 `CWinApp::InitInstance`에서 사용하는 각 DLL에 대해 다음과 같은 미리 정의된 초기화 함수 중 하나를 호출해야 합니다.

|MFC 형식 지원|호출할 초기화 함수|
|-------------------------|-------------------------------------|
|MFC OLE(MFCO *version* D.dll)|`AfxOleInitModule`|
|MFC 데이터베이스(MFCD *version* D.dll)|`AfxDbInitModule`|
|MFC 소켓(MFCN *version* D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>MFC 확장 DLL 초기화

MFC 확장 DLL에는 일반 MFC DLL과 같은 `CWinApp` 파생 개체가 없으므로 MFC DLL 마법사가 생성하는 `DllMain` 함수에 초기화 및 종료 코드를 추가해야 합니다.

이 마법사는 MFC 확장 DLL에 대해 다음 코드를 제공합니다. 코드에서 `PROJNAME`은 프로젝트의 이름에 대한 자리 표시자입니다.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      TRACE0("PROJNAME.DLL Initializing!\n");

      // MFC extension DLL one-time initialization
      AfxInitExtensionModule(PROJNAMEDLL,
                                 hInstance);

      // Insert this DLL into the resource chain
      new CDynLinkLibrary(Dll3DLL);
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      TRACE0("PROJNAME.DLL Terminating!\n");
   }
   return 1;   // ok
}
```

초기화 도중 새 `CDynLinkLibrary` 개체를 만들면 MFC 확장 DLL에서 `CRuntimeClass` 개체 또는 리소스를 클라이언트 애플리케이션으로 내보낼 수 있습니다.

하나 이상의 일반 MFC DLL에서 MFC 확장 DLL을 사용하려는 경우 `CDynLinkLibrary` 개체를 만드는 초기화 함수를 내보내야 합니다. 이 함수는 MFC 확장 DLL을 사용하는 각 일반 MFC DLL에서 호출해야 합니다. 이 초기화 함수를 호출하는 적절한 위치는 MFC 확장 DLL의 내보낸 클래스 또는 함수를 사용하기 전에 일반 MFC DLL의 `CWinApp` 파생 개체의 `InitInstance` 멤버 함수입니다.

MFC DLL 마법사가 생성하는 `DllMain`에서 `AfxInitExtensionModule`을 호출하면 모듈의 런타임 클래스(`CRuntimeClass` 구조체)가 캡처되고 `CDynLinkLibrary` 개체가 만들어질 때 사용할 수 있도록 개체 팩터리(`COleObjectFactory` 개체)도 캡처됩니다. `AfxInitExtensionModule`의 반환 값을 확인해야 합니다. `AfxInitExtensionModule`에서 0 값을 반환하는 경우 `DllMain` 함수에서 0을 반환합니다.

MFC 확장 DLL이 실행 파일에 명시적으로 연결된 경우(즉 실행 파일이 `AfxLoadLibrary`를 호출하여 DLL로 연결됨) `DLL_PROCESS_DETACH`에서 `AfxTermExtensionModule` 호출을 추가해야 합니다. 이 함수를 사용하면 각 프로세스가 MFC 확장 DLL에서 분리될 때(프로세스가 종료되거나 DLL이 `AfxFreeLibrary` 호출로 인해 언로드되는 경우에 발생) MFC가 MFC 확장 DLL을 정리할 수 있습니다. MFC 확장 DLL이 애플리케이션에 암시적으로 연결되는 경우 `AfxTermExtensionModule` 호출이 필요하지 않습니다.

MFC 확장 DLL에 명시적으로 연결되는 애플리케이션은 DLL을 해제할 때 `AfxTermExtensionModule`을 호출해야 합니다. 또한 애플리케이션에서 여러 스레드를 사용하는 경우 Win32 함수 `LoadLibrary` 및 `FreeLibrary` 대신 `AfxLoadLibrary` 및 `AfxFreeLibrary`를 사용해야 합니다. `AfxLoadLibrary` 및 `AfxFreeLibrary`를 사용하면 MFC 확장 DLL이 로드 및 언로드될 때 실행되는 시작 및 종료 코드가 전역 MFC 상태를 손상하지 않습니다.

MFCx0.dll은 `DllMain`이 호출될 때 완전히 초기화되기 때문에 `DllMain` 내에서 메모리를 할당하고 MFC 함수를 호출할 수 있습니다(16비트 버전 MFC와는 다름).

확장 DLL은 `DllMain` 함수의 `DLL_THREAD_ATTACH` 및 `DLL_THREAD_DETACH` 사례를 처리하여 다중 스레딩을 관리할 수 있습니다. 이러한 사례는 스레드가 DLL에서 연결 및 분리될 때 `DllMain`에 전달됩니다. DLL이 연결될 때 [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)을 호출하면 DLL이 DLL에 연결된 모든 스레드의 TLS(스레드 로컬 스토리지) 인덱스를 유지할 수 있습니다.

헤더 파일 Afxdllx.h에는 `AFX_EXTENSION_MODULE` 및 `CDynLinkLibrary` 정의와 같은 MFC 확장 DLL에서 사용되는 구조체에 대한 특수 정의가 포함되어 있습니다. MFC 확장 DLL에 이 헤더 파일을 포함해야 합니다.

> [!NOTE]
> *pch.h*(Visual Studio 2017 및 이전 버전의 *stdafx.h*)의 `_AFX_NO_XXX` 매크로는 정의하거나 정의 해제하지 않는 것이 중요합니다. 이러한 매크로는 특정 대상 플랫폼이 해당 기능을 지원하는지 여부를 확인하기 위한 목적으로만 존재합니다. 프로그램을 작성하여 이러한 매크로를 확인할 수 있지만(예: `#ifndef _AFX_NO_OLE_SUPPORT`) 프로그램이 이러한 매크로를 정의하거나 정의 해제해서는 안됩니다.

다중 스레딩을 처리하는 샘플 초기화 함수는 Windows SDK의 [동적 연결 라이브러리에서 스레드 로컬 스토리지 사용](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)에 포함되어 있습니다. 이 샘플은 `LibMain`이라는 진입점 함수를 포함하지만 MFC 및 C 런타임 라이브러리와 함께 작동하도록 이 함수의 이름을 `DllMain`으로 지정해야 합니다.

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)<br/>
[DllMain 진입점](/windows/win32/Dlls/dllmain)<br/>
[동적 연결 라이브러리 모범 사례](/windows/win32/Dlls/dynamic-link-library-best-practices)
