---
description: '자세한 정보: 컴파일러 오류 C2128'
title: 컴파일러 오류 C2128
ms.date: 11/04/2016
f1_keywords:
- c2128
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
ms.openlocfilehash: fd72ffd45206a885d56b3d2f1821240279f06e21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323170"
---
# <a name="compiler-error-c2128"></a>컴파일러 오류 C2128

' function ': alloc_text/same_seg는 C 링크가 있는 함수에만 적용할 수 있습니다.

`#pragma alloc_text` 는 C 링크를 포함 하도록 선언 된 함수에만 사용할 수 있습니다.

다음 샘플에서는 C2128를 생성 합니다.

```cpp
// C2128.cpp
// compile with: /c

// Delete the following line to resolve.
void func();
// #pragma alloc_text("my segment", func)   // C2128

extern "C" {
void func();
}

#pragma alloc_text("my segment", func)
void func() {}
```
