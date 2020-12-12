---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4339'
title: 컴파일러 경고(수준 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: e05a7a73ac0cbbf056e5e30db0989e7fe933d01e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294524"
---
# <a name="compiler-warning-level-4-c4339"></a>컴파일러 경고(수준 4) C4339

'type' : WinRT 또는 CLR 메타데이터에 정의되지 않은 형식이 사용되었습니다. 이 형식을 사용하면 런타임 예외가 발생할 수 있습니다.

Windows 런타임 또는 공용 언어 런타임에 대해 컴파일된 코드에서 형식이 정의되지 않았습니다. 가능한 런타임 예외가 발생하지 않도록 형식을 정의합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4339 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```
