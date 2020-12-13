---
description: '자세한 정보: 컴파일러 오류 C2886'
title: 컴파일러 오류 C2886
ms.date: 11/04/2016
f1_keywords:
- C2886
helpviewer_keywords:
- C2886
ms.assetid: c01588a1-484c-4dc9-a3f1-f900c6e44543
ms.openlocfilehash: 0a2591a18fc7113b77f90e689860906d35fa9460
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337468"
---
# <a name="compiler-error-c2886"></a>컴파일러 오류 C2886

' class:: identifier ':-선언을 사용 하 여 기호를 멤버에 사용할 수 없습니다.

선언에는 **`using`** 네임 스페이스 이름과 같은 기호가 사용 됩니다. **`using`** 선언은 기본 클래스 멤버를 선언 하는 데 사용할 수 있습니다.

다음 샘플에서는 C2886를 생성 합니다.

```cpp
// C2886.cpp
// compile with: /c
namespace Z {
    int i;
}

class B {
protected:
    int i;
};

class D : public B {
    // Error: Z is a namespace
    using Z::i;   // C2886

    // OK: B is a base class
    using B::i;
};
```
