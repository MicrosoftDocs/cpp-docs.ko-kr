---
description: '자세한 정보: 컴파일러 오류 C3270'
title: 컴파일러 오류 C3270
ms.date: 11/04/2016
f1_keywords:
- C3270
helpviewer_keywords:
- C3270
ms.assetid: 70e6e76b-7415-48f5-a61e-2ed50caf08e4
ms.openlocfilehash: 976e4c9e6b1448c01b58b754d6ca4a09a1607fbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185897"
---
# <a name="compiler-error-c3270"></a>컴파일러 오류 C3270

'field': FieldOffset 특성은 필요한 StructLayout(Explicit) 컨텍스트에서만 사용할 수 있습니다.

**StructLayout (Explicit)** 가 적용 되는 경우에만 허용 되는 **FieldOffset** 으로 표시 된 필드입니다.

다음 샘플에서는 C3270을 생성합니다.

```cpp
// C3270_2.cpp
// compile with: /clr /c
using namespace System::Runtime::InteropServices;

[ StructLayout(LayoutKind::Sequential) ]
// try the following line instead
// [ StructLayout(LayoutKind::Explicit) ]
public value struct MYUNION
{
   [FieldOffset(0)] int a;   // C3270
   // ...
};
```
