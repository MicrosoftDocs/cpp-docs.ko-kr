---
title: '참조: vcperf 명령'
description: 명령줄 유틸리티 vcperf.exe에 대한 참조입니다.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c251d93ce7e9e7325a7146f5697150344cb02d96
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508820"
---
# <a name="reference-vcperf-commands"></a>참조: vcperf 명령

::: moniker range="<=vs-2017"

C++ Build Insights 도구는 Visual Studio 2019에서 사용할 수 있습니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range="vs-2019"

이 문서에서는 *vcperf.exe*에서 사용할 수 있는 명령과 사용 방법을 나열하고 설명합니다.

## <a name="commands-to-start-and-stop-traces"></a>추적을 시작 및 중지하는 명령

*중요: 다음 명령에는 모두 관리 권한이 필요합니다.*

| 옵션           | 인수 및 설명 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 지정된 세션 이름에서 추적을 시작하도록 *vcperf.exe*에 지시합니다. 지정된 머신에서 한 번에 하나의 활성 세션만 있을 수 있습니다. <br/><br/> `/nocpusampling` 옵션이 지정되면 *vcperf.exe*에서 CPU 샘플을 수집하지 않습니다. Windows 성능 분석기에서 CPU 사용량(샘플링) 보기를 사용하지 못하도록 하지만 수집된 추적을 더 작게 만듭니다. <br/><br/> 추적이 시작되면 *vcperf.exe*가 즉시 반환됩니다. 머신에서 실행되는 모든 프로세스에 대해 시스템 전체에서 이벤트가 수집됩니다. 즉, *vcperf.exe*를 실행하는 데 사용한 것과 동일한 명령 프롬프트에서 프로젝트를 빌드할 필요가 없습니다. 예를 들어 Visual Studio에서 프로젝트를 빌드할 수 있습니다. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 지정된 세션 이름으로 식별되는 추적을 중지합니다. 추적에서 후처리 단계를 실행하여 WPA(Windows 성능 분석기)에서 볼 수 있는 파일을 생성합니다. 최상의 보기 환경을 위해 C++ Build Insights 추가 기능이 포함된 WPA 버전을 사용합니다. 자세한 내용은 [C++ Build Insights 시작](../get-started-with-cpp-build-insights.md)을 참조하세요. `<outputFile.etl>` 매개 변수는 출력 파일을 저장할 위치를 지정합니다. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 지정된 세션 이름으로 식별되는 추적을 중지하고 지정된 출력 파일에 처리되지 않은 원시 데이터를 씁니다. 결과 파일은 WPA에서 볼 수 없습니다. <br/><br/> `/stop` 명령과 관련된 후처리 단계는 때때로 길어질 수 있습니다. `/stopnoanalyze` 명령을 사용하여 이 후처리 단계를 지연시킬 수 있습니다. Windows 성능 분석기에서 볼 수 있는 파일을 생성할 준비가 되면 `/analyze` 명령을 사용합니다. |

## <a name="miscellaneous-commands"></a>기타 명령

| 옵션     | 인수 및 설명 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | `/stopnoanalyze` 명령으로 생성된 원시 추적 파일을 허용합니다. 이 추적에서 후처리 단계를 실행하여 Windows 성능 분석기에서 볼 수 있는 파일을 생성합니다. 최상의 보기 환경을 위해 C++ Build Insights 추가 기능이 포함된 WPA 버전을 사용합니다. 자세한 내용은 [C++ Build Insights 시작](../get-started-with-cpp-build-insights.md)을 참조하세요. |

## <a name="see-also"></a>참조

[C++ Build Insights 활용 시작](../get-started-with-cpp-build-insights.md)\
[자습서: Windows Performance Analyzer 기본 사항](../tutorials/wpa-basics.md)\
[참조: Windows Performance Analyzer 보기](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
