---
description: '자세한 정보: 수명 및 표시 유형에 대한 요약'
title: 수명 및 표시 유형에 대한 요약
ms.date: 11/04/2016
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
ms.openlocfilehash: a1ce139b4fdc2562862eaef1828ec481685eca60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114483"
---
# <a name="summary-of-lifetime-and-visibility"></a>수명 및 표시 유형에 대한 요약

다음 표에서는 대부분의 식별자에 대한 수명 및 표시 유형 특징을 요약합니다. 처음 세 열에서는 수명과 표시 유형을 정의하는 특성을 제공합니다. 처음 세 열에서 제공하는 특성이 있는 식별자의 수명과 표시 유형은 4번째 열과 5번째 열에 표시되어 있습니다. 가능한 모든 경우가 이 표에 포함되어 있지는 않습니다. 자세한 내용은 [스토리지 클래스](../c-language/c-storage-classes.md)를 참조하세요.

### <a name="summary-of-lifetime-and-visibility"></a>수명 및 표시 유형에 대한 요약

|특성:<br /><br /> Level|항목|스토리지 클래스<br /><br /> 지정자|결과:<br /><br /> 수명|표시 유형|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|파일 범위|변수 정의|**`static`**|전역|이 항목이 발생하는 소스 파일의 나머지 부분|
||변수 선언|**`extern`**|전역|이 항목이 발생하는 소스 파일의 나머지 부분|
||함수 프로토타입 또는 정의|**`static`**|전역|단일 소스 파일|
||함수 프로토타입|**`extern`**|전역|소스 파일의 나머지 부분|
|블록 범위|변수 선언|**`extern`**|전역|블록|
||변수 정의|**`static`**|전역|블록|
||변수 정의|**`auto`** 또는 **`register`**|로컬|블록|

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 변수의 블록, 중첩 및 표시 유형을 보여 줍니다.

### <a name="code"></a>코드

```c
// Lifetime_and_Visibility.c

#include <stdio.h>

int i = 1;  // i defined at external level

int main()  // main function defined at external level
{
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)
    {                                 // Begin first nested block
        int i = 2, j = 3;          // i and j defined at internal level
        printf_s( "%d %d\n", i, j );  // Prints 2, 3
        {                             // Begin second nested block
            int i = 0;                // i is redefined
            printf_s( "%d %d\n", i, j ); // Prints 0, 3
        }                             // End of second nested block
        printf_s( "%d\n", i );        // Prints 2 (outer definition
                                      //  restored)
    }                                 // End of first nested block
    printf_s( "%d\n", i );            // Prints 1 (external level
                                      // definition restored)
    return 0;
}
```

### <a name="comments"></a>주석

이 예제에는 네 가지 수준의 표시 유형(외부 수준과 세 가지 블록 수준)이 있습니다. 값은 각 문 다음에 있는 주석에 언급된 것처럼 화면에 출력됩니다.

## <a name="see-also"></a>참조

[수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)
