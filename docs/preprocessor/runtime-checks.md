---
description: pragmaMicrosoft C/c + +의 runtime_checks 지시문에 대해 자세히 알아보세요.
title: runtime_checks pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragma, runtime_checks
no-loc:
- pragma
ms.openlocfilehash: 4932126ffe33d2f8a99f6d94e3c58d2c0322df92
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98712819"
---
# <a name="runtime_checks-no-locpragma"></a>`runtime_checks` pragma

컴파일러 옵션 설정을 사용 하지 않도록 설정 하거나 복원 [`/RTC`](../build/reference/rtc-run-time-error-checks.md) 합니다.

## <a name="syntax"></a>구문

> **`#pragma runtime_checks( "`** [ *런타임 검사 옵션* ] **`",`** { **`restore`** | **`off`** } **`)`**

## <a name="remarks"></a>설명

컴파일러 옵션으로 설정 되지 않은 런타임 검사를 사용 하도록 설정할 수 없습니다. 예를 들어 명령줄에을 지정 하지 않는 경우 **`/RTCs`** 를 지정 하면 `#pragma runtime_checks( "s", restore)` 스택 프레임 확인을 사용 하지 않습니다.

는 **`runtime_checks`** pragma 함수 외부에 표시 되어야 하 고가 표시 된 후에 정의 된 첫 번째 함수에 적용 pragma 됩니다. **`restore`** 및 **`off`** 인수는 **`runtime_checks`** pragma on 또는 off에 지정 된 옵션을 설정 합니다.

*런타임 검사 옵션* 은 다음 표에 표시 된 0 개 이상의 매개 변수를 사용할 수 있습니다.

### <a name="parameters-of-the-runtime_checks-pragma"></a>runtime_checks Pragma의 매개 변수

| 매개 변수 | 런타임 검사 형식 |
|--------------------|-----------------------------|
| **`s`** | 스택(프레임)을 확인하도록 설정합니다. |
| **`c`** | 데이터 손실이 발생하는 더 작은 데이터 형식에 값이 할당되는 경우 이를 보고합니다. |
| **`u`** | 변수가 정의 되기 전에 사용 되는 경우를 보고 합니다. |

이러한 매개 변수는 컴파일러 옵션에 사용 된 것과 동일 합니다 **`/RTC`** . 예:

```cpp
#pragma runtime_checks( "sc", restore )
```

**`runtime_checks`** pragma 빈 문자열 ()과 함께를 사용 하는 **`""`** 것은 특별 한 형태의 지시문입니다.

- 매개 변수를 사용 하는 경우 **`off`** 위의 표에 나열 된 런타임 오류 검사를 해제 합니다.

- 매개 변수를 사용 하는 경우 **`restore`** 컴파일러 옵션을 사용 하 여 지정 된 런타임 오류 검사를 다시 설정 합니다 **`/RTC`** .

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
