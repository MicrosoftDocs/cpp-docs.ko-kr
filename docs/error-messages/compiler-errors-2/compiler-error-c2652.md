---
description: '자세한 정보: 컴파일러 오류 C2652'
title: 컴파일러 오류 C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 6d0f85a089c527ce299e007ce04d96ac68daaf56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286178"
---
# <a name="compiler-error-c2652"></a>컴파일러 오류 C2652

' identifier ': 복사 생성자가 잘못 되었습니다. 첫 번째 매개 변수는 ' identifier '가 아니어야 합니다.

복사 생성자의 첫 번째 매개 변수는 해당 매개 변수가 정의 된 클래스, 구조체 또는 공용 구조체와 동일한 형식입니다. 첫 번째 매개 변수는 형식에 대 한 참조가 될 수 있지만 형식 자체는 아닙니다.

다음 샘플에서는 C2651를 생성 합니다.

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
