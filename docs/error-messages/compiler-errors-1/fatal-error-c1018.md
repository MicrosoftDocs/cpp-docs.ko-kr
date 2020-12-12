---
description: '자세한 정보: 심각한 오류 C1018'
title: 심각한 오류 C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 68b81406916ef358a73112c9f6f8b2370c627e54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316416"
---
# <a name="fatal-error-c1018"></a>심각한 오류 C1018

예기치 않은 #elif입니다.

`#elif` 지시문이 `#if`, `#ifdef`또는 `#ifndef` 구문 외부에 표시됩니다. `#elif` 는 이러한 구문 중 하나 내에서만 사용합니다.

다음 샘플에서는 C1018을 생성합니다.

```cpp
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

해결 방법:

```cpp
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```
