---
title: 컴파일러 오류 C2748 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2748
dev_langs:
- C++
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d57c7919cd33f9e27ad34b1298d8af36ec360200
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058070"
---
# <a name="compiler-error-c2748"></a>컴파일러 오류 C2748

관리되는 배열 또는 WinRT 배열 만들기에는 배열 크기 및 배열 이니셜라이저가 있어야 합니다.

관리되는 배열 또는 WinRT 배열의 형식이 잘못되었습니다. 자세한 내용은 [배열](../../windows/arrays-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 C2748 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```