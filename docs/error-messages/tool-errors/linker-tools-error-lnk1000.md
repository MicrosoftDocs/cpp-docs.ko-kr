---
title: 링커 도구 오류 LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 8e53dc898addb4adeec63027c358b42a6a836b50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501727"
---
# <a name="linker-tools-error-lnk1000"></a>링커 도구 오류 LNK1000

> 알 수 없는 오류입니다. 기술 지원 옵션에 대 한 설명서를 참조 하세요.

오류 상황을 파악 하는 시도 문제를 파악 하 여 재현 가능한 테스트 사례를 만듭니다. 조사 하 고 이러한 오류를 보고 하는 방법에 대 한 자세한 내용은 [Visual c + + 도구 집합 또는 문서를 사용 하 여 문제를 보고 하는 방법을](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)합니다.

표준 헤더 파일 (예를 들어, Windows.h) 및 고유한 파일을 혼합 하면이 오류가 발생할 수 있습니다. 모든, 가장 먼저 다음 표준 헤더를 헤더 파일을 직접 오는 경우 미리 컴파일된 헤더를 포함 합니다.