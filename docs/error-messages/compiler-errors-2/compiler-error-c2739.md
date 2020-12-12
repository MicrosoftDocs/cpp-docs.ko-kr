---
description: '자세한 정보: 컴파일러 오류 C2739'
title: 컴파일러 오류 C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 2a65f552eeb8a0b475b5559aaa3f1ab6b0da0e25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123086"
---
# <a name="compiler-error-c2739"></a>컴파일러 오류 C2739

'number' : 관리되는 배열 또는 WinRT 배열의 명시적 차원은 1에서 32 사이여야 합니다.

배열 차원이 1에서 32 사이가 아니었습니다.

다음 샘플에서는 C2739 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
