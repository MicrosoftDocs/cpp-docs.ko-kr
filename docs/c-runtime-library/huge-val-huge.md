---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
api_name:
- _HUGE
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 3a0469b7158e765b1b1c6f34cb01c0e90beb1401
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940274"
---
# <a name="huge_val-_huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>구문

```
#include <math.h>
```

## <a name="remarks"></a>설명

`HUGE_VAL`은 표현할 수 있는 가장 큰 double 값입니다. 오류가 발생하면 여러 런타임 수학 함수에 의해 이 값이 반환됩니다. 일부 함수의 경우 -`HUGE_VAL`가 반환됩니다. `HUGE_VAL`이 `_HUGE`로 정의되지만 런타임 수학 함수는 `HUGE_VAL`을 반환합니다. 또한 일관성을 위해 코드에 `HUGE_VAL`를 사용해야 합니다.

## <a name="see-also"></a>참고 항목

[전역 상수](../c-runtime-library/global-constants.md)
