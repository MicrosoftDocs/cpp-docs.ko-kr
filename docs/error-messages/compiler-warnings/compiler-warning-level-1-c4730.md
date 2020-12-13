---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4730'
title: 컴파일러 경고 (수준 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: e026d44bc76d58c934eeccc363f4385f43d15597
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150659"
---
# <a name="compiler-warning-level-1-c4730"></a>컴파일러 경고 (수준 1) C4730

' main ': _m64와 부동 소수점 식을 함께 지정 하면 잘못 된 코드가 생성 될 수 있습니다.

함수는 [__m64](../../cpp/m64.md) 및 **`float`** / **`double`** 형식을 사용 합니다. MMX 및 부동 소수점 레지스터는 동일한 실제 레지스터 공간을 공유 하므로 (동시에 사용할 수 없음) **`__m64`** **`float`** / **`double`** 같은 함수에서 및 형식을 사용 하면 데이터가 손상 되어 예외가 발생할 수 있습니다.

**`__m64`** 동일한 함수에서 형식 및 부동 소수점 형식을 안전 하 게 사용 하려면 형식 중 하나를 사용 하는 각 명령을 **_m_empty ()** (MMX) 또는 **_M_femms ()** (현재 위치 지정) 내장 함수를 사용 하 여 구분 해야 합니다.

다음 샘플에서는 C4730를 생성 합니다.

```cpp
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```
