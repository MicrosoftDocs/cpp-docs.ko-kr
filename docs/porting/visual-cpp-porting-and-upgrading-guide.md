---
title: Microsoft c + + 포팅 및 업그레이드 가이드
description: Microsoft c + + 코드를 최신 버전의 Visual Studio로 업그레이드 합니다.
ms.date: 09/10/2020
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: b6cd3461ee16a44162fdb641170a2f05d9b77369
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039536"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Microsoft c + + 포팅 및 업그레이드 가이드

이 문서에서는 Microsoft c + + 코드를 최신 버전의 Visual Studio로 업그레이드 하는 방법에 대 한 지침을 제공 합니다. Visual Studio 2010 ~ 2015에서 만든 프로젝트의 경우 Visual Studio 2019에서 프로젝트를 엽니다. 두 단계로 Visual Studio 2008 또는 이전 프로젝트를 업그레이드할 수 있습니다. 먼저 Visual Studio 2010을 사용 하 여 프로젝트를 MSBuild 형식으로 변환 합니다. 그런 다음 Visual Studio 2019에서 프로젝트를 엽니다. 전체 지침은 [이전 버전의 Visual Studio에서 c + + 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)를 참조 하세요.

Visual Studio 2015, Visual Studio 2017 및 Visual Studio 2019의 도구 집합은 이진 호환성이 있습니다. 이제 라이브러리 종속성을 업그레이드 하지 않고도 최신 버전의 컴파일러로 업그레이드할 수 있습니다. 자세한 내용은 [c + + 이진 호환성 2015-2019](binary-compat-2015-2017.md)을 참조 하세요.

오픈 소스 라이브러리를 사용 하거나 여러 플랫폼에서 실행 되는 프로젝트를 업그레이드 하는 경우 CMake 기반 프로젝트로 마이그레이션하는 것이 좋습니다. 자세한 내용은 [Visual Studio의 cmake 프로젝트](../build/cmake-projects-in-visual-studio.md) 를 참조 하세요.

## <a name="reasons-to-upgrade-c-code"></a>C + + 코드를 업그레이드 하는 이유

레거시 응용 프로그램을 안전 하 게 실행 하는 경우 보안 환경에서 개발이 진행 되 고 있지 않은 경우 업그레이드 하는 데 많은 계기가 없을 수 있습니다. 그러나 이러한 경우에는 응용 프로그램에 지속적인 유지 관리가 필요 합니다. 또는 새로운 기능 개발을 수행 하거나 성능이 나 보안을 개선 하 고 있습니다. 업그레이드는 다음과 같은 이점을 제공 합니다.

- 컴파일러 최적화가 향상 되었으므로 동일한 코드를 더 빠르게 실행할 수 있습니다.

- 최신 c + + 기능 및 프로그래밍 사례는 버그의 많은 일반적인 원인을 제거 하 고 이전 C 스타일 관용구 보다 훨씬 더 쉽게 유지 관리할 수 있는 코드를 생성 합니다.

- 컴파일러 및 링커의 성능 향상으로 인해 빌드 시간이 더 빠릅니다.

- 표준 준수가 향상 되었습니다. [/Permissive-](../build/reference/permissive-standards-conformance.md) 컴파일러 옵션을 사용 하면 현재 c + + 표준을 준수 하지 않는 코드를 식별할 수 있습니다. [새 전처리기](../preprocessor/preprocessor-experimental-overview.md) 는 코드 규칙도 지원 합니다.

- 보다 안전한 [C 런타임 라이브러리](../c-runtime-library/security-features-in-the-crt.md) 기능을 포함 하 여 더 나은 런타임 보안. 및은 [가드 검사](../build/reference/guard-enable-guard-checks.md) 및 주소 Sanitizers (Visual Studio 2019 버전 16.4의 새로운 기능)와 같은 컴파일러 기능을 제공 합니다.

## <a name="multitargeting-vs-upgrading"></a>다중 대상 및 업그레이드

코드 베이스를 새 도구 집합으로 업그레이드 하는 것은 사용자에 게 적합 한 옵션이 아닙니다. 최신 Visual Studio를 사용 하 여 이전 도구 집합 및 라이브러리를 사용 하는 프로젝트를 작성 하 고 편집할 수 있습니다. Visual Studio 2019에서는 다음과 같은 기능을 활용할 수 있습니다.

- 소스 코드의 잠재적인 문제를 식별 하는 데 도움이 되는 C++ Core Guidelines 체커 및 Clang를 비롯 한 최신 정적 분석 도구입니다.

- 사용자가 선택한 최신 스타일에 따라 자동 서식 지정을 사용 하면 레거시 코드를 보다 읽기 쉽게 만들 수 있습니다.

자세한 내용은 [Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](use-native-multi-targeting.md)를 참조하세요.

## <a name="in-this-section"></a>단원 내용

|제목|Description|
|-----------|-----------------|
|[이전 버전의 Visual Studio에서 c + + 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|코드 베이스를 Visual Studio 2019로 업그레이드 하 고 컴파일러를 v142 하는 방법입니다.|
|[C++ 코드를 업그레이드하기 위한 IDE 도구](ide-tools-for-upgrading-code.md)|업그레이드 프로세스에 도움이 되는 유용한 IDE 기능입니다.|
|[C++ 이진 호환성 2015-2019](binary-compat-2015-2017.md)|V142 프로젝트에서 v140 및 v141 라이브러리를 그대로 사용 합니다.|
|[Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](use-native-multi-targeting.md)|이전 컴파일러 및 라이브러리와 함께 Visual Studio 2019을 사용 합니다.|
|[Visual C++ 변경 기록 2003 - 2015](visual-cpp-change-history-2003-2015.md)|코드를 변경 해야 할 수 있는 Visual Studio 2003 ~ 2015의 Microsoft c + + 라이브러리 및 빌드 도구의 모든 변경 내용 목록입니다.|
|[Visual C++ 2003~2015의 새로운 기능](visual-cpp-what-s-new-2003-through-2015.md)|Visual Studio 2003에서 Visual Studio 2015까지 Microsoft c + +에 대 한 모든 "새로운 기능" 정보를 제공 합니다.|
|[포팅 및 업그레이드: 예제 및 사례 연구](porting-and-upgrading-examples-and-case-studies.md)|이 섹션에서는 여러 가지 샘플 및 애플리케이션을 포팅 및 업그레이드하고 경험과 결과를 설명했습니다. 이러한 문서를 통해 포팅 및 업그레이드 프로세스와 관련 된 내용을 이해할 수 있습니다. 프로세스 전반에 걸쳐 업그레이드를 위한 팁과 트릭을 설명하고 특정 오류를 수정한 방법을 보여 줍니다.|
|[유니버설 Windows 플랫폼으로 포팅](porting-to-the-universal-windows-platform-cpp.md)|Windows 10으로 코드를 이식하는 방법에 대한 정보를 포함합니다.|
|[UNIX 사용자를 위한 Visual C++ 소개](introduction-to-visual-cpp-for-unix-users.md)|Visual C++를 처음 사용하며 생산성을 높이려는 UNIX 사용자에게 정보를 제공합니다.|
|[Windows에서 Linux 프로그램 실행](porting-from-unix-to-win32.md)|UNIX 애플리케이션을 Windows로 마이그레이션하는 옵션을 설명합니다.|

## <a name="see-also"></a>참고 항목

[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[Visual Studio에서 C++ 컴파일러의 새로운 기능](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)<br/>
