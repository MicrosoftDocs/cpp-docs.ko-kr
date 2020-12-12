---
description: '자세한 정보: 컴파일러 오류 C3271'
title: 컴파일러 오류 C3271
ms.date: 11/04/2016
f1_keywords:
- C3271
helpviewer_keywords:
- C3271
ms.assetid: 16d8bd1d-2e30-4c6a-a07f-0c4f3342fab5
ms.openlocfilehash: 62ff98d27757aa8f339d99aa6a10d50bf7503a27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113661"
---
# <a name="compiler-error-c3271"></a>컴파일러 오류 C3271

'member': FieldOffset 특성에 대한 값 'value'가 잘못되었습니다.

**FieldOffset** 특성에 음수가 전달되었습니다.

다음 샘플에서는 C3271을 생성합니다.

```cpp
// C3271.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
value class MyStruct1 {
   public: [FieldOffset(0)] int a;
   public: [FieldOffset(-1)] long b;   // C3271
};
```
