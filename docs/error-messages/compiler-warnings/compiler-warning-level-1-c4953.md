---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4953'
title: 컴파일러 경고(수준 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1f10f757297bd4b0e71ec5246024a3ce7a313689
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327944"
---
# <a name="compiler-warning-level-1-c4953"></a>컴파일러 경고(수준 1) C4953

> 프로필 데이터가 수집 된 이후 '*function*' 인라인 대상 편집 되었습니다. 프로필 데이터가 사용 되지 않습니다.

[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)를 사용하는 경우 컴파일러에서 `/LTCG:PGINSTRUMENT` 이후 다시 컴파일되었으며 편집된 함수(*function*)가 있고 기존 테스트 실행에서 함수가 인라인 후보로 식별된 입력 모듈을 발견했습니다. 그러나 모듈을 다시 컴파일하면 함수가 더 이상 인라인 후보가 아닙니다.

이 경고는 정보 제공용입니다. 이 경고를 해결하려면 `/LTCG:PGINSTRUMENT`를 실행하고 모든 테스트 실행을 다시 수행한 다음 `/LTCG:PGOPTIMIZE`를 실행해야 합니다.

`/LTCG:PGOPTIMIZE` 를 사용한 경우 이 경고는 오류로 대체됩니다.
