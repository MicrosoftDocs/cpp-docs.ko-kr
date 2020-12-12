---
description: '자세한 정보: c + + 프로젝트에 대 한 MSBuild 참조'
title: Visual Studio의 c + + 프로젝트에 대 한 MSBuild 참조
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 898757c8b7f1427c36e68a7227ec145abab8d078
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190616"
---
# <a name="msbuild-reference-for-c-projects"></a>C++ 프로젝트용 MSBuild 참조

MSBuild는 c + + 프로젝트를 비롯 하 여 Visual Studio의 모든 프로젝트에 대 한 기본 빌드 시스템입니다. Visual Studio IDE (통합 개발 환경)에서 프로젝트를 빌드하면 msbuild.exe 도구를 호출 합니다 .이 도구는 .vcxproj 프로젝트 파일 및 다양 한 .targets 및 props 파일을 사용 합니다. 일반적으로 Visual Studio IDE를 사용 하 여 프로젝트 속성을 설정 하 고 MSBuild를 호출 하는 것이 좋습니다. 프로젝트 파일을 수동으로 편집 하면 심각한 문제가 발생할 수 있습니다.

어떤 이유로 명령줄에서 MSBuild를 직접 사용 하려는 경우 [명령줄에서 Msbuild 사용](../msbuild-visual-cpp.md)을 참조 하세요. 일반적인 MSBuild에 대 한 자세한 내용은 Visual Studio 설명서의 [msbuild](/visualstudio/msbuild/msbuild) 를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[C++ 프로젝트용 MSBuild 내부](msbuild-visual-cpp-overview.md)<br/>
속성 및 대상의 저장 및 사용 방법에 대 한 정보입니다.

[빌드 명령 및 속성에 대한 일반 매크로](common-macros-for-build-commands-and-properties.md)<br/>
경로 및 제품 버전과 같은 속성을 정의 하는 데 사용할 수 있는 매크로 (컴파일 타임 상수)에 대해 설명 합니다.

[C + + 프로젝트용으로 만들어지는 파일 형식](file-types-created-for-visual-cpp-projects.md)<br/>
Visual Studio에서 다양 한 프로젝트 형식에 대해 만드는 다양 한 종류의 파일에 대해 설명 합니다.

[Visual Studio c + + 프로젝트 템플릿](visual-cpp-project-types.md)<br>
C + +에 사용할 수 있는 MSBuild 기반 프로젝트 형식에 대해 설명 합니다.

[C++ 새 항목 템플릿](using-visual-cpp-add-new-item-templates.md)<br>
Visual Studio 프로젝트에 추가할 수 있는 소스 파일 및 기타 항목에 대해 설명 합니다.

[미리 컴파일된 헤더 파일](../creating-precompiled-header-files.md) 미리 컴파일된 헤더 파일을 사용 하는 방법 및 빌드 시간을 단축 하기 위해 미리 컴파일된 사용자 지정 코드를 만드는 방법

[Visual Studio 프로젝트 속성 참조](property-pages-visual-cpp.md)<br/>
Visual Studio IDE에 설정 된 프로젝트 속성에 대 한 참조 설명서입니다.

## <a name="see-also"></a>참조

[C/C++ 빌드 참조](c-cpp-building-reference.md)
