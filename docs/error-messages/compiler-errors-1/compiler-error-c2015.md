---
description: '자세한 정보: 컴파일러 오류 C2015'
title: 컴파일러 오류 C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 0c27dbf8f7383ebd6424e9482fd1ce8cc0839a39
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220957"
---
# <a name="compiler-error-c2015"></a>컴파일러 오류 C2015

상수에 문자가 너무 많습니다.

문자 상수에는 두 개 이상의 문자가 포함 되어 있습니다. 한도는 표준 문자 상수에 대 한 문자이 고, 긴 문자 상수인 경우 두 문자입니다.

이스케이프 시퀀스 (예: \t)는 단일 문자로 변환 됩니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2015를 생성 합니다.

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

C2015은 정수로 변환 된 Microsoft 확장 문자 상수를 사용 하는 경우에도 발생할 수 있습니다.  다음 샘플에서는 C2015를 생성 합니다.

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
