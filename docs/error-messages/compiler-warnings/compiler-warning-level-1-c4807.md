---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4807'
title: 컴파일러 경고(수준 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 4c015d2ee7c566199411374402719c4a8eaee37f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238143"
---
# <a name="compiler-warning-level-1-c4807"></a>컴파일러 경고(수준 1) C4807

'operation': 'type' 형식과 'type' 형식의 부호 있는 비트 필드를 함께 사용하는 것은 안전하지 않습니다.

이 경고는 1 비트 부호 있는 비트 필드를 변수와 비교할 때 생성 됩니다 **`bool`** . 1 비트 부호 있는 비트 필드에는-1 또는 0 값만 포함할 수 있으므로과 비교 하는 것은 위험 **`bool`** 합니다. **`bool`** 과는 동일 하 **`bool`** 고 0 또는 1만 포함할 수 있으므로 혼합 및 1 비트 부호 없는 비트 필드에 대 한 경고가 생성 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4807을 생성합니다.

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
