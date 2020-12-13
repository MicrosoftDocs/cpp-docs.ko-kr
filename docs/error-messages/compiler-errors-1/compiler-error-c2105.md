---
description: '자세한 정보: 컴파일러 오류 C2105'
title: 컴파일러 오류 C2105
ms.date: 11/04/2016
f1_keywords:
- C2105
helpviewer_keywords:
- C2105
ms.assetid: 19b7f7bc-a9da-4d23-8193-005b6d09274f
ms.openlocfilehash: aaf00390e13bcc432251731c347b963ba3c3dc16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341271"
---
# <a name="compiler-error-c2105"></a>컴파일러 오류 C2105

' operator '에 l-value가 필요 합니다.

연산자에는 피연산자로 l-value가 있어야 합니다.

다음 샘플에서는 C2105를 생성 합니다.

```cpp
// C2105.cpp
int main() {
   unsigned char * p1 = 0;
   unsigned int * p2 = (unsigned int *)p1;
   p2++;

   unsigned int * p = 0;
   p++;   // ok

   p2 = (unsigned int *)p1;
   ((unsigned int *)p1)++;   // C2105
}
```

다음 샘플에서는 C2105를 생성 합니다.

```cpp
// C2105b.cpp
int main() {
   int a[10] = {0};
   int b[10] = {0};
   ++(a , b);   // C2105

   // OK
   ++(a[0] , b[0]);
   ++a[0];
}
```
