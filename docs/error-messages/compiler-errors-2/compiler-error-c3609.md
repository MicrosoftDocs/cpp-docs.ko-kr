---
title: 컴파일러 오류 C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 2eff238aed756c9f056da9a1b9a70fca9de24fa3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230807"
---
# <a name="compiler-error-c3609"></a>컴파일러 오류 C3609

'member': 봉인 함수 또는 최종 함수는 virtual이어야 합니다.

[Sealed](../../extensions/sealed-cpp-component-extensions.md) 및 [final](../../cpp/final-specifier.md) 키워드는로 표시 된 클래스, 구조체 또는 멤버 함수 에서만 사용할 수 있습니다 **`virtual`** .

다음 샘플에서는 C3609 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
