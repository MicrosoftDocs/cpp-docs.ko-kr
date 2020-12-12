---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4097'
title: 컴파일러 경고 (수준 1) C4097
ms.date: 11/04/2016
f1_keywords:
- C4097
helpviewer_keywords:
- C4097
ms.assetid: 2525be51-fac2-43b2-b57c-3bbf1a2268f7
ms.openlocfilehash: 77c9cf9afd3601597418e6151518c6ced4a472c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272276"
---
# <a name="compiler-warning-level-1-c4097"></a>컴파일러 경고 (수준 1) C4097

pragma 매개 변수는 'restore' 또는 'off'이어야 합니다.

Pragma에 잘못된 값이 전달되었습니다.

다음 샘플에서는 C4097을 생성합니다.

```cpp
// C4097.cpp
// compile with: /W1
#pragma runtime_checks("",test)   // C4097
// try the following line instead
// #pragma runtime_checks("",off)

int main() {
}
```
