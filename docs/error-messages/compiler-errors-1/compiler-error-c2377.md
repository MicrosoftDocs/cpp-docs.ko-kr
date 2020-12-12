---
description: '자세한 정보: 컴파일러 오류 C2377'
title: 컴파일러 오류 C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: 727472410bea0db9f837388956e8af5c9a8433d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174743"
---
# <a name="compiler-error-c2377"></a>컴파일러 오류 C2377

'identifier': 재정의. 다른 기호를 사용하여 형식 정의를 오버로드할 수 없습니다.

식별자가 다시 **`typedef`** 정의 됩니다.

다음 샘플에서는 C2377을 생성합니다.

```cpp
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```
