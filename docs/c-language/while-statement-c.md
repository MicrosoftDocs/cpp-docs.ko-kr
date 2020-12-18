---
description: '자세한 정보: while 문(C)'
title: while 문 (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 3461372de48980a0591f890fdd366c9373aea78f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221854"
---
# <a name="while-statement-c"></a>while 문 (C)

**`while`** 문을 사용하면 지정된 식이 false가 될 때까지 문을 반복할 수 있습니다.

## <a name="syntax"></a>구문

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (**  *expression*  **)**  *statement*

*expression* 은 산술 형식이나 포인터 형식이어야 합니다. 다음과 같이 실행됩니다.

1. *expression* 이 계산됩니다.

1. 식이 처음에 false인 경우 **`while`** 문의 본문이 실행되지 않으며, **`while`** 문에서 프로그램의 다음 문으로 제어가 전달됩니다.

   *expression* 이 true(0이 아님)인 경우 문의 본문이 실행되고 1단계부터 반복됩니다.

문 본문 안에 있는 **`break`** , **`goto`** 또는 **`return`** 이 실행될 때 해당 **`while`** 문도 종료될 수 있습니다. **`while`** 루프를 종료하지 않고 반복을 종료하려면 **`continue`** 문을 사용합니다. **`continue`** 문은 **`while`** 문의 다음 반복으로 제어를 전달합니다.

다음은 **`while`** 문의 예제입니다.

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

이 예제에서는 `string2`의 문자를 `string1`에 복사합니다. `i`가 0보다 크거나 같은 경우 `string2[i]`가 `string1[i]`에 할당되고 `i`는 감소합니다. `i`가 0에 도달하거나 0 미만이면 **`while`** 문의 실행이 종료됩니다.

## <a name="see-also"></a>참조

[while 문(C++)](../cpp/while-statement-cpp.md)
