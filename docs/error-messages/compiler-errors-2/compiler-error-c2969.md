---
description: '자세한 정보: 컴파일러 오류 C2969'
title: 컴파일러 오류 C2969
ms.date: 11/04/2016
f1_keywords:
- C2969
helpviewer_keywords:
- C2969
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
ms.openlocfilehash: d0b52e6033338adc249cc9c7181cbb5dc25f7f8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210402"
---
# <a name="compiler-error-c2969"></a>컴파일러 오류 C2969

구문 오류: 'symbol': 멤버 함수 정의가 '}'로 끝나야 합니다.

템플릿 멤버 함수 정의에 짝이 맞지 않는 닫는 중괄호가 있습니다.

다음 샘플에서는 C2969를 생성합니다.

```cpp
// C2969.cpp
// compile with: /c
class A {
   int i;
public:
   A(int i) {}
};

A anA(1);

class B {
   A a;
   B() : a(anA);   // C2969
   // try the following line instead
   // B() : a(anA) {}
};
```
