---
title: 컴파일러 경고 (수준 2) C4356 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4356
dev_langs:
- C++
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 463ecd1bdd41c07baab0cf90c978411e51b4be04
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118728"
---
# <a name="compiler-warning-level-2-c4356"></a>컴파일러 경고(수준 2) C4356

'member': 파생된 클래스를 통해 정적 데이터 멤버를 초기화할 수 없습니다

정적 데이터 멤버의 초기화 형식이 잘못 되었습니다. 컴파일러가 초기화를 허용 합니다. 경고를 방지 하려면 기본 클래스를 통해 멤버를 초기화 합니다.

사용 합니다 [경고](../../preprocessor/warning.md) pragma를이 경고를 표시 합니다.

다음 샘플에서는 C4356 오류가 생성 됩니다.

```
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