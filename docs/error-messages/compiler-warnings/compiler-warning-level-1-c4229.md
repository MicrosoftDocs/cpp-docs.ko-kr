---
title: 컴파일러 경고(수준 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: 79e97949f1c2c999c2800a708461ca9c68de0a5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223228"
---
# <a name="compiler-warning-level-1-c4229"></a>컴파일러 경고(수준 1) C4229

오래 된 사용: 데이터의 한정자는 무시 됩니다.

데이터 선언에와 같은 Microsoft 한정자를 사용 하 **`__cdecl`** 는 것은 오래 된 방법입니다.

## <a name="example"></a>예제

```cpp
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```
