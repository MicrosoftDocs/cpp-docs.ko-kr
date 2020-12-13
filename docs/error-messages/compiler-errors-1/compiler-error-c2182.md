---
description: '자세한 정보: 컴파일러 오류 C2182'
title: 컴파일러 오류 C2182
ms.date: 11/04/2016
f1_keywords:
- C2182
helpviewer_keywords:
- C2182
ms.assetid: dfd8d47d-9606-496e-bd96-4bf41ba1f857
ms.openlocfilehash: c8ad265810d287a32b4bffe3aa133c1437420ec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335173"
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
