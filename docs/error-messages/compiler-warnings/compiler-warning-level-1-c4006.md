---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4006'
title: 컴파일러 경고(수준 1) C4006
ms.date: 11/04/2016
f1_keywords:
- C4006
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
ms.openlocfilehash: 1d0b38e2ac3d224f26a0a52ac2d7f2343a1f955d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335984"
---
# <a name="compiler-warning-level-1-c4006"></a>컴파일러 경고(수준 1) C4006

\#undef에 식별자가 필요 합니다.

`#undef` 지시문에서 정의 해제할 식별자를 지정하지 않았습니다. 지시문이 무시됩니다. 이 경고를 해결하려면 식별자를 지정해야 합니다. 다음 샘플에서는 C4006을 생성합니다.

```cpp
// C4006.cpp
// compile with: /W1
#undef   // C4006

// try..
// #undef TEST

int main() {
}
```
