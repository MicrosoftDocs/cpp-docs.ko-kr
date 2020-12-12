---
description: '자세한 정보: 컴파일러 오류 C2106'
title: 컴파일러 오류 C2106
ms.date: 11/04/2016
f1_keywords:
- C2106
helpviewer_keywords:
- C2106
ms.assetid: d5c91a2e-04e4-4770-8478-788b98c52a53
ms.openlocfilehash: edcd926763fc76fba0329ccc22b4d263b5042f4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170154"
---
# <a name="compiler-error-c2106"></a>컴파일러 오류 C2106

' operator ': 왼쪽 피연산자는 l-value 여야 합니다.

연산자의 왼쪽 피연산자로 l-value가 있어야 합니다.

다음 샘플에서는 C2106를 생성 합니다.

```cpp
// C2106.cpp
int main() {
   int a;
   1 = a;   // C2106
   a = 1;   // OK
}
```
