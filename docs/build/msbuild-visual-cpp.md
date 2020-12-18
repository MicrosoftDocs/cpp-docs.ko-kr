---
description: '자세한 정보: 명령줄에서 MSBuild 사용 - C++'
title: 명령줄에서 MSBuild 사용 - C++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: 9d78c50b398b0ad97cfd75727fdb4219677c546b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179852"
---
# <a name="msbuild-on-the-command-line---c"></a>명령줄에서 MSBuild 사용 - C++

일반적으로 Visual Studio를 사용하여 프로젝트 속성을 설정하고 MSBuild 시스템을 호출하는 것이 좋습니다. 하지만 **MSBuild** 도구를 명령 프롬프트에서 직접 사용할 수도 있습니다. 빌드 프로세스는 직접 만들고 편집할 수 있는 프로젝트 파일(.vcxproj)의 정보로 제어합니다. 프로젝트 파일에서는 빌드 단계, 조건 및 이벤트에 따라 빌드 옵션을 지정합니다. 또한 0개 이상의 명령줄 *options* 인수를 지정할 수 있습니다.

> **msbuild.exe** [ *project_file* ] [ *options* ]

**/target**(또는 **/t**) 및 **/property**(또는 **/p**) 명령줄 옵션을 사용하여 프로젝트 파일에 지정된 특정 속성 및 대상을 재정의할 수 있습니다.

프로젝트 파일의 필수 기능은 프로젝트에 적용되는 특정 작업인 ‘대상’을 지정하고 해당 작업을 수행하는 데 필요한 입력과 출력을 지정하는 것입니다.  프로젝트 파일에서는 기본 대상을 포함할 수 있는 하나 이상의 대상을 지정할 수 있습니다.

각 대상은 일련의 ‘작업’ 하나 이상으로 구성됩니다.  각 작업은 하나의 실행 가능한 명령을 포함하는 .NET Framework 클래스로 나타냅니다. 예를 들어 [CL 작업](/visualstudio/msbuild/cl-task)은 [cl.exe](reference/compiling-a-c-cpp-program.md) 명령을 포함합니다.

‘작업 매개 변수’는 클래스 작업의 속성이며 일반적으로 실행 가능한 명령의 명령줄 옵션을 나타냅니다.  예를 들어 `CL` 작업의 `FavorSizeOrSpeed` 매개 변수는 **/Os** 및 **/Ot** 컴파일러 옵션에 해당합니다.

추가 작업 매개 변수는 MSBuild 인프라를 지원합니다. 예를 들어 `Sources` 작업 매개 변수는 다른 작업에서 사용할 수 있는 작업 집합을 지정합니다. MSBuild 작업에 대한 자세한 내용은 [작업 참조](/visualstudio/msbuild/msbuild-task-reference)를 참조하세요.

작업 대부분에는 파일 이름, 경로, 문자열, 숫자 또는 부울 매개 변수와 같은 입력 및 출력이 필요합니다. 예를 들어 공통된 입력은 컴파일할 .cpp 소스 파일의 이름입니다. 중요한 입력 매개 변수는 빌드 구성 및 플랫폼을 지정하는 문자열(예: “Debug\|Win32”)입니다. 입력 및 출력은 `ItemGroup` 요소에 포함되는 하나 이상의 사용자 정의 XML `Item` 요소로 지정합니다.

프로젝트 파일에서 사용자 정의 ‘속성’과 `ItemDefinitionGroup` ‘항목’도 지정할 수 있습니다.   속성 및 항목은 이름/값 쌍의 형식이며 빌드에서 변수로 사용될 수 있습니다. 쌍의 이름 구성 요소는 ‘매크로’를 정의하고 값 구성 요소는 ‘매크로 값’을 선언합니다.   속성 매크로는 $(*name*) 표기를 사용하여 액세스하고 항목 매크로는 %(*name*) 표기를 사용하여 액세스합니다.

프로젝트 파일의 다른 XML 요소는 매크로를 테스트한 다음 조건부로 매크로의 값을 설정하거나 빌드 실행을 제어할 수 있습니다. 매크로 이름과 리터럴 문자열을 연결하여 경로 및 파일 이름과 같은 구문을 생성할 수 있습니다. 명령줄에서 **/property** 옵션은 프로젝트 속성을 설정하거나 재정의합니다. 명령줄에서 항목은 참조할 수 없습니다.

MSBuild 시스템에서는 다른 대상의 이전 또는 이후에 조건부로 대상을 실행할 수 있습니다. 또한 시스템에서는 대상이 사용하는 파일이 내보내는 파일보다 최신인지 아닌지에 따라 대상을 빌드할 수 있습니다.

MSBuild에 대한 자세한 내용은 다음을 참조하세요.

- [MSBuild](/visualstudio/msbuild/msbuild) MSBuild 개념에 관한 개요입니다.

- [MSBuild 참조](/visualstudio/msbuild/msbuild-reference) MSBuild 시스템에 대한 참조 정보입니다.

- [프로젝트 파일 스키마 참조](/visualstudio/msbuild/msbuild-project-file-schema-reference) MSBuild XML 스키마 요소와 함께 해당 특성과 부모 및 자식 요소를 나열합니다. 특히 [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [Target](/visualstudio/msbuild/target-element-msbuild)및 [Task](/visualstudio/msbuild/task-element-msbuild) 요소를 확인하세요.

- [명령줄 참조](/visualstudio/msbuild/msbuild-command-line-reference) msbuild.exe에 사용할 수 있는 명령줄 인수와 옵션을 설명합니다.

- [작업 참조](/visualstudio/msbuild/msbuild-task-reference) MSBuild 작업을 설명합니다. 특히 Visual C++와 관련된 [BscMake 작업](/visualstudio/msbuild/bscmake-task), [CL 작업](/visualstudio/msbuild/cl-task), [CPPClean 작업](/visualstudio/msbuild/cppclean-task), [LIB 작업](/visualstudio/msbuild/lib-task), [링크 작업](/visualstudio/msbuild/link-task), [MIDL 작업](/visualstudio/msbuild/midl-task), [MT 작업](/visualstudio/msbuild/mt-task), [RC 작업](/visualstudio/msbuild/rc-task), [SetEnv 작업](/visualstudio/msbuild/setenv-task), [VCMessage 작업](/visualstudio/msbuild/vcmessage-task)을 확인하세요.

## <a name="in-this-section"></a>섹션 내용

|용어|정의|
|----------|----------------|
|[연습: MSBuild를 사용하여 C++ 프로젝트 만들기](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|**MSBuild** 를 사용하여 C++ Visual Studio 프로젝트를 만드는 방법을 보여 줍니다.|
|[방법: MSBuild 프로젝트에서 빌드 이벤트 사용](how-to-use-build-events-in-msbuild-projects.md)|빌드 시작 전, 연결 단계 시작 전, 빌드 종료 후와 같은 빌드의 특정 단계에 수행되는 작업을 지정하는 방법을 보여 줍니다.|
|[방법: MSBuild 프로젝트에 사용자 지정 빌드 단계 추가](how-to-add-a-custom-build-step-to-msbuild-projects.md)|빌드 순서에 사용자 정의 단계를 추가하는 방법을 보여 줍니다.|
|[방법: MSBuild 프로젝트에 사용자 지정 빌드 도구 추가](how-to-add-custom-build-tools-to-msbuild-projects.md)|빌드 도구를 특정 파일에 연결하는 방법을 보여 줍니다.|
|[방법: 사용자 지정 도구를 프로젝트 속성에 통합](how-to-integrate-custom-tools-into-the-project-properties.md)|사용자 지정 도구의 옵션을 프로젝트 속성에 추가하는 방법을 보여 줍니다.|
|[방법: 대상 프레임워크 및 플랫폼 도구 세트 수정](how-to-modify-the-target-framework-and-platform-toolset.md)|여러 프레임워크 또는 도구 집합을 위한 프로젝트를 컴파일하는 방법을 보여 줍니다.|

## <a name="see-also"></a>참조

[명령줄에서 MSVC 도구 집합 사용](building-on-the-command-line.md)
