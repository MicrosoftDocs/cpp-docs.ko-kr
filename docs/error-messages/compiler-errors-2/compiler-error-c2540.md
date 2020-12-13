---
description: '자세한 정보: 컴파일러 오류 C2540'
title: 컴파일러 오류 C2540
ms.date: 11/04/2016
f1_keywords:
- C2540
helpviewer_keywords:
- C2540
ms.assetid: 92c805a3-2dd9-46ca-a63d-3845c18ecc95
ms.openlocfilehash: 488d18e37080d6bca5c8479a5f3d71b807b39b46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341791"
---
# <a name="compiler-error-c2540"></a>컴파일러 오류 C2540

배열이 바인딩된 비상수 식

배열에는 상수가 바인딩되어야 합니다.

다음 샘플에서는 C2540를 생성 합니다.

```cpp
// C2540.cpp
void func(int n, int pC[]) {
   int i = ((int [n])pC)[1];   // C2540
}

void func2(int n, int pC[]) {
   int i = (pC)[1];   // OK
}

int main() {
   int pC[100];
   func(100, pC);
   func2(100, pC);
}
```
