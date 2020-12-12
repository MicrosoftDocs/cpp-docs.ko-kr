---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4074'
title: 컴파일러 경고 (수준 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: cb04b242415769e995a46a9cdf3e0dff827ec1db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267627"
---
# <a name="compiler-warning-level-1-c4074"></a>컴파일러 경고 (수준 1) C4074

이니셜라이저가 컴파일러 예약 초기화 영역에 있습니다.

[#Pragma init_seg](../../preprocessor/init-seg.md)에 의해 지정 되는 컴파일러 초기화 영역은 Microsoft에서 예약 합니다. 이 영역의 코드는 C 런타임 라이브러리를 초기화 하기 전에 실행할 수 있습니다.

다음 샘플에서는 C4074를 생성 합니다.

```cpp
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
