---
description: '자세한 정보: 컴파일러 오류 C2391'
title: 컴파일러 오류 C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 3161cd6ade15817142cc24f38c61fd3e09eb8857
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337578"
---
# <a name="compiler-error-c2391"></a>컴파일러 오류 C2391

' identifier ': 형식 정의 중에는 ' friend '를 사용할 수 없습니다.

선언에는 **`friend`** 완전 한 클래스 선언이 포함 됩니다. **`friend`** 선언은 멤버 함수 또는 상세 형식 지정자를 지정할 수 있지만 전체 클래스 선언은 지정할 수 없습니다.

다음 샘플에서는 C2326을 생성합니다.

```cpp
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```
