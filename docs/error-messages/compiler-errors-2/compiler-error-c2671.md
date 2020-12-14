---
description: '자세한 정보: 컴파일러 오류 C2671'
title: 컴파일러 오류 C2671
ms.date: 11/04/2016
f1_keywords:
- C2671
helpviewer_keywords:
- C2671
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
ms.openlocfilehash: ec70961a9ea57920a56f2b460a5e6ed481963233
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282109"
---
# <a name="compiler-error-c2671"></a>컴파일러 오류 C2671

' function ': 정적 멤버 함수에 ' this ' 포인터가 없습니다.

**`static`** 멤버 함수가에 액세스 하려고 했습니다 **`this`** .

다음 샘플에서는 C2671를 생성 합니다.

```cpp
// C2671.cpp
struct S {
   static S* const func() { return this; }  // C2671
};
```
