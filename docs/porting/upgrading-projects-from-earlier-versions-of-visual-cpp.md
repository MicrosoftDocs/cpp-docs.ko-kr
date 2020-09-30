---
title: 이전 버전의 Visual Studio에서 c + + 프로젝트 업그레이드
description: 이전 버전의 Visual Studio에서 Microsoft C++ 프로젝트를 업그레이드하는 방법.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 7a4ab98c196d601bc458fe33bb1e2cb45ac30088
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505889"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>이전 버전의 Visual Studio에서 c + + 프로젝트 업그레이드

이전 버전의 Visual Studio에서 만든 프로젝트를 업그레이드 하려면 최신 버전의 Visual Studio에서 프로젝트를 열어야 합니다. Visual Studio에서는 프로젝트를 현재 스키마로 업그레이드 합니다.

**아니요**를 선택 하면 프로젝트가 업그레이드 되지 않습니다. Visual Studio 2010 이상에서 만든 프로젝트의 경우에도 최신 버전의 Visual Studio에서 프로젝트를 사용할 수 있습니다. 이전 도구 집합을 대상으로 계속 하려면 프로젝트 속성을 설정 하기만 하면 됩니다. 이전 버전의 Visual Studio를 컴퓨터에 두는 경우에는 이후 버전에서 해당 도구 집합을 사용할 수 있습니다. 예를 들어 Windows XP에서 프로젝트를 계속 실행 해야 하는 경우 Visual Studio 2019로 업그레이드할 수 있습니다. 그런 다음 프로젝트 속성에서 v141_xp 또는 이전 버전으로 도구 집합을 지정 합니다. 자세한 내용은 [Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](use-native-multi-targeting.md)를 참조하세요.

**예**를 선택 하면 프로젝트가 원위치에서 업그레이드 됩니다. 이전 버전으로 다시 변환할 수 없습니다. 업그레이드 시나리오에서는 기존 프로젝트 및 솔루션 파일의 백업 복사본을 만드는 것이 좋습니다.

## <a name="upgrade-reports"></a>보고서 업그레이드

프로젝트를 업그레이드 하면 업그레이드 보고서가 표시 됩니다. 또한 보고서는 UpgradeLog.htm으로 프로젝트 폴더에 저장 됩니다. 업그레이드 보고서는 변환 하는 동안 발견 된 문제에 대 한 요약을 표시 합니다. 다음을 포함 하 여 변경 된 내용에 대 한 일부 정보를 나열 합니다.

- 프로젝트 속성입니다.

- 포함 파일.

- 컴파일러 규칙 향상 이나 표준 변경으로 인해 더 이상 컴파일되지 않는 코드입니다.

- 더 이상 사용할 수 없는 Visual Studio 또는 Windows 기능에 의존 하는 코드입니다. 또는 Visual Studio의 기본 설치에 포함 되지 않거나 제품에서 제거 된 헤더 파일입니다.

- 이름이 바뀐 Api, 변경 된 함수 서명 또는 사용 되지 않는 함수와 같은 Api 변경 내용으로 인해 더 이상 컴파일되지 않는 코드입니다.

- 진단 변경 내용으로 인해 더 이상 컴파일되지 않는 코드입니다 (예: 오류가 되는 경고).

- 특히/NODEFAULTLIB를 사용 하는 경우 변경 된 라이브러리로 인해 링커 오류가 발생 합니다.

- 동작 변경으로 인 한 런타임 오류 또는 예기치 않은 결과입니다.

- 도구에 도입 된 오류입니다. 문제가 발견 되 면 일반적인 지원 채널을 통해 또는 [Visual Studio c + + 개발자 커뮤니티](https://developercommunity.visualstudio.com/spaces/62/index.html) 페이지를 사용 하 여 Visual C++ 팀에 보고 합니다.

일부 업그레이드 된 프로젝트 및 솔루션은 수정 없이 성공적으로 빌드할 수 있습니다. 그러나 대부분의 프로젝트에는 프로젝트 설정과 소스 코드를 모두 변경 해야 할 가능성이 있습니다. 이러한 문제를 해결 하는 방법에는 올바른 방법이 없지만 단계적 접근 방식을 사용 하는 것이 좋습니다. 시작 하기 전에 여러 종류의 일반적인 오류에 대 한 자세한 내용은 [잠재적인 업그레이드 문제 개요](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) 를 검토 합니다.

1. 플랫폼 도구 집합, c + + 언어 표준 및 Windows SDK 버전 (해당 하는 경우)을 기본 설정 버전으로 설정 합니다. (**프로젝트**  >  **속성**  >  **구성 속성**  >  **일반**)

1. 오류가 많이 발생 하는 경우 일부 옵션을 수정 하는 동안 일시적으로 해제할 수 있습니다. [/Permissive-](../build/reference/permissive-standards-conformance.md) 옵션을 해제 하려면 **프로젝트**  >  **속성**  >  **구성 속성**  >  **C/c + +**  >  **언어**를 사용 합니다. [코드 분석](../code-quality/code-analysis-for-c-cpp-overview.md) 옵션을 해제 하려면 **프로젝트**  >  **속성**  >  **구성 속성**  >  **코드 분석**을 사용 합니다.

1. 모든 종속성이 있고 포함 경로 또는 라이브러리 위치가 올바른지 확인 하십시오. (**프로젝트**  >  **속성**  >  **구성 속성**  >  **VC + + 디렉터리**)

1. 더 이상 존재 하지 않는 Api에 대 한 참조로 인해 발생 하는 오류를 식별 하 고 해결 합니다.

1. 컴파일을 방해 하는 나머지 오류를 수정 합니다. 일반적인 오류에 대 한 수정에 대 한 [잠재적인 업그레이드 문제 개요](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) 를 참조 하세요.

1. **/Permissive-** 를 다시 설정 하 고 이전에 MSVC에서 컴파일한 비호환 코드로 인 한 새로운 오류를 수정 합니다.

1. 코드 분석을 사용 하 여 더 이상 허용 되지 않는 것으로 간주 되는 잠재적 문제나 오래 된 코딩 패턴을 식별 합니다. 코드 분석에서 많은 오류를 표시 하는 경우 가장 중요 한 경고에 초점을 맞추기 위해 일부 경고를 해제할 수 있습니다. IDE는 일부 종류의 문제를 신속 하 게 해결 하는 데 도움이 될 수 있습니다.

1. 코드를 현대화 하는 다른 기회를 고려 합니다. 예를 들어, 사용자 지정 데이터 구조 및 알고리즘을 c + + 표준 라이브러리 또는 오픈 소스 라이브러리 부스트와 같이 바꿉니다. 표준 기능을 사용 하면 다른 사용자가 코드를 쉽게 유지 관리할 수 있습니다. 표준 위원회 및 광범위 한 c + + 커뮤니티에서 많은 전문가가이 코드를 잘 테스트 하 고 검토 했는지 확신할 수 있습니다.

오류를 수정 하려면 Stack Overflow 또는 [c + + 개발자 커뮤니티](https://developercommunity.visualstudio.com/spaces/62/index.html)에서 질문을 검색 하거나 게시 해 보세요.

## <a name="in-this-section"></a>섹션 내용

[잠재적인 업그레이드 문제 개요](overview-of-potential-upgrade-issues-visual-cpp.md)\
[코드를 유니버설 CRT로 업그레이드](upgrade-your-code-to-the-universal-crt.md)\
[WINVER 및 _WIN32_WINNT 업데이트](modifying-winver-and-win32-winnt.md)\
[라이브러리 내부 구조에 대 한 종속성 수정](fix-your-dependencies-on-library-internals.md)\
[부동 소수점 마이그레이션 문제](floating-point-migration-issues.md)\
[Visual Studio 2019에서 사용 되지 않는 c + + 기능](features-deprecated-in-visual-studio.md)\
[VCBuild 및 MSBuild](build-system-changes.md)\
[타사 라이브러리 포팅](porting-third-party-libraries.md)

## <a name="see-also"></a>참고 항목

[새로워진 Visual Studio의 Visual C++ 기능](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ 변경 기록 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[비표준 동작](../cpp/nonstandard-behavior.md)\
[데이터 애플리케이션 포팅](../data/data-access-programming-mfc-atl.md)
