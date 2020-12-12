---
description: '자세한 정보: 컴파일러 오류 C3217'
title: 컴파일러 오류 C3217
ms.date: 11/04/2016
f1_keywords:
- C3217
helpviewer_keywords:
- C3217
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
ms.openlocfilehash: 3e38c188f5e6d061312cc9994e86143a6661a287
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173716"
---
# <a name="compiler-error-c3217"></a>컴파일러 오류 C3217

'param': 제네릭 매개 변수는 이 선언에서 제약을 받을 수 없습니다.

제약 조건의 형식이 잘못되었습니다. 제약 조건 제네릭 매개 변수는 제네릭 클래스 템플릿 매개 변수와 일치해야 합니다.

다음 샘플에서는 C3217을 생성합니다.

```cpp
// C3217.cpp
// compile with: /clr
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T : A   // C3217
   void f();
};
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3217b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T1 : A
   void f();
};
```
