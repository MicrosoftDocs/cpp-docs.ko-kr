---
title: 컴파일러 오류 C2428 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2428
dev_langs:
- C++
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac8b176db26ed615874569a9ed646b9d89ec4db0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097941"
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