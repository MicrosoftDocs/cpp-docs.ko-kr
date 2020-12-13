---
description: '자세한 정보: 컴파일러 오류 C2111'
title: 컴파일러 오류 C2111
ms.date: 11/04/2016
f1_keywords:
- C2111
helpviewer_keywords:
- C2111
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
ms.openlocfilehash: 604e793d787ceabd761d76146108df4b687c1e3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341258"
---
# <a name="compiler-error-c2111"></a>컴파일러 오류 C2111

'+': 포인터 더하기에는 정수 계열 피연산자가 있어야 합니다.

더하기( `+` ) 연산자를 사용하여 포인터에 정수 계열이 아닌 값을 추가하려고 했습니다.

다음 샘플에서는 C2111을 생성합니다.

```cpp
// C2111.cpp
int main() {
   int *a = 0, *pa = 0, b = 0;
   double d = 0.00;

   a = pa + d;   // C2111
   a = pa + b;   // OK
}
```
