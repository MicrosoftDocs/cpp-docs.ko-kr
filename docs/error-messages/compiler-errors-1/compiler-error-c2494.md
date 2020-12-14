---
description: '자세한 정보: 컴파일러 오류 C2494'
title: 컴파일러 오류 C2494
ms.date: 11/04/2016
f1_keywords:
- C2494
helpviewer_keywords:
- C2494
ms.assetid: 5dfd07ab-351d-49c9-b54e-f0a104776ab8
ms.openlocfilehash: 4842ad7360b4d8a943ee118cb56d79b694232c84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283656"
---
# <a name="compiler-error-c2494"></a>컴파일러 오류 C2494

> 필터 식 또는 __finally/finally 블록 내에서 '*keyword*'를 호출할 수 없습니다.

또는 블록에서 *키워드* 를 사용할 수 없습니다 **`__finally`** **`finally`** .

다음 샘플에서는 C2494를 생성 합니다.

```cpp
// C2494.cpp
#include <malloc.h>

int main() {
   __try {}
   __except ( _alloca(100), 1 ) {}   // C2494
   __try {}
   __finally {
      _alloca(100);   // C2494
   }
}
```

C2494는 **/clr** 을 사용 하는 경우에도 발생할 수 있습니다.

```cpp
// C2494b.cpp
// compile with: /clr
#include <malloc.h>

int main() {
   char * buf;
   try {}
   catch (char * buf2) {}
   finally {
      _alloca(100);   // C2494
   }
}
```
