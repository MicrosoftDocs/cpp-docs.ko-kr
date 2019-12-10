---
title: 컴파일러 오류 C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735933"
---
# <a name="compiler-error-c2061"></a>컴파일러 오류 C2061

구문 오류: ' identifier ' 식별자입니다.

컴파일러가 예상한 식별자를 찾지 못했습니다. 사용 하기 전에 `identifier`을 선언 했는지 확인 합니다.

이니셜라이저를 괄호로 묶을 수 있습니다. 이 문제를 방지 하려면 선언 자를 괄호로 묶거나 `typedef`로 만듭니다.

컴파일러가 식을 클래스 템플릿 인수로 검색 하는 경우에도이 오류가 발생할 수 있습니다. [typename](../../cpp/typename.md) 을 사용 하 여 컴파일러에 형식을 알립니다.

다음 샘플에서는 C2061를 생성 합니다.

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061는 인스턴스 이름을 [typeid](../../extensions/typeid-cpp-component-extensions.md)에 전달 하는 경우 발생할 수 있습니다.

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
