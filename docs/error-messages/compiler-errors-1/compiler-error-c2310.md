---
description: '자세한 정보: 컴파일러 오류 C2310'
title: 컴파일러 오류 C2310
ms.date: 11/04/2016
f1_keywords:
- C2310
helpviewer_keywords:
- C2310
ms.assetid: 1969c682-b97e-43fb-b9a9-f783e7ff1710
ms.openlocfilehash: 235a80c8b144e348ec650baea7fd372de810b7a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282185"
---
# <a name="compiler-error-c2310"></a>컴파일러 오류 C2310

catch 처리기는 형식을 하나 지정 해야 합니다.

Catch 처리기에서 형식이 나 여러 형식을 지정 하지 않았습니다.

다음 샘플에서는 C2310를 생성 합니다.

```cpp
// C2310.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try {
      throw "Out of memory!";
   }
   catch( int ,int) {}   // C2310 two types
   // try the following line instead
   // catch( int)  {}
}
```
