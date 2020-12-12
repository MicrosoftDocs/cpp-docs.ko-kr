---
description: '자세한 정보: 컴파일러 오류 C2863'
title: 컴파일러 오류 C2863
ms.date: 11/04/2016
f1_keywords:
- C2863
helpviewer_keywords:
- C2863
ms.assetid: 32561d67-a795-486b-b3b6-4b90a1acb176
ms.openlocfilehash: d4847d07bceda6fe1a34969cd290a59472135176
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305465"
---
# <a name="compiler-error-c2863"></a>컴파일러 오류 C2863

' interface ': 인터페이스에는 friend를 사용할 수 없습니다.

인터페이스에 대해 friend를 선언할 수 없습니다.

다음 샘플에서는 C2863를 생성 합니다.

```cpp
// C2863.cpp
// compile with: /c
#include <unknwn.h>

class CMyClass {
   void *f();
};

__interface IMyInterface {
   void g();

   friend int h();   // 2863
   friend interface IMyInterface1;  // C2863
   friend void *CMyClass::f();  // C2863
};
```
