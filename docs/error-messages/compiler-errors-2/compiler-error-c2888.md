---
description: '자세한 정보: 컴파일러 오류 C2888'
title: 컴파일러 오류 C2888
ms.date: 11/04/2016
f1_keywords:
- C2888
helpviewer_keywords:
- C2888
ms.assetid: 244f593e-ff25-4dad-b31f-84dafa3bc84a
ms.openlocfilehash: f2440b628c2929b850664eb2f7c58148b0562c2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337457"
---
# <a name="compiler-error-c2888"></a>컴파일러 오류 C2888

' identifier ': ' namespace ' 네임 스페이스 내에서 기호를 정의할 수 없습니다.

네임 스페이스에 속하는 기호는를 포함 하는 네임 스페이스에 정의 되어야 합니다.

다음 샘플에서는 C2888를 생성 합니다.

```cpp
// C2888.cpp
// compile with: /c
namespace M {
   namespace N {
      void f1();
      void f2();
   }

   void N::f1() {}   // OK: namspace M encloses N
}

namespace O {
   void M::N::f2() {}   // C2888 namespace O does not enclose M
}
```
