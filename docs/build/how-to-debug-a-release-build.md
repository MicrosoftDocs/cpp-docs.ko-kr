---
description: '자세한 정보: 방법: 릴리스 빌드 디버그'
title: '방법: 릴리스 빌드 디버그'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: bbe70a534a9d953ea1b739dba3a32296c7893930
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162705"
---
# <a name="how-to-debug-a-release-build"></a>방법: 릴리스 빌드 디버그

애플리케이션의 릴리스 빌드를 디버그할 수 있습니다.

### <a name="to-debug-a-release-build"></a>릴리스 빌드를 디버그하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](working-with-project-properties.md)을 참조합니다.

1. **C/C++** 노드를 클릭합니다. **디버그 정보 형식** 을 [C7 호환(/Z7)](reference/z7-zi-zi-debug-information-format.md) 또는 **프로그램 데이터베이스(/Zi)** 로 설정합니다.

1. **링커** 를 확장하 고 **일반** 노드를 클릭합니다. **증분 링크 사용** 을 [아니요(/INCREMENTAL:NO)](reference/incremental-link-incrementally.md)로 설정합니다.

1. **디버깅** 노드를 선택합니다. **디버그 정보 생성** 을 [예(/DEBUG)](reference/debug-generate-debug-info.md)로 설정합니다.

1. **최적화** 노드를 선택합니다. **참조** 를 [/OPT:REF](reference/opt-optimizations.md)로, **COMDAT 정리 사용** 을 [/OPT:ICF](reference/opt-optimizations.md)로 설정합니다.

1. 이제 릴리스 빌드 애플리케이션을 디버그할 수 있습니다. 문제를 찾으려면 코드를 단계별로 실행하거나 Just-In-Time 디버깅을 사용하여 오류가 발생한 위치를 찾은 다음 잘못된 매개 변수 또는 코드를 확인합니다.

   애플리케이션이 디버그 빌드에서 작동하지만 릴리스 빌드에서는 실패하는 경우 컴파일러 최적화 중 하나에서 소스 코드의 결함을 노출할 수 있습니다. 문제를 격리하려면 문제를 일으키는 파일 및 최적화를 찾을 때까지 각 소스 코드 파일에 대해 선택한 최적화를 사용하지 않도록 설정합니다. (프로세스를 신속하게 진행하려면 파일을 두 그룹으로 나누어 한 그룹에서 최적화를 사용하지 않도록 설정하고 그룹에서 문제를 찾으면 문제 파일을 격리할 때까지 계속 분할할 수 있습니다.)

   [/RTC](reference/rtc-run-time-error-checks.md)를 사용하여 디버그 빌드에서 버그를 노출해 볼 수 있습니다.

   자세한 내용은 [Optimizing Your Code](optimizing-your-code.md)(코드 최적화)를 참조하세요.

## <a name="see-also"></a>참조

[릴리스 빌드 문제 해결](fixing-release-build-problems.md)
