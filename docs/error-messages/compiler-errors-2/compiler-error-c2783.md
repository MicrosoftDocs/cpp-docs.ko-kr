---
title: 컴파일러 오류 C2783
ms.date: 11/04/2016
f1_keywords:
- C2783
helpviewer_keywords:
- C2783
ms.assetid: 1ce94a11-bb8b-4be3-a222-f1f105da74b3
ms.openlocfilehash: adba87853bac764d4975d6b6fa9aa44940ced03c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739677"
---
# <a name="compiler-error-c2783"></a>컴파일러 오류 C2783

' 선언 ': ' identifier '의 템플릿 인수를 추론할 수 없습니다.

컴파일러가 템플릿 인수를 확인할 수 없습니다. 기본 인수를 사용 하 여 템플릿 인수를 추론할 수 없습니다.

다음 샘플에서는 C2783를 생성 합니다.

```cpp
// C2783.cpp
template<typename T1, typename T2>
T1 f(T2) {
   return 248;
}

int main() {
   f(1);   // C2783
   // try the following line instead
   int i = f<int>(1);
}
```

제네릭을 사용 하는 경우에도 C2783이 발생할 수 있습니다.

```cpp
// C2783b.cpp
// compile with: /clr
using namespace System;
generic<typename T1, typename T2>
T1 gf(T2) {
   T1 t1 = safe_cast<T1>( Activator::CreateInstance(T1::typeid));
   return t1;
}

ref class MyClass{};

int main() {
   int i;
   i = gf(9);   // C2783

   // OK
   i = gf<int>(9);
}
```
