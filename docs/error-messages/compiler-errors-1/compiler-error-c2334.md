---
description: '자세한 정보: 컴파일러 오류 C2334'
title: 컴파일러 오류 C2334
ms.date: 11/04/2016
f1_keywords:
- C2334
helpviewer_keywords:
- C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
ms.openlocfilehash: 875520c55550aa8507f28567b56b4fd83f53912a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234867"
---
# <a name="compiler-error-c2334"></a>컴파일러 오류 C2334

': 또는 {' 앞에 예기치 않은 토큰이 있습니다. 명백한 함수 본문을 건너뜁니다.

다음 샘플에서는 C2334를 생성 합니다. 이 오류는 오류 C2059 후에 발생 합니다.

```cpp
// C2334.cpp
// compile with: /c
// C2059 expected
struct s1 {
   s1   {}   // C2334
   s1() {}   // OK
};
```
