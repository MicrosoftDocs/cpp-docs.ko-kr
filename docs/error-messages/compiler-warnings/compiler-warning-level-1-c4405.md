---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4405'
title: 컴파일러 경고(수준 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 53b70ea7d3e55ed23f398c912daeb69827715a58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311086"
---
# <a name="compiler-warning-level-1-c4405"></a>컴파일러 경고(수준 1) C4405

' identifier ': 식별자가 예약어입니다.

인라인 어셈블리에 대해 예약 된 단어가 변수 이름으로 사용 됩니다. 이로 인해 예기치 않은 결과가 발생할 수 있습니다. 이 경고를 해결 하려면 인라인 어셈블리를 위해 예약 된 단어를 사용 하 여 변수 이름을 지정 하지 마십시오. 다음 샘플에서는 C4405를 생성 합니다.

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```
