---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4307'
title: 컴파일러 경고(수준 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: 5de4279d430f3275d61c6dca3d9db161c4ac5f11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339202"
---
# <a name="compiler-warning-level-2-c4307"></a>컴파일러 경고(수준 2) C4307

' operator ': 정수 계열 상수 오버플로입니다.

연산자는 할당 된 공간을 오버플로 하는 정수 상수를 반환 하는 식에 사용 됩니다. 상수에 대해 더 큰 형식을 사용 해야 할 수도 있습니다. **`signed int`** **`unsigned int`** 에서 **`signed int`** 부호를 나타내기 위해 1 비트를 사용 하기 때문에는 보다 작은 값을 보유 합니다.

다음 샘플에서는 C4307를 생성 합니다.

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```
