---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4319'
title: 컴파일러 경고(수준 1) C4319
ms.date: 01/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: af38714ab506fad389d9d2407b5a83aebf01f7c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340062"
---
# <a name="compiler-warning-level-1-c4319"></a>컴파일러 경고(수준 1) C4319

> ' ~ ': '*type1*'을 (를) 큰 크기의 '*type2*'로 확장 합니다.

**~**(비트 보수) 연산자의 결과는 부호 없는 형식으로 변환 될 때 0으로 확장 됩니다.

## <a name="example"></a>예제

다음 예제에서 `~(a - 1)` 는 32 비트의 부호 없는 long 식으로 계산 된 후 64 비트 0 확장으로 변환 됩니다. 따라서 예기치 않은 결과가 발생할 수 있습니다.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
