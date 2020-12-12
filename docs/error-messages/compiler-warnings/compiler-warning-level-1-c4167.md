---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4167'
title: 컴파일러 경고(수준 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: 8d0b08ea4d97c6e85f5e07ce4844abdae7afafbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266990"
---
# <a name="compiler-warning-level-1-c4167"></a>컴파일러 경고(수준 1) C4167

function: 내장 함수로만 사용할 수 있습니다.

**#pragma 함수** 는 컴파일러에서 내장 형식으로 사용해야 하는 함수에 대해 기존 호출을 사용하도록 강제하려고 합니다. pragma가 무시됩니다.

이 경고를 방지하려면 **#pragma 함수** 를 제거합니다.

## <a name="example"></a>예제

```cpp
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```
