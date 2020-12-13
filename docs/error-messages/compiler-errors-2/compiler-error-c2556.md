---
description: '자세한 정보: 컴파일러 오류 C2556'
title: 컴파일러 오류 C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 6c2233e10e763e959511c6b435e0d894e921905a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134487"
---
# <a name="compiler-error-c2556"></a>컴파일러 오류 C2556

' identifier ': 오버 로드 된 함수는 반환 형식만 다릅니다.

오버 로드 된 함수의 반환 형식은 같지만 동일한 매개 변수 목록입니다. 오버 로드 된 각 함수에는 고유한 형식 매개 변수 목록이 있어야 합니다.

다음 샘플에서는 C2556를 생성 합니다.

```cpp
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```
