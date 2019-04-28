---
title: 컴파일러 오류 C2782
ms.date: 11/04/2016
f1_keywords:
- C2782
helpviewer_keywords:
- C2782
ms.assetid: 8b685422-294d-4f64-9f3d-c14eaf03a93d
ms.openlocfilehash: 58fb298ef188c37ebebea6b5c87fe84daeea8aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257272"
---
# <a name="compiler-error-c2782"></a>컴파일러 오류 C2782

'declaration': 템플릿 매개 변수 'identifier' 모호 합니다.

컴파일러는 템플릿 인수의 형식을 확인할 수 없습니다.

다음 샘플에서는 C2782를 생성합니다.

```
// C2782.cpp
template<typename T>
void f(T, T) {}

int main() {
   f(1, 'c');   // C2782
   // try the following line instead
   // f<int>(1, 'c');
}
```

C2782는 제네릭을 사용할 때도 발생할 수 있습니다.

```
// C2782b.cpp
// compile with: /clr
generic<typename T> void gf(T, T) { }

int main() {
   gf(1, 'c'); // C2782
   // try the following line instead
   // gf<int>(1, 'c');
}
```