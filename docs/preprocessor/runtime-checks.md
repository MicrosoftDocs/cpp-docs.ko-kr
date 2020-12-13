---
description: '다음에 대 한 자세한 정보: runtime_checks pragma'
title: runtime_checks pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: 2ee04751e9cc978487670314675d3fa4ae52bd3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342298"
---
# <a name="runtime_checks-pragma"></a>runtime_checks pragma

[/RTC](../build/reference/rtc-run-time-error-checks.md) 설정을 사용할 수 없도록 설정하거나 복원합니다.

## <a name="syntax"></a>Syntax

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **restore**  |  **off** } **)**

## <a name="remarks"></a>설명

컴파일러 옵션으로 설정 되지 않은 런타임 검사를 사용 하도록 설정할 수 없습니다. 예를 들어 명령줄에을 지정 하지 않는 경우 `/RTCs` 를 지정 하면 `#pragma runtime_checks( "s", restore)` 스택 프레임 확인을 사용 하지 않습니다.

**Runtime_checks** pragma는 함수 외부에 표시 되어야 하며 pragma가 표시 된 후에 정의 된 첫 번째 함수에 적용 됩니다. **restore** 및 **off** 인수는 **runtime_checks** 에 지정된 옵션을 켜거나 끕니다.

**runtime_checks** 는 다음 표에 표시된 0개 이상의 매개 변수가 될 수 있습니다.

### <a name="parameters-of-the-runtime_checks-pragma"></a>runtime_checks Pragma의 매개 변수

| 매개 변수 | 런타임 검사 형식 |
|--------------------|-----------------------------|
| **s** | 스택(프레임)을 확인하도록 설정합니다. |
| **c** | 데이터 손실이 발생하는 더 작은 데이터 형식에 값이 할당되는 경우 이를 보고합니다. |
| **u** | 변수가 정의 되기 전에 사용 되는 경우를 보고 합니다. |

이러한 매개 변수는 컴파일러 옵션에 사용 된 것과 동일 합니다 `/RTC` . 예를 들어:

```cpp
#pragma runtime_checks( "sc", restore )
```

**runtime_checks** pragma를 빈 문자열(**""**)과 함께 사용하는 것은 특별한 형태의 지시문입니다.

- **Off** 매개 변수를 사용 하는 경우 위의 표에 나열 된 런타임 오류 검사를 해제 합니다.

- **Restore** 매개 변수를 사용 하는 경우 컴파일러 옵션을 사용 하 여 지정 된 런타임 오류 검사를 다시 설정 합니다 `/RTC` .

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
