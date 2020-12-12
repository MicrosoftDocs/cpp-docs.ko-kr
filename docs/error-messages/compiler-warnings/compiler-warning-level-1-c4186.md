---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4186'
title: 컴파일러 경고(수준 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: 08ab6c490c404d9dabef1d5222cd388b5db7a891
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266613"
---
# <a name="compiler-warning-level-1-c4186"></a>컴파일러 경고(수준 1) C4186

\#' attribute ' 특성을 가져오려면 count 인수가 필요 합니다. 무시

`#import` 특성의 인수 개수가 잘못되었습니다.

## <a name="example"></a>예제

```cpp
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

`no_namespace` 특성은 인수를 사용하지 않습니다. **rename** 특성은 두 개의 인수만 사용합니다.
