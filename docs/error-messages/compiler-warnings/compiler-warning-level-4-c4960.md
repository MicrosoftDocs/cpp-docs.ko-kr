---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4960'
title: 컴파일러 경고(수준 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 9a1e3d5390ffa4ffad101d1ea2c3164c04d12ca8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234581"
---
# <a name="compiler-warning-level-4-c4960"></a>컴파일러 경고(수준 4) C4960

'function'이 너무 커서 프로파일링할 수 없습니다.

[/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)를 사용하는 경우 컴파일러에서 65,535개 명령보다 큰 함수를 포함하는 입력 모듈을 발견했습니다. 이렇게 큰 함수는 프로필 기반 최적화에 사용할 수 없습니다.

이 경고를 해결하려면 함수 크기를 줄입니다.
