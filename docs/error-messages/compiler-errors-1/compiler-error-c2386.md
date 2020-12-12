---
description: '자세한 정보: 컴파일러 오류 C2386'
title: 컴파일러 오류 C2386
ms.date: 11/04/2016
f1_keywords:
- C2386
helpviewer_keywords:
- C2386
ms.assetid: aaaa1284-34a0-4da2-8547-9fcbb559dae0
ms.openlocfilehash: 65dca1cf052cab1292f6f594a316536a5097a032
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204097"
---
# <a name="compiler-error-c2386"></a>컴파일러 오류 C2386

'symbol': 이름이 같은 기호가 현재 범위에 이미 있습니다.

네임스페이스 별칭을 만들려고 했지만 선택한 이름이 이미 있습니다.

다음 샘플에서는 C2386을 생성합니다.

```cpp
// C2386.cpp
namespace A {
   int k;
}

int i;
namespace i = A;   // C2386, i already exists
```
