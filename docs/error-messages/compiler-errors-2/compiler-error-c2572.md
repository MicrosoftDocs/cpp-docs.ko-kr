---
description: '자세한 정보: 컴파일러 오류 C2572'
title: 컴파일러 오류 C2572
ms.date: 11/04/2016
f1_keywords:
- C2572
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
ms.openlocfilehash: ff0549309df0567e2d1d7f26f98f95c3c3b629d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208959"
---
# <a name="compiler-error-c2572"></a>컴파일러 오류 C2572

' class:: member ': 기본 매개 변수 재정의: parameter param

기본 매개 변수는 다시 정의할 수 없습니다. 매개 변수에 다른 값을 지정 해야 하는 경우에는 기본 매개 변수를 정의 하지 않은 상태로 두어야 합니다.

다음 샘플에서는 C2572를 생성 합니다.

```cpp
// C2572.cpp
// compile with: /c
void f(int i = 1);   // function declaration

// function definition
void f(int i = 1) {}   // C2572

// try the following line instead
// void f(int i) {}
```
