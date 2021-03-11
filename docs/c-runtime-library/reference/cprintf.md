---
description: '자세히 알아보기: cprintf'
title: cprintf
ms.date: 3/9/2021
api_name:
- cprintf
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cprintf
helpviewer_keywords:
- cprintf function
ms.openlocfilehash: b31865ac14653b80ff79f89df968128b727c9991
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102621921"
---
# <a name="cprintf"></a>cprintf

Microsoft 전용 함수 이름은 `cprintf` [_cprintf](cprintf-cprintf-l-cwprintf-cwprintf-l.md) 함수에 사용 되지 않는 별칭입니다. 기본적으로 [컴파일러 경고 (수준 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)를 생성 합니다. 이름은 구현 관련 이름에 대해 표준 C 규칙을 따르지 않으므로 사용 되지 않습니다. 그러나 함수는 여전히 지원 됩니다.

대신 [_cprintf](cprintf-cprintf-l-cwprintf-cwprintf-l.md) 또는 보안이 강화 된 [_cprintf_s](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md) 함수를 사용 하는 것이 좋습니다. 또는이 함수 이름을 계속 사용 하 고 경고를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [경고](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) 및 [POSIX 함수 이름](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)해제를 참조 하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.
>
> Windows 10 버전 2004 (빌드 19041)부터 `printf` 함수 패밀리는 반올림을 위한 IEEE 754 규칙에 따라 표현 가능한 부동 소수점 숫자를 정확 하 게 출력 합니다. 이전 버전의 Windows에서는 ' 5 '로 끝나는 정확히 표현할 수 있는 부동 소수점 숫자가 항상 반올림 됩니다. IEEE 754은 가장 가까운 짝수 ("은행원의 반올림"이 라고도 함)로 반올림 해야 함을 명시 합니다. 예를 들어 및는 둘 다 `printf("%1.0f", 1.5)` `printf("%1.0f", 2.5)` 2로 반올림 됩니다. 이전에는 1.5가 2로 반올림 되 고 2.5가 3으로 반올림 됩니다. 이 변경은 정확히 표현할 수 있는 숫자에만 영향을 줍니다. 예를 들어 2.35 (메모리에 표시 되는 경우 2.35000000000000008에 가까울수록)는 계속 2.4으로 반올림 됩니다. 이러한 함수에서 수행 하는 반올림은 이제에 의해 설정 된 부동 소수점 반올림 모드와도 동일 [`fesetround`](fegetround-fesetround2.md) 합니다. 이전에는 반올림이 항상 동작을 선택 `FE_TONEAREST` 했습니다. 이 변경 내용은 Visual Studio 2019 버전 16.2 이상을 사용 하 여 빌드된 프로그램에만 영향을 줍니다. 레거시 부동 소수점 반올림 동작을 사용 하려면를 사용 하 여 연결 [`legacy_stdio_float_rounding.obj`](../link-options.md) 합니다.