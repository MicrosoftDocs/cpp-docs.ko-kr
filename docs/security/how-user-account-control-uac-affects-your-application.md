---
description: '자세히 알아보기: UAC (사용자 계정 컨트롤)가 응용 프로그램에 미치는 영향'
title: UAC(사용자 계정 컨트롤)가 애플리케이션에 주는 영향
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 64196e0cac0a5b4edcf0b24fd95df2e5291ec45a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320068"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>UAC(사용자 계정 컨트롤)가 애플리케이션에 주는 영향

UAC(사용자 계정 컨트롤)는 사용자 계정의 권한을 제한하는 Windows Vista의 기능입니다. UAC에 대한 자세한 정보는 다음 사이트에서 찾아볼 수 있습니다.

- [최소 권한의 환경에서 응용 프로그램에 대 한 개발자 모범 사례 및 지침](/windows/win32/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>UAC를 사용하도록 설정한 후에 프로젝트 빌드

UAC를 사용 하지 않도록 설정 된 Windows Vista에서 Visual Studio c + + 프로젝트를 빌드하고 나중에 UAC를 사용 하도록 설정 하는 경우 제대로 작동 하려면 프로젝트를 정리 하 고 다시 빌드해야 합니다.

## <a name="applications-that-require-administrative-privileges"></a>관리 권한이 필요한 애플리케이션

기본적으로 Visual C++ 링커는 실행 수준이 인 응용 프로그램의 매니페스트에 UAC 조각을 포함 합니다 `asInvoker` . 관리 권한이 있어야 애플리케이션이 제대로 실행되는 경우(예: 레지스트리의 HKLM 노드를 수정하거나 Windows 디렉터리와 같은 디스크의 보호된 영역에 쓰는 경우) 애플리케이션을 수정해야 합니다.

첫 번째 옵션은 실행 수준을 *requireAdministrator* 로 변경 하도록 매니페스트의 UAC 조각을 수정 하는 것입니다. 그러면 애플리케이션이 실행되기 전에 사용자에게 관리자 자격 증명을 요구합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [/MANIFESTUAC (매니페스트에 UAC 정보 포함)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md)를 참조 하세요.

두 번째 옵션은 `/MANIFESTUAC:NO` 링커 옵션을 지정하여 UAC 조각을 매니페스트에 포함하지 않는 것입니다. 이 경우에는 애플리케이션이 가상화되어 실행됩니다. 레지스트리 또는 파일 시스템의 변경 사항은 애플리케이션이 종료된 후에 유지되지 않습니다.

다음 순서도는 UAC의 사용 여부와 애플리케이션에 UAC 매니페스트가 있는지 여부에 따라 애플리케이션이 어떻게 실행되는지를 설명합니다.

![Windows 로더 동작](media/uacflowchart.png "Windows 로더 동작")

## <a name="see-also"></a>참고 항목

[보안 모범 사례](security-best-practices-for-cpp.md)
