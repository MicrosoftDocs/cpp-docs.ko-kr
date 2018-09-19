---
title: 컴파일러 오류 C2353 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2353
dev_langs:
- C++
helpviewer_keywords:
- C2353
ms.assetid: d57f8f77-d9b1-4bba-a940-87ec269ad183
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3685db97a213f6347fccedefdaeebfdeaaffb7bc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109277"
---
# <a name="compiler-error-c2353"></a>컴파일러 오류 C2353

예외 사양이 허용 되지 않습니다.

관리 되는 클래스의 멤버 함수에 예외 사양이 허용 되지 않습니다.

다음 샘플에서는 C2353 오류가 생성 됩니다.

```
// C2353.cpp
// compile with: /clr /c
ref class X {
   void f() throw(int);   // C2353
   void f();   // OK
};
```