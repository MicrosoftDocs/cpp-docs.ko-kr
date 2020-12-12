---
description: '자세한 정보: 컴파일러 오류 C2042'
title: 컴파일러 오류 C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 3dd4ae7471997e518c854d570b4a2e3aa4ec3856
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175211"
---
# <a name="compiler-error-c2042"></a>컴파일러 오류 C2042

signed/unsigned 키워드는 함께 사용할 수 없습니다.

및 키워드 **`signed`** 는 **`unsigned`** 단일 선언에 사용 됩니다.

다음 샘플에서는 C2042를 생성합니다.

```cpp
// C2042.cpp
unsigned signed int i;   // C2042
```

해결 방법:

```cpp
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```
