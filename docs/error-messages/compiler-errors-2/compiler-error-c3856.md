---
description: '자세한 정보: 컴파일러 오류 C3856'
title: 컴파일러 오류 C3856
ms.date: 11/04/2016
f1_keywords:
- C3856
helpviewer_keywords:
- C3856
ms.assetid: 242d9322-c325-4f20-be58-b2be6da56d60
ms.openlocfilehash: f15dbb4029a8eb0c8571e11dda71b3352a834117
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328121"
---
# <a name="compiler-error-c3856"></a>컴파일러 오류 C3856

' type ': 클래스가 클래스 형식이 아닙니다.

이 오류의 가장 일반적인 원인은 선언 시점에 있는 것 보다 정의 지점에 제네릭 또는 템플릿 매개 변수 목록이 더 있는 경우입니다.

다음 샘플에서는 C3856를 생성 합니다.

```cpp
// C3856.cpp
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>   // C3856
template <class T1>
template <class T2>  // extra template parameter list in definition
struct S<T>::S1{};
```

해결 방법:

```cpp
// C3856b.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1{};
```

제네릭을 사용 하는 경우에도 C3856이 발생할 수 있습니다.

```cpp
// C3856c.cpp
// compile with: /clr
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GS<T>::GS2 {};   // C3856
```

해결 방법:

```cpp
// C3856d.cpp
// compile with: /clr /c
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
ref struct GS<T>::GS2 {};
```
