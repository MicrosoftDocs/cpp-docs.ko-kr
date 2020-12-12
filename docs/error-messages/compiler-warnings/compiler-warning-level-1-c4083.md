---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4083'
title: 컴파일러 경고 (수준 1) C4083
ms.date: 11/04/2016
f1_keywords:
- C4083
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
ms.openlocfilehash: 2913e4a55b7c777ae4c910631b8fb10120dd3463
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272333"
---
# <a name="compiler-warning-level-1-c4083"></a>컴파일러 경고 (수준 1) C4083

' token '이 필요 합니다. ' identifier ' 식별자를 찾았습니다.

**#Pragma** 문에서 식별자가 잘못 된 경우

## <a name="example"></a>예제

```cpp
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

[#Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) 지시문의 구문을 확인 합니다.
