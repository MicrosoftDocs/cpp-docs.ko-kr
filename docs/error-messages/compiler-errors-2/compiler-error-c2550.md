---
description: '자세한 정보: 컴파일러 오류 C2550'
title: 컴파일러 오류 C2550
ms.date: 11/04/2016
f1_keywords:
- C2550
helpviewer_keywords:
- C2550
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
ms.openlocfilehash: 046cb88be2dfdb0e73273a7c370d6d7fdd97243f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204084"
---
# <a name="compiler-error-c2550"></a>컴파일러 오류 C2550

' identifier ': 생성자 이니셜라이저 목록은 생성자 정의에만 사용할 수 있습니다.

기본 클래스 이니셜라이저 목록은 생성자가 아닌 함수의 정의에 사용 됩니다.

다음 샘플에서는 C2550를 생성 합니다.

```cpp
// C2550.cpp
// compile with: /c
class C {
public:
   C();
};

class D : public C {
public:
   D();
   void func();
};

void D::func() : C() {}  // C2550
D::D() : C() {}   // OK
```
