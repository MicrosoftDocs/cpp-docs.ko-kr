---
title: C++ Build Insights 활용 시작
description: 대략적인 C++ Build Insights 개요입니다.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4ebbb280a5cccaa35b5efc7f90e9b570600c47b
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923641"
---
# <a name="get-started-with-c-build-insights"></a>C++ Build Insights 활용 시작

::: moniker range="<=msvc-150"

C++ Build Insights 도구는 Visual Studio 2019에서 사용할 수 있습니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range="msvc-160"

C++ Build Insights는 MSVC(Microsoft Visual C++) 도구 체인에 대한 향상된 가시성을 제공하는 도구 모음입니다. 이 도구는 C++ 빌드에 대한 데이터를 수집하여 다음과 같은 일반적인 질문에 답하는 데 도움이 되는 형식으로 표시합니다.

- 빌드가 충분히 병렬화되어 있나요?
- 미리 컴파일된 헤더(PCH)에 무엇을 포함해야 하나요?
- 빌드 속도를 높이기 위해 집중해야 하는 특정 병목 현상이 있나요?

이 기술의 주요 구성 요소는 다음과 같습니다.

- 빌드에 대한 추적을 수집하는 데 사용할 수 있는 명령줄 유틸리티인 *vcperf.exe*
- WPA(Windows Performance Analyzer)에서 빌드 추적을 볼 수 있는 WPA 확장
- C++ Build Insights 데이터를 사용하는 자체 도구 생성을 위한 소프트웨어 개발 도구인 C++ Build Insights SDK

## <a name="documentation-sections"></a>설명서 섹션

[자습서: vcperf 및 Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
C++ 프로젝트의 빌드 추적을 수집하고 WPA에서 보는 방법을 알아봅니다.

[자습서: Windows 성능 기본 사항](tutorials/wpa-basics.md)\
빌드 추적을 분석하는 데 유용한 WPA 팁을 검색합니다.

[C++ Build Insights SDK](reference/sdk/overview.md)\
C++ Build Insights SDK의 개요입니다.

## <a name="articles"></a>문서

C++ Build Insights에 대한 자세한 내용은 공식 팀 블로그의 다음 문서를 참조하세요.

[C++ Build Insights 소개](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[C++ Build Insights SDK를 사용하여 프로그래밍 방식으로 빌드 분석](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[C++ Build Insights를 사용하여 빌드 병목 상태 찾기](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[C++ Build Insights에서 PCH 제안을 사용하여 더 빠른 빌드](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end
