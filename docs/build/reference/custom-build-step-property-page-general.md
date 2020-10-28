---
title: '사용자 지정 빌드 단계 속성 페이지: 일반'
description: 이 문서에서는 속성 페이지 대화 상자의 사용자 지정 빌드 단계 페이지에서 사용할 수 있는 속성을 설명 합니다.
ms.date: 10/27/2020
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: 53f2deef931821981b3301f44ba37660975fb811
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907586"
---
# <a name="custom-build-step-property-page-general"></a>사용자 지정 빌드 단계 속성 페이지: 일반

프로젝트의 각 프로젝트 구성 및 대상 플랫폼 조합에 대해 프로젝트가 빌드될 때 실행할 사용자 지정 단계를 지정할 수 있습니다.

이 페이지의 Linux 버전은 [사용자 지정 빌드 단계 속성(Linux C++)](../../linux/prop-pages/custom-build-step-linux.md)을 참조하세요.

## <a name="general-page"></a>일반 페이지

- **명령줄**

   사용자 지정 빌드 단계에서 실행할 명령입니다.

- **설명**

   사용자 지정 빌드 단계를 실행할 때 표시되는 메시지입니다.

- **출력**

   사용자 지정 빌드 단계에서 생성되는 출력 파일입니다. 증분 빌드가 올바로 작동하려면 이 설정이 필요합니다.

- **추가 종속성**

   사용자 지정 빌드 단계에 사용할 추가 입력 파일의 세미콜론으로 구분한 목록입니다.

- **이후 실행 및 이전 실행**

   이러한 옵션은 나열된 대상 기준으로 빌드 프로세스에서 사용자 지정 빌드 단계가 실행되는 때를 정의합니다. 가장 일반적으로 나열 되는 `BuildGenerateSources` 대상은 `BuildCompile` `BuildLink` 빌드 프로세스의 주요 단계를 나타내므로, 및입니다. 자주 나열 되는 다른 대상은 `Midl` , `CLCompile` 및 `Link` 입니다.

- **출력을 콘텐츠로 처리**

   이 옵션은 패키지의 모든 콘텐츠 파일을 포함 하는 유니버설 Windows 플랫폼 또는 Windows Phone 앱에만 의미가 *`.appx`* 있습니다.

### <a name="to-specify-a-custom-build-step"></a>사용자 지정 빌드 단계를 지정하려면

1. 메뉴 모음에서 **프로젝트** > **속성** 을 선택합니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **속성 페이지** 대화 상자에서 **구성 속성**  >  **사용자 지정 빌드 단계**  >  **일반** 페이지로 이동 합니다.

1. 설정을 수정합니다.

## <a name="see-also"></a>참조

[C++ 프로젝트 속성 페이지 참조](property-pages-visual-cpp.md)
