---
description: '자세한 정보: 컴파일러 오류 C3139'
title: 컴파일러 오류 C3139
ms.date: 11/04/2016
f1_keywords:
- C3139
helpviewer_keywords:
- C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
ms.openlocfilehash: c04e7b3da1325a473f90f26f99a1e187d9b8f71c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304235"
---
# <a name="compiler-error-c3139"></a>컴파일러 오류 C3139

' struct ': 멤버 없이 UDT를 내보낼 수 없습니다.

빈 UDT (사용자 정의 형식)에 [내보내기](../../windows/attributes/export.md) 특성을 적용 하려고 했습니다. 예를 들어:

```cpp
// C3139.cpp
#include "unknwn.h"
[emitidl];
[module(name=xx)];

[export] struct MyStruct {   // C3139 empty type
};
int main(){}
```
