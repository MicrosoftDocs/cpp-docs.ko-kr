---
description: '자세한 정보: 빌드 사용자 지정 문제 해결'
title: 빌드 사용자 지정 문제 해결
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: e75dfeb32caf8c9c712c06b9dfb9e71f3e3c29b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277442"
---
# <a name="troubleshooting-build-customizations"></a>빌드 사용자 지정 문제 해결

사용자 지정 빌드 단계 또는 이벤트가 예상대로 작동하지 않는 경우, 무엇이 잘못되었는지 파악하기 위해 몇 가지 방법을 사용할 수 있습니다.

- 사용자 지정 빌드 단계에서 생성하는 파일이 출력으로 선언한 파일과 일치하는지 확인합니다.

- 사용자 지정 빌드 단계에서 다른 빌드 단계(사용자 지정 또는 기타)의 입력 또는 종속 파일을 생성하는 경우, 해당 파일이 프로젝트에 추가되었는지 확인합니다. 그리고 이러한 파일을 사용하는 도구는 사용자 지정 빌드 단계 후에 실행되는지 확인합니다.

- 사용자 지정 빌드 단계에서 실제로 수행되는 작업을 표시하려면 첫 번째 명령으로 `@echo on`을 추가합니다. 빌드 이벤트 및 빌드 단계는 임시 .bat 파일에 저장되고 프로젝트가 빌드될 때 실행됩니다. 따라서 빌드 이벤트 또는 빌드 단계 명령에 오류 검사를 추가할 수 있습니다.

- 중간 파일 디렉터리의 빌드 로그를 검사하여 실제로 실행된 항목을 확인합니다. 빌드 로그의 경로와 이름은 **MSBuild** 매크로 식 **$(IntDir)\\$(MSBuildProjectName).log** 로 표시됩니다.

- 빌드 로그에서 기본 정보보다 많은 정보를 수집하도록 프로젝트 설정을 수정합니다. **도구** 메뉴에서 **옵션** 을 클릭합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션** 노드를 클릭한 다음, **빌드 및 실행** 노드를 클릭합니다. 그런 다음, **MSBuild 프로젝트 빌드 로그 파일의 자세한 정도** 상자에서 **자세히** 를 클릭합니다.

- 사용 중인 파일 이름 또는 디렉터리 매크로의 값을 확인합니다. 매크로를 개별적으로 출력하거나 사용자 지정 빌드 단계의 시작 부분에 `copy %0 command.bat`를 추가하여 사용자 지정 빌드 단계의 명령을 모든 매크로가 확장된 command.bat로 복사할 수 있습니다.

- 사용자 지정 빌드 단계를 실행하고 이벤트를 개별적으로 빌드하여 동작을 확인합니다.

## <a name="see-also"></a>참조

[사용자 지정 빌드 단계 및 빌드 이벤트 이해](understanding-custom-build-steps-and-build-events.md)
