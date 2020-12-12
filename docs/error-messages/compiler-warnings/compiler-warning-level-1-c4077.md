---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4077'
title: 컴파일러 경고(수준 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: 96e611db6d36dfa62d96561deb2f4c4d57638c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208712"
---
# <a name="compiler-warning-level-1-c4077"></a>컴파일러 경고(수준 1) C4077

알 수 없는 check_stack 옵션입니다.

이전 **check_stack** pragma 형식이 알 수 없는 인수와 함께 사용되었습니다. 인수는 `+`, `-`, `(on)`, `(off)`이거나 비어 있어야 합니다.

컴파일러가 해당 pragma를 무시하고 스택 검사를 변경되지 않은 상태로 그대로 둡니다.

## <a name="example"></a>예제

```cpp
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```
