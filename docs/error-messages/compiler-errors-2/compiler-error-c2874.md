---
title: 컴파일러 오류 C2874
ms.date: 11/04/2016
f1_keywords:
- C2874
helpviewer_keywords:
- C2874
ms.assetid: b54fa9d8-8df5-40d9-9b3b-aa3e9dd6a3be
ms.openlocfilehash: 04cbce14fc1fcb1d5bbb07c7f847c479988224a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514779"
---
# <a name="compiler-error-c2874"></a>컴파일러 오류 C2874

using 선언 하면 'symbol'의 여러 선언

선언 하면 동일한 항목을 두 번 정의 됩니다.

다음 샘플에서는 C2874 오류가 생성 됩니다.

```
// C2874.cpp
namespace Z {
   int i;
}

int main() {
   int i;
   using Z::i;   // C2874, i already declared
}
```