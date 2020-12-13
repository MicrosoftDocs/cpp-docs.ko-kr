---
description: '자세한 정보: 컴파일러 오류 C2400'
title: 컴파일러 오류 C2400
ms.date: 11/04/2016
f1_keywords:
- C2400
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
ms.openlocfilehash: 64582d04e232c574dd132741dd1663e4055fe05f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145368"
---
# <a name="compiler-error-c2400"></a>컴파일러 오류 C2400

' context '에서 인라인 어셈블러 구문 오류가 발생 했습니다. ' token '이 있습니다.

토큰에 지정 된 컨텍스트에서 구문 오류가 발생 했습니다.

다음 샘플에서는 C2400를 생성 합니다.

```cpp
// C2400.cpp
// processor: x86
int main() {
   __asm {
      heh ax,bx;   // C2400, heh is not a valid x86 instruction
      mov ax,bx;   // OK
   }
}
```
