---
title: '방법: 사용자 지정 도구를 프로젝트 속성에 통합'
description: Visual Studio C++ 프로젝트에서 사용자 지정 도구를 프로젝트 속성에 통합하는 방법입니다.
ms.date: 10/08/2020
helpviewer_keywords:
- 'MSBuild (C++), howto: integrate custom tools'
ms.openlocfilehash: 4b88bf94a92efaf5046fd83e5c6358f3fdf80895
ms.sourcegitcommit: 6e5429e076e552b32e8bdc49480c51498d7924c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099669"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>방법: 사용자 지정 도구를 프로젝트 속성에 통합

XML 파일을 만들어 Visual Studio **속성 페이지** 창에 사용자 지정 도구 옵션을 추가할 수 있습니다.

**속성 페이지** 창의 **구성 속성** 섹션에 ’규칙’이라는 설정 그룹이 표시됩니다. 모든 규칙에는 도구 또는 기능 그룹에 대한 설정이 포함됩니다. 예를 들어 **링커** 규칙은 링커 도구에 대한 설정을 포함합니다. 규칙의 설정은 *범주* 로 세분화할 수 있습니다.

Visual Studio가 시작될 때 속성이 로드되도록 사용자 지정 도구의 속성이 포함된 규칙 파일을 만듭니다. 파일을 수정하는 방법에 대한 자세한 내용은 Visual Studio Project Team 블로그에서 [플랫폼 확장성 2부](/archive/blogs/vsproject/platform-extensibility-part-2)를 참조하세요.

::: moniker range="vs-2015"

규칙 파일을 저장할 폴더는 사용 중인 Visual Studio의 로캘 및 버전에 따라 다릅니다. Visual Studio 2015 이전 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>`* 입니다. Visual Studio 2015에서 `<version>` 값은 *`v140`* 입니다. `<locale>`은 LCID(예: 영어의 경우 `1033`)입니다. 설치된 각 Visual Studio 버전과 각각의 언어에 대해 다른 경로를 사용합니다. 예를 들어, Visual Studio 2015 Community 영어 버전의 기본 규칙 폴더 경로는 *`C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140\1033\`* 입니다.

::: moniker-end

::: moniker range="vs-2017"

규칙 파일을 저장할 폴더는 사용 중인 Visual Studio의 로캘 및 버전에 따라 다릅니다. Visual Studio 2017 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* 입니다. `<locale>`은 LCID(예: 영어의 경우 `1033`)입니다. Visual Studio 2015 이전 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* 입니다. 여기서 `<version>` 값은 Visual Studio 2015의 경우 *`v140`* 입니다. 설치된 각 Visual Studio 버전과 각각의 언어에 대해 다른 경로를 사용합니다. 예를 들어, Visual Studio 2017 Community 영어 버전의 기본 규칙 폴더 경로는 *`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\`* 입니다.

::: moniker-end

::: moniker range=">=vs-2019"

규칙 파일을 저장할 폴더는 사용 중인 Visual Studio의 로캘 및 버전에 따라 다릅니다. Visual Studio 2019 이상 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\<locale>\`* 입니다. 여기서 `<version>` 값은 Visual Studio 2019의 경우 *`v160`* 입니다. `<locale>`은 LCID(예: 영어의 경우 `1033`)입니다. Visual Studio 2017에서 규칙 폴더는 *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* 입니다. Visual Studio 2015 이전 버전의 개발자 명령 프롬프트에서 규칙 폴더는 *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* 입니다. 설치된 각 Visual Studio 버전과 각각의 언어에 대해 다른 경로를 사용합니다. 예를 들어, Visual Studio 2019 Community 영어 버전의 기본 규칙 폴더 경로는 *`C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\1033\`* 입니다.

::: moniker-end

### <a name="to-add-or-change-project-properties"></a>프로젝트 속성을 추가하거나 변경하려면

1. XML 편집기에서 XML 파일을 만듭니다.

1. 기본 규칙 폴더에 파일을 저장합니다. 언어와 Visual Studio 버전에 맞게 경로를 조정합니다. **속성 페이지** 창의 모든 규칙은 이 폴더에서 XML 파일로 표시됩니다. 파일의 이름은 폴더 내에서 고유해야 합니다.

1. 기존 규칙 파일(예: *`rc.xml`* )의 콘텐츠를 복사하고 변경 내용을 저장하지 않고 닫은 다음, 새 XML 파일에 콘텐츠를 붙여넣습니다. 템플릿으로 사용할 XML 스키마 파일을 복사할 수 있습니다. 사용하는 도구와 유사한 항목을 선택합니다.

1. 새 XML 파일에서 요구 사항에 따라 콘텐츠를 수정합니다. 파일 맨 위의 **규칙 이름** 과 **Rule.DisplayName** 을 변경해야 합니다.

1. 변경 내용을 저장하고 파일을 닫습니다.

1. Visual Studio가 시작되면 규칙 폴더의 XML 파일이 로드됩니다. 새 파일을 테스트하려면 Visual Studio를 다시 시작합니다.

1. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **속성** 을 선택합니다. **속성 페이지** 창에 해당 규칙 이름이 있는 새 노드가 있는지 확인합니다.

## <a name="see-also"></a>참조

[명령줄의 MSBuild - C++](msbuild-visual-cpp.md)
