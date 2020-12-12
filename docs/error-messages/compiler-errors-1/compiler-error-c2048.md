---
description: '자세한 정보: 컴파일러 오류 C2048'
title: 컴파일러 오류 C2048
ms.date: 11/04/2016
f1_keywords:
- C2048
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
ms.openlocfilehash: cc87d0ca1670daa4cb137f4c3053030d188884e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175081"
---
# <a name="compiler-error-c2048"></a>컴파일러 오류 C2048

기본값이 둘 이상입니다.

**`switch`** 문에 레이블이 여러 개 포함 되어 있습니다 **`default`** . **`default`** 오류를 해결 하려면 레이블 중 하나를 삭제 합니다.

다음 샘플에서는 C2048을 생성합니다.

```cpp
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

해결 방법:

```cpp
// C2048b.cpp
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
