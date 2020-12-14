---
description: '자세한 정보: 심각한 오류 C1019'
title: 심각한 오류 C1019
ms.date: 11/04/2016
f1_keywords:
- C1019
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
ms.openlocfilehash: d11a4300b29e497fef2f148d07963997586781ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316390"
---
# <a name="fatal-error-c1019"></a>심각한 오류 C1019

예기치 않은 #else입니다.

`#else` 지시문이 `#if`, `#ifdef`또는 `#ifndef` 구문 외부에 표시됩니다. `#else` 는 이러한 구문 중 하나 내에서만 사용합니다.

다음 샘플에서는 C1019를 생성합니다.

```cpp
// C1019.cpp
#else   // C1019
#endif

int main() {}
```

해결 방법:

```cpp
// C1019b.cpp
#if 1
#else
#endif

int main() {}
```
