---
description: '자세한 정보: 컴파일러 오류 C2882'
title: 컴파일러 오류 C2882
ms.date: 11/04/2016
f1_keywords:
- C2882
helpviewer_keywords:
- C2882
ms.assetid: 617018ee-5a0d-4b8d-9612-77e8ae52679b
ms.openlocfilehash: b060fbc741bc768c2f27625c25345f5e8ed1a484
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332357"
---
# <a name="compiler-error-c2882"></a>컴파일러 오류 C2882

' name ': 식에서 네임 스페이스 식별자를 잘못 사용 했습니다.

식에서 네임 스페이스의 이름을 사용 하려고 했습니다.

다음 샘플에서는 C2882를 생성 합니다.

```cpp
// C2882.cpp
// compile with: /c
namespace A {
   int k;
}

int i = A;   // C2882, can't assign A to i
```
