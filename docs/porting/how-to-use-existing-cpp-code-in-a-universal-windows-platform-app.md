---
title: '방법: 유니버설 Windows 플랫폼 앱에서 기존 C++ 코드 사용'
description: 유니버설 Windows 플랫폼 apps에서 기존 코드 앱 및 라이브러리를 사용 하는 방법입니다.
ms.date: 09/04/2020
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: fd23c875d67654e96a828f4dba412dd74652912a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503668"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>방법: 유니버설 Windows 플랫폼 앱에서 기존 C++ 코드 사용

UWP (유니버설 Windows 플랫폼) 프로젝트에서 기존 c + + 코드를 사용할 수 있는 여러 가지 방법이 있습니다. 일부 방법에서는 구성 요소 확장 (c + +/CX)을 사용 하도록 설정 하 고 (즉, 옵션을 사용 하 여) 코드를 다시 컴파일할 필요가 없습니다 `/ZW` . 코드를 표준 c + +로 유지 하거나 일부 코드에 대 한 클래식 Win32 컴파일 환경을 유지 해야 할 수 있습니다. 적절 한 아키텍처를 선택 하 여 계속 수행할 수 있습니다. UWP UI와 c #, Visual Basic 및 JavaScript 호출자에 게 노출 되는 형식을 포함 하는 모든 코드를 고려 합니다. 이 코드는 Windows 앱 프로젝트 및 Windows 런타임 구성 요소 프로젝트에 있어야 합니다. C + +/CX (c + +/CX 포함) 에서만 호출 하는 코드는 `/ZW` 옵션 또는 표준 c + + 프로젝트를 사용 하 여 컴파일되는 프로젝트에 있을 수 있습니다. 허용 되지 않는 Api를 사용 하지 않는 이진 전용 코드는 정적 라이브러리로 연결 하 여 사용할 수 있습니다. 또는 앱을 콘텐츠로 패키지 하 고 DLL에서 로드할 수 있습니다.

데스크톱 프로그램을 UWP 환경에서 실행되게 하는 가장 쉬운 방법은 데스크톱 브리지 기술을 사용하는 것입니다. 여기에는 코드를 변경할 필요 없이 기존 응용 프로그램을 UWP 앱으로 패키징하는 데스크톱 앱 변환기가 포함 됩니다. 자세한 내용은 [데스크톱 브리지](/windows/uwp/porting/desktop-to-uwp-root)를 참조하세요.

이 문서의 나머지 부분에서는 c + + 라이브러리 (Dll 및 정적 라이브러리)를 유니버설 Windows 플랫폼로 이식 하는 방법에 대해 설명 합니다. 핵심 c + + 논리를 여러 UWP 앱에서 사용할 수 있도록 코드를 이식 하는 것이 좋습니다.

UWP 앱은 보호 된 환경에서 실행 됩니다. 따라서 플랫폼 보안을 손상 시킬 수 있는 많은 Win32, COM 및 CRT API 호출이 허용 되지 않습니다. `/ZW`컴파일러 옵션은 이러한 호출을 검색 하 고 오류를 생성할 수 있습니다. 응용 프로그램에서 앱 인증 키트를 사용 하 여 허용 되지 않는 Api를 호출 하는 코드를 검색할 수 있습니다. 자세한 내용은 [Windows 앱 인증 키트](/windows/uwp/debug-test-perf/windows-app-certification-kit)를 참조하세요.

라이브러리에 대 한 소스 코드를 사용할 수 있는 경우 허용 되지 않는 API 호출을 제거 하려고 할 수 있습니다. 허용 되지 않는 Api 목록은 [UWP 앱 용 Win32 및 COM api](/uwp/win32-and-com/win32-and-com-for-uwp-apps) 및 [유니버설 Windows 플랫폼 앱에서 지원 되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조 하세요. 일부 대안은 [UWP 앱에서 Windows API의 대안](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)에서 찾을 수 있습니다.

유니버설 Windows 프로젝트의 참조를 클래식 데스크톱 라이브러리에 추가 하려고 하면 라이브러리가 호환 되지 않는다는 오류 메시지가 표시 됩니다. 정적 라이브러리의 경우 *`.lib`* 클래식 Win32 응용 프로그램에서와 같은 방식으로 라이브러리 (파일)를 링커 입력에 추가 하 여 라이브러리에 링크할 수 있습니다. 이진 라이브러리만 사용할 수 있는 경우 유일한 옵션입니다. 정적 라이브러리는 앱의 실행 파일에 연결 됩니다. 그러나 UWP 앱에서 사용 하는 Win32 DLL은 프로젝트에 포함 하 고 콘텐츠로 표시 하 여 앱에 패키지 해야 합니다. UWP 앱에서 Win32 DLL을 로드 하려면 또는 대신를 호출 해야 [`LoadPackagedLibrary`](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) `LoadLibrary` `LoadLibraryEx` 합니다.

DLL 또는 정적 라이브러리의 소스 코드가 있는 경우 컴파일러 옵션을 사용 하 여 UWP 프로젝트로 다시 컴파일할 수 있습니다 `/ZW` . 그런 다음 **솔루션 탐색기**를 사용 하 여 참조를 추가 하 고 c + + UWP 앱에서 사용할 수 있습니다. 내보내기 라이브러리를 사용 하 여 DLL을 연결 합니다.

다른 언어로 호출자에게 기능을 노출하기 위해 라이브러리를 Windows 런타임 구성 요소로 변환할 수 있습니다. Windows 런타임 구성 요소는 *`.winmd`* .net 및 JavaScript 소비자가 요구 하는 방식으로 콘텐츠를 설명 하는 파일 형식의 메타 데이터를 포함 한다는 점에서 일반적인 dll과 다릅니다.  API 요소를 다른 언어에 노출 하기 위해 ref 클래스와 같은 c + +/CX 구문을 추가 하 고이를 공용으로 설정할 수 있습니다. Windows 10 이상에서는 c + +/CX 대신 [c + +/Winrt 라이브러리](https://github.com/microsoft/cppwinrt) 를 권장 합니다.

위의 설명은 다르게 처리 되어야 하는 COM 구성 요소에 적용 되지 않습니다. EXE 또는 DLL에 COM 서버가 있는 경우 유니버설 Windows 프로젝트에서 사용할 수 있습니다. 등록 하지 않아도 되는 [COM 구성 요소로](/windows/win32/sbscs/creating-registration-free-com-objects)패키지를 추가 하 고 프로젝트에 콘텐츠 파일로 추가 하 고를 사용 하 여 인스턴스화합니다 [`CoCreateInstanceFromApp`](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp) . 자세한 내용은 [Windows 스토어 C++ 프로젝트에서 Free-COM DLL 사용](/archive/blogs/win8devsupport/using-free-com-dll-in-windows-store-c-project)을 참조하세요.

기존 COM 라이브러리를 UWP로 이식 하려는 경우에는이를 Windows 런타임 구성 요소로 변환할 수 있습니다. 이러한 포트에 대 한 c + +/WinRT 라이브러리를 사용 하는 것이 좋지만 [Windows 런타임 c + + 템플릿 라이브러리 (WRL)](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md)를 사용 하는 것도 가능 합니다. WRL는 더 이상 사용 되지 않으며 ATL 및 OLE의 모든 기능을 지원 하지 않습니다. 이러한 포트가 적합 한지 여부는 구성 요소에 필요한 COM, ATL 및 OLE의 기능에 따라 달라 집니다.

어떤 개발 시나리오를 선택 하 든 많은 매크로 정의를 알고 있어야 합니다. 코드에서 이러한 매크로를 사용 하 여 클래식 데스크톱 Win32 및 UWP에서 조건부로 코드를 컴파일할 수 있습니다.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

이러한 문은 각각 UWP 앱, Windows Phone 스토어 앱 중 하나 또는 둘 다에 적용되거나 적용되지 않습니다(클래식 Win32 데스크톱만 해당). 이러한 매크로는 Windows SDK 8.1 이상 에서만 사용할 수 있습니다.

이 문서에는 다음과 같은 절차가 포함 되어 있습니다.

- [UWP 앱에서 Win32 DLL 사용](#BK_Win32DLL)

- [UWP 앱에서 네이티브 c + + 정적 라이브러리 사용](#BK_StaticLib)

- [Windows 런타임 구성 요소로 c + + 라이브러리 포팅](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a> UWP 앱에서 Win32 DLL 사용

보안과 안정성을 높이기 위해 유니버설 Windows 앱은 제한 된 런타임 환경에서 실행 됩니다. 클래식 Windows 데스크톱 응용 프로그램에서 사용 하는 것과 같은 방식으로 네이티브 DLL을 사용할 수 없습니다. DLL의 소스 코드가 있는 경우 UWP에서 실행되도록 코드를 이식할 수 있습니다. 먼저 프로젝트를 UWP 프로젝트로 식별하기 위해 몇 가지 프로젝트 설정과 프로젝트 파일 메타데이터를 변경합니다. `/ZW`C + +/cx를 사용 하는 옵션을 사용 하 여 라이브러리 코드를 다시 컴파일합니다. 특정 API 호출은 해당 환경에 연결 된 더 엄격한 제어 때문에 UWP 앱에서 허용 되지 않습니다. 자세한 내용은 [UWP 앱 용 Win32 및 COM api](/uwp/win32-and-com/win32-and-com-for-uwp-apps)를 참조 하세요.

`__declspec(dllexport)`을 사용하여 함수를 내보내는 네이티브 DLL이 있는 경우 DLL을 UWP 프로젝트로 다시 컴파일하여 UWP 앱에서 해당 함수를 호출할 수 있습니다. 예를 들어 다음 헤더 파일과 같은 코드를 사용 하 여 몇 가지 클래스와 해당 메서드를 내보내는 이름이 *기린* 인 Win32 DLL 프로젝트가 있다고 가정 합니다.

```cpp
// giraffe.h
// Define GIRAFFE_EXPORTS when building this DLL
#pragma once

#ifdef GIRAFFE_EXPORTS
#define GIRAFFE_API __declspec(dllexport)
#else
#define GIRAFFE_API
#endif

GIRAFFE_API int giraffeFunction();

class Giraffe
{
    int id;
        Giraffe(int id_in);
    friend class GiraffeFactory;

public:
    GIRAFFE_API int GetID();
};

class GiraffeFactory
{
    static int nextID;

public:
    GIRAFFE_API GiraffeFactory();
    GIRAFFE_API static int GetNextID();
    GIRAFFE_API static Giraffe* Create();
};
```

다음 코드 파일이 있다고 가정합니다.

```cpp
// giraffe.cpp
#include "pch.h"
#include "giraffe.h"

Giraffe::Giraffe(int id_in) : id(id_in)
{
}

int Giraffe::GetID()
{
    return id;
}

int GiraffeFactory::nextID = 0;

GiraffeFactory::GiraffeFactory()
{
    nextID = 0;
}

int GiraffeFactory::GetNextID()
{
    return nextID;
}

Giraffe* GiraffeFactory::Create()
{
    return new Giraffe(nextID++);
}

int giraffeFunction();
```

프로젝트의 다른 모든 항목 ( *`pch.h`* , *`dllmain.cpp`* )은 표준 Win32 프로젝트 템플릿의 일부입니다. 이 코드는 `GIRAFFE_API` 가 정의 된 경우로 확인 되는 매크로를 정의 합니다 `__declspec(dllexport)` `GIRAFFE_EXPORTS` . 즉, 프로젝트가 DLL로 빌드될 때 정의 되지만 클라이언트에서 헤더를 사용 하는 경우에는 정의 되지 않습니다 *`giraffe.h`* . 이 DLL은 소스 코드를 변경 하지 않고 UWP 프로젝트에서 사용할 수 있습니다. 일부 프로젝트 설정과 속성만 변경 해야 합니다.

다음 절차는를 사용 하 여 함수를 노출 하는 네이티브 DLL이 있는 경우에 적용 됩니다 `__declspec(dllexport)` .

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>새 프로젝트를 만들지 않고 네이티브 DLL을 UWP로 이식하려면

1. Visual Studio에서 DLL 프로젝트를 엽니다.

1. DLL 프로젝트에 대한 **프로젝트 속성**을 열고 **구성**을 **모든 구성**으로 설정합니다.

1. **프로젝트 속성**의 **C/C++** > **일반** 탭에서 **Windows 런타임 확장 사용**을 **예(/ZW)** 로 설정합니다. 이 속성을 사용 하면 구성 요소 확장 (c + +/CX)을 사용할 수 있습니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 바로 가기 메뉴를 연 다음 **프로젝트 언로드**를 선택 합니다. 그런 다음 언로드된 프로젝트 노드에서 바로 가기 메뉴를 열고 프로젝트 파일을 편집하도록 선택합니다. `WindowsTargetPlatformVersion` 요소를 찾아서 다음 요소로 바꿉니다.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   *`.vcxproj`* 파일을 닫고 바로 가기 메뉴를 다시 연 다음 **프로젝트 다시 로드**를 선택 합니다.

   이제 **솔루션 탐색기**는 프로젝트를 유니버설 Windows 프로젝트로 식별합니다.

1. 미리 컴파일된 헤더 파일 이름이 올바른지 확인합니다. **미리 컴파일된 헤더** 섹션에서 **미리 컴파일된 헤더 파일** 을에서 *`pch.h`* 로 변경 *`stdafx.h`* 하거나 다음과 같은 오류가 표시 되는 다른 방법으로 변경 해야 할 수 있습니다.

   > 오류 C2857: 명령줄 옵션을 사용 하 여 지정한 ' #include ' 문이 **`/Ycpch.h`** 소스 파일에 없습니다.

   문제는 이전 프로젝트 템플릿에서 미리 컴파일된 헤더 파일에 다른 명명 규칙을 사용 한다는 것입니다. Visual Studio 2019 이상 프로젝트는 *`pch.h`* 를 사용 합니다.

1. 프로젝트를 빌드합니다. 호환 되지 않는 명령줄 옵션에 대 한 몇 가지 오류가 발생할 수 있습니다. 예를 들어 현재 더 이상 사용되지 않지만 자주 사용되는 옵션인 **최소 다시 빌드 가능(/Gm)** 은 기본적으로 많은 이전 C++ 프로젝트에서 설정되며 `/ZW`와 호환되지 않습니다.

   유니버설 Windows 플랫폼를 컴파일할 때 일부 함수를 사용할 수 없습니다. 모든 문제에 대 한 컴파일러 오류가 표시 됩니다. 빌드를 정리할 때까지 이러한 오류를 해결 합니다.

1. 동일한 솔루션의 uwp 앱에서 DLL을 사용 하려면 uwp 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 참조 **추가**를 선택  >  **Reference**합니다.

   **프로젝트**  >  **솔루션**아래에서 DLL 프로젝트 옆에 있는 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

1. UWP 앱의 파일에 라이브러리의 헤더 파일을 포함 *`pch.h`* 합니다.

    ```cpp
    #include "..\Giraffe\giraffe.h"
    ```

1. 함수를 호출하고 DLL에서 형식을 만드는 코드를 UWP 프로젝트에서 일반적인 방식으로 추가합니다.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a> UWP 앱에서 네이티브 C++ 정적 라이브러리 사용

UWP 프로젝트에서 네이티브 C++ 정적 라이브러리를 사용할 수 있지만 알아두어야 할 몇 가지 제한 사항이 있습니다. [C++/CX의 정적 라이브러리](../cppcx/static-libraries-c-cx.md)에 대한 내용을 읽고 시작합니다. UWP 앱에서 정적 라이브러리의 네이티브 코드에 액세스할 수 있지만 이러한 정적 라이브러리에서는 공용 ref 형식을 만들지 않는 것이 좋습니다. `/ZW` 옵션을 사용하여 정적 라이브러리를 컴파일하는 경우 라이브러리 관리자(실제로는 가장된 링커)는 다음과 같이 경고합니다.

> LNK4264: /ZW로 컴파일된 개체 파일을 정적 라이브러리에 보관합니다. Windows 런타임 형식을 작성할 때는 Windows 런타임 메타데이터를 포함하는 정적 라이브러리와 연결하지 않는 것이 좋습니다.

그러나로 컴파일하지 않고 UWP 앱에서 정적 라이브러리를 사용할 수 있습니다 `/ZW` . 라이브러리는 ref 형식을 선언 하거나 c + +/CX 구문을 사용할 수 없습니다. 하지만 네이티브 코드의 라이브러리를 사용 하려는 경우에는 다음 단계를 수행 하 여이 작업을 수행할 수 있습니다.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>UWP 프로젝트에서 네이티브 C++ 정적 라이브러리를 사용하려면

1. UWP 프로젝트에 대 한 프로젝트 속성의 왼쪽 창에서 **구성 속성**  >  **링커**  >  **입력** 을 선택 합니다. 오른쪽 창에서 **추가 종속성** 속성의 라이브러리에 경로를 추가합니다. 예를 들어 프로젝트에서 출력을 배치 하는 라이브러리의 경우 *`<SolutionFolder>\Debug\MyNativeLibrary\MyNativeLibrary.lib`* 상대 경로를 추가 *`Debug\MyNativeLibrary\MyNativeLibrary.lib`* 합니다.

1. 파일 (있는 경우)에 헤더 파일을 참조 하는 include 문을 추가 하 *`pch.h`* *`.cpp`* 고 라이브러리를 사용 하는 코드를 추가 하기 시작 합니다.

   ```cpp
   #include "..\MyNativeLibrary\MyNativeLibrary.h"
   ```

   **솔루션 탐색기**의 **참조** 노드에서 참조를 추가 하지 마세요. 해당 메커니즘은 Windows 런타임 구성 요소에만 적용됩니다.

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a> Windows 런타임 구성 요소로 C++ 라이브러리 포팅

UWP 앱의 정적 라이브러리에서 네이티브 Api를 사용 하려는 경우를 가정해 보겠습니다. 네이티브 라이브러리에 대 한 소스 코드가 있는 경우 코드를 Windows 런타임 구성 요소로 이식할 수 있습니다. 더 이상 정적 라이브러리가 아닙니다. 모든 c + + UWP 앱에서 사용할 수 있는 DLL로 전환 합니다. 이 절차는 c + +/CX 확장을 사용 하는 새 Windows 런타임 구성 요소를 만드는 방법에 대해 설명 합니다. C + +/WinRT를 사용 하는 구성 요소를 만드는 방법에 대 한 자세한 내용은 [c + +/vb를 사용 하 여 구성 요소 Windows 런타임](/windows/uwp/winrt-components/create-a-windows-runtime-component-in-cppwinrt)

C + +/CX를 사용 하는 경우 모든 UWP 앱 코드에서 클라이언트가 사용할 수 있는 ref 형식 및 다른 c + +/CX 구문을 추가할 수 있습니다. C #, Visual Basic 또는 JavaScript에서 이러한 형식에 액세스할 수 있습니다. 기본 절차는 다음과 같습니다.

- Windows 런타임 구성 요소 (유니버설 Windows) 프로젝트 만들기
- 정적 라이브러리에 대 한 코드를 여기에 복사 합니다.
- 옵션에 의해 발생 한 컴파일러의 오류를 해결 `/ZW` 합니다.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Windows 런타임 구성 요소로 C++ 라이브러리를 이식하려면

1. Windows 런타임 구성 요소 (유니버설 Windows) 프로젝트를 만듭니다.

1. 프로젝트를 닫습니다.

1. **Windows 파일 탐색기**에서 새 프로젝트를 찾습니다. 그런 다음 이식 하려는 코드가 포함 된 c + + 라이브러리 프로젝트를 찾습니다. C + + 라이브러리 프로젝트에서 소스 파일 (하위 디렉터리에 포함 된 헤더 파일, 코드 파일 및 기타 모든 리소스)을 복사 합니다. 동일한 폴더 구조를 유지 하기 위해 새 프로젝트 폴더에 붙여 넣습니다.

1. Windows 런타임 구성 요소 프로젝트를 다시 엽니다. **솔루션 탐색기**에서 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **Add**  >  **기존 항목**추가를 선택 합니다.

1. 원래 프로젝트에서 추가할 모든 파일을 선택하고 **확인**을 선택합니다. 필요한 경우 하위 폴더를 대상으로 반복합니다.

1. 이제 중복된 일부 코드가 있을 수도 있습니다. 미리 컴파일된 헤더가 두 개 이상 있는 경우 (예를 들어 *`stdafx.h`* 및 모두 *`pch.h`* ) 유지할 항목을 하나 선택 합니다. 유지할 헤더에 include 문과 같은 필요한 코드를 복사합니다. 그런 다음 다른 항목을 삭제 하 고 프로젝트 속성의 **미리 컴파일된 헤더**에서 헤더 파일의 이름이 올바른지 확인 합니다.

   미리 컴파일된 헤더로 사용할 파일을 변경한 경우 각 파일에 대한 미리 컴파일된 헤더 옵션이 올바른지 확인합니다. 각 *`.cpp`* 파일을 차례로 선택 하 고 속성 창을 연 다음 **만들기 (/yc)** 로 설정 되어야 하는 미리 컴파일된 헤더를 제외 하 고 모두 **사용 (/yu)** 으로 설정 되어 있는지 확인 합니다.

1. 프로젝트를 빌드하고 모든 오류를 해결합니다. 이러한 오류는 옵션을 사용 하 여 발생 `/ZW` 하거나 새 버전의 Windows SDK 때문일 수 있습니다. 또는 라이브러리가 종속 된 헤더 파일과 같은 종속성 이나 이전 프로젝트와 새 프로젝트 간의 프로젝트 설정 차이를 반영할 수도 있습니다.

1. Public ref 형식을 프로젝트에 추가 하거나 일반 형식을 ref 형식으로 변환 합니다. 이러한 형식을 사용 하 여 UWP 앱에서 호출 하려는 기능에 대 한 진입점을 노출 합니다.

1. UWP 앱 프로젝트에서 구성 요소에 대한 참조를 추가하여 구성 요소를 테스트하고 만든 공용 API를 호출하는 코드를 추가합니다.

## <a name="see-also"></a>참고 항목

[유니버설 Windows 플랫폼으로 포팅](../porting/porting-to-the-universal-windows-platform-cpp.md)
