---
description: '자세한 정보: 컴파일러 오류 C2318'
title: 컴파일러 오류 C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: 3cec8dbb46b10b4889a9cd026144bea228a28f15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322151"
---
# <a name="compiler-error-c2318"></a>컴파일러 오류 C2318

이 catch 처리기와 관련된 try 블록이 없습니다.

**`catch`** 처리기가 정의 되어 있지만 블록 앞에 오지 않습니다 **`try`** .

다음 샘플에서는 C2318을 생성합니다.

```cpp
// C2318.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   // no try block
   catch( int ) {}   // C2318
}
```

해결 방법:

```cpp
// C2318b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try{}
   catch( int ) {}
}
```
