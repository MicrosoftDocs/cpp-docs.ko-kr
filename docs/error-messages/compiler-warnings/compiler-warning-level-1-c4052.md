---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4052'
title: 컴파일러 경고(수준 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4052
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 0da0823b3268e8f957a87d1c975fb82098fe2511
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160560"
---
# <a name="compiler-warning-level-1-c4052"></a>컴파일러 경고(수준 1) C4052

함수 선언이 다릅니다. 한쪽에 가변 인수가 들어 있습니다.

하나의 함수 선언에 변수 인수가 없습니다. 무시됩니다.

다음 샘플에서는 C4052를 생성합니다.

```c
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```
