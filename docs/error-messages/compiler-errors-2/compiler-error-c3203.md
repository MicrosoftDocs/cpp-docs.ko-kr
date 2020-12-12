---
description: '자세한 정보: 컴파일러 오류 C3203'
title: 컴파일러 오류 C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: ea0c54fc54cfa19d4d41a712fba0fa24fe03abb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291859"
---
# <a name="compiler-error-c3203"></a>컴파일러 오류 C3203

'type' : 특수화되지 않은 클래스 템플릿 또는 제네릭은 템플릿 또는 제네릭 매개 변수 'param'에 대한 템플릿 또는 제네릭 인수로 사용할 수 없습니다. 실제 형식이 필요합니다.

클래스 템플릿 또는 제네릭에 잘못된 인수를 전달했습니다. 클래스 템플릿 또는 제네릭에는 매개 변수로 형식이 필요합니다.

이 오류는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. 특수화 되지 않은 클래스 템플릿은 기본 클래스 목록에서 템플릿 인수로 사용할 수 없습니다. C3203 오류를 해결하려면 템플릿 형식 매개 변수를 기본 클래스 목록의 템플릿 매개 변수로 사용할 때 명시적으로 템플릿 클래스 이름에 추가합니다.

```cpp
// C3203.cpp
template< typename T >
struct X {
   void f(X) {}
};

template< typename T >
struct Y : public X<Y> {   // C3203
// try the following line instead
// struct Y : public X<Y<T> > {
   void f(Y) {}
};

int main() {
   Y<int> y;
}
```

다음 샘플에서는 C3203 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3203_b.cpp
// compile with: /c
template <class T>
struct S1 {};

template <class T>
class C1 {};

typedef C1<S1> MyC1;   // C3203

// OK
template <template <class> class T>
class C2 {};

typedef C2<S1> MyC1;

template <class T>
class C3 {};

typedef C3<S1<int> > MyC12;
```

제네릭을 사용할 때도 C3203이 발생할 수 있습니다.

```cpp
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```
