---
description: '자세히 알아보기: 최적화 pragma'
title: 최적화 pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragma, optimize
- optimize pragma
no-loc:
- pragma
ms.openlocfilehash: d9044788d0eea394867622d0f7aea1e365ad3399
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713456"
---
# <a name="optimize-no-locpragma"></a>`optimize` pragma

함수 별로 최적화를 지정 합니다.

## <a name="syntax"></a>구문

> **`#pragma optimize( "`** [ *최적화 목록* ] **`",`** { **`on`** | **`off`** } **`)`**

## <a name="remarks"></a>설명

는 **`optimize`** pragma 함수 외부에 표시 되어야 합니다. 가 표시 된 후에 정의 된 첫 번째 함수에 적용 됩니다 pragma . **`on`** 및 **`off`** 인수는 *최적화 목록* 에 지정 된 옵션을 on 또는 off로 설정 합니다.

*최적화 목록은* 다음 표에 표시 된 0 개 이상의 매개 변수를 사용할 수 있습니다.

### <a name="parameters-of-the-optimize-pragma"></a>optimize Pragma의 매개 변수

| 매개 변수 | 최적화 형식 |
|--------------------|--------------------------|
| **`g`** | 전역 최적화를 활성화합니다. |
| **`s`** 또는 **`t`** | 짧거나 빠른 기계어 코드 시퀀스를 지정합니다. |
| **`y`** | 프로그램 스택에서 프레임 포인터를 생성합니다. |

이러한 매개 변수는 컴파일러 옵션과 함께 사용 되는 동일한 문자 [`/O`](../build/reference/o-options-optimize-code.md) 입니다. 예를 들어 다음은 pragma **`/Os`** 컴파일러 옵션과 같습니다.

```cpp
#pragma optimize( "s", on )
```

**`optimize`** pragma 빈 문자열 ()과 함께를 사용 하는 **`""`** 것은 특별 한 형태의 지시문입니다.

매개 변수를 사용 하면 **`off`** 모든 최적화,,, **`g`** **`s`** **`t`** 및 **`y`** 가 해제 됩니다.

매개 변수를 사용 하는 경우 **`on`** 컴파일러 옵션을 사용 하 여 지정한 대로 최적화를 다시 설정 합니다 [`/O`](../build/reference/o-options-optimize-code.md) .

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
