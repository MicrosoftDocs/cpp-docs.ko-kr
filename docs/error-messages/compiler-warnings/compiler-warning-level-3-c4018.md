---
title: 컴파일러 경고 (수준 3) C4018
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: e136a82f8a0ecb3f5375d3a486dd017df7edb6e0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051976"
---
# <a name="compiler-warning-level-3-c4018"></a>컴파일러 경고 (수준 3) C4018

' expression ': signed/unsigned가 일치 하지 않습니다.

부호 있는 숫자와 부호 없는 숫자를 비교 하려면 컴파일러가 부호 있는 값을 unsigned로 변환 해야 합니다.

서명 및 서명 되지 않은 형식을 테스트할 때 두 가지 형식 중 하나를 캐스팅 하는 경우이 경고를 해결할 수 있습니다.

다음 샘플에서는 C4018를 생성 합니다.

```cpp
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```