---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4810'
title: 컴파일러 경고(수준 1) C4810
ms.date: 11/04/2016
f1_keywords:
- C4810
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
ms.openlocfilehash: 4cebcf6b4cabc2539d5fcf25363f573a704ae577
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328093"
---
# <a name="compiler-warning-level-1-c4810"></a>컴파일러 경고(수준 1) C4810

pragma pack(show)의 값 == n

이 경고는 **pack** pragma의 [표시](../../preprocessor/pack.md) 옵션을 사용할 때 발생합니다. *n* 은 현재 팩 값입니다.

예를 들어 다음 코드는 C4810 경고가 pack pragma에서 작동하는 방식을 보여 줍니다.

```cpp
// C4810.cpp
// compile with: /W1 /LD
// C4810 expected
#pragma pack(show)
#pragma pack(4)
#pragma pack(show)
```
