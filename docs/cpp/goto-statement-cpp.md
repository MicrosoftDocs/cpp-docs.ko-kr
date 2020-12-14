---
description: '다음에 대 한 자세한 정보: goto 문 (c + +)'
title: goto 문 (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: c8f94a5c2dfbd6ff3bd33223944180a4d1642b0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221386"
---
# <a name="goto-statement-c"></a>goto 문 (C++)

**`goto`** 문은 지정 된 식별자로 레이블이 지정 된 문으로 제어를 무조건 전송 합니다.

## <a name="syntax"></a>구문

```
goto identifier;
```

## <a name="remarks"></a>설명

`identifier`에 의해 지정된 레이블 문은 현재 함수에 있어야 합니다. 모든 `identifier` 이름은 내부 네임스페이스의 멤버이므로 다른 식별자를 방해하지 않습니다.

문 레이블은 문에만 의미가 있으며 **`goto`** , 그렇지 않은 경우에는 문 레이블이 무시 됩니다. 레이블을 다시 선언할 수 없습니다.

**`goto`** 문은 해당 위치의 범위에 있는 변수의 초기화를 건너뛴 위치로 제어를 전달할 수 없습니다. 다음 예에서는 C2362을 발생 시킵니다.

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

**`break`** **`continue`** **`return`** 가능 하면 문 대신, 및 문을 사용 하는 것이 좋은 프로그래밍 스타일입니다 **`goto`** . 그러나 **`break`** 문은 한 수준의 루프 에서만 종료 되므로 문을 사용 하 여 **`goto`** 깊게 중첩 된 루프를 종료 해야 할 수도 있습니다.

레이블 및 문에 대 한 자세한 내용은 레이블 **`goto`** [문](../cpp/labeled-statements.md)을 참조 하십시오.

## <a name="example"></a>예제

이 예제에서 문은가 **`goto`** 3 인 경우 레이블이 지정 된 지점으로 제어를 전달 `stop` `i` 합니다.

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>참고 항목

[점프 문](../cpp/jump-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
