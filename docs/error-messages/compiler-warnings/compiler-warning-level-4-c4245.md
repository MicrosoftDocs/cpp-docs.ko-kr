---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4245'
title: 컴파일러 경고(수준 4) C4245
ms.date: 11/04/2016
f1_keywords:
- C4245
helpviewer_keywords:
- C4245
ms.assetid: 85083d53-9cc2-4d12-b58c-6dad28f15cbe
ms.openlocfilehash: 8e75c82ca775881d3ac2771a19f0f68b789e1940
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341700"
---
# <a name="compiler-warning-level-4-c4245"></a>컴파일러 경고(수준 4) C4245

> '*conversion*': '*type1*'에서 '*type2*' (으)로의 변환, 부호 있는/부호 없는 불일치

**`signed const`** 음수 값을 가진 형식을 형식으로 변환 하려고 했습니다 **`unsigned`** .

다음 샘플에서는 C4245를 생성 합니다.

```cpp
// C4245.cpp
// compile with: /W4 /c
const int i = -1;
unsigned int j = i; // C4245

const int k = 1;
unsigned int l = k; // okay

int m = -1;
unsigned int n = m; // okay

void Test(size_t i) {}

int main() {
   Test( -19 );   // C4245
}
```
