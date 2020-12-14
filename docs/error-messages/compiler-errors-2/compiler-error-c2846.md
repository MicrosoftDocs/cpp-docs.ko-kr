---
description: '자세한 정보: 컴파일러 오류 C2846'
title: 컴파일러 오류 C2846
ms.date: 11/04/2016
f1_keywords:
- C2846
helpviewer_keywords:
- C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
ms.openlocfilehash: ecd6d480bdd485e3c623da8563c7f0eefe8e70c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260230"
---
# <a name="compiler-error-c2846"></a>컴파일러 오류 C2846

' constructor ': 인터페이스에는 생성자를 사용할 수 없습니다.

Visual C++ [인터페이스](../../cpp/interface.md) 에는 생성자를 사용할 수 없습니다.

다음 샘플에서는 C2846를 생성 합니다.

```cpp
// C2846.cpp
// compile with: /c
__interface C {
   C();   // C2846 constructor not allowed in an interface
};
```
