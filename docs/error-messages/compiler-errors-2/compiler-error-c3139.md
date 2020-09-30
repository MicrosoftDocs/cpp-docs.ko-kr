---
title: 컴파일러 오류 C3139
ms.date: 11/04/2016
f1_keywords:
- C3139
helpviewer_keywords:
- C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
ms.openlocfilehash: 86f905653c6e1574a1d1c0a1225294b3a4dc5f3e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506180"
---
# <a name="compiler-error-c3139"></a>컴파일러 오류 C3139

' struct ': 멤버 없이 UDT를 내보낼 수 없습니다.

빈 UDT (사용자 정의 형식)에 [내보내기](../../windows/attributes/export.md) 특성을 적용 하려고 했습니다. 다음은 그 예입니다.

```cpp
// C3139.cpp
#include "unknwn.h"
[emitidl];
[module(name=xx)];

[export] struct MyStruct {   // C3139 empty type
};
int main(){}
```
