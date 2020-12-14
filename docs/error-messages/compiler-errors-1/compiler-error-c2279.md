---
description: '자세한 정보: 컴파일러 오류 C2279'
title: 컴파일러 오류 C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: e0f8822c77bd243bc2ec6002027d8eadb2aaf8a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228978"
---
# <a name="compiler-error-c2279"></a>컴파일러 오류 C2279

typedef 선언에는 예외 사양이 나타날 수 없습니다.

**/Za** 에서는 typedef 선언에 [예외 사양을](../../cpp/exception-specifications-throw-cpp.md) 사용할 수 없습니다.

다음 샘플에서는 C2279를 생성 합니다.

```cpp
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```
