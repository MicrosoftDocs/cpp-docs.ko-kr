---
description: '자세한 정보: 컴파일러 오류 C2488'
title: 컴파일러 오류 C2488
ms.date: 11/04/2016
f1_keywords:
- C2488
helpviewer_keywords:
- C2488
ms.assetid: cd435909-43e4-43c6-a57c-5d02468ef75f
ms.openlocfilehash: bb6a36749b630c4193174314f47a150f0981b0df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305496"
---
# <a name="compiler-error-c2488"></a>컴파일러 오류 C2488

' identifier ': ' naked '는 비멤버 함수 정의에만 적용할 수 있습니다.

[Naked](../../cpp/naked-cpp.md) 특성이 함수 선언에 적용 되었습니다.

다음 샘플에서는 C2488를 생성 합니다.

```cpp
// C2488.cpp
// compile with: /c
// processor: x86
__declspec( naked ) void func();   // C2488  declaration, not definition
__declspec( naked ) void i;   // C2488  i is not a function

__declspec( naked ) void func() {}   // OK
```
