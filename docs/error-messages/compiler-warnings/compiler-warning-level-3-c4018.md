---
title: 컴파일러 경고 (수준 3) C4018
description: Microsoft C/c + + 컴파일러 경고 C4018, 해당 원인 및 해결 방법
ms.date: 10/16/2020
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.openlocfilehash: b9d01f6b733c2ca18880aa6f4b6fca9771f8123f
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176180"
---
# <a name="compiler-warning-level-3-c4018"></a>컴파일러 경고 (수준 3) C4018

> '*token*': signed/unsigned가 일치 하지 않습니다.

*토큰* 연산자를 사용 하 여 **`signed`** 및 숫자를 비교 하 고 **`unsigned`** 컴파일러에서 값을로 변환 해야 합니다 **`signed`** **`unsigned`** .

## <a name="remarks"></a>설명

이 경고를 해결 하는 한 가지 방법은 및 형식을 비교할 때 두 가지 형식 중 하나를 캐스팅 하는 것입니다 **`signed`** **`unsigned`** .

## <a name="example"></a>예제

이 샘플에서는 C4018를 생성 하 고 해결 방법을 보여 줍니다.

```cpp
// C4018.cpp
// compile with: cl /EHsc /W4 C4018.cpp
int main() {
    unsigned int uc = 0;
    int c = 0;
    unsigned int c2 = c; // implicit conversion

    if (uc < c)           // C4018
        uc = 0;

    if (uc < unsigned(c)) // OK
        uc = 0;

    if (uc < c2)          // Also OK
       uc = 0;
}
```

## <a name="see-also"></a>참고 항목

[컴파일러 경고 (수준 4) C4388](c4388.md)\
[컴파일러 경고 (수준 4) C4389](compiler-warning-level-4-c4389.md)
