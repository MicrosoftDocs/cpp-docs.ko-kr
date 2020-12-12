---
description: '자세한 정보: 컴파일러 오류 C2583'
title: 컴파일러 오류 C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: 067e65f6085d033ca8d7372ee5e4d169e1b411dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177694"
---
# <a name="compiler-error-c2583"></a>컴파일러 오류 C2583

' identifier ': ' const/volatile ' ' this ' 포인터는 생성자/소멸자에 사용할 수 없습니다.

생성자 또는 소멸자가 또는로 선언 되었습니다 **`const`** **`volatile`** . 이것은 허용되지 않습니다.

다음 샘플에서는 C2583를 생성 합니다.

```cpp
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```
