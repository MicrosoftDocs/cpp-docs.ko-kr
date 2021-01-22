---
title: 오류 처리 및 알림
description: '자세한 정보: DLL 지연 로드 오류 처리 및 알림'
ms.date: 01/19/2021
helpviewer_keywords:
- error handling, and notification
ms.openlocfilehash: a0161814a07bd5bbedbaa6d13c7c32cd3aeab559
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666955"
---
# <a name="error-handling-and-notification"></a>오류 처리 및 알림

프로그램이 지연 로드 된 Dll을 사용 하는 경우 프로그램을 실행 하는 동안 발생 하는 오류로 인해 처리 되지 않은 예외가 발생 하기 때문에 오류를 강력 하 게 처리 해야 합니다. 실패 처리는 후크를 통한 복구와 예외를 통해 보고의 두 부분으로 구성 됩니다.

DLL 지연 로드 오류 처리 및 알림에 대 한 자세한 내용은 [도우미 함수 이해](understanding-the-helper-function.md)를 참조 하세요.

후크 함수에 대 한 자세한 내용은 [구조체 및 상수 정의](structure-and-constant-definitions.md)를 참조 하세요.

## <a name="recovery-through-a-hook"></a>후크를 통해 복구

코드에서 오류를 복구 하거나 대체 라이브러리나 루틴을 제공 해야 할 수 있습니다. 대체 코드를 제공할 수 있는 도우미 함수에 대 한 후크를 제공 하거나 문제를 해결할 수 있습니다. 후크 루틴은 적절 한 값을 반환 해야 하므로 처리를 계속할 수 있습니다 ( `HINSTANCE` 또는 `FARPROC` ). 또는 0을 반환 하 여 예외를 throw 해야 함을 나타낼 수 있습니다. 자체 예외를 throw 하거나 후크를 제외할 수도 있습니다 `longjmp` . 알림 후크 및 오류 후크가 있습니다.

## <a name="reporting-via-an-exception"></a>예외를 통해 보고

오류를 처리 하는 데 필요한 모든 것이 프로시저를 중단 하는 것 이라면 사용자 코드에서 예외를 처리할 수 있다면 후크가 필요 하지 않습니다.

다음 문서에서는 오류 처리 및 알림에 대해 설명 합니다.

- [알림 후크](notification-hooks.md)

- [오류 후크](failure-hooks.md)

- [DLL 지연 로드 예외 코드](exceptions-c-cpp.md)

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)
