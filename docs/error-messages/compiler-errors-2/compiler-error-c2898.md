---
description: '자세한 정보: 컴파일러 오류 C2898'
title: 컴파일러 오류 C2898
ms.date: 11/04/2016
f1_keywords:
- C2898
helpviewer_keywords:
- C2898
ms.assetid: 68466e11-2541-4f6b-b772-13a642f30dfb
ms.openlocfilehash: 3cffde947d5e2940a7625dda873b27e08324421a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270773"
---
# <a name="compiler-error-c2898"></a>컴파일러 오류 C2898

' 선언 ': 멤버 함수 템플릿은 가상 일 수 없습니다.

다음 샘플에서는 C2898를 생성 합니다.

```cpp
// C2898.cpp
// compile with: /c
class X {
public:
   template<typename T> virtual void f(T t) {}   // C2898
};
```
