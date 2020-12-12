---
description: '자세한 정보: 컴파일러 오류 C2831'
title: 컴파일러 오류 C2831
ms.date: 11/04/2016
f1_keywords:
- C2831
helpviewer_keywords:
- C2831
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
ms.openlocfilehash: 65fece68763e38de8c5047c66327e0615865fa9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194503"
---
# <a name="compiler-error-c2831"></a>컴파일러 오류 C2831

' operator operator '에는 기본 매개 변수를 사용할 수 없습니다.

3 개의 연산자만 기본 매개 변수를 사용할 수 있습니다.

- [new](../../cpp/new-operator-cpp.md)

- 할당 =

- 왼쪽 괄호 (

다음 샘플에서는 C2831를 생성 합니다.

```cpp
// C2831.cpp
// compile with: /c
#define BINOP <=
class A {
public:
   int i;
   int operator BINOP(int x = 1) {   // C2831
   // try the following line instead
   // int operator BINOP(int x) {
      return i+x;
   }
};
```
