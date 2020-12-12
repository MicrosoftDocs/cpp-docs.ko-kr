---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4558'
title: 컴파일러 경고(수준 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: b35f127daad10d0346a8adc30e712d6de56d5805
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173677"
---
# <a name="compiler-warning-level-1-c4558"></a>컴파일러 경고(수준 1) C4558

' value ' 피연산자의 값이 ' lowerbound-상한값 ' 범위를 벗어났습니다.

어셈블리 언어 명령에 전달 된 값이 매개 변수에 지정 된 범위를 벗어났습니다. 값이 잘립니다.

다음 샘플에서는 C4558를 생성 합니다.

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```
