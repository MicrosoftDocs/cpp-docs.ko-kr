---
title: 컴파일러 경고(수준 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 737cf7ad00bfefd429792eed3f730844789e0c02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391766"
---
# <a name="compiler-warning-level-1-c4163"></a>컴파일러 경고(수준 1) C4163

'identifier': 내장 함수로 사용할 수 없습니다.

지정된 함수를 [intrinsic](../../preprocessor/intrinsic.md) 함수로 사용할 수 없습니다. 컴파일러에서 잘못된 함수 이름은 무시합니다.

다음 샘플에서는 C4163을 생성합니다.

```
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```