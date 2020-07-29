---
title: 컴파일러 오류 C2493
ms.date: 11/04/2016
f1_keywords:
- C2493
helpviewer_keywords:
- C2493
ms.assetid: 68316cd5-682b-49c3-b6ea-23c4e5d296cf
ms.openlocfilehash: e3c38167ff2b6d2b2f78a1357a9450a70cb421cc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216195"
---
# <a name="compiler-error-c2493"></a>컴파일러 오류 C2493

__based 형식이 잘못 되었습니다.

**`__based`** 식은 포인터를 기반으로 해야 합니다.

다음 샘플에서는 C2493를 생성 합니다.

```cpp
// C2493.cpp
// compile with: /c
char mybase;
int __based(mybase) ptr;   // C2493

// OK
char * mybase;
int __based(mybase) * ptr;
```
