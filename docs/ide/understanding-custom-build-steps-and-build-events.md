---
title: 사용자 지정 빌드 단계 및 빌드 이벤트 이해 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16c1bdf088e0545292a672458c066364b5a47ff4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206297"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>사용자 지정 빌드 단계 및 빌드 이벤트 이해
Visual C++ 개발 환경 내에서 빌드 프로세스를 사용자 지정하는 세 가지 기본 방법은 다음과 같습니다.  
  
 **사용자 지정 빌드 단계**  
 사용자 지정 빌드 단계는 프로젝트와 연결된 빌드 규칙입니다. 사용자 지정 빌드 단계에서는 실행할 명령줄, 추가 입력 또는 출력 파일 및 표시할 메시지를 지정할 수 있습니다. 자세한 내용은 [방법: MSBuild 프로젝트에 사용자 지정 빌드 단계 추가](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)를 참조하세요.  
  
 **사용자 지정 빌드 도구**  
 사용자 지정 빌드 도구는 하나 이상의 파일과 연결된 빌드 규칙입니다. 사용자 지정 빌드 단계에서는 하나 이상의 출력 파일을 생성하는 사용자 지정 빌드 도구에 입력 파일을 전달할 수 있습니다. 예를 들어 MFC 응용 프로그램의 도움말 파일은 사용자 지정 빌드 도구로 작성됩니다. 자세한 내용은 [방법: MSBuild 프로젝트에 사용자 지정 빌드 도구 추가](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) 및 [사용자 지정 빌드 도구 지정](../ide/specifying-custom-build-tools.md)을 참조하세요.  
  
 **빌드 이벤트**  
 빌드 이벤트를 사용하면 프로젝트의 빌드를 사용자 지정할 수 있습니다. 빌드 이벤트에는 *빌드 전*, *링크 전* 및 *빌드 후*의 세 가지 방법이 있습니다. 빌드 이벤트를 사용하면 빌드 프로세스의 특정 시간에 수행할 작업을 지정할 수 있습니다. 예를 들어 빌드 이벤트를 사용하여 프로젝트 빌드가 완료된 후 **regsvr32.exe**로 파일을 등록할 수 있습니다. 자세한 내용은 [빌드 이벤트 지정](../ide/specifying-build-events.md)을 참조하세요.  
  
 [빌드 사용자 지정 문제 해결](../ide/troubleshooting-build-customizations.md)은 사용자 지정 빌드 단계 및 빌드 이벤트가 예상대로 실행되도록 합니다.  
  
 사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식도 도구의 유용성을 향상시킬 수 있습니다. 자세한 내용은 [사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식 지정](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md)을 참조하세요.  
  
 빌드 이벤트 및 사용자 지정 빌드 단계는 다른 빌드 단계와 함께 다음 순서로 실행됩니다.  
  
1.  빌드 전 이벤트  
  
2.  개별 파일에 대한 사용자 지정 빌드 도구  
  
3.  MIDL  
  
4.  리소스 컴파일러  
  
5.  C/C++ 컴파일러  
  
6.  링크 전 이벤트  
  
7.  링커 또는 라이브러리 관리자(해당하는 경우)  
  
8.  매니페스트 도구  
  
9. BSCMake  
  
10. 프로젝트의 사용자 지정 빌드 단계  
  
11. 빌드 후 이벤트  
  
 다른 모든 빌드 프로세스가 완료된 후 `custom build step on the project` 및 `post-build event`가 순차적으로 실행됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 C++ 프로젝트 빌드](../ide/building-cpp-projects-in-visual-studio.md)   
 [빌드 명령 및 속성에 대한 일반 매크로](../ide/common-macros-for-build-commands-and-properties.md)   
 [도구 빌드 순서 대화 상자](https://msdn.microsoft.com/6204c5b1-7ce9-4948-9ff6-0268642ee14c)