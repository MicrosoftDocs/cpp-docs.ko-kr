---
description: '자세한 정보: 컴파일러 오류 C2007'
title: 컴파일러 오류 C2007
ms.date: 11/04/2016
f1_keywords:
- C2007
helpviewer_keywords:
- C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
ms.openlocfilehash: fa2ad780269079ef081f22d2c222e106443200e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298489"
---
# <a name="compiler-error-c2007"></a>컴파일러 오류 C2007

\#구문 정의

뒤에는 식별자가 표시 되지 않습니다 `#define` . 오류를 해결 하려면 식별자를 사용 합니다.

다음 샘플에서는 C2007를 생성 합니다.

```cpp
// C2007.cpp
#define   // C2007
```

해결 방법:

```cpp
// C2007b.cpp
// compile with: /c
#define true 1
```
