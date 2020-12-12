---
description: '자세한 정보: 컴파일러 오류 C2063'
title: 컴파일러 오류 C2063
ms.date: 11/04/2016
f1_keywords:
- C2063
helpviewer_keywords:
- C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
ms.openlocfilehash: 18b2cd6bf68144245b85d744923404f4a27d63f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328614"
---
# <a name="compiler-error-c2063"></a>컴파일러 오류 C2063

'identifier': 함수가 아닙니다.

식별자가 함수로 사용되었지만 함수로 선언되지 않았습니다.

다음 샘플에서는 C2063을 생성합니다.

```c
// C2063.c
int main() {
   int i, j;
   j = i();    // C2063, i is not a function
}
```

해결 방법:

```c
// C2063b.c
int i() { return 0;}
int main() {
   int j;
   j = i();
}
```
