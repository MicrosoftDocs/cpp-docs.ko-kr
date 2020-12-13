---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4913'
title: 컴파일러 경고(수준 4) C4913
ms.date: 11/04/2016
f1_keywords:
- C4913
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
ms.openlocfilehash: f47c72bfbc714e8834ba27a604b8f6a58203628f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330455"
---
# <a name="compiler-warning-level-4-c4913"></a>컴파일러 경고(수준 4) C4913

**사용자 정의 이항 연산자 ','가 존재하지만 오버로드가 모든 피연산자를 변환하지 못했습니다. 기본 내장 이항 연산자 ','를 사용합니다.**

오버로드된 쉼표 연산자도 있는 프로그램에서 기본 제공 쉼표 연산자에 대한 호출이 발생하고 예상했던 변환이 발생하지 않았습니다.

다음 코드 샘플에서는 C4913을 생성합니다.

```cpp
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```
