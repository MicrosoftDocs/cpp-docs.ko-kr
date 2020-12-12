---
description: '자세한 정보: 컴파일러 오류 C3212'
title: 컴파일러 오류 C3212
ms.date: 11/04/2016
f1_keywords:
- C3212
helpviewer_keywords:
- C3212
ms.assetid: 9e271bb6-a51f-4b96-b26b-9f4ca28fca0a
ms.openlocfilehash: f78234f1176319739be74841e0a982afa591045d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173846"
---
# <a name="compiler-error-c3212"></a>컴파일러 오류 C3212

'specialization': 템플릿 멤버의 명시적 특수화는 명시적 특수화의 멤버여야 합니다.

명시적 특수화의 형식이 잘못되었습니다.

다음 샘플에서는 C3212를 생성합니다.

```cpp
// C3212.cpp
// compile with: /LD
template <class T>
struct S {
   template <class T1>
   struct S1;
};

template <class T>   // C3212
template <>
struct S<T>::S1<int> {};

/*
// try the following instead
template <>
template <>
struct S<int>::S1<int> {};
*/

/*
// or, the following
template <>
struct S<int> {
   template <class T1>
   struct S1;
};

template <>
struct S<int>::S1<int> {
};
*/
```
