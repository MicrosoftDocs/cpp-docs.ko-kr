---
description: '자세한 정보: 컴파일러 오류 C3855'
title: 컴파일러 오류 C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: eeb0dbda6f67d59470cd021ff37877d3a5201862
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328147"
---
# <a name="compiler-error-c3855"></a>컴파일러 오류 C3855

' class ': 형식 매개 변수 ' param '이 (가) 선언과 호환 되지 않습니다.

컴파일러가 이름이 다른 비형식 템플릿 또는 제네릭 매개 변수를 찾았습니다. 템플릿 특수화 정의의 지정 된 템플릿 매개 변수가 선언과 호환 되지 않는 경우이 오류가 발생할 수 있습니다.

다음 샘플에서는 C3855를 생성 합니다.

```cpp
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

해결 방법:

```cpp
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

제네릭을 사용 하는 경우에도 C3855이 발생할 수 있습니다.

```cpp
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

해결 방법:

```cpp
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```
