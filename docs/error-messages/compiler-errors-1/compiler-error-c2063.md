---
title: 컴파일러 오류 C2063
ms.date: 11/04/2016
f1_keywords:
- C2063
helpviewer_keywords:
- C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
ms.openlocfilehash: 5d91dc595798793899eb8ac33e2a6c71cabad02a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444367"
---
# <a name="compiler-error-c2063"></a>컴파일러 오류 C2063

'identifier': 함수가 아닙니다.

식별자가 함수로 사용되었지만 함수로 선언되지 않았습니다.

다음 샘플에서는 C2063을 생성합니다.

```
// C2063.c
int main() {
   int i, j;
   j = i();    // C2063, i is not a function
}
```

해결 방법:

```
// C2063b.c
int i() { return 0;}
int main() {
   int j;
   j = i();
}
```