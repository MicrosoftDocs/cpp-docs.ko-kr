---
title: 컴파일러 오류 C2427
ms.date: 11/04/2016
f1_keywords:
- C2427
helpviewer_keywords:
- C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
ms.openlocfilehash: d92f3bce54a4558702d2a6d3870323eb0edd5d4d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744617"
---
# <a name="compiler-error-c2427"></a>컴파일러 오류 C2427

' class ':이 범위에서는 클래스를 정의할 수 없습니다.

중첩 된 클래스를 정의 하려고 했지만 중첩 된 클래스는 가장 많이 포함 하는 클래스가 아니라 기본 클래스의 멤버입니다.

다음 샘플에서는 C2427를 생성 합니다.

```cpp
// C2427.cpp
// compile with: /c
template <class T>
struct S {
   struct Inner;
};

struct Y : S<int> {};

struct Y::Inner {};   // C2427

// OK
template<typename T>
struct S<T>::Inner {};
```
