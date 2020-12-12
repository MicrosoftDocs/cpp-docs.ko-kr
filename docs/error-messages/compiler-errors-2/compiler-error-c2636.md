---
description: '자세한 정보: 컴파일러 오류 C2636'
title: 컴파일러 오류 C2636
ms.date: 11/04/2016
f1_keywords:
- C2636
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
ms.openlocfilehash: 789da819b85435bfb54d0f88c6e6c1414f04b6f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208738"
---
# <a name="compiler-error-c2636"></a>컴파일러 오류 C2636

' identifier ': 참조 멤버에 대 한 포인터가 잘못 되었습니다.

참조 멤버에 대 한 포인터가 선언 되었습니다.

다음 샘플에서는 C2636를 생성 합니다.

```cpp
// C2636.cpp
struct S {};
int main() {
   int &S::*prs;   // C2636
   int S::*prs1;   // OK
   int *S::*prs2;   // OK
}
```
