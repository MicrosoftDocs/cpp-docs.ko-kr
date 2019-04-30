---
title: 컴파일러 경고 (수준 1) C4083
ms.date: 11/04/2016
f1_keywords:
- C4083
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
ms.openlocfilehash: 854d4a9887b8a9ada12adc94509745458a1e9523
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300273"
---
# <a name="compiler-warning-level-1-c4083"></a>컴파일러 경고 (수준 1) C4083

예상 된 ' token'; 'identifier' 식별자가 발견

식별자에 잘못 된 위치에서 발생 한 **#pragma** 문입니다.

## <a name="example"></a>예제

```
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

구문을 확인 합니다 [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) 지시문입니다.