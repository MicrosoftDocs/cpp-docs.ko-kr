---
description: '자세한 정보: 컴파일러 오류 C3766'
title: 컴파일러 오류 C3766
ms.date: 11/04/2016
f1_keywords:
- C3766
helpviewer_keywords:
- C3766
ms.assetid: b5af2089-2e1e-4e45-a41d-495b6c55656e
ms.openlocfilehash: f410b79cc0cd54f2702effb91e76f0e5e6908521
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291755"
---
# <a name="compiler-error-c3766"></a>컴파일러 오류 C3766

' t r u e '는 ' function ' 인터페이스 메서드의 구현을 제공 해야 합니다.

인터페이스에서 상속 하는 클래스는 인터페이스 멤버를 구현 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3766를 생성 합니다.

```cpp
// C3766.cpp
// compile with: /clr /c

delegate void MyDel();

interface struct IFace {
   virtual event MyDel ^ E;
};

ref struct Class1 : public IFace {};   // C3766

// OK
ref struct Class2 : public IFace {
   virtual event MyDel ^ E {
      void add(MyDel ^) {}
      void remove(MyDel ^) {}
   }
};
```
