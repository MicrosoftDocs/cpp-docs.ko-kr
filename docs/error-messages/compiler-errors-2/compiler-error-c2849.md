---
description: '자세한 정보: 컴파일러 오류 C2849'
title: 컴파일러 오류 C2849
ms.date: 11/04/2016
f1_keywords:
- C2849
helpviewer_keywords:
- C2849
ms.assetid: e28f6b3e-e0e7-4f92-b006-ebaa81d368e6
ms.openlocfilehash: 890d8e9d257e1efc20058f0e2f47ccf04ea3217b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260191"
---
# <a name="compiler-error-c2849"></a>컴파일러 오류 C2849

' 소멸자 ': 인터페이스에는 소멸자를 사용할 수 없습니다.

Visual C++ [인터페이스](../../cpp/interface.md) 에는 소멸자를 사용할 수 없습니다.

다음 샘플에서는 C2849를 생성 합니다.

```cpp
// C2849.cpp
// compile with: /c
__interface C {
   ~C();   // C2849 destructor not allowed in an interface
};
```
