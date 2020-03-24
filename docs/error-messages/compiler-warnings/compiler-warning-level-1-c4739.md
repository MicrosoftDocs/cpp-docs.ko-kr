---
title: 컴파일러 경고(수준 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 9c68a9e0a2873de7e919fafbef68835f0970c03b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185700"
---
# <a name="compiler-warning-level-1-c4739"></a>컴파일러 경고(수준 1) C4739

'var' 변수에 대한 참조가 스토리지 공간을 초과합니다.

값이 변수에 할당되었지만 해당 값이 변수의 크기보다 큽니다. 메모리가 변수의 메모리 위치를 벗어나서 기록되기 때문에 데이터가 손실될 수 있습니다.

이 경고를 해결하려면 변수 크기 안에 들어갈 수 있는 값만 변수에 할당합니다.

다음 샘플에서는 C4739를 생성합니다.

```cpp
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```
