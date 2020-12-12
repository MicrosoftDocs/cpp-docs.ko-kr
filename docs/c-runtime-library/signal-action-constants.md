---
description: '자세한 정보: 신호 동작 상수'
title: 신호 작업 상수
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: 380fed21b097b674958c6e2aae2f6b8c53845943
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276987"
---
# <a name="signal-action-constants"></a>신호 작업 상수

인터럽트 신호를 받을 때 수행되는 작업은 `func` 값에 따라 다릅니다.

## <a name="syntax"></a>구문

```
#include <signal.h>
```

## <a name="remarks"></a>설명

`func` 인수는 함수 주소 또는 아래에 나열되고 SIGNAL.H에 정의된 매니페스트 상수 중 하나여야 합니다.

|상수|설명|
|-|-|
| `SIG_DFL`  | 시스템 기본 응답을 사용합니다. 호출 프로그램이 스트림 I/O를 사용하는 경우 런타임 라이브러리에 의해 생성된 버퍼는 플러시되지 않습니다.  |
| `SIG_IGN`  | 인터럽트 신호를 무시합니다. 프로세스의 부동 소수점 상태가 정의되지 않은 상태로 유지되므로 `SIGFPE`에 대해서는 이 값이 지정되지 않습니다.  |
| `SIG_SGE`  | 신호에서 오류가 발생했음을 나타냅니다.  |
| `SIG_ACK`  | 승인을 수신되었음을 나타냅니다.  |
| `SIG_ERR`  | 오류가 발생했음을 나타내는 신호의 반환 형식  |

## <a name="see-also"></a>참고 항목

[signal](../c-runtime-library/reference/signal.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
