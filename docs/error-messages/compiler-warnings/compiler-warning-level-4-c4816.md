---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4816'
title: 컴파일러 경고(수준 4) C4816
ms.date: 11/04/2016
f1_keywords:
- C4816
helpviewer_keywords:
- C4816
ms.assetid: 60f730ae-d942-4db9-ab97-41d4a874d8da
ms.openlocfilehash: b48f6f0141966a75a9a15f3f172a32fd81a52354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330501"
---
# <a name="compiler-warning-level-4-c4816"></a>컴파일러 경고(수준 4) C4816

'param': 매개 변수에 크기가 0인 배열이 있으면 잘리게 됩니다(개체가 참조로 전달된 경우 제외).

크기가 0인 배열을 가진 개체에 대한 매개 변수가 참조로 전달되지 않았습니다. 개체가 전달될 때 배열이 복사되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4816을 생성합니다.

```cpp
// C4816.cpp
// compile with: /W4
#include <stdio.h>

extern "C" int printf_s(const char *, ...);

#pragma warning(disable : 4200)

struct S1
{
    int i;
    char cArr[];
};

void TestErr(S1 s1)   // C4816 param with zero-array
                      // not passed by reference
{
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);
}

void TestOk(S1 &s1)
{
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);
}

int main()
{
    S1 myS_1 = { 6, 'a', 'b', 'c' };
    TestErr(myS_1);
    TestOk(myS_1);
}
```
