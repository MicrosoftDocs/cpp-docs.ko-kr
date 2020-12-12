---
description: '자세한 정보: 컴파일러 오류 C2469'
title: 컴파일러 오류 C2469
ms.date: 11/04/2016
f1_keywords:
- C2469
helpviewer_keywords:
- C2469
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
ms.openlocfilehash: 861b023d4233343458957a0e4ed51c94a9dd4625
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164551"
---
# <a name="compiler-error-c2469"></a>컴파일러 오류 C2469

'operator': 'type' 개체를 할당할 수 없습니다.

연산자에 잘못된 형식이 전달되었습니다.

다음 샘플에서는 C2469를 생성합니다.

```cpp
// C2469.cpp
int main() {
   int *i = new void;   // C2469
   int *i = new int;   // OK
}
```
