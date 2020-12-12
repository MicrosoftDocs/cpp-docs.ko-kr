---
description: '자세한 정보: 컴파일러 오류 C2070'
title: 컴파일러 오류 C2070
ms.date: 11/04/2016
f1_keywords:
- C2070
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
ms.openlocfilehash: b56b59a1aa9df1b653fd7f023c7db5fc6bcd9a41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213147"
---
# <a name="compiler-error-c2070"></a>컴파일러 오류 C2070

' type ': sizeof 피연산자가 잘못 되었습니다.

[Sizeof](../../cpp/sizeof-operator.md) 연산자에는 식 또는 형식 이름이 필요 합니다.

다음 샘플에서는 C2070를 생성 합니다.

```cpp
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

해결 방법:

```cpp
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```
