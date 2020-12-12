---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4228'
title: 컴파일러 경고(수준 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: efb247d64ced8c44e84b8f3cfb4e15705eb57b1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266353"
---
# <a name="compiler-warning-level-1-c4228"></a>컴파일러 경고(수준 1) C4228

비표준 확장이 사용 됨: 선언 자 목록에서 쉼표 뒤의 한정자가 무시 됩니다.

변수를 선언할 때 쉼표와 같은 한정자를 사용 하는 **`const`** **`volatile`** 것은 Microsoft 확장 ([/ze](../../build/reference/za-ze-disable-language-extensions.md))입니다.

## <a name="example"></a>예제

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```
