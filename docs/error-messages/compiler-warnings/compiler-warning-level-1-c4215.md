---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4215'
title: 컴파일러 경고(수준 1) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: 4d2e4d170b31c483f216fa85369c05ada38c30d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266561"
---
# <a name="compiler-warning-level-1-c4215"></a>컴파일러 경고(수준 1) C4215

비표준 확장이 사용 됨: long float

기본 Microsoft 확장 (/Ze)은 **long float** 를로 처리 **`double`** 합니다. ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))은 그렇지 않습니다. **`double`** 를 사용 하 여 호환성을 유지 합니다.

다음 샘플에서는 C4215를 생성 합니다.

```cpp
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```
