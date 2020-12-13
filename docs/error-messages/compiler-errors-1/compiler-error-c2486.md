---
description: '자세한 정보: 컴파일러 오류 C2486'
title: 컴파일러 오류 C2486
ms.date: 11/04/2016
f1_keywords:
- C2486
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
ms.openlocfilehash: c45e0bdb0f515743694fe372bea3afdb24e00177
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339360"
---
# <a name="compiler-error-c2486"></a>컴파일러 오류 C2486

' __LOCAL_SIZE '는 ' naked ' 특성이 있는 함수에만 사용할 수 있습니다.

인라인 어셈블리 함수에서 이름은 `__LOCAL_SIZE` [naked](../../cpp/naked-cpp.md) 특성으로 선언 된 함수에 예약 되어 있습니다.

다음 샘플에서는 C2486를 생성 합니다.

```cpp
// C2486.cpp
// processor: x86
void __declspec(naked) f1() {
   __asm {
      mov   eax,   __LOCAL_SIZE
   }
}
void f2() {
   __asm {
      mov   eax,   __LOCAL_SIZE   // C2486
   }
}
```
