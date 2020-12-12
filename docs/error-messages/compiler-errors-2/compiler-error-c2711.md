---
description: '자세한 정보: 컴파일러 오류 C2711'
title: 컴파일러 오류 C2711
ms.date: 11/04/2016
f1_keywords:
- C2711
helpviewer_keywords:
- C2711
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
ms.openlocfilehash: 19c55327b4d2726f679494bba1de188537f6e094
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320846"
---
# <a name="compiler-error-c2711"></a>컴파일러 오류 C2711

' function ':이 함수를 관리 되는 것으로 컴파일할 수 없습니다. 관리 되지 않는 #pragma를 사용 하십시오.

일부 지침에 따라 컴파일러가 바깥쪽 함수에 대해 MSIL을 생성 하지 못합니다.

다음 샘플에서는 C2711를 생성 합니다.

```cpp
// C2711.cpp
// compile with: /clr
// processor: x86
using namespace System;
value struct V {
   static const t = 10;
};

void bar() {
   V::t;
   __asm int 3   // C2711 inline asm can't be compiled managed
}
```
