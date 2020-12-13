---
description: '자세한 정보: 컴파일러 오류 C2258'
title: 컴파일러 오류 C2258
ms.date: 11/04/2016
f1_keywords:
- C2258
helpviewer_keywords:
- C2258
ms.assetid: 105eaa87-befb-4ecb-9a3f-e09e14d2f5bf
ms.openlocfilehash: cb82994b582df91198fcd7455179666e66543247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134721"
---
# <a name="compiler-error-c2258"></a>컴파일러 오류 C2258

순수 구문이 잘못되었습니다. '= 0'이어야 합니다.

순수 가상 함수를 잘못된 구문으로 선언했습니다.

다음 샘플에서는 C2258을 생성합니다.

```cpp
// C2258.cpp
// compile with: /c
class A {
public:
   void virtual func1() = 1; // C2258
   void virtual func2() = 0;   // OK
};
```
