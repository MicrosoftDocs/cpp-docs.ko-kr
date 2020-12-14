---
description: '자세한 정보: 컴파일러 오류 C2001'
title: 컴파일러 오류 C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 81c033288ae673e95bc3454e2754d371f84225e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298632"
---
# <a name="compiler-error-c2001"></a>컴파일러 오류 C2001

상수에서 줄 바꿈

다음을 수행 하지 않으면 두 번째 줄에서 문자열 상수를 계속할 수 없습니다.

- 백슬래시를 사용 하 여 첫 번째 줄을 종료 합니다.

- 첫 번째 줄에서 큰따옴표를 사용 하 여 문자열을 닫고 다음 줄에서 문자열을 다른 큰따옴표로 엽니다.

\N을 사용 하 여 첫 번째 줄을 끝내는 것 만으로는 충분 하지 않습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2001를 생성 합니다.

```cpp
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

줄 연속 문자 뒤의 다음 줄의 시작 부분에 있는 공백은 문자열 상수에 포함 됩니다. 위에 표시 된 예제 중에는 줄 바꿈 문자가 문자열 상수에 포함 되지 않습니다. 다음과 같이 줄 바꿈 문자를 포함할 수 있습니다.

```cpp
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
