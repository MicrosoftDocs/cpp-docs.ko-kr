---
description: '자세한 정보: 컴파일러 오류 C2046'
title: 컴파일러 오류 C2046
ms.date: 11/04/2016
f1_keywords:
- C2046
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
ms.openlocfilehash: 7d1735c4f27c80f2830b7f36a9f3533033119535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175159"
---
# <a name="compiler-error-c2046"></a>컴파일러 오류 C2046

대/소문자가 잘못되었습니다.

키워드는 `case` 문에만 나타날 수 있습니다 **`switch`** .

다음 샘플에서는 C2046을 생성합니다.

```cpp
// C2046.cpp
int main() {
   case 0:   // C2046
}
```

해결 방법:

```cpp
// C2046b.cpp
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
