---
description: '자세한 정보: 컴파일러 오류 C3206'
title: 컴파일러 오류 C3206
ms.date: 11/04/2016
f1_keywords:
- C3206
helpviewer_keywords:
- C3206
ms.assetid: d62995b5-e349-4418-bbe8-8a5e776ca7b0
ms.openlocfilehash: ea4ded5daebe0f002a3d0363fba125c2c02f332b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174015"
---
# <a name="compiler-error-c3206"></a>컴파일러 오류 C3206

'function': 'param'에 대한 형식 인수가 잘못되었습니다. 클래스 형식 'typename'에 대한 형식 인수 목록이 없습니다.

템플릿 함수가 템플릿 형식 인수를 사용하도록 정의되어 있습니다. 그러나 template 템플릿 인수가 전달되었습니다.

다음 샘플에서는 C3206을 생성합니다.

```cpp
// C3206.cpp
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S>();   // C3206
   // try the following line instead
   // f<S<int> >();
}
```

해결 방법:

```cpp
// C3206b.cpp
// compile with: /c
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S<int> >();
}
```

C3206은 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C3206c.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS>();   // C3206
}
```

해결 방법:

```cpp
// C3206d.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS<int> >();
}
```

클래스 템플릿은 템플릿 형식 인수로 허용되지 않습니다. 다음 샘플에서는 C3206을 발생 시킵니다.

```cpp
// C3206e.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T<int> t;
}

int main() {
   func<S>();   // C3206 S is not a type.
}
```

해결 방법:

```cpp
// C3206f.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T t;
}

int main() {
   func<S<int> >();
}
```

템플릿 템플릿 매개 변수가 필요한 경우 템플릿 템플릿 매개 변수를 사용 하는 템플릿 클래스에서 함수를 래핑해야 합니다.

```cpp
// C3206g.cpp
template <class T>
struct S {};

template<template<class> class TT>
struct X {
   static void func() {
      TT<int> t1;
      TT<char> t2;
   }
};

int main() {
   X<S>::func();
}
```
