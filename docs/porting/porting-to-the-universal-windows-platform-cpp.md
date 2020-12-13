---
description: '자세한 정보: 유니버설 Windows 플랫폼로 포팅 (c + +)'
title: 유니버설 Windows 플랫폼으로 포팅(C++)
ms.date: 10/23/2019
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
ms.openlocfilehash: e5bc8dfdfb44fa59e860a571b119914309e5a660
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331225"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>유니버설 Windows 플랫폼으로 포팅(C++)

이 항목에서는 Windows 10 앱 플랫폼인 유니버설 Windows 플랫폼에 기존 C++ 코드를 이식하는 방법에 대한 정보를 찾을 수 있습니다. *유니버설* 이라는 용어는 Windows 10을 실행 하는 모든 장치에서 코드를 실행할 수 있다는 것입니다. Windows 10을 실행하는 모든 디바이스에서 제대로 작동하는 단일 XAML 기반 사용자 인터페이스 및 단일 프로젝트를 만듭니다. XAML의 동적 레이아웃 기능을 사용하여 앱 UI를 다른 디스플레이 크기에 맞출 수 있습니다.

Windows 개발자 센터 설명서에는 유니버설 Windows 플랫폼으로 Windows 8.1 앱을 포팅하기 위한 가이드가 포함되어 있습니다. [Windows 런타임 8에서 UWP로 이동](/windows/uwp/porting/w8x-to-uwp-root)을 참조하세요. 이 가이드는 C# 코드에 주로 초점을 맞추고 있지만 대부분의 지침이 C++에도 적용됩니다. 다음 절차에는 보다 자세한 정보가 포함되어 있습니다. 또한 [데스크톱 응용 프로그램에서 UWP로 이동을](/windows/uwp/porting/desktop-to-uwp-migrate)참조 하세요.

이 항목에는 코드를 UWP로 포팅하기 위한 다음 절차가 포함되어 있습니다.

- [UWP에 Windows 8.1 스토어 앱 포팅](#BK_81StoreApp)

- [Windows 8.1 런타임 구성 요소를 UWP에 포팅](#BK_81Component)

클래식 데스크톱 Win32 DLL이 있는 상태에서 UWP 애플리케이션에서 이 파일을 호출하려는 경우에도 이 작업을 수행할 수 있습니다. 이러한 절차를 사용하여 기존 클래식 Windows 데스크톱 C++ 애플리케이션에 대한 UWP 사용자 인터페이스 레이어 또는 플랫폼 간 표준 C++ 코드를 만들 수 있습니다. [방법: 유니버설 Windows 플랫폼 앱에서 기존 C++ 코드 사용](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)을 참조하세요.

## <a name="porting-a-windows-81-store-app-to-the-uwp"></a><a name="BK_81StoreApp"></a> Windows 8.1 스토어 앱을 UWP에 이식

Windows 8.1 스토어 앱을 사용하는 경우 이러한 작업을 위해 UWP 및 Windows 10을 실행하는 모든 디바이스에서 다음 절차를 사용할 수 있습니다.  먼저 Visual Studio 2019을 사용 하 여 프로젝트를 Windows 8.1 프로젝트로 빌드하여 컴파일러 및 라이브러리의 변경 내용으로 인해 발생 하는 모든 문제를 제거 하는 것이 좋습니다. 작업을 완료한 후 이 작업을 Windows 10 UWP 프로젝트로 변환하는 두 가지 방법이 있습니다. 가장 쉬운 방법은(다음 절차에서 설명) 유니버설 Windows 프로젝트를 만들고 기존 코드를 복사하는 것입니다. Windows 8.1 데스크톱 및 Windows 8.1 Phone용 유니버설 프로젝트를 사용한 경우 프로젝트는 XAML의 두 개의 다른 레이아웃으로 시작되지만 디스플레이 크기에 맞게 조정되는 단일 동적 레이아웃으로 끝납니다.

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Windows 8.1 스토어 앱을 UWP에 이식하려면

1. Visual Studio 2017에서 아직 Windows 8.1 앱 프로젝트를 열지 않은 경우 프로젝트를 열고 지침에 따라 프로젝트 파일을 업그레이드합니다.

   **Visual Studio 설정에서 Windows 8.1 도구** 를 설치해야 합니다. 이러한 도구가 설치 되어 있지 않은 경우 **프로그램 및 기능** 창에서 **visual studio** 설치 프로그램을 시작 하 고 **visual studio 2017** 을 선택한 다음 설치 창에서 **수정** 을 선택 합니다. **Windows 8.1 도구** 를 찾아 선택 했는지 확인 하 고 **확인** 을 선택 합니다.

1. **프로젝트 속성** 창을 열고 **C++** > **일반** 에서 **플랫폼 도구 집합** 을 Visual Studio 2017용 도구 집합인 **v141** 로 설정합니다.

1. 프로젝트를 Windows 8.1 프로젝트로 빌드하고 빌드 오류를 해결합니다. 이 단계에서 발생하는 모든 오류는 빌드 도구 및 라이브러리의 주요 변경 내용 때문일 수 있습니다. 코드에 영향을 줄 수 있는 변경 내용에 대한 자세한 내용은 [Visual C++ 변경 기록 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)을 참조하세요.

   프로젝트가 잘 빌드되면 유니버설 Windows(Windows 10)에 이식할 수 있습니다.

1. 빈 템플릿을 사용하여 새 유니버설 Windows 앱 프로젝트를 만듭니다. 기존 프로젝트와 동일한 이름을 부여할 수 있지만 이렇게 하려면 두 프로젝트를 다른 디렉터리에 두어야 합니다.

1. 솔루션을 닫은 다음, **Windows 탐색기** 또는 명령줄을 사용하여 Windows 8.1 프로젝트의 코드 파일(확장명 .cpp, .h 및 .xaml)을 1단계에서 만든 프로젝트의 프로젝트 파일(.vcxproj)과 동일한 폴더로 복사합니다. Package.appxmanifest 파일은 복사하지 않도록 합니다. Windows 8.1 데스크톱 및 휴대폰에 대해 별도 코드를 작성한 경우 둘 중 하나를 먼저 선택하여 이식합니다(나중에 두 코드 조정을 위한 작업이 필요함). 하위 폴더와 해당 내용도 복사해야 합니다. 이름이 중복된 파일이 있으면 파일을 바꾸라는 메시지가 표시됩니다.

1. 솔루션을 다시 열고   >  프로젝트 노드에 대 한 바로 가기 메뉴에서 **기존 항목** 추가를 선택 합니다. 프로젝트에 이미 속해 있는 파일을 제외하고 복사한 모든 파일을 선택합니다.

   모든 하위 폴더를 선택하고 포함된 파일도 모두 추가합니다.

1. 이전 프로젝트와 이름이 같은 프로젝트를 사용하지 않을 경우 Package.appxmanifest 파일을 열고 `App` 클래스에 대한 네임스페이스 이름을 반영하도록 **진입점** 을 업데이트합니다.

   Package.appxmanifest 파일의 **진입점** 필드에는 `App` 클래스에 대해 범위가 지정된 이름이 포함됩니다. 이 이름에는 `App` 클래스를 포함하는 네임스페이스가 들어 있습니다. 유니버설 Windows 프로젝트를 만들 경우 네임스페이스는 프로젝트의 이름으로 설정됩니다. 이전 프로젝트에서 복사한 파일에 포함된 것과 다를 경우 일치하도록 업데이트해야 합니다.

1. 프로젝트를 빌드하고 여러 다른 Windows SDK 버전 간의 주요 변경 사항으로 인해 발생하는 빌드 오류를 해결합니다.

1. 로컬 데스크톱에서 프로젝트를 실행합니다. 배포 오류가 없고, 앱 레이아웃이 제대로 표시되고, 데스크톱에서 기능이 제대로 작동하는지 확인합니다.

1. 다른 디바이스(Windows Phone 8.1)용의 별도 코드 파일 및 .xaml이 있을 경우 이 코드를 검사하고 표준 디바이스와 다른 부분을 확인합니다. 레이아웃에서만 차이가 있는 경우 xaml에서 **Visual State Manager** 를 사용하여 화면 크기에 따라 디스플레이를 사용자 지정할 수 있습니다. 다른 차이점에 대해서는 다음 #if 문을 사용하여 코드에서 조건 섹션을 사용할 수 있습니다.

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   이러한 문은 각각 UWP 앱, Windows Phone 스토어 앱 중 하나 또는 둘 다에 적용되거나 적용되지 않습니다(클래식 Win32 데스크톱만 해당). 이러한 매크로는 Windows SDK 8.1 이상에서만 사용할 수 있으므로 이전 버전의 Windows SDK 또는 Windows 이외의 다른 플랫폼 용으로 코드를 컴파일해야 하면 이러한 매크로가 정의되지 않은 경우도 고려해야 합니다.

1. 앱이 지원하는 각 디바이스 종류에 대해 에뮬레이터 또는 실제 디바이스에서 앱을 실행하고 디버그합니다. 에뮬레이터를 실행하려면 가상 머신이 아닌 실제 컴퓨터에서 Visual Studio를 실행해야 합니다.

## <a name="porting-a-windows-81-runtime-component-to-the-uwp"></a><a name="BK_81Component"></a> Windows 8.1 런타임 구성 요소를 UWP에 이식

Windows 8.1 스토어 앱에서 이미 작동되는 DLL 또는 Windows 런타임 구성 요소가 있는 경우 다음 절차에 따라 구성 요소 또는 DLL이 UWP 및 Windows 10에서 작동되도록 할 수 있습니다. 기본 절차는 새 프로젝트를 만들고 코드를 복사하는 것입니다.

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Windows 8.1 런타임 구성 요소를 UWP에 포팅하려면

1. Visual Studio 2017의 **새 프로젝트** 대화 상자에서 **Windows 유니버설** 노드를 찾습니다. 이 노드가 표시되지 않으면 먼저 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)를 설치하세요. **Windows 런타임 구성 요소** 템플릿을 선택하고 구성 요소에 이름을 지정한 다음 **확인** 단추를 선택합니다. 구성 요소 이름은 네임스페이스 이름으로 사용되므로 이전 프로젝트의 네임스페이스와 동일한 이름을 사용하려고 할 수 있습니다. 그러려면 이전과 다른 폴더에 프로젝트를 만들어야 합니다. 다른 이름을 선택하면 생성된 코드 파일에서 네임스페이스 이름을 업데이트할 수 있습니다.

1. 프로젝트를 닫습니다.

1. 새로 만든 프로젝트에 Windows 8.1 구성 요소의 모든 코드 파일(.cpp, .h,.xaml 등)을 복사합니다. Package.appxmanifest 파일은 복사하지 마세요.

1. 빌드하고 여러 다른 Windows SDK 버전 간의 주요 변경 사항으로 인해 발생하는 오류를 해결합니다.

## <a name="troubleshooting"></a>문제 해결

UWP로 코드를 포팅하는 프로세스 동안 다양한 오류가 발생할 수 있습니다. 다음은 발생할 수 있는 몇 가지 문제입니다.

### <a name="project-configuration-issues"></a>프로젝트 구성 문제

다음 오류가 발생할 수 있습니다.

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

이 문제가 발생하면 프로젝트가 Windows 유니버설 프로젝트로 빌드되지 않습니다. 프로젝트 파일을 확인하고, 프로젝트를 Windows 유니버설 프로젝트로 식별하는 올바른 XML 요소가 있는지 확인합니다. 다음과 같은 요소가 있어야 합니다(대상 플랫폼의 버전 번호가 다를 수 있음).

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Visual Studio를 사용하여 새 UWP 프로젝트를 만든 경우 이 오류가 나타나지 않습니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 포팅 가이드](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[UWP(유니버설 Windows 플랫폼)용 앱 개발](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)
