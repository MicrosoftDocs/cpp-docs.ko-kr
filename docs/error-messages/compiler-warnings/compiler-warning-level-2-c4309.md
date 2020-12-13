---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4309'
title: 컴파일러 경고(수준 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: 8ae49967078f8569a7830c2a2e2ce61f9d25e20d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339173"
---
# <a name="compiler-warning-level-2-c4309"></a>컴파일러 경고(수준 2) C4309

' conversion ': 상수 값이 잘렸습니다.

형식 변환으로 인해 상수가 할당 된 공간을 초과 합니다. 상수에 대해 더 큰 형식을 사용 해야 할 수도 있습니다.

다음 샘플에서는 C4309를 생성 합니다.

```cpp
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```
