---
description: '자세한 정보: 컴파일러 오류 C3634'
title: 컴파일러 오류 C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 21407af8a86a3f82331d0f2a1d424457d8bee833
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239248"
---
# <a name="compiler-error-c3634"></a>컴파일러 오류 C3634

' function ': 관리 되는 또는 WinRTclass의 추상 메서드를 정의할 수 없습니다.

WinRT 또는 관리되는 클래스에서 추상 메서드를 선언할 수 있지만 정의할 수는 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3634 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
