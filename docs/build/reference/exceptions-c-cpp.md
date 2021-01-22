---
description: '자세한 정보: 지연 로드 예외 (C/c + +)'
title: DLL 지연 로드 예외 코드
ms.date: 01/19/2021
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.openlocfilehash: 214d8514baba7b180b8d838af8a6b6c0543cc1ce
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667172"
---
# <a name="dll-delay-load-exception-codes"></a>DLL 지연 로드 예외 코드

오류가 발생 하면 두 가지 구조화 된 예외 코드를 발생 시킬 수 있습니다.

- 실패 한 경우 `LoadLibrary`

- 실패 한 경우 `GetProcAddress`

예외 정보 매크로는 다음과 같습니다.

```C
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Throw 된 예외 코드는 표준 `VcppException(ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND)` 및 `VcppException(ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND)` 값입니다. 예외는 `DelayLoadInfo` `LPDWORD` `GetExceptionInformation` 필드의 구조에서 검색할 수 있는 값의 구조체에 대 한 포인터를 전달 합니다 [`EXCEPTION_RECORD`](/windows/win32/api/winnt/ns-winnt-exception_record) `ExceptionInformation[0]` .

또한 필드에 잘못 된 비트가 설정 되어 있으면 `grAttrs` 예외가 `ERROR_INVALID_PARAMETER` throw 됩니다. 이 예외는 모든 의도 및 목적을 위해 치명적입니다.

자세한 내용은 [구조체 및 상수 정의](structure-and-constant-definitions.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[오류 처리 및 알림](error-handling-and-notification.md)
