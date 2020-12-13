---
description: '자세한 정보: 컴파일러 오류 C3644'
title: 컴파일러 오류 C3644
ms.date: 11/04/2016
f1_keywords:
- C3644
helpviewer_keywords:
- C3644
ms.assetid: 2e3f6c41-3ec5-4a01-82bc-f11b61ebe68e
ms.openlocfilehash: e08471583dea096481115f3d710a1854ef00baf9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340283"
---
# <a name="compiler-error-c3644"></a>컴파일러 오류 C3644

' function ': 함수를 컴파일하여 관리 코드를 생성할 수 없습니다.

함수에 일부 키워드가 있으면 함수가 네이티브로 컴파일됩니다.

다음 샘플에서는 C3644를 생성 합니다.

```cpp
// C3644.cpp
// compile with: /clr
// processor: x86

void __clrcall Func2(int i) {
   __asm {}   // C3644
}
```
