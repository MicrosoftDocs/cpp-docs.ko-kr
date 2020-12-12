---
description: '자세한 정보: 컴파일러 오류 C2047'
title: 컴파일러 오류 C2047
ms.date: 11/04/2016
f1_keywords:
- C2047
helpviewer_keywords:
- C2047
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
ms.openlocfilehash: 40df340017b134a3d2abe092478658f92142298d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175120"
---
# <a name="compiler-error-c2047"></a>컴파일러 오류 C2047

기본값이 잘못되었습니다.

키워드는 **`default`** 문에만 나타날 수 있습니다 **`switch`** .

다음 샘플에서는 C2047을 생성합니다.

```cpp
// C2047.cpp
int main() {
   int i = 0;
   default:   // C2047
   switch(i) {
      case 0:
      break;
   }
}
```

해결 방법:

```cpp
// C2047b.cpp
int main() {
   int i = 0;
   switch(i) {
      case 0:
      break;
      default:
      break;
   }
}
```
