---
description: '자세한 정보: return 문 (c + +)'
title: return 문 (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: bb847900a0a9fc4c5d723d1b0392f27b6b5cf667
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340478"
---
# <a name="return-statement-c"></a>return 문 (C++)

함수 실행을 종료하고 컨트롤을 호출 함수(또는 `main` 함수에서 컨트롤을 이전하는 경우 운영 체제로)로 반환합니다. 호출 바로 다음 지점의 호출 함수에서 실행을 다시 시작합니다.

## <a name="syntax"></a>구문

```
return [expression];
```

## <a name="remarks"></a>설명

`expression` 절(있는 경우)은 초기화가 수행되고 있었던 것처럼 함수 선언에 지정된 형식으로 변환됩니다. 식의 형식을 **`return`** 함수 형식으로 변환 하면 임시 개체가 생성 될 수 있습니다. 임시 개체를 만드는 방법 및 시기에 대 한 자세한 내용은 [임시 개체](../cpp/temporary-objects.md)를 참조 하세요.

`expression` 절 값이 호출 함수에 반환됩니다. 식을 생략하면 함수의 반환 값이 정의되지 않습니다. 생성자와 소멸자 및 형식의 함수 **`void`** 는 문에 식을 지정할 수 없습니다 **`return`** . 다른 모든 형식의 함수는 문에 식을 지정 해야 합니다 **`return`** .

제어 흐름에서 함수 정의를 포함 하는 블록을 끝내 면 **`return`** 식이 없는 문이 실행 된 경우와 동일한 결과가 발생 합니다. 값을 반환할 때 선언되는 함수에는 올바르지 않습니다.

함수는 개수에 관계 없이 문을 포함할 수 있습니다 **`return`** .

다음 예에서는 문을 포함 하는 식을 사용 하 여 **`return`** 두 개의 정수 중 가장 큰 값을 가져옵니다.

## <a name="example"></a>예제

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>참고 항목

[점프 문](../cpp/jump-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
