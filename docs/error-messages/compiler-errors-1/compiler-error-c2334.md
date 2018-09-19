---
title: 컴파일러 오류 C2334 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2334
dev_langs:
- C++
helpviewer_keywords:
- C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68ce0a6096cfd8a3a4e0fe52d897690f037be40b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073819"
---
# <a name="compiler-error-c2334"></a>컴파일러 오류 C2334

예기치 않은 토큰이 있습니다. 위의 ': 또는 {'; 명백한 함수 본문을 건너뜁니다.

다음 샘플 C2334를 생성합니다. 이 오류는 오류 C2059 후 발생합니다.

```
// C2334.cpp
// compile with: /c
// C2059 expected
struct s1 {
   s1   {}   // C2334
   s1() {}   // OK
};
```