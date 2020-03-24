---
title: 컴파일러 경고(수준 2) C4356
ms.date: 11/04/2016
f1_keywords:
- C4356
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
ms.openlocfilehash: ffcf0098799b893f83e331b3b4cc602e1b538b1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161830"
---
# <a name="compiler-warning-level-2-c4356"></a>컴파일러 경고(수준 2) C4356

' member ': 정적 데이터 멤버는 파생 클래스를 통해 초기화할 수 없습니다.

정적 데이터 멤버의 초기화 형식이 잘못 되었습니다. 컴파일러가 초기화를 수락 했습니다. 이 경고를 방지 하려면 기본 클래스를 통해 멤버를 초기화 합니다.

이 경고를 표시 하지 않으려면 [warning](../../preprocessor/warning.md) pragma를 사용 합니다.

다음 샘플에서는 C4356를 생성 합니다.

```cpp
// C4356.cpp
// compile with: /W2 /EHsc
#include <iostream>

template <class T>
class C {
   static int n;
};

class D : C<int> {};

int D::n = 0; // C4356
// try the following line instead
// int C<int>::n = 0;

class A {
public:
   static int n;
};

class B : public A {};

int B::n = 10;   // C4356
// try the following line instead
// int A::n = 99;

int main() {
   using namespace std;
   cout << B::n << endl;
}
```
