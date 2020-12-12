---
description: '자세한 정보: 컴파일러 오류 C2811'
title: 컴파일러 오류 C2811
ms.date: 11/04/2016
f1_keywords:
- C2811
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
ms.openlocfilehash: 02b4770b08bdfc9ee15386874ebba2265716536d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194854"
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
