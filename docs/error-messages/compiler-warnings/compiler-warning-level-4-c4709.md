---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4709'
title: 컴파일러 경고(수준 4) C4709
ms.date: 11/04/2016
f1_keywords:
- C4709
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
ms.openlocfilehash: 3138b8d95fd05cac113166ee9de9e7979f08223d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136229"
---
# <a name="compiler-warning-level-4-c4709"></a>컴파일러 경고(수준 4) C4709

배열 인덱스 식 내에 쉼표 연산자가 있습니다.

배열 인덱스 식에서 쉼표를 사용 하는 경우 컴파일러는 마지막 쉼표 뒤의 값을 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4709를 생성 합니다.

```cpp
// C4709.cpp
// compile with: /W4
#include <stdio.h>

int main()
{
    int arr[2][2];
    arr[0][0] = 10;
    arr[0][1] = 11;

    // Prints 10, not 11
    printf_s("\n%d",arr[0][1,0]);   // C4709
}
```
