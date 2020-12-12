---
description: '자세한 정보: 컴파일러 오류 C2896'
title: 컴파일러 오류 C2896
ms.date: 11/04/2016
f1_keywords:
- C2896
helpviewer_keywords:
- C2896
ms.assetid: b600407b-cb05-42e3-9069-2aa6960f0eaa
ms.openlocfilehash: 096650ab4ced95ace9bbf51680339ba0258eff45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270903"
---
# <a name="compiler-error-c2896"></a>컴파일러 오류 C2896

' function1 ': ' function2 ' 함수 템플릿을 인수로 사용할 수 없습니다.

함수 템플릿은 다른 함수 템플릿에 대 한 인수 일 수 없습니다.

다음 샘플에서는 C2896를 생성 합니다.

```cpp
// C2896.cpp
template<class T1, class T2> void f1(void(*)(T1, T2));
template<class T1, class T2> void f2(T1, T2);

int main() {
   f1(f2);   // C2896
}
```

제네릭을 사용 하는 경우에도 C2896이 발생할 수 있습니다.

```cpp
// C2896b.cpp
// compile with: /clr
generic<class T1> void gf1(T1){}
generic<class T1> void gf2(T1){}

int main() {
   gf1(gf2);   // C2896
   gf1(1);   // OK
}
```
