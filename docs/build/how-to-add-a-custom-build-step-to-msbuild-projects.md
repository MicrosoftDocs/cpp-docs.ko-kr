---
description: '자세한 정보: 방법: MSBuild 프로젝트에 사용자 지정 빌드 단계 추가'
title: '방법: MSBuild 프로젝트에 사용자 지정 빌드 단계 추가'
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 1373aa2333fda6e0be9c7c574c5acc7840b9721a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156400"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>방법: MSBuild 프로젝트에 사용자 지정 빌드 단계 추가

사용자 지정 빌드 단계는 빌드의 사용자 정의 단계입니다. 사용자 지정 빌드 단계는 표준 컴파일 또는 링크 도구 단계와 같은 다른 ‘명령 도구’ 단계처럼 동작합니다. 

프로젝트 파일(.vcxproj)에서 사용자 지정 빌드 단계를 지정합니다. 이 단계에서는 실행할 명령줄, 추가 입력 또는 출력 파일 및 표시할 메시지를 지정할 수 있습니다. **MSBuild** 에서 출력 파일이 입력 파일을 기준으로 최신 상태가 아니라고 확인하면 메시지를 표시하고 명령을 실행합니다.

빌드 대상 시퀀스에서 사용자 지정 빌드 단계의 위치를 지정하려면 프로젝트 파일의 `CustomBuildAfterTargets` 및 `CustomBuildBeforeTargets` XML 요소 중 하나 또는 둘 다 사용합니다. 예를 들어 사용자 지정 빌드 단계가 링크 도구 대상 이후와 매니페스트 대상 도구 이전에 실행되도록 지정할 수 있습니다. 사용 가능한 실제 대상 집합은 특정 빌드에 따라 다릅니다.

특정 대상이 실행되기 전에 사용자 지정 빌드 단계를 실행하려면 `CustomBuildBeforeTargets` 요소를 지정하고, 특정 대상 이후에 단계를 실행하려면 `CustomBuildAfterTargets` 요소를 지정하고, 인접하는 두 대상 사이에 단계를 실행하려면 두 요소 모두 지정합니다. 두 요소를 모두 지정하지 않으면 사용자 지정 빌드 도구는 **Link** 대상 뒤에 있는 기본 위치에서 실행됩니다.

사용자 지정 빌드 단계 및 사용자 지정 빌드 도구는 `CustomBuildBeforeTargets` 및 `CustomBuildAfterTargets` XML 요소에 지정된 정보를 공유합니다. 따라서 프로젝트 파일에서 해당 대상을 한 번만 지정합니다.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>사용자 지정 빌드 단계에서 실행할 작업을 지정하려면

1. 프로젝트 파일에 속성 그룹을 추가합니다. 이 속성 그룹에서 다음 예제와 같이 명령, 명령의 입력과 출력 및 메시지를 지정합니다. 이 예제에서는 [연습: MSBuild를 사용하여 C++ 프로젝트 만들기](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)에서 만든 main.cpp 파일에서 .cab 파일을 만들 수 있습니다.

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>빌드에서 사용자 지정 빌드 단계를 실행할 위치를 정의하려면

1. 다음 속성 그룹을 프로젝트 파일에 추가합니다. 두 대상을 모두 지정하거나 특정 대상 이전 또는 이후에만 사용자 지정 단계를 실행하려는 경우 하나를 생략할 수 있습니다. 이 예제에서는 **MSBuild** 가 컴파일 단계 후, 링크 단계 전에 사용자 지정 단계를 수행하도록 지시합니다.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>참조

[연습: MSBuild를 사용하여 C++ 프로젝트 만들기](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[방법: MSBuild 프로젝트에서 빌드 이벤트 사용](how-to-use-build-events-in-msbuild-projects.md)<br/>
[방법: MSBuild 프로젝트에 사용자 지정 빌드 도구 추가](how-to-add-custom-build-tools-to-msbuild-projects.md)
