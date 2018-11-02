---
title: 컴파일러 오류 C2488
ms.date: 11/04/2016
f1_keywords:
- C2488
helpviewer_keywords:
- C2488
ms.assetid: cd435909-43e4-43c6-a57c-5d02468ef75f
ms.openlocfilehash: 9b49d49c8a261bb3d636446f820a45699361830f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452119"
---
# <a name="compiler-error-c2488"></a>컴파일러 오류 C2488

'identifier': 'naked'만 적용할 수 있습니다 비멤버 함수 정의

합니다 [naked](../../cpp/naked-cpp.md) 함수 선언에 특성이 적용 되었습니다.

다음 샘플에서는 C2488 오류가 생성 됩니다.

```
// C2488.cpp
// compile with: /c
// processor: x86
__declspec( naked ) void func();   // C2488  declaration, not definition
__declspec( naked ) void i;   // C2488  i is not a function

__declspec( naked ) void func() {}   // OK
```