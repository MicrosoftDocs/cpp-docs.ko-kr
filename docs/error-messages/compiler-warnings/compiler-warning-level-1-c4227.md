---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4227'
title: 컴파일러 경고(수준 1) C4227
ms.date: 11/04/2016
f1_keywords:
- C4227
helpviewer_keywords:
- C4227
ms.assetid: 78f98374-c00b-4000-aefa-1b1c67b4666b
ms.openlocfilehash: f919f3765836548b7aa7410002facd942b942395
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266327"
---
# <a name="compiler-warning-level-1-c4227"></a>컴파일러 경고(수준 1) C4227

오래 된 사용: 참조에 대 한 한정자는 무시 됩니다.

**`const`** **`volatile`** C + + 참조와 같은 한정자를 사용 하는 것은 오래 된 방법입니다.

## <a name="example"></a>예제

```cpp
// C4227.cpp
// compile with: /W1 /c
int j = 0;
int &const i = j;   // C4227
```
