---
description: '자세한 정보: 예외 (C/c + +)'
title: DLL 로드 예외 코드 (C/c + +)
ms.date: 11/19/2019
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
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: 53ae6ab9a21309159b29a96e58d077f45fe30e12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200847"
---
# <a name="exceptions-cc"></a>예외(C/C++)

오류가 발생 하면 두 가지 예외 코드가 발생할 수 있습니다.

- **LoadLibrary** 오류

- **GetProcAddress** 오류의 경우

예외 정보는 다음과 같습니다.

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Throw 된 예외 코드는 표준 VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) 및 VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND) 값입니다. 예외는 [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) 구조, exceptioninformation [0] 필드의 **getexceptioninformation** 에서 검색할 수 있는 Lpdword 값의 **delayloadinfo** 구조에 대 한 포인터를 전달 합니다.

또한 grAttrs 필드에 잘못 된 비트가 설정 되어 있으면 ERROR_INVALID_PARAMETER 예외가 throw 됩니다. 이 예외는 모든 의도 및 목적을 위해 치명적입니다.

자세한 내용은 [구조체 및 상수 정의](structure-and-constant-definitions.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[오류 처리 및 알림](error-handling-and-notification.md)
