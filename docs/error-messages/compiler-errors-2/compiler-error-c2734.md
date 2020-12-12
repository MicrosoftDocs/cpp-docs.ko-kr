---
description: '자세한 정보: 컴파일러 오류 C2734'
title: 컴파일러 오류 C2734
ms.date: 11/04/2016
f1_keywords:
- C2734
helpviewer_keywords:
- C2734
ms.assetid: e53a77b7-825c-42d1-a655-90e1c93b833e
ms.openlocfilehash: c867ef8456be35d0e566056aedc4de43d16c8f14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123177"
---
# <a name="compiler-error-c2734"></a>컴파일러 오류 C2734

' identifier ': extern이 아닌 경우에는 const 개체를 초기화 해야 합니다.

식별자가 선언 **`const`** 되었지만 초기화 되지 않았습니다 **`extern`** .

다음 샘플에서는 C2734를 생성 합니다.

```cpp
// C2734.cpp
const int j;   // C2734
extern const int i;   // OK, declared as extern
```
