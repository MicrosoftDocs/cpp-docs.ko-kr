---
description: '자세한 정보: 컴파일러 오류 C3272'
title: 컴파일러 오류 C3272
ms.date: 11/04/2016
f1_keywords:
- C3272
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
ms.openlocfilehash: 1222db43922081efbb8195c29b905d2efc7bbe5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185754"
---
# <a name="compiler-error-c3272"></a>컴파일러 오류 C3272

'symbol': 기호는 StructLayout(LayoutKind::Explicit)으로 정의된 typename 형식의 멤버이므로 FieldOffset이 필요합니다.

`StructLayout(LayoutKind::Explicit)`이 적용 되는 경우 필드는로 표시 되어야 합니다 `FieldOffset` .

다음 샘플에서는 C3272를 생성합니다.

```cpp
// C3272_2.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
ref struct X
{
   int data_;   // C3272
   // try the following line instead
   // [FieldOffset(0)] int data_;
};
```
