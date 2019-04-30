---
title: 컴파일러 오류 C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 5ff8b0bee1f79d9534841e4368fd5a5249cbb413
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153400"
---
# <a name="compiler-error-c2267"></a>컴파일러 오류 C2267

'function': 블록 범위가 있는 정적 함수는 사용할 수 없습니다.

로컬 함수를 선언 `static`합니다. 정적 함수는 전역 범위를 가져야 합니다.

다음 샘플에서는 C2267 오류가 생성 됩니다.

```
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```