---
description: pragmaMicrosoft C/c + +의 check_stack 지시문에 대해 자세히 알아보세요.
title: check_stack pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragma, check_stack
- pragma, check_stack usage table
no-loc:
- pragma
ms.openlocfilehash: a395471625fed60fcf750ebac8f3159a89ba1487
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713716"
---
# <a name="check_stack-no-locpragma"></a>`check_stack` pragma

**`off`**(또는)가 지정 된 경우 스택 프로브를 해제 **`-`** 하거나 **`on`** (또는)가 지정 된 경우 스택 프로브를 설정 하도록 컴파일러에 지시 **`+`** 합니다.

## <a name="syntax"></a>구문

> **`#pragma check_stack(`** [{ **`on`** | **`off`** }] **`)`**\
> **`#pragma check_stack`** { **`+`** | **`-`** }

## <a name="remarks"></a>설명

이는 pragma 가 표시 된 후 정의 된 첫 번째 함수에 적용 됩니다 pragma . 스택 프로브는 인라인으로 생성된 함수의 일부나 매크로의 일부가 아닙니다.

에 대 한 인수를 지정 하지 않으면 **`check_stack`** pragma 스택 검사가 명령줄에 지정 된 동작으로 되돌아갑니다. 자세한 내용은 [컴파일러 옵션](../build/reference/compiler-options.md)을 참조하세요. 및 옵션의 상호 작용은 `#pragma check_stack` [`/Gs`](../build/reference/gs-control-stack-checking-calls.md) 다음 표에 요약 되어 있습니다.

### <a name="using-the-check_stack-pragma"></a>check_stack Pragma 사용

| 구문 | /Gs 옵션을 사용한<br /><br /> `/Gs` option? | 작업 |
|--|--|--|
| `#pragma check_stack( )` 또는<br /><br /> `#pragma check_stack` | 예 | 뒤에 오는 함수에 대한 스택 검사 해제 |
| `#pragma check_stack( )` 또는<br /><br /> `#pragma check_stack` | 아니요 | 뒤에 오는 함수에 대한 스택 검사 설정 |
| `#pragma check_stack(on)`<br /><br /> 또는 `#pragma check_stack +` | Yes 또는 No | 뒤에 오는 함수에 대한 스택 검사 설정 |
| `#pragma check_stack(off)`<br /><br /> 또는 `#pragma check_stack -` | Yes 또는 No | 뒤에 오는 함수에 대한 스택 검사 해제 |

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
