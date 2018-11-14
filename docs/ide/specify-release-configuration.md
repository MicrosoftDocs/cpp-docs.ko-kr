---
title: 기존 코드에서 새 프로젝트 릴리스 구성
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.releasesettings
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
ms.openlocfilehash: 10dec5e36531c9c0bf549b37bbfa892a624d0bf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511825"
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>기존 코드 파일에서 새 프로젝트 만들기 마법사, 릴리스 구성 설정 지정

기존 코드 파일에서 새 프로젝트 만들기 마법사 페이지를 사용하여 릴리스 구성 프로젝트 설정을 지정합니다.

## <a name="task-list"></a>작업 목록

[방법: 기존 코드로 C++ 프로젝트 만들기](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>UI 요소 목록

- **디버그 구성과 동일**

   마법사가 디버그 구성 프로젝트 설정과 동일한 릴리스 구성 프로젝트 설정을 생성하도록 지정합니다. 기본적으로 이 옵션은 선택되어 있습니다. 이 상자의 선택을 취소하지 않으면 이 페이지의 다른 모든 옵션이 비활성화됩니다.

- **빌드 명령줄**

   새 프로젝트를 빌드하는 명령줄을 지정합니다. 새 프로젝트를 빌드하는 데 사용하려는 모든 스위치 또는 인수에 더해 컴파일러 이름을 입력합니다. 이 옵션은 **외부 빌드 시스템 사용** 옵션을 **프로젝트 설정 지정** 페이지에서 선택할 때 사용할 수 있습니다.

- **다시 빌드 명령줄**

   새 프로젝트를 다시 빌드하는 명령줄을 지정합니다. 이 옵션은 **외부 빌드 시스템 사용** 옵션을 **프로젝트 설정 지정** 페이지에서 선택할 때 사용할 수 있습니다.

- **정리 명령줄**

   새 프로젝트에 대한 빌드 도구에서 생성한 지원 파일을 삭제하도록 명령줄을 지정합니다. 이 옵션은 **외부 빌드 시스템 사용** 옵션을 **프로젝트 설정 지정** 페이지에서 선택할 때 사용할 수 있습니다.

- **출력(디버깅용)**

   새 프로젝트의 디버그 구성에 대한 출력 파일의 디렉터리 경로를 지정합니다. 이 옵션은 **외부 빌드 시스템 사용** 옵션을 **프로젝트 설정 지정** 페이지에서 선택할 때 사용할 수 있습니다.

- **전처리기 정의(/D)**

   새 프로젝트에 대한 전처리기 기호를 정의합니다. 자세한 내용은 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)을 참조하세요.

- **포함 검색 경로(/I)**

   컴파일러가 새 프로젝트에서 전처리기 지시문에 전달된 파일 참조를 확인하기 위해 검색할 디렉터리 목록에 추가할 디렉터리 경로를 지정합니다. 자세한 내용은 [/I(추가 포함 디렉터리)](../build/reference/i-additional-include-directories.md)를 참조하세요.

- **강제 포함 파일(/FI)**

   새 프로젝트를 빌드할 때 처리할 헤더 파일을 지정합니다. 자세한 내용은 [/FI(강제 포함 파일 이름 지정)](../build/reference/fi-name-forced-include-file.md)를 참조하세요.

- **.NET 어셈블리 검색 경로(/AI)**

   컴파일러가 새 프로젝트에서 전처리기 지시문에 전달된 .NET 어셈블리 참조를 확인하기 위해 검색할 디렉터리 경로를 지정합니다. 자세한 내용은 [/AI(메타데이터 디렉터리 지정)](../build/reference/ai-specify-metadata-directories.md)를 참조하세요.

- **강제 사용 .NET 어셈블리(/FU)**

   새 프로젝트를 빌드할 때 처리할 .NET 어셈블리를 지정합니다. 자세한 내용은 [/FU(강제 #using 파일 이름 지정)](../build/reference/fu-name-forced-hash-using-file.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[기존 코드 파일에서 새 프로젝트 만들기 마법사, 프로젝트 설정 지정](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)