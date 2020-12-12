---
description: '자세한 정보: 컴파일러 오류 C2149'
title: 컴파일러 오류 C2149
ms.date: 11/04/2016
f1_keywords:
- C2149
helpviewer_keywords:
- C2149
ms.assetid: 7a106dab-d79f-41b9-85be-f36e86e4d2ab
ms.openlocfilehash: c93efe0648ebe064024177d61acd9d07150a1a1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235348"
---
# <a name="compiler-error-c2149"></a>컴파일러 오류 C2149

'identifier': 명명된 비트 필드의 너비가 0일 수 없습니다.

비트 필드는 명명되지 않은 경우에만 너비가 0일 수 있습니다.

다음 샘플에서는 C2149를 생성합니다.

```cpp
// C2149.cpp
// compile with: /c
struct C {
   int i : 0;   // C2149
   int j : 2;   // OK
};
```
