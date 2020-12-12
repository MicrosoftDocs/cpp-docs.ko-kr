---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4756'
title: 컴파일러 경고(수준 2) C4756
ms.date: 11/04/2016
f1_keywords:
- C4756
helpviewer_keywords:
- C4756
ms.assetid: 5a16df83-6b82-4619-83bd-319af4ef1d1d
ms.openlocfilehash: 3031a882feaba0d96adf588481de29431b337ad7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173456"
---
# <a name="compiler-warning-level-2-c4756"></a>컴파일러 경고(수준 2) C4756

상수 산술 연산에서 오버플로가 발생 했습니다.

컴파일하는 동안 상수 산술 연산을 수행 하는 동안 컴파일러에서 예외가 발생 했습니다.

다음 샘플에서는 C4756를 생성 합니다.

```cpp
// C4756.cpp
// compile with: /W2 /Od
int main()
{
   float f = 1e100+1e100;   // C4756
}
```
