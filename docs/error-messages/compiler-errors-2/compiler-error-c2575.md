---
description: '자세한 정보: 컴파일러 오류 C2575'
title: 컴파일러 오류 C2575
ms.date: 11/04/2016
f1_keywords:
- C2575
helpviewer_keywords:
- C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
ms.openlocfilehash: c08404ec3ce2d260d19b9889b668c0d98db265b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208881"
---
# <a name="compiler-error-c2575"></a>컴파일러 오류 C2575

' identifier ': 멤버 함수와 기본만 virtual 일 수 있습니다.

전역 함수 또는 클래스가 선언 됩니다 **`virtual`** . 이것은 허용되지 않습니다.

다음 샘플에서는 C2575를 생성 합니다.

```cpp
// C2575.cpp
// compile with: /c
virtual void func() {}   // C2575

void func2() {}
struct A {
   virtual void func2(){}
};
```
