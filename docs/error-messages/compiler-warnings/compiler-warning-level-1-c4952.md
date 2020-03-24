---
title: 컴파일러 경고(수준 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: 560705edeb0bbdd6be760736a8d4a19d914133d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174572"
---
# <a name="compiler-warning-level-1-c4952"></a>컴파일러 경고(수준 1) C4952

> '*function*': 프로그램 데이터베이스 '*pgd_file*'에 프로필 데이터가 없습니다.

[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)를 사용할 때 컴파일러에서 `/LTCG:PGINSTRUMENT` 이후 다시 컴파일된 입력 모듈을 검색했습니다. 이 모듈에는 새 함수(*function*)가 있습니다.

이 경고는 정보 제공용입니다. 이 경고를 해결하려면 `/LTCG:PGINSTRUMENT`를 실행하고 모든 테스트 실행을 다시 수행한 다음 `/LTCG:PGOPTIMIZE`를 실행해야 합니다.

`/LTCG:PGOPTIMIZE` 를 사용한 경우 이 경고는 오류로 대체됩니다.
