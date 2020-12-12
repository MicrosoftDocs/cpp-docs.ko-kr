---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4659'
title: 컴파일러 경고(수준 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 05ec1e088e00b184ba083b6b197afc6041707449
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318817"
---
# <a name="compiler-warning-level-1-c4659"></a>컴파일러 경고(수준 1) C4659

\#pragma ' pragma ': ' segment ' 예약 세그먼트를 사용 하 여 정의 되지 않은 동작이 있습니다. #pragma 주석 (링커, ...)을 사용 하십시오.

.Drectve 옵션을 사용 하 여 옵션을 링커에 전달 했습니다. 대신 링커 옵션을 전달 하기 위해 pragma [주석을](../../preprocessor/comment-c-cpp.md) 사용 합니다.

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
