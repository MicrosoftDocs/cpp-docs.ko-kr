---
description: '자세한 정보: 컴파일러 오류 C2531'
title: 컴파일러 오류 C2531
ms.date: 11/04/2016
f1_keywords:
- C2531
helpviewer_keywords:
- C2531
ms.assetid: c49afe15-55f8-4dc8-ac01-bf653622a7db
ms.openlocfilehash: 1ab3f18ca91f1dd77a1d06ee43adcb1cc52e05e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302237"
---
# <a name="compiler-error-c2531"></a>컴파일러 오류 C2531

' identifier ': 비트 필드에 대 한 참조가 잘못 되었습니다.

비트 필드에 대 한 참조는 허용 되지 않습니다.

다음 샘플에서는 C2531를 생성 합니다.

```cpp
// C2531.cpp
// compile with: /c
class P {
   int &b1 : 10;   // C2531
   int b2 : 10;   // OK
};
```
