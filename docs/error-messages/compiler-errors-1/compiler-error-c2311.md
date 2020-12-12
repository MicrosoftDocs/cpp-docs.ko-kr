---
description: '자세한 정보: 컴파일러 오류 C2311'
title: 컴파일러 오류 C2311
ms.date: 11/04/2016
f1_keywords:
- C2311
helpviewer_keywords:
- C2311
ms.assetid: 1aff9bd5-ed0b-4db6-bbc0-01ac89850cf2
ms.openlocfilehash: bf835f9add53951c6c61cbf1345917587e046b65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282212"
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
