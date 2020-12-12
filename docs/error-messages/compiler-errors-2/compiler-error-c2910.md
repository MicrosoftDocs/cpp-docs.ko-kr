---
description: '자세한 정보: 컴파일러 오류 C2910'
title: 컴파일러 오류 C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: d4bb87b054f28e0eab5bc1eef815fd1770d45809
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270630"
---
# <a name="compiler-error-c2910"></a>컴파일러 오류 C2910

' function ': 명시적으로 특수화할 수 없습니다.

컴파일러가 함수를 명시적으로 두 번 특수화 하려고 했습니다.

다음 샘플에서는 C2910를 생성 합니다.

```cpp
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

템플릿이 아닌 멤버를 명시적으로 특수화 하려고 하면 C2910이 생성 될 수도 있습니다. 즉, 함수 템플릿만 명시적으로 특수화할 수 있습니다.

다음 샘플에서는 C2910를 생성 합니다.

```cpp
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

이 오류는 Visual Studio .NET 2003:에서 수행한 컴파일러 규칙 작업의 결과로도 생성 됩니다.

코드는 Visual Studio .NET 2003 및 Visual Studio .NET 버전의 Visual C++, 제거에서 유효 `template <>` 합니다.

다음 샘플에서는 C2910를 생성 합니다.

```cpp
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```
