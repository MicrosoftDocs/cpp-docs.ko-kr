---
description: '자세한 정보: 컴파일러 오류 C3828'
title: 컴파일러 오류 C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 90c731ffc636355b5c9a1963facbcccabf356700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249323"
---
# <a name="compiler-error-c3828"></a>컴파일러 오류 C3828

' object type ': 관리 되는 또는 WinRTclasses의 인스턴스를 만드는 동안에는 배치 인수를 사용할 수 없습니다.

관리 되는 형식 또는 Windows 런타임 형식의 개체를 만들 때 operator [new, gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) 또는 [new](../../cpp/new-operator-cpp.md)연산자의 배치 형태를 사용할 수 없습니다.

다음 샘플에서는 C3828 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```
