---
description: '자세한 정보: 컴파일러 오류 C2153'
title: 컴파일러 오류 C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: 0b5ded0908f3c12033f1c2b3b034b41b52e847cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181295"
---
# <a name="compiler-error-c2153"></a>컴파일러 오류 C2153

16 진수 상수에는 16 진수가 적어도 하나는 있어야 합니다.

16 진수 상수 0x, 0X 및 \x가 잘못 되었습니다. 하나 이상의 16 진수가 x 또는 X 뒤에와 야 합니다.

다음 샘플에서는 C2153를 생성 합니다.

```cpp
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```
