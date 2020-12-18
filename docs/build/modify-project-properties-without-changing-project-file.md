---
description: '자세한 정보: 방법: 프로젝트 파일을 변경하지 않고 C++ 프로젝트 속성 및 대상 수정'
title: '방법: 프로젝트 파일을 변경하지 않고 C++ 프로젝트 속성 및 대상 수정'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: 91f71ccf7764307fef174d31a63583d6a3ce2aeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179865"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>방법: 프로젝트 파일을 변경하지 않고 C++ 프로젝트 속성 및 대상 수정

파일을 변경하지 않고 MSBuild 명령 프롬프트에서 프로젝트 속성 및 대상을 재정의할 수 있습니다. 일시적으로 또는 경우에 따라 일부 속성을 적용하려는 경우에 유용합니다. MSBuild의 일부 정보를 가정합니다. 자세한 내용은 [MSBuild](/visualstudio/msbuild/msbuild)를 참조하세요.

> [!IMPORTANT]
> .props 또는 .targets 파일을 만들려면 Visual Studio의 XML 편집기 또는 모든 텍스트 편집기를 사용할 수 있습니다. **속성 관리자** 가 프로젝트 파일에 속성을 추가하기 때문에 이 시나리오에서는 사용하지 마십시오.

*프로젝트 속성을 재정의하려면:*

1. 재정의하려는 속성을 지정하는 .props 파일을 만듭니다.

1. 명령 프롬프트에서: ForceImportBeforeCppTargets="C:\sources\my_props.props" 설정

*프로젝트 대상을 재정의하려면:*

1. 해당 구현 또는 특정 대상으로 .targets 파일 만들기

2. 명령 프롬프트에서: ForceImportAfterCppTargets ="C:\sources\my_target.targets" 설정

/p: 옵션을 사용하여 msbuild 명령줄에서 두 옵션 중 하나를 설정할 수도 있습니다.

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

이런 방식으로 속성 및 대상을 재정의하는 것은 솔루션의 모든 .vcxproj 파일에 다음의 가져오기를 추가하는 것과 동일합니다.

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
