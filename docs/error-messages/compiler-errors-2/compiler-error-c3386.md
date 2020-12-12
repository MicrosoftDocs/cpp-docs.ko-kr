---
description: '자세한 정보: 컴파일러 오류 C3386'
title: 컴파일러 오류 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 5bc80abe7c43e30c4114d0f3ffd7733c8ea3e9d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115900"
---
# <a name="compiler-error-c3386"></a>컴파일러 오류 C3386

> '*type-name*': `__declspec(dllexport)` / `__declspec(dllimport)` 관리 되는 형식 또는 WinRT 형식에 적용할 수 없습니다.

[`dllimport`](../../cpp/dllexport-dllimport.md)및 [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** 한정자는 관리 되는 형식 또는 Windows 런타임 형식에서 유효 하지 않습니다.

다음 샘플에서는 C3386 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
