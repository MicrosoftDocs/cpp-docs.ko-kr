---
title: 컴파일러 오류 C2311
ms.date: 11/04/2016
f1_keywords:
- C2311
helpviewer_keywords:
- C2311
ms.assetid: 1aff9bd5-ed0b-4db6-bbc0-01ac89850cf2
ms.openlocfilehash: e72ff7325e293697b0117e527b0d9edd55840481
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748179"
---
# <a name="compiler-error-c2311"></a>컴파일러 오류 C2311

' exception ': ' ... '에 의해 catch 되었습니다. 줄 번호

줄임표 (...)에 대 한 catch 처리기는 throw를 위한 마지막 처리기 여야 합니다.

다음 샘플에서는 C2311를 생성 합니다.

```cpp
// C2311.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try {
      throw "ooops!";
   }
   catch( ... ) {}
   catch( int ) {}   // C2311  ellipsis handler not last catch
}
```
