---
description: '자세한 정보: 컴파일러 오류 C3140'
title: 컴파일러 오류 C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: d4655589c5901a0ba609bde0cb5cb96907e087c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304222"
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
