---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4486'
title: 컴파일러 경고(수준 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: e664c9654b41932ab81c596494953807b8bb5d13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212443"
---
# <a name="compiler-warning-level-1-c4486"></a>컴파일러 경고(수준 1) C4486

' function ': ref 클래스 또는 값 클래스의 전용 가상 메서드는 ' sealed '로 표시 되어야 합니다.

관리 되는 클래스 또는 구조체의 전용 가상 멤버 함수는 액세스 하거나 재정의할 수 없으므로 [sealed](../../extensions/sealed-cpp-component-extensions.md)로 표시 되어야 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C4486를 생성 합니다.

```cpp
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

다음 샘플에서는 전용 sealed 가상 함수를 사용 하는 한 가지 방법을 보여 줍니다.

```cpp
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```
