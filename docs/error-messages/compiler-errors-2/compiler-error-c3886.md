---
description: '자세한 정보: 컴파일러 오류 C3886'
title: 컴파일러 오류 C3886
ms.date: 11/04/2016
f1_keywords:
- C3886
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
ms.openlocfilehash: ed82fcc8a21d19f88bf9381431711e3a7a397c6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144354"
---
# <a name="compiler-error-c3886"></a>컴파일러 오류 C3886

' var ': 리터럴 데이터 멤버를 초기화 해야 합니다.

[리터럴](../../extensions/literal-cpp-component-extensions.md) 변수는 declaraed 될 때 초기화 되어야 합니다.

다음 샘플에서는 C3886를 생성 합니다.

```cpp
// C3886.cpp
// compile with: /clr /c
ref struct Y1 {
   literal int staticConst;   // C3886
   literal int staticConst2 = 0;   // OK
};
```
