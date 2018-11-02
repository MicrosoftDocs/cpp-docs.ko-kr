---
title: 컴파일러 오류 C2337
ms.date: 11/04/2016
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: 63f18a12ccd1962dd221324f5557c29be89eb04c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637777"
---
# <a name="compiler-error-c2337"></a>컴파일러 오류 C2337

'attribute name': 특성을 찾을 수 없습니다.

이 버전의 Visual C++에서 지원되지 않는 특성을 사용했습니다.

다음 샘플에서는 C2337을 생성합니다.

```
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```