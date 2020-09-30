---
title: 컴파일러 오류 C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: 672930d8c1d864c8ee5c2a08daca663bd29df167
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506151"
---
# <a name="compiler-error-c3140"></a>컴파일러 오류 C3140

같은 컴파일 단위에 여러 개의 ' module ' 특성을 사용할 수 없습니다.

[Module](../../windows/attributes/module-cpp.md) 특성은 프로젝트당 한 번만 정의할 수 있습니다.

다음 샘플에서는 C3140를 생성 합니다.

```cpp
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```
