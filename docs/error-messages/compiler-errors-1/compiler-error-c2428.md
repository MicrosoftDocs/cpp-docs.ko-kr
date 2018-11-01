---
title: 컴파일러 오류 C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: 299a4e899a41bf47eec5eaf5b54d2307e557078e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614671"
---
# <a name="compiler-error-c2428"></a>컴파일러 오류 C2428

'operation': 'bool' 형식의 피연산자에 사용할 수 없습니다

형식의 개체에 감소 연산자를 적용할 수 없습니다. `bool`합니다.

다음 샘플에서는 C2428 오류가 생성 됩니다.

```
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```