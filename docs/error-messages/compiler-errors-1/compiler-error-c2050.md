---
description: '자세한 정보: 컴파일러 오류 C2050'
title: 컴파일러 오류 C2050
ms.date: 11/04/2016
f1_keywords:
- C2050
helpviewer_keywords:
- C2050
ms.assetid: 66aaed7d-00db-4ce1-a9d6-4447c1cf07ce
ms.openlocfilehash: a6e6221b0985ee509953b517ae04de9f0962fe3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175042"
---
# <a name="compiler-error-c2050"></a>컴파일러 오류 C2050

switch 식이 정수 계열이 아닙니다.

**`switch`** 식은 정수가 아닌 값으로 계산 됩니다. 이 오류를 해결 하려면 switch 문에서 정수 값만 사용 합니다.

다음 샘플에서는 C2050를 생성 합니다.

```cpp
// C2050.cpp
int main() {
   int a = 1;
   switch ("a") {   // C2050
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```

해결 방법:

```cpp
// C2050b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```
