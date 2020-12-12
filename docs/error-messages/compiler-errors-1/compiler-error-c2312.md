---
description: '자세한 정보: 컴파일러 오류 C2312'
title: 컴파일러 오류 C2312
ms.date: 11/04/2016
f1_keywords:
- C2312
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
ms.openlocfilehash: 424f94a65162c9e2f0f138b6e42f1fe4981e1609
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282252"
---
# <a name="compiler-error-c2312"></a>컴파일러 오류 C2312

'exception1': 줄 번호에서 'exception2'에 의해 catch되었습니다.

두 개의 처리기가 동일한 예외 형식을 catch합니다.

다음 샘플에서는 C2312를 생성합니다.

```cpp
// C2312.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
    try {
        throw "ooops!";
    }
    catch( signed int ) {}
    catch( int ) {}   // C2312
}
```
