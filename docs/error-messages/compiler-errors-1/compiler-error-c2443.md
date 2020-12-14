---
description: '자세한 정보: 컴파일러 오류 C2443'
title: 컴파일러 오류 C2443
ms.date: 11/04/2016
f1_keywords:
- C2443
helpviewer_keywords:
- C2443
ms.assetid: 315330d5-24bc-4193-a531-0642095be58f
ms.openlocfilehash: 122cc2aabe2d01ffb5e1d28420fbf6c08be0617d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189719"
---
# <a name="compiler-error-c2443"></a>컴파일러 오류 C2443

피연산자 크기가 충돌 합니다.

명령에는 피연산자의 크기가 동일 해야 합니다.

다음 샘플에서는 C2443를 생성 합니다.

```cpp
// C2443.cpp
// processor: x86
short var;
int main() {
   __asm xchg ax,bl   // C2443
   __asm mov al,red   // C2443
   __asm mov al,BYTE PTR var   // OK
}
```
