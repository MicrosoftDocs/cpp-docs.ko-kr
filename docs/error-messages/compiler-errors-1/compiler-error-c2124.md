---
description: '자세한 정보: 컴파일러 오류 C2124'
title: 컴파일러 오류 C2124
ms.date: 11/04/2016
f1_keywords:
- C2124
helpviewer_keywords:
- C2124
ms.assetid: 93392aaa-5582-4d68-8cc5-bd9c62a0ae7e
ms.openlocfilehash: 3ccfba5dfa45cfe0b190a03b84f8b753caec681c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335205"
---
# <a name="compiler-error-c2124"></a>컴파일러 오류 C2124

0으로 나누기 또는 나머지 연산을 수행했습니다.

상수 식의 분모가 0입니다. 이 오류를 해결하려면 0으로 나누지 마세요.

다음 샘플에서는 C2124를 생성합니다.

```cpp
// C2124.cpp
int main() {
  int i = 1 / 0;   // C2124  do not divide by zero
  int i2 = 12 / 2;   // OK
}
```
