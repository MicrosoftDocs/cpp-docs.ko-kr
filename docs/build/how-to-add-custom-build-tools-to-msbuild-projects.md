---
description: '자세한 정보: 방법: MSBuild 프로젝트에 사용자 지정 빌드 도구 추가'
title: '방법: MSBuild 프로젝트에 사용자 지정 빌드 도구 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 66ec4a488fd2a089f09ac775d1150300ff662ff2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162822"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>방법: MSBuild 프로젝트에 사용자 지정 빌드 도구 추가

사용자 지정 빌드 도구는 특정 파일에 연결된 사용자 정의 명령줄 도구입니다.

특정 파일에 대해 프로젝트 파일(.vcxproj)에 실행할 명령줄, 추가 입력 또는 출력 파일 및 표시할 메시지를 지정합니다. **MSBuild** 에서 출력 파일이 입력 파일을 기준으로 최신 상태가 아니라고 확인하면 메시지를 표시하고 명령줄 도구를 실행합니다.

사용자 지정 빌드 도구가 실행되는 시간을 지정하려면 프로젝트 파일의 `CustomBuildBeforeTargets` 및 `CustomBuildAfterTargets` XML 요소 중 하나 또는 둘 다 사용합니다. 예를 들어 사용자 지정 빌드 도구가 MIDL 컴파일러 이후, C/C++ 컴파일러 이전에 실행되도록 지정할 수 있습니다. 특정 대상이 실행되기 전에 도구를 실행하려면 `CustomBuildBeforeTargets` 요소를 지정하고, 특정 대상 이후에 도구를 실행하려면 `CustomBuildAfterTargets` 요소를 지정하고, 두 대상 사이에 도구를 실행하려면 두 요소 모두 지정합니다. 두 요소를 모두 지정하지 않으면 사용자 지정 빌드 도구는 **MIDL** 대상 앞에 있는 기본 위치에서 실행됩니다.

사용자 지정 빌드 단계 및 사용자 지정 빌드 도구는 `CustomBuildBeforeTargets` 및 `CustomBuildAfterTargets` XML 요소에 지정된 정보를 공유합니다. 프로젝트 파일에서 관련 대상을 한 번 지정합니다.

### <a name="to-add-a-custom-build-tool"></a>사용자 지정 빌드 도구를 추가하려면

1. 프로젝트 파일에 항목 그룹을 추가하고 각 입력 파일의 항목을 추가합니다. 여기에 표시된 것처럼 명령, 추가 입력, 출력 및 메시지를 항목 메타데이터로 지정합니다. 이 예제에서는 “faq.txt” 파일이 프로젝트와 동일한 디렉터리에 있다고 가정합니다.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>빌드에서 사용자 지정 빌드 도구를 실행할 위치를 정의하려면

1. 다음 속성 그룹을 프로젝트 파일에 추가합니다. 하나 이상의 대상을 지정해야 하지만, 특정 대상 전 또는 후에만 빌드 단계를 실행하려는 경우 다른 대상을 생략할 수 있습니다. 이 예제에서는 컴파일 이후, 연결하기 전에 사용자 지정 단계를 수행합니다.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>참조

[연습: MSBuild를 사용하여 C++ 프로젝트 만들기](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[방법: MSBuild 프로젝트에서 빌드 이벤트 사용](how-to-use-build-events-in-msbuild-projects.md)<br/>
[방법: MSBuild 프로젝트에 사용자 지정 빌드 단계 추가](how-to-add-a-custom-build-step-to-msbuild-projects.md)
