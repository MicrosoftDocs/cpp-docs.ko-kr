---
title: 컴파일러 오류 C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: dc976a0c16d19d1fd2340676e43eb71903163aa5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659059"
---
# <a name="compiler-error-c2627"></a>컴파일러 오류 C2627

'function': 멤버 함수를 익명 공용 구조체에 사용할 수 없습니다

[익명 공용 구조체](../../cpp/unions.md#anonymous_unions) 멤버 함수를 사용할 수 없습니다.

다음 샘플에서는 C2627 오류가 생성 됩니다.

```
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```