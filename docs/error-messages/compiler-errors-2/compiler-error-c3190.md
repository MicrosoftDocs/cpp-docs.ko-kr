---
description: '자세한 정보: 컴파일러 오류 C3190'
title: 컴파일러 오류 C3190
ms.date: 11/04/2016
f1_keywords:
- C3190
helpviewer_keywords:
- C3190
ms.assetid: 7c701afa-85a7-4f7a-8881-0662436ac244
ms.openlocfilehash: 2a0ed65d67f4847dbe5140561fb2629c19f85c8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322012"
---
# <a name="compiler-error-c3190"></a>컴파일러 오류 C3190

제공 된 템플릿 인수를 사용 하는 ' 인스턴스화 '는 ' type ' 멤버 함수의 명시적 인스턴스화가 아닙니다.

컴파일러가 명시적 함수 인스턴스화를 시도 하는 것을 발견 했습니다. 그러나 제공 된 형식 인수는 가능한 함수와 일치 하지 않습니다.

다음 샘플에서는 C3190를 생성 합니다.

```cpp
// C3190.cpp
// compile with: /LD
template<class T>
struct A {
   A(int x = 0) {
   }
   A(int x, int y) {
   }
};

template A<float>::A();   // C3190
// try the following line instead
// template A<int>::A(int);

struct Y {
   template<class T> void f(T);
};

template<class T> void Y::f(T) { }

template void Y::f(int,int);   // C3190

template<class OT> class X {
   template<class T> void f2(T,OT);
};

template<class OT> template<class T> void X<OT>::f2(T,OT) {}

template void X<float>::f2<int>(int,char);   // C3190
// try one of the following lines instead
// template void X<char>::f2(int, char);
// template void X<char>::f2<int>(int,char);
// template void X<char>::f2<>(int,char);
```
