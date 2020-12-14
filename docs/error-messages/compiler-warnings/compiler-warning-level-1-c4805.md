---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4805'
title: 컴파일러 경고(수준 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: c63b117e20e6e4aef650ac07ba0475060cc37d0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238260"
---
# <a name="compiler-warning-level-1-c4805"></a>컴파일러 경고(수준 1) C4805

'operation': 연산에 'type' 형식과 'type' 형식을 함께 사용하는 것은 안전하지 않습니다.

이 경고는 [bool](../../cpp/bool-cpp.md) 과 [int](../../c-language/integer-types.md)간의 비교 작업에 대해 생성 됩니다. 다음 샘플에서는 C4805를 생성 합니다.

```cpp
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```
