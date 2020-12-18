---
description: '자세한 정보: 예제 프로그램'
title: 예제 프로그램
ms.date: 11/04/2016
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
ms.openlocfilehash: 85cba2263e2e9f8f94bf8fda8ca1359cecc9a5d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196518"
---
# <a name="example-program"></a>예제 프로그램

다음 C 소스 프로그램은 두 개의 소스 파일로 구성됩니다. 이 프로그램에서는 C 프로그램에서 가능한 다양한 선언 및 정의 중 몇 가지를 간략하게 보여 줍니다. 이 설명서의 이후 섹션에서는 이러한 선언, 정의 및 초기화를 작성하는 방법과 **`static`** , **`extern`** 등의 C 키워드를 사용하는 방법을 설명합니다. `printf` 함수는 C 헤더 파일 STDIO.H에서 선언됩니다.

`main` 및 `max` 함수는 별도의 파일에 있는 것으로 간주되며, 프로그램의 실행은 `main` 함수로 시작됩니다. `main` 전에는 명시적 사용자 함수가 실행되지 않습니다.

```
/*****************************************************************
                    FILE1.C - main function
*****************************************************************/

#define ONE     1
#define TWO     2
#define THREE   3
#include <stdio.h>

int a = 1;                       // Defining declarations
int b = 2;                       //  of external variables

extern int max( int a, int b );  // Function prototype

int main()                       // Function definition
{                                //  for main function
    int c;                       // Definitions for
    int d;                       //  two uninitialized
                                 //  local variables

    extern int u;                // Referencing declaration
                                 //  of external variable
                                 //  defined elsewhere
    static int v;                // Definition of variable
                                 //  with continuous lifetime

    int w = ONE, x = TWO, y = THREE;
    int z = 0;

    z = max( x, y );             // Executable statements
    w = max( z, w );
    printf_s( "%d %d\n", z, w );
    return 0;
}

/****************************************************************
            FILE2.C - definition of max function
****************************************************************/

int max( int a, int b )          // Note formal parameters are
                                 //  included in function header
{
    if( a > b )
        return( a );
    else
        return( b );
}
```

FILE1.C에는 `max` 함수에 대한 프로토타입이 포함되어 있습니다. 함수가 사용되기 전에 선언되기 때문에 이러한 종류의 선언을 "정방향 선언"이라고 하기도 합니다. `main` 함수에 대한 정의에는 `max`에 대한 호출이 포함되어 있습니다.

`#define`으로 시작하는 줄은 전처리기 지시문입니다. 이러한 지시문은 FILE1.C 전반에서 `ONE`, `TWO` 및 `THREE` 식별자를 각각 숫자 `1`, `2` 및 `3`으로 대체하도록 전처리기에 지시합니다. 하지만 지시문은 별도로 컴파일된 후 FILE1.C와 연결되는 FILE2.C에 적용되지 않습니다. `#include`로 시작되는 줄은 `printf` 함수의 프로토타입이 포함된 STDIO.H 파일을 포함하도록 컴파일러에 지시합니다. [전처리기 지시문](../preprocessor/preprocessor-directives.md)은 *전처리기 참조* 에 설명되어 있습니다.

FILE1.C는 정의하는 선언을 사용하여 전역 변수 `a` 및 `b`를 초기화합니다. 지역 변수 `c` 및 `d`는 선언되지만 초기화되지는 않습니다. 이러한 모든 변수에 대해 스토리지가 할당됩니다. 정적 및 외부 변수 `u` 및 `v`는 자동으로 0으로 초기화됩니다. 따라서 `a`, `b`, `u` 및 `v`만 선언될 때 명시적으로나 암시적으로 초기화되기 때문에 의미 있는 값을 포함합니다. FILE2.C에는 `max`에 대한 함수 정의가 포함되어 있습니다. 이 정의는 FILE1.C에서 `max`에 대한 호출을 충족시킵니다.

식별자의 수명 및 표시 유형은 [수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)에 설명되어 있습니다. 함수에 대한 자세한 내용은 [함수](../c-language/functions-c.md)를 참조하세요.

## <a name="see-also"></a>참조

[원본 파일 및 원본 프로그램](../c-language/source-files-and-source-programs.md)
