---
description: '자세한 정보: 컴파일러 오류 C2723'
title: 컴파일러 오류 C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: ab6eacd4279f0fd7b1c44b86b72cbe62ee51020e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155516"
---
# <a name="compiler-error-c2723"></a>컴파일러 오류 C2723

'function' : 함수 정의에는 'specifier' 지정자를 사용할 수 없습니다.

클래스 정의가 클래스 선언 외부에 있는 경우 지정자가 나타날 수 없습니다. **`virtual`** 지정자는 클래스 선언 내의 멤버 함수 선언에만 지정할 수 있습니다.

다음 샘플에서는 C2723 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```
