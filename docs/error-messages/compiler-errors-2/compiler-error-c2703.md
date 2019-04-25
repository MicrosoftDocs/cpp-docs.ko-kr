---
title: 컴파일러 오류 C2703
ms.date: 11/04/2016
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 363e3de497a7226a7c1dddd5769a047e6ea53e29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161396"
---
# <a name="compiler-error-c2703"></a>컴파일러 오류 C2703

잘못 된 __leave 문이

A `__leave` 문 내에 있어야 합니다.는 `__try` 블록입니다.

다음 샘플에서는 C2703를 생성합니다.

```
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```