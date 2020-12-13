---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4668'
title: 컴파일러 경고(수준 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 559043027bf9fab38470223ea7735ca70297aabf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134058"
---
# <a name="compiler-warning-level-4-c4668"></a>컴파일러 경고(수준 4) C4668

'symbol'은(는) 전처리기 매크로로 정의되어 있지 않으므로 'directives'에 해당하는 '0'으로 바뀝니다.

정의 되지 않은 기호가 전처리기 지시문과 함께 사용 되었습니다. 기호는 false로 평가 됩니다. 기호를 정의 하려면 [#define 지시문](../../preprocessor/hash-define-directive-c-cpp.md) 또는 [/d](../../build/reference/d-preprocessor-definitions.md) 컴파일러 옵션 중 하나를 사용할 수 있습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4668를 생성 합니다.

```cpp
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```
