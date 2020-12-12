---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4180'
title: 컴파일러 경고(수준 1) C4180
ms.date: 11/04/2016
f1_keywords:
- C4180
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
ms.openlocfilehash: d85097212086d98b70b71837b01ef1522f87580c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266717"
---
# <a name="compiler-warning-level-1-c4180"></a>컴파일러 경고(수준 1) C4180

함수 형식에 적용되는 한정자가 의미가 없으므로 무시됩니다.

와 같은 한정자가로 **`const`** 정의 된 함수 형식에 적용 됩니다 **`typedef`** .

## <a name="example"></a>예제

```cpp
// C4180.cpp
// compile with: /W1 /c
typedef int FuncType(void);

// the const qualifier cannot be applied to the
// function type FuncType
const FuncType f;   // C4180
```
