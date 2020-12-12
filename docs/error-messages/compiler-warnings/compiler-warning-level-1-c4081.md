---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4081'
title: 컴파일러 경고(수준 1) C4081
ms.date: 11/04/2016
f1_keywords:
- C4081
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
ms.openlocfilehash: 01c03255361676cfbe9876c73d77a7e2c9356eda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278157"
---
# <a name="compiler-warning-level-1-c4081"></a>컴파일러 경고(수준 1) C4081

'token1'이 필요한데 'token2'가 있습니다.

이 컨텍스트에서는 컴파일러에 다른 토큰이 필요합니다.

## <a name="example"></a>예제

```cpp
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```
