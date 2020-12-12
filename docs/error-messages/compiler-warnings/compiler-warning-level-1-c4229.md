---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4229'
title: 컴파일러 경고(수준 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: 5c91a3730ff85d71d519c646a1dab64cc08b1003
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266366"
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
