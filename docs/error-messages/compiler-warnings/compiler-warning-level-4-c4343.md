---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4343'
title: 컴파일러 경고(수준 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: 906dee40eb0e9ef55c67657e93f42a6e2279a9d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294498"
---
# <a name="compiler-warning-level-4-c4343"></a>컴파일러 경고(수준 4) C4343

\#pragma optimize ("g", off)는/Og 옵션을 재정의 합니다.

이 경고는 IPF(Itanium Processor Family) 컴파일러에서만 사용되며 pragma [optimize](../../preprocessor/optimize.md) 가 [/Og](../../build/reference/og-global-optimizations.md) 컴파일러 옵션을 재정의했음을 보고합니다.

다음 샘플에서는 C4343을 생성합니다.

```cpp
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```
