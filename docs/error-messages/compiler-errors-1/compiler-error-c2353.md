---
description: '자세한 정보: 컴파일러 오류 C2353'
title: 컴파일러 오류 C2353
ms.date: 11/04/2016
f1_keywords:
- C2353
helpviewer_keywords:
- C2353
ms.assetid: d57f8f77-d9b1-4bba-a940-87ec269ad183
ms.openlocfilehash: d2fc96a74256f37b6c7cb9bc9515d46ad70fd83d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291885"
---
# <a name="compiler-error-c2353"></a>컴파일러 오류 C2353

예외 사양을 사용할 수 없습니다.

관리 되는 클래스의 멤버 함수에는 예외 사양을 사용할 수 없습니다.

다음 샘플에서는 C2353를 생성 합니다.

```cpp
// C2353.cpp
// compile with: /clr /c
ref class X {
   void f() throw(int);   // C2353
   void f();   // OK
};
```
