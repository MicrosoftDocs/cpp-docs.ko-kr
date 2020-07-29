---
title: 컴파일러 오류 C2182
ms.date: 11/04/2016
f1_keywords:
- C2182
helpviewer_keywords:
- C2182
ms.assetid: dfd8d47d-9606-496e-bd96-4bf41ba1f857
ms.openlocfilehash: 0312a1144b3afec52b2041cc25374b691ed97d0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209879"
---
# <a name="compiler-error-c2182"></a>컴파일러 오류 C2182

'identifier': 'void' 형식을 잘못 사용했습니다.

변수가 선언 된 형식입니다 **`void`** .

다음 샘플에서는 C2182를 생성합니다.

```cpp
// C2182.cpp
// compile with: /c
int main() {
   int i = 10;
   void &ir = i;   // C2182 cannot have a reference to type void
   int &ir = i;   // OK
}
```
