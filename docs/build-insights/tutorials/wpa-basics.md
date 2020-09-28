---
title: '자습서: Windows Performance Analyzer 기본 사항'
description: Windows Performance Analyzer에서 기본 작업을 완료하는 방법에 대한 자습서입니다.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 449fc2ddabc2bcf5b9b9f130a5e6816cdf4bc98d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685517"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>자습서: Windows Performance Analyzer 기본 사항

::: moniker range="<=vs-2017"

C++ Build Insights 도구는 Visual Studio 2019에서 사용할 수 있습니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights를 효과적으로 사용하려면 Windows Performance Analyzer(WPA)에 대한 몇 가지 지식이 필요합니다. 이 문서는 일반적인 WPA 작업을 익히는 데 도움이 됩니다. WPA를 사용하는 방법에 대한 자세한 내용은 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) 설명서를 참조하세요.

## <a name="change-the-view-mode"></a>보기 모드 변경

WPA는 추적을 탐색하는 데 사용할 수 있는

- 그래프 모드 및
- 테이블 모드라는 두 가지 기본 보기 모드를 제공합니다.

보기 창의 맨 위에 있는 보기 모드 아이콘을 사용하여 둘 사이를 전환할 수 있습니다.

![그래프 모드와 테이블 모드 간 전환.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>사전 설정 선택

대부분의 C++ Build Insights WPA 보기에는 선택할 수 있는 여러 사전 설정이 있습니다. 보기 창의 맨 위에 있는 드롭다운 메뉴를 사용하여 원하는 사전 설정을 선택할 수 있습니다.

![사전 설정 선택.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>확대/축소

일부 빌드 추적은 매우 커서 세부 정보를 확인하기 어렵습니다. 관심 있는 영역을 확대하려면 그래프를 마우스 오른쪽 단추로 클릭하고 **확대/축소**를 선택합니다. **확대/축소 실행 취소**를 선택하여 언제든지 이전 설정으로 돌아갈 수 있습니다. 이 이미지는 선택 항목과 **확대/축소** 명령을 사용하여 그래프의 일부를 확대하는 예를 보여 줍니다.

![그래프 확대를 보여 주는 짧은 동영상.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>여러 열을 기준으로 그룹화

추적이 표시되는 방식을 사용자 지정할 수 있습니다. 보기 창의 맨 위에 있는 톱니바퀴 아이콘을 클릭하고 빌드 탐색기 보기 편집기에서 열을 다시 정렬합니다. 이 대화 상자에서 노란색 줄 위에 있는 열은 데이터 행이 그룹화되는 기준인 열입니다. 노란색 선 바로 위의 열은 특별하여 그래프 보기에서 색이 지정된 막대에 표시됩니다.

이 이미지는 링크 호출의 예시 막대 그래프를 보여 줍니다. 톱니바퀴 아이콘을 사용하여 빌드 탐색기 보기 편집기 대화 상자를 엽니다. 그런 다음 구성 요소 및 이름 열 항목을 노란색 줄 위로 끕니다. 세부 수준이 높아지고 실제로 링커 내에서 발생한 상황을 확인할 수 있도록 구성이 변경됩니다.

![여러 열을 기준으로 그룹화하는 방법을 보여 주는 짧은 동영상](media/wpa-grouping.gif)

## <a name="see-also"></a>추가 정보

[자습서: vcperf 및 Windows Performance Analyzer](vcperf-and-wpa.md)\
[참조: vcperf 명령](/cpp/build-insights/reference/vcperf-commands)\
[참조: Windows Performance Analyzer 보기](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
