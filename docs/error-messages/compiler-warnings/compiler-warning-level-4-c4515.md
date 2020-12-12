---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4515'
title: 컴파일러 경고(수준 4) C4515
ms.date: 11/04/2016
f1_keywords:
- C4515
helpviewer_keywords:
- C4515
ms.assetid: 167b5177-3f89-418b-b6c8-7de634f6b28f
ms.openlocfilehash: 6b9b3b84dfb49b56df49dbd4ad2f4510c9981976
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203421"
---
# <a name="compiler-warning-level-4-c4515"></a>컴파일러 경고(수준 4) C4515

' namespace ': 네임 스페이스가 자신을 사용 합니다.

네임 스페이스는 재귀적으로 사용 됩니다.

다음 샘플에서는 C4515를 생성 합니다.

```cpp
// C4515.cpp
// compile with: /W4
namespace A
{
   using namespace A; // C4515
}

int main()
{
}
```
