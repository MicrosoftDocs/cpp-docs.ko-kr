---
description: '자세한 정보: 컴파일러 오류 C3239'
title: 컴파일러 오류 C3239
ms.date: 11/04/2016
f1_keywords:
- C3239
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
ms.openlocfilehash: ed16767b8076d93176936e53922426d1c87b35da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307355"
---
# <a name="compiler-error-c3239"></a>컴파일러 오류 C3239

'type': 공용 언어 런타임에서 interior/pin 포인터에 대한 pointer는 허용되지 않습니다.

컴파일러가 잘못된 형식을 찾았습니다.

다음 샘플에서는 C3229를 생성합니다.

```cpp
// C3239.cpp
// compile with: /clr
int main() {
   interior_ptr<int>* pip0;   // C3239

   // OK
   int * pip1;
   interior_ptr<int> pip2;
   int ** pip;
}
```
