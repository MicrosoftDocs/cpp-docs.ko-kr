---
title: 컴파일러 경고(수준 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: 246eed6592b892c3bd233d9217e26e7bf7a49ff8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502308"
---
# <a name="compiler-warning-level-3-c4645"></a>컴파일러 경고(수준 3) C4645

__declspec(noreturn)으로 선언된 함수에 return 문이 있습니다.

[Noreturn](../../cpp/noreturn.md) 한정자로 표시 된 함수에 [return](../../cpp/program-termination.md) 문이 있습니다 **`__declspec`** . **`return`** 문이 무시 되었습니다.

다음 샘플에서는 C4645를 생성합니다.

```cpp
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```
