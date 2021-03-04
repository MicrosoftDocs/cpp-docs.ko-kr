---
title: C++ 이진 호환성 2015-2019
description: Visual Studio 2015, 2017 및 2019의 컴파일된 c + + 파일 간에 이진 호환성이 작동 하는 방식을 설명 합니다. 하나의 Microsoft Visual C++ 재배포 가능 패키지는 세 가지 버전 모두에 대해 작동 합니다.
ms.date: 02/17/2021
helpviewer_keywords:
- binary compatibility, Visual C++
ms.openlocfilehash: d8c4c0312003496db522e59dba84a9633e94b1b4
ms.sourcegitcommit: 5efc34c2b98d4d0d3e41aec38b213f062c19d078
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844522"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>Visual Studio 2015, 2017 및 2019 간 c + + 이진 호환성

Visual Studio 2013 및 이전 버전의 Microsoft c + + (MSVC) 컴파일러 도구 집합은 주 버전에서 이진 호환성을 보장 하지 않습니다. 이러한 도구 집합의 다른 버전으로 작성 된 개체 파일, 정적 라이브러리, 동적 라이브러리 및 실행 파일은 연결할 수 없습니다. ABIs, 개체 형식 및 런타임 라이브러리가 호환 되지 않습니다.

Visual Studio 2015, 2017 및 2019에서이 동작을 변경 했습니다. 이러한 버전의 컴파일러에서 컴파일된 런타임 라이브러리와 앱은 이진 호환성이 있습니다. 3 가지 버전 모두에 대해 14로 시작 하는 c + + 도구 집합의 주 번호에 반영 됩니다. 도구 집합 버전은 Visual Studio 2015, v141 for 2017 및 v142 for 2019에 대 한 v140입니다. Visual Studio 2015에서 빌드된 타사 라이브러리를 포함 하 고 있다고 가정 합니다. Visual Studio 2017 또는 2019에서 빌드된 응용 프로그램에서 계속 사용할 수 있습니다. 일치 하는 도구 집합을 사용 하 여 다시 컴파일할 필요가 없습니다. 최신 버전의 Microsoft Visual C++ 재배포 가능 패키지 (재배포 가능 패키지)는 모든 항목에 대해 작동 합니다.

## <a name="restrictions-on-binary-compatibility"></a>이진 호환성에 대 한 제한 사항

V140, v141 및 v142 도구 집합과 부 번호 버전 업데이트 간의 이진 호환성에는 세 가지 중요 한 제한이 있습니다.

- 서로 다른 버전의 v140, v141 및 v142 도구 집합으로 빌드된 이진 파일을 혼합할 수 있습니다. 그러나 앱에서 가장 최근 이진으로 가장 최근 버전의 도구 집합을 사용 하 여 연결 해야 합니다. 예제는 다음과 같습니다. 2017 도구 집합을 사용 하 여 컴파일된 앱 (v141, 버전 15.0 ~ 15.9)을 버전 16.2 또는 이후 도구 집합을 사용 하 여 연결 된 경우 v142 (Visual Studio 2019 버전 16.2)를 사용 하 여 컴파일된 정적 라이브러리에 연결할 수 있습니다. 16.4 이상 도구 집합을 사용 하는 경우 버전 16.2 라이브러리를 버전 16.4 앱에 연결할 수 있습니다.

- 앱에서 사용 하는 재배포 가능 패키지에는 비슷한 이진 호환성 제한이 적용 됩니다. 지원 되는 다른 버전의 도구 집합을 기반으로 하는 이진 파일을 혼합할 경우 재배포 가능 버전은 최소한 앱 구성 요소에서 사용 하는 최신 도구 집합과 동일 해야 합니다.

- [ `/GL` (전체 프로그램 최적화)](../build/reference/gl-whole-program-optimization.md) 컴파일러 스위치를 사용 하 여 컴파일된 정적 라이브러리나 개체 파일이 나 [ `/LTCG` (링크 타임 코드 생성)](../build/reference/ltcg-link-time-code-generation.md) 를 사용 하 여 컴파일된 개체 파일은 부 버전 업데이트를 비롯 한 여러 버전에서 이진 호환 *되지 않습니다* . 및를 사용 하 여 컴파일된 모든 개체 파일 및 라이브러리는 **`/GL`** **`/LTCG`** 컴파일 및 최종 링크에 대해 정확히 동일한 도구 집합을 사용 해야 합니다. 예를 들어 **`/GL`** Visual studio 2019 버전 16.7 도구 집합에서를 사용 하 여 빌드한 코드는 **`/GL`** visual studio 2019 버전 16.8 도구 집합에서를 사용 하 여 빌드된 코드에 연결할 수 없습니다. 컴파일러는 [심각한 오류 c 1047](../error-messages/compiler-errors-1/fatal-error-c1047.md)를 내보냅니다.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Visual Studio 2015 또는 2017에서 Visual Studio 2019로 Microsoft Visual C++ 재배포 가능 패키지 업그레이드

Microsoft Visual C++ 재배포 가능 주 버전 번호는 Visual Studio 2015, 2017 및 2019에 대해 동일 하 게 유지 됩니다. 즉, 한 번에 재배포 가능의 인스턴스를 하나만 설치할 수 있습니다. 최신 버전은 이미 설치 된 이전 버전을 덮어씁니다. 예를 들어 하나의 앱이 Visual Studio 2015에서 재배포 가능 패키지를 설치할 수 있습니다. 그런 다음 다른 앱이 Visual Studio 2019에서 재배포 가능 패키지를 설치 합니다. 2019 버전은 이전 버전을 덮어쓰므로 이진 호환 되기 때문에 이전 앱은 여전히 제대로 작동 합니다. 최신 버전의 재배포 가능 패키지에 최신 기능, 보안 업데이트 및 버그 수정이 모두 포함 되어 있는지 확인 합니다. 따라서 항상 사용 가능한 최신 버전으로 업그레이드 하는 것이 좋습니다.

마찬가지로 최신 버전이 이미 설치 되어 있는 경우에는 이전 재배포 가능 패키지를 설치할 수 없습니다. 시도 하는 경우 설치 관리자에서 오류를 보고 합니다. 2019 버전이 이미 설치 된 컴퓨터에 2015 또는 2017 재배포 가능 패키지를 설치 하는 경우 다음과 같은 오류가 표시 됩니다.

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

이 오류는 의도적입니다. 최신 버전을 설치 하는 것이 좋습니다. 설치 관리자가이 오류를 자동으로 복구할 수 있는지 확인 합니다.

## <a name="see-also"></a>참고 항목

[변경 기록 Visual C++](../porting/visual-cpp-change-history-2003-2015.md)\
[지원 되는 최신 Visual C++ 재배포 가능 다운로드](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
