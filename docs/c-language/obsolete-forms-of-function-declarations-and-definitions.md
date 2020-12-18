---
description: '자세한 정보: 사용되지 않는 함수 선언 및 정의 폼'
title: 사용되지 않는 함수 선언 및 정의 폼
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: 7cd66ba1600d4a5fd381819f4b1d3f0beeb30f0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256915"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>사용되지 않는 함수 선언 및 정의 폼

이전 스타일 함수 선언 및 정의는 매개 변수 선언에 대해 ANSI C 표준에 의해 권장되는 구문과 약간 다른 규칙을 사용합니다. 첫째로 이전 스타일 선언에는 매개 변수 목록이 없습니다. 둘째로 함수 정의에서는 매개 변수가 나열되지만 해당 형식은 매개 변수 목록에 선언되지 않습니다. 형식 선언은 함수 본문을 구성하는 복합 문의 앞에 와야 합니다. 이전 스타일 구문은 사용되지 않으며 새 코드에 사용하면 안 됩니다. 그러나 이전 스타일 구문을 사용하는 코드는 여전히 지원됩니다. 다음 예제에서는 사용되지 않는 선언 및 정의 형태를 보여 줍니다.

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

**`int`** 와 동일한 크기의 정수 또는 포인터를 반환하는 함수는 선언을 가질 필요가 없습니다(선언이 권장되기는 함).

ANSI C 표준에 부합하기 위해 줄임표를 사용하는 이전 스타일 함수 선언은 이제 /Za 옵션으로 컴파일할 때 오류를 생성하며 /Ze로 컴파일할 때 수준 4 경고를 생성합니다. 예를 들어:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

다음과 같이 이 선언을 프로토타입으로 다시 작성해야 합니다.

```cpp
void funct1( int a, ... )
{
}
```

승격된 형식과 동일하지 않은 형식이 있는 매개 변수나 줄임표로 동일한 함수를 이후에 선언하거나 정의하는 경우에도 이전 스타일 함수 선언으로 인해 경고가 생성됩니다.

다음 섹션 [C 함수 정의](../c-language/c-function-definitions.md)에서는 이전 스타일 구문을 포함하여 함수 정의를 위한 구문을 보여 줍니다. 이전 스타일 구문에서 매개 변수 목록의 비터미널은 *identifier-list* 입니다.

## <a name="see-also"></a>참조

[함수 개요](../c-language/overview-of-functions.md)
