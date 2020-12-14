---
description: '자세한 정보: 심각한 오류 C1022'
title: 심각한 오류 C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: cd608aded29b4f3ebf329586ebc03ce2e325c970
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249765"
---
# <a name="fatal-error-c1022"></a>심각한 오류 C1022

#endif가 필요합니다.

`#if`, `#ifdef`또는 `#ifndef` 지시문에 일치하는 `#endif` 지시문이 없습니다. 각 `#if`, `#ifdef`또는 `#ifndef` 에 일치하는 `#endif`가 있어야 합니다.

다음 샘플에서는 C1022를 생성합니다.

```cpp
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

해결 방법:

```cpp
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```
