---
description: '자세한 정보: 컴파일러 오류 C2051'
title: 컴파일러 오류 C2051
ms.date: 11/04/2016
f1_keywords:
- C2051
helpviewer_keywords:
- C2051
ms.assetid: 81c0469a-78e2-49fa-bd76-97cdb135e3ea
ms.openlocfilehash: ceea0466ef5f285c9cf7b3aa6bdf312ec25f283e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175016"
---
# <a name="compiler-error-c2051"></a>컴파일러 오류 C2051

case 식이 상수가 아닙니다.

Case 식은 정수 상수 여야 합니다.

다음 샘플에서는 C2051를 생성 합니다.

```cpp
// C2051.cpp
class X {};

int main() {
   static X x;
   int i = 0;

   switch (i) {
      case x:   // C2051 use constant expression to resolve error
         break;
      default:
         break;
   }
}
```

해결 방법:

```cpp
// C2051b.cpp
class X {};

int main() {
   static X x;
   int i = 0;

   switch (i) {
      case 1:
         break;
      default:
         break;
   }
}
```
