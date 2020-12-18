---
description: '자세한 정보: CppProperties.json 참조'
title: CppProperties.json 참조
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: 9067a186d3ab111eda11246d06e3a9d7a164455f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163056"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json 참조

CMake를 사용하지 않는 폴더 열기 프로젝트는 *CppProperties.json* 파일에 IntelliSense에 대한 프로젝트 구성 설정을 저장할 수 있습니다. (CMake 프로젝트는 [CMakeSettings.json](customize-cmake-settings.md) 파일을 사용합니다.) 구성은 이름/값 쌍으로 구성되며 #include 경로, 컴파일러 스위치 및 기타 매개 변수를 정의합니다. 폴더 열기 프로젝트에서 구성을 추가하는 방법에 대한 자세한 내용은 [C++의 폴더 열기 프로젝트](open-folder-projects-cpp.md)를 참조하세요. 다음 섹션에서는 다양한 설정을 간략하게 설명합니다. 스키마에 대한 자세한 설명을 보려면 *CppProperties.json* 이 열려 있을 때 코드 편집기 맨 위에 전체 경로가 제공되는 *CppProperties_schema* 로 이동하세요.

## <a name="configuration-properties"></a>구성 속성

구성에는 다음 속성 중 하나가 있을 수 있습니다.

|이름|Description|
|-|-|
|`inheritEnvironments`| 이 구성에 적용되는 환경을 지정합니다.|
|`name`|C++ 구성 드롭다운에 표시될 구성 이름|
|`includePath`|include 경로에 지정해야 하는 쉼표로 구분된 폴더 목록(대부분의 컴파일러에서 /I에 매핑됨)|
|`defines`|정의해야 하는 매크로 목록(대부분의 컴파일러에서 /D에 매핑됨)|
|`compilerSwitches`|IntelliSense 동작에 영향을 줄 수 있는 하나 이상의 추가 스위치|
|`forcedInclude`|모든 컴파일 단위에 자동으로 포함될 헤더(MSVC에서 /FI에 매핑되거나 clang에서 -include에 매핑됨)|
|`undefines`|정의되지 않은 매크로 목록(MSVC에서 /U에 매핑됨)|
|`intelliSenseMode`|사용할 IntelliSense 엔진. MSVC, gcc 또는 Clang에 대해 미리 정의된 아키텍처 특정 변형 중 하나를 지정할 수 있습니다.|
|`environments`|명령 프롬프트에서 환경 변수처럼 동작하고 ${env.\<VARIABLE>} 매크로를 사용하여 액세스하는 사용자 정의 변수 집합입니다.|

### <a name="intellisensemode-values"></a>intelliSenseMode 값

입력을 시작하면 코드 편집기에 사용할 수 있는 옵션이 표시됩니다.

![IntelliSense 폴더 열기](media/open-folder-intellisense-mode.png "IntelliSense 폴더 열기")

지원되는 값은 다음과 같습니다.

- windows-msvc-x86
- windows-msvc-x64
- windows-msvc-arm
- windows-msvc-arm64
- android-clang-x86
- android-clang-x64
- android-clang-arm
- android-clang-arm64
- ios-clang-x86
- ios-clang-x64
- ios-clang-arm
- ios-clang-arm64
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- windows-clang-arm64
- linux-gcc-x86
- linux-gcc-x64
- linux-gcc-arm

참고: `msvc-x86` 및 `msvc-x64` 값은 레거시의 목적으로만 지원됩니다. 대신에 `windows-msvc-*` 변형을 사용하세요.

## <a name="pre-defined-environments"></a>미리 정의된 환경

Visual Studio에서는 해당 개발자 명령 프롬프트에 매핑되는 다음과 같은 미리 정의된 환경을 Microsoft C++에 제공합니다. 이러한 환경 중 하나를 상속하는 경우 ${env.\<VARIABLE>}이라는 매크로 구문과 함께 전역 속성 `env`를 사용하여 환경 변수 중 어떤 것이라도 참조할 수 있습니다.

|변수 이름|설명|
|-----------|-----------------|
|vsdev|기본 Visual Studio 환경|
|msvc_x86|x86 도구를 사용하여 x86용으로 컴파일|
|msvc_x64|64비트 도구를 사용하여 AMD64용으로 컴파일|
|msvc_arm|x86 도구를 사용하여 ARM용으로 컴파일|
|msvc_arm64|x86 도구를 사용하여 ARM64용으로 컴파일|
|msvc_x86_x64|x86 도구를 사용하여 AMD64용으로 컴파일|
|msvc_arm_x64|64비트 도구를 사용하여 ARM용으로 컴파일|
|msvc_arm64_x64|64비트 도구를 사용하여 ARM64용으로 컴파일|

Linux 워크로드가 설치되면 원격으로 Linux 및 WSL을 대상으로 지정하는 데 사용할 수 있는 환경은 다음과 같습니다.

|변수 이름|설명|
|-----------|-----------------|
|linux_x86|원격으로 x86 Linux를 대상 지정|
|linux_x64|원격으로 x64 Linux를 대상 지정|
|linux_arm|원격으로 ARM Linux를 대상 지정|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a> 사용자 정의 환경

`environments` 속성 사용을 선택하면 *CppProperties.json* 에서 전역으로 또는 구성별로 변수 집합을 정의할 수 있습니다. 이러한 변수는 Open Folder 프로젝트의 컨텍스트에서 환경 변수처럼 동작하며, 여기에서 변수를 정의한 후 ${env.\<VARIABLE>} 구문을 사용하여 *tasks.vs.json* 및 *launch.vs.json* 으로부터 액세스할 수 있습니다. 그러나 Visual Studio에서 내부적으로 사용하는 모든 명령 프롬프트에서 실제 환경 변수로 반드시 설정되는 것은 아닙니다.

**Visual Studio 2019 버전 16.4 이상:** *CppProperties.json* 에 정의된 구성별 변수는 `inheritEnvironments`를 설정할 필요 없이 디버그 대상 및 작업에 의해 자동으로 선택됩니다. 디버그 대상은 *CppProperties.json* 에서 지정하는 환경과 함께 자동으로 시작됩니다.

**Visual Studio 2019 버전 16.3 이하:** 환경을 사용하는 경우 환경이 동일한 구성의 일부로 정의된 경우에도 `inheritsEnvironments` 속성에서 지정해야 합니다. `environment` 속성은 환경의 이름을 지정합니다. 다음 예에서는 MSYS2 설치에서 GCC에 대해 IntelliSense를 사용하도록 설정하는 샘플 구성을 보여줍니다. 이 구성에서 `mingw_64` 환경을 정의하고 상속하는 방법과 `includePath` 속성이 `INCLUDE` 변수에 액세스할 수 있는 방법을 참고하세요.

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

구성 내에서 **환경** 속성을 정의하면 이 속성을 통해 동일한 이름의 모든 전역 변수가 재정의됩니다.

## <a name="built-in-macros"></a>기본 제공 매크로

*CppProperties.json* 내에서 액세스할 수 있는 기본 제공 매크로는 다음과 같습니다.

|매크로|Description|
|-|-|
|`${workspaceRoot}`| 작업 영역 폴더의 전체 경로|
|`${projectRoot}`| *CppProperties.json* 이 있는 폴더의 전체 경로|
|`${env.vsInstallDir}`| 실행 중인 Visual Studio 인스턴스가 설치되는 폴더의 전체 경로|

### <a name="example"></a>예제

예를 들어 프로젝트에 include 폴더가 있고 *windows.h* 및 Windows SDK의 다른 일반 헤더가 포함되어 있으면 *CppProperties.json* 구성 파일을 다음과 같은 include로 업데이트할 수 있습니다.

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%` 및 `%VCToolsInstallDir%`은 글로벌 환경 변수로 설정되지 않으므로 devenv.exe는 이러한 변수를 정의하는 개발자 명령 프롬프트에서 시작해야 합니다. (Windows 시작 메뉴에 "개발자" 입력)

## <a name="troubleshoot-intellisense-errors"></a>IntelliSense 오류 문제 해결

기대하는 IntelliSense가 표시되지 않는 경우 **도구** > **옵션** > **텍스트 편집기** > **C/C++**  > **고급** 으로 이동하고 **로깅 사용** 을 **`true`** 로 설정하여 문제를 해결할 수 있습니다. 먼저 **로깅 수준** 은 5로, **로깅 필터** 는 8로 설정해 보세요.

![진단 로깅](media/diagnostic-logging.png)

출력은 **출력 창** 으로 파이프되며 **다음에서 출력 보기: Visual C++ 로그** 를 선택하면 표시됩니다. 출력에는 무엇보다 IntelliSense에서 사용하려는 실제 include 경로의 목록이 포함됩니다. 이 경로가 *CppProperties.json* 의 경로와 일치하지 않으면 폴더를 닫고 캐시된 검색 데이터를 포함하는 *.vs* 하위 폴더를 삭제해 보세요.

include 경로 누락으로 인한 IntelliSense 오류 문제를 해결하려면, **오류 목록** 을 열고, 출력을 "IntelliSense 전용" 및 E1696 오류 코드("소스 파일을 열 수 없습니다. ...")로 필터링합니다.
