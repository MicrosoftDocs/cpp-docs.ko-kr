---
description: '자세한 정보: 컴파일러 오류 C2876'
title: 컴파일러 오류 C2876
ms.date: 11/04/2016
f1_keywords:
- C2876
helpviewer_keywords:
- C2876
ms.assetid: 8b674bf1-f9f4-4a8e-8127-e884c1d1708f
ms.openlocfilehash: 5d83c1dd57c074354d3643452a1a2189bcbd860e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320501"
---
# <a name="compiler-error-c2876"></a>컴파일러 오류 C2876

' class:: symbol ': 모든 오버 로드에 액세스할 수 없습니다.

기본 클래스에서 모든 오버 로드 된 형식의 함수는 파생 클래스에서 액세스할 수 있어야 합니다.

다음 샘플에서는 C2876를 생성 합니다.

```cpp
// C2876.cpp
// compile with: /c
class A {
public:
   double a(double);
private:
   int a(int);
};

class B : public A {
   using A::a;   // C2876 one overload is private in base class
};
```
