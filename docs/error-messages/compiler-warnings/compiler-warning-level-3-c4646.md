---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4646'
title: 컴파일러 경고(수준 3) C4646
ms.date: 11/04/2016
f1_keywords:
- C4646
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
ms.openlocfilehash: 045c5d4557a50824235833528f8b46ff77b683e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301830"
---
# <a name="compiler-warning-level-3-c4646"></a>컴파일러 경고(수준 3) C4646

__declspec(noreturn)으로 선언된 함수에 void가 아닌 반환 형식이 있습니다.

[Noreturn](../../cpp/noreturn.md) 한정자로 표시 된 함수에는 **`__declspec`** [void](../../cpp/void-cpp.md) 반환 형식이 있어야 합니다.

다음 샘플에서는 C4646을 생성합니다.

```cpp
// C4646.cpp
// compile with: /W3 /WX
int __declspec(noreturn) TestFunction()
{   // C4646  make return type void
}
```
