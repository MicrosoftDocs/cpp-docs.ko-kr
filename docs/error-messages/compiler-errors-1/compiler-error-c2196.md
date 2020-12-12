---
description: '자세한 정보: 컴파일러 오류 C2196'
title: 컴파일러 오류 C2196
ms.date: 11/04/2016
f1_keywords:
- C2196
helpviewer_keywords:
- C2196
ms.assetid: fd2f6a58-48ce-4e58-96f8-e37720feb8e7
ms.openlocfilehash: 7c82cd145cff43d8773f87e65a09eee32185ffb4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305475"
---
# <a name="compiler-error-c2196"></a>컴파일러 오류 C2196

case 값 'value'를 이미 사용했습니다.

switch 문에서 동일한 case 값을 두 번 이상 사용합니다.

다음 샘플에서는 C2196을 생성합니다.

```cpp
// C2196.cpp
int main() {
   int i = 0;
   switch( i ) {
   case 0:
      break;
   case 0:   // C2196
   // try the following line instead
   // case 1:
      break;
   }
}
```
