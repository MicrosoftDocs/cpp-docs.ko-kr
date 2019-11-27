---
title: 컴파일러 경고(수준 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541770"
---
# <a name="compiler-warning-level-4-c4234"></a>컴파일러 경고(수준 4) C4234

비표준 확장이 사용 됨: ' keyword ' 키워드는 나중에 사용 하도록 예약 되었습니다.

컴파일러가 사용한 키워드를 아직 구현 하지 않습니다.

이 경고는 자동으로 오류로 승격 됩니다. 이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)를 사용 합니다. 예를 들어 수준 4 경고 문제로 C4234을 만들려면 다음을 수행 합니다.

```cpp
#pragma warning(2:4234)
```

소스 코드 파일에 있습니다.