---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4463'
title: 컴파일러 경고 (수준 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: fe4ea13c50e16bf5b72f5753fa989970db3cadde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251325"
---
# <a name="compiler-warning-level-4-c4463"></a>컴파일러 경고 (수준 4) C4463

> 오버플로 *low_value* *high_value* 에만 값을 보유할 수 있는 비트 필드에 *값* 할당

할당 된 *값* 이 비트 필드에서 보유할 수 있는 값 범위를 벗어납니다. 부호 있는 비트 필드 형식은 부호에 대해 상위 비트를 사용 하므로 *n* 이 비트 필드 크기인 경우 부호 있는 비트 필드의 범위는-2 <sup>n-1</sup> -2 <sup>n-1</sup>-1이 고, 부호 없는 비트 필드의 범위는 0에서 2 <sup>n</sup>-1 사이입니다.

## <a name="example"></a>예제

이 예제에서는 크기가 2 인 형식의 비트 필드에 값 3을 할당 하려고 하기 때문에 C4463를 생성 **`int`** 합니다. 범위는-2에서 1 사이입니다.

이 문제를 해결 하려면 할당 된 값을 허용 된 범위의 특정 값으로 변경할 수 있습니다. 비트 필드에서 0에서 3 범위의 부호 없는 값을 유지 하려면 선언 형식을로 변경 하면 됩니다 **`unsigned`** . 필드에-4에서 3 사이의 값을 저장 하려는 경우 비트 필드 크기를 3으로 변경할 수 있습니다.

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
