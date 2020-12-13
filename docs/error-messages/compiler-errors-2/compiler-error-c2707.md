---
description: '자세한 정보: 컴파일러 오류 C2707'
title: 컴파일러 오류 C2707
ms.date: 11/04/2016
f1_keywords:
- C2707
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
ms.openlocfilehash: 1f615da7ebd2884cbaae26d7c1966725186e2883
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144835"
---
# <a name="compiler-error-c2707"></a>컴파일러 오류 C2707

' identifier ': 내장 함수의 컨텍스트가 잘못 되었습니다.

특정 컨텍스트에서는 구조적 예외 처리 내장 함수를 사용할 수 없습니다.

- `_exception_code()`예외 필터 또는 블록 외부 **`__except`**

- `_exception_info()` 예외 필터 외부

- `_abnormal_termination()`블록 외부 **`__finally`**

오류를 해결 하려면 예외 처리 내장 함수를 적절 한 컨텍스트에 배치 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2707를 생성 합니다.

```cpp
// C2707.cpp
#include <windows.h>
#include <stdio.h>

LONG MyFilter(LONG excode)
{
    return (excode == EXCEPTION_ACCESS_VIOLATION ?
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK
}

LONG func(void)
{
    int x, y;
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);

    __try
    {
        y = 0;
        x = 4 / y;
        return 0;
     }

    __except(MyFilter(GetExceptionCode()))
    {
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);
    }
}

int main()
{
    __try
    {
        func();
    } __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf_s("Caught exception\n");
    }
}
```
