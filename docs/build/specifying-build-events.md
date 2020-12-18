---
description: '자세한 정보: 빌드 이벤트 지정'
title: 빌드 이벤트 지정
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
ms.openlocfilehash: 1d1dc9a1f0e379c3abe36117beaf9ef58bcbd064
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275401"
---
# <a name="specifying-build-events"></a>빌드 이벤트 지정

빌드 이벤트를 사용하여 빌드 시작 전, 연결 프로세스 전 또는 빌드 완료 후 실행되는 명령을 지정할 수 있습니다.

빌드 이벤트는 빌드가 빌드 프로세스의 해당 지점에 성공적으로 도달할 경우에만 실행됩니다. 빌드에서 오류가 발생하는 경우 *빌드 후* 이벤트가 발생하지 않습니다. 연결 단계 전에 오류가 발생한 경우 *연결 전* 또는 *빌드 후* 이벤트가 발생하지 않습니다. 또한 파일이 연결될 필요가 없는 경우 *연결 전* 이벤트가 발생하지 않습니다. *연결 전* 이벤트는 연결 단계를 포함하지 않는 프로젝트에서 지원되지 않습니다.

파일을 빌드할 필요가 없는 경우 빌드 이벤트가 발생하지 않습니다.

빌드 이벤트에 대한 일반적인 정보는 [사용자 지정 빌드 단계 및 빌드 이벤트 이해](understanding-custom-build-steps-and-build-events.md)를 참조하세요.

### <a name="to-specify-a-build-event"></a>빌드 이벤트를 지정하려면

1. **솔루션 탐색기** 에서 빌드 이벤트를 지정할 프로젝트를 선택합니다.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 컴파일러 및 빌드 속성 설정](working-with-project-properties.md)을 참조합니다.

1. **빌드 이벤트** 폴더에서 빌드 이벤트 속성 페이지를 선택합니다.

1. 빌드 이벤트와 연결된 속성을 지정합니다.

   - **명령줄** 에서 명령 프롬프트에 지정한 경우와 같이 명령을 지정합니다. 유효한 명령이나 일괄 처리 파일 및 필수 입력이나 출력 파일을 지정합니다. 모든 후속 명령이 실행되도록 보장하려면 일괄 처리 파일의 이름 앞에 **호출** 일괄 처리 명령을 지정합니다.

      여러 입력 및 출력 파일은 MSBuild 매크로를 사용하여 기호로 지정될 수 있습니다. 파일의 위치 또는 파일 집합의 이름을 지정하는 방법에 대한 정보는 [빌드 명령 및 속성에 대한 일반적인 매크로](reference/common-macros-for-build-commands-and-properties.md)를 참조하세요.

      '%' 문자를 MSBuild에서 예약했기 때문에 각 환경 변수를 지정한 경우 각 **%** 이스케이프 문자를 **%25** 16진수 이스케이프 시퀀스로 바꿉니다. 예를 들어 **%WINDIR%** 를 **%25WINDIR%25** 로 바꿉니다. MSBuild는 환경 변수에 액세스하기 전에 각 **%25** 시퀀스를 **%** 문자로 바꿉니다.

   - **설명** 에서 이 이벤트에 대한 설명을 입력합니다. 이 이벤트가 발생할 때 설명은 **출력** 창으로 인쇄됩니다.

   - **빌드에서 제외** 에서 이벤트를 실행하지 않도록 **예** 를 지정합니다.

## <a name="see-also"></a>참조

[사용자 지정 빌드 단계 및 빌드 이벤트 이해](understanding-custom-build-steps-and-build-events.md)<br>
[빌드 명령 및 속성에 대한 일반 매크로](reference/common-macros-for-build-commands-and-properties.md)<br>
[빌드 사용자 지정 문제 해결](troubleshooting-build-customizations.md)
