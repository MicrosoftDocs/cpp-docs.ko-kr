---
description: '자세한 정보: 사용자 지정 빌드 도구 지정'
title: 사용자 지정 빌드 도구 지정
ms.date: 06/05/2018
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: db3162e3f7ad3f007d3f26e1ee2a279e5a132eb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275336"
---
# <a name="specify-custom-build-tools"></a>사용자 지정 빌드 도구 지정

*사용자 지정 빌드 도구* 는 빌드 시스템에 특정 입력 파일을 빌드하는 데 필요한 정보를 제공합니다. 사용자 지정 빌드 도구는 실행할 명령, 입력 파일의 목록, 명령에 의해 생성된 출력 파일 목록 및 도구에 대한 옵션 설명을 지정합니다.

사용자 지정 빌드 도구 및 사용자 지정 빌드 단계에 대한 일반 정보는 [사용자 지정 빌드 단계 및 빌드 이벤트 이해](understanding-custom-build-steps-and-build-events.md)를 참조하세요.

### <a name="to-specify-a-custom-build-tool"></a>사용자 지정 빌드 도구를 지정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 컴파일러 및 빌드 속성 설정](working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 을 선택하여 **구성** 상자를 사용하도록 설정합니다. **구성** 상자에서 사용자 지정 빌드 도구를 지정하려는 구성을 선택합니다.

1. **솔루션 탐색기** 에서 사용자 지정 빌드 도구의 입력 파일을 선택합니다.

   **사용자 지정 빌드 도구** 폴더가 표시되지 않는 경우 선택한 파일의 파일 확장명은 기본 도구와 연결됩니다. 예를 들어 .c 및 .cpp 파일의 기본 도구는 컴파일러입니다. 기본 도구 설정을 재정의하려면 **구성 속성** 노드의 **일반** 폴더에 있는 **항목 형식** 속성에서 **사용자 지정 빌드 도구** 를 선택합니다. **적용** 을 선택하면 **사용자 지정 빌드 도구** 노드가 표시됩니다.

1. **사용자 지정 빌드 도구** 노드의 **일반** 폴더에서 사용자 지정 빌드 도구와 연결된 속성을 지정합니다.

   - **추가 종속성** 에서 사용자 지정 빌드 도구를 정의한 하나 이상의 추가 파일을 지정합니다(사용자 지정 빌드 도구와 연결된 파일은 암시적으로 도구에 대한 입력으로 간주됨). 입력 파일을 추가하는 것은 사용자 지정 빌드 도구에 대한 요구 사항이 아닙니다. 추가 입력이 여러 개 있는 경우 세미콜론으로 구분합니다.

      **추가 종속성** 파일의 날짜가 입력 파일보다 나중인 경우 사용자 지정 빌드 도구가 실행됩니다. 모든 **추가 종속성** 파일이 입력 파일보다 오래된 경우 및 입력 파일이 **출력** 속성 파일보다 오래된 경우 사용자 지정 빌드 도구가 실행되지 않습니다.

      예를 들어 입력으로 MyInput.x를 사용하고 MyInput.cpp를 생성하며, MyInput.x에 MyHeader.h라는 헤더 파일이 포함된 사용자 지정 빌드 도구가 있다고 가정합니다. MyInput.x에 대한 입력 종속성으로 MyHeader.h를 지정할 수 있습니다. 또한 빌드 시스템이 MyInput.x 또는 MyHeader.h에 대하여 만료될 때 MyInput.cpp를 빌드합니다.

      입력 종속성은 사용자 지정 빌드 도구를 원하는 순서로 실행하도록 보장할 수도 있습니다. 앞의 예제에서 MyHeader.h가 실제로 사용자 지정 빌드 도구의 출력이라고 가정합니다. MyHeader.h가 MyInput.x의 종속성이기 때문에 빌드 시스템은 MyInput.x에서 사용자 지정 빌드 도구를 실행하기 전에 먼저 Myheader.h를 빌드합니다.

   - **명령줄** 에서 명령 프롬프트에 지정한 경우와 같이 명령을 지정합니다. 유효한 명령이나 일괄 처리 파일 및 필수 입력이나 출력 파일을 지정합니다. 모든 후속 명령이 실행되도록 보장하려면 일괄 처리 파일의 이름 앞에 **호출** 일괄 처리 명령을 지정합니다.

      여러 입력 및 출력 파일은 MSBuild 매크로를 사용하여 기호로 지정될 수 있습니다. 파일의 위치 또는 파일 집합의 이름을 지정하는 방법에 대한 정보는 [빌드 명령 및 속성에 대한 일반적인 매크로](reference/common-macros-for-build-commands-and-properties.md)를 참조하세요.

      '%' 문자를 MSBuild에서 예약했기 때문에 각 환경 변수를 지정한 경우 각 **%** 이스케이프 문자를 **%25** 16진수 이스케이프 시퀀스로 바꿉니다. 예를 들어 **%WINDIR%** 를 **%25WINDIR%25** 로 바꿉니다. MSBuild는 환경 변수에 액세스하기 전에 각 **%25** 시퀀스를 **%** 문자로 바꿉니다.

   - **설명** 에서 이 사용자 지정 빌드 도구에 대한 설명 메시지를 입력합니다. 빌드 시스템에서 이 도구를 처리할 때 메시지는 **출력** 창에 인쇄됩니다.

   - **출력** 에서 출력 파일의 이름을 지정합니다. 이 항목은 필수 항목입니다. 이 속성에 대한 값이 없으면 사용자 지정 빌드 도구가 실행되지 않습니다. 사용자 지정 빌드 도구에 둘 이상의 출력이 있는 경우 파일 이름을 세미콜론으로 구분합니다.

      출력 파일의 이름이 **명령줄** 속성에 지정된 것과 동일해야 합니다. 프로젝트 빌드 시스템은 파일을 찾고 날짜를 검사합니다. 출력 파일이 입력 파일보다 오래된 경우 또는 출력 파일을 찾을 수 없는 경우 사용자 지정 빌드 도구가 실행됩니다. 모든 **추가 종속성** 파일이 입력 파일보다 오래된 경우 및 입력 파일이 **출력** 속성에 지정된 파일보다 오래된 경우 사용자 지정 빌드 도구가 실행되지 않습니다.

빌드 시스템이 사용자 지정 빌드 도구에서 생성한 출력 파일에서 작동되도록 하려는 경우 프로젝트에 수동으로 추가해야 합니다. 사용자 지정 빌드 도구는 빌드하는 동안 파일을 업데이트합니다.

## <a name="example"></a>예제

프로젝트에서 parser.l이라는 파일을 포함하려고 한다고 가정합니다. 실행 파일 경로에 **lexer.exe** 라는 어휘 분석기가 있습니다. 이 기능을 사용하여 동일한 기본 이름(parser.c)을 가진 .c 파일을 생성하기 위해 parser.l을 처리하려고 합니다.

먼저 parser.l과 parser.c를 프로젝트에 추가합니다. 파일이 아직 존재하지 않는 경우 파일에 참조를 추가합니다. parser.l에 대한 사용자 지정 빌드 도구를 만들고 **명령** 속성에서 다음을 입력합니다.

> **lexer %(FullPath) .\%(Filename).c**

이 명령은 parser.l에서 어휘 분석기를 실행하고 프로젝트 디렉터리에 parser.c를 출력합니다.

**출력** 속성에서 다음과 같이 입력합니다.

> **.\%(Filename).c**

프로젝트를 빌드할 때 빌드 시스템은 parser.l와 parser.c의 타임스탬프를 비교합니다. parser.l가 최신인 경우 또는 parser.c가 존재하지 않는 경우 빌드 시스템은 **명령줄** 속성의 값을 실행하여 parser.c를 최신 상태로 변경합니다. 또한 parser.c가 프로젝트에 추가되었으므로 빌드 시스템은 parser.c를 컴파일합니다.

## <a name="see-also"></a>참조

[빌드 명령 및 속성에 대한 일반 매크로](reference/common-macros-for-build-commands-and-properties.md)<br>
[빌드 사용자 지정 문제 해결](troubleshooting-build-customizations.md)
