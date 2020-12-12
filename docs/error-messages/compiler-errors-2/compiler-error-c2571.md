---
description: '자세한 정보: 컴파일러 오류 C2571'
title: 컴파일러 오류 C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 773cab05204e15a22a4412364bd8f89cddfd92ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208972"
---
# <a name="compiler-error-c2571"></a>컴파일러 오류 C2571

' function ': 가상 함수는 ' union ' 공용 구조체에 있을 수 없습니다.

Union은 가상 함수를 사용 하 여 선언 됩니다. 가상 함수는 클래스 또는 구조체 에서만 선언할 수 있습니다.  가능한 해결 방법은 다음과 같습니다.

1. 공용 구조체를 클래스나 구조체로 변경 합니다.

1. 함수를 비가상으로 만듭니다.

다음 샘플에서는 C2571를 생성 합니다.

```cpp
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
