---
description: '자세한 정보: 컴파일러 오류 C3283'
title: 컴파일러 오류 C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 577f3fa6c3316c58bf6e9dca94b22a168a451b17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311879"
---
# <a name="compiler-error-c3283"></a>컴파일러 오류 C3283

'type': 인터페이스에는 인스턴스 생성자를 사용할 수 없습니다.

CLR [인터페이스](../../extensions/interface-class-cpp-component-extensions.md) 에는 인스턴스 생성자를 사용할 수 없습니다.  정적 생성자는 허용됩니다.

다음 샘플에서는 C3283을 생성합니다.

```cpp
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

해결 방법:

```cpp
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```
