---
description: '자세한 정보: 컴파일러 오류 C2428'
title: 컴파일러 오류 C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: a91819591251e1c291ef8a3291525c0493af20ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190148"
---
# <a name="compiler-error-c2428"></a>컴파일러 오류 C2428

' operation ': ' bool ' 형식의 피연산자에 사용할 수 없습니다.

유형의 개체에 감소 연산자를 적용할 수 없습니다 **`bool`** .

다음 샘플에서는 C2428를 생성 합니다.

```cpp
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```
