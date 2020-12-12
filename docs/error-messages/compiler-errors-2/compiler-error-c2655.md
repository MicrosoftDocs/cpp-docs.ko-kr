---
description: '자세한 정보: 컴파일러 오류 C2655'
title: 컴파일러 오류 C2655
ms.date: 11/04/2016
f1_keywords:
- C2655
helpviewer_keywords:
- C2655
ms.assetid: beaefa6e-51b3-4df9-9150-960f3fbf40e0
ms.openlocfilehash: 113de213ab53892447666824c48510f7c9654d4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286113"
---
# <a name="compiler-error-c2655"></a>컴파일러 오류 C2655

' identifier ': 현재 범위에서 잘못 된 정의 또는 재선언입니다.

식별자는 전역 범위 에서만 다시 선언할 수 있습니다.

다음 샘플에서는 C2655를 생성 합니다.

```cpp
// C2655.cpp
class A {};
class B {
public:
   static int i;
};

int B::i;  // OK

int main() {
   A B::i;  // C2655
}
```
