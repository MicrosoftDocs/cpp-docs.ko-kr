---
title: 컴파일러 오류 C2811
ms.date: 11/04/2016
f1_keywords:
- C2811
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
ms.openlocfilehash: 95d6385cea95f22bbb9bbb9197dace22bd1a3adf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755254"
---
# <a name="compiler-error-c2811"></a>컴파일러 오류 C2811

' type1 ': ' type2 '에서 상속할 수 없습니다. ref 클래스는 ref 클래스 또는 인터페이스 클래스 에서만 상속할 수 있습니다.

관리 되지 않는 클래스를 관리 되는 클래스의 기본 클래스로 사용 하려고 했습니다.

다음 샘플에서는 C2811를 생성 합니다.

```cpp
// C2811.cpp
// compile with: /clr /c
struct S{};
ref struct T {};
ref class C : public S {};   // C2811
ref class D : public T {};   // OK
```
