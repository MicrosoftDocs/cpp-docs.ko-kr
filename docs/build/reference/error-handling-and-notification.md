---
title: 오류 처리 및 알림
description: '자세한 정보: DLL 지연 로드 오류 처리 및 알림'
ms.date: 01/19/2021
helpviewer_keywords:
- error handling, and notification
ms.openlocfilehash: efff7ba9956bee8fe6ccf1df96a3f4b49852ce43
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522562"
---
# <a name="error-handling-and-notification"></a>오류 처리 및 알림

프로그램이 지연 로드 된 Dll을 사용 하는 경우 프로그램을 실행 하는 동안 발생 하는 오류로 인해 처리 되지 않은 예외가 발생 하기 때문에 오류를 강력 하 게 처리 해야 합니다. 실패 처리는 후크를 통한 복구와 예외를 통해 보고의 두 부분으로 구성 됩니다.

DLL 지연 로드 오류 처리 및 알림에 대 한 자세한 내용은 [도우미 함수 이해](understanding-the-helper-function.md)를 참조 하세요.

후크 함수에 대 한 자세한 내용은 [구조체 및 상수 정의](understanding-the-helper-function.md#structure-and-constant-definitions)를 참조 하세요.

## <a name="recovery-through-a-hook"></a>후크를 통해 복구

코드에서 오류를 복구 하거나 대체 라이브러리나 루틴을 제공 해야 할 수 있습니다. 대체 코드를 제공할 수 있는 도우미 함수에 대 한 후크를 제공 하거나 문제를 해결할 수 있습니다. 후크 루틴은 적절 한 값을 반환 해야 하므로 처리를 계속할 수 있습니다 ( `HINSTANCE` 또는 `FARPROC` ). 또는 0을 반환 하 여 예외를 throw 해야 함을 나타낼 수 있습니다. 자체 예외를 throw 하거나 후크를 제외할 수도 있습니다 `longjmp` . 알림 후크 및 오류 후크가 있습니다. 둘 다에 동일한 루틴을 사용할 수 있습니다.

## <a name="notification-hooks"></a><a name="notification-hooks"></a> 알림 후크

지연 로드 알림 후크는 도우미 루틴에서 다음 작업을 수행 하기 직전에 호출 됩니다.

- 라이브러리에 저장 된 핸들이 이미 로드 되었는지 확인 합니다.

- `LoadLibrary` DLL의 로드를 시도 하기 위해가 호출 됩니다.

- `GetProcAddress` 프로시저의 주소를 가져오려고 하기 위해가 호출 됩니다.

- 지연 가져오기 로드 썽크로 돌아갑니다.

알림 후크가 사용 됩니다.

- `__pfnDliNotifyHook2`알림을 받는 자체 함수를 가리키도록 초기화 된 포인터의 새 정의를 제공 합니다.

   \-또는-

- `__pfnDliNotifyHook2`프로그램 로드를 지연 시키는 DLL을 호출 하기 전에 후크 함수에 대 한 포인터를 설정 합니다.

알림이 인 경우 `dliStartProcessing` 후크 함수는 다음을 반환할 수 있습니다.

- `NULL`

   기본 도우미는 DLL 로드를 처리 합니다. 단지 정보를 제공 하기 위해를 호출 하는 것이 유용 합니다.

- 함수 포인터

   기본 지연 로드 처리를 무시 합니다. 사용자 고유의 부하 처리기를 제공할 수 있습니다.

알림이 인 경우 `dliNotePreLoadLibrary` 후크 함수는 다음을 반환할 수 있습니다.

- 0-정보 알림이 필요한 경우

- `HMODULE`로드 된 dll (dll 자체를 로드 한 경우)에 대 한입니다.

알림이 인 경우 `dliNotePreGetProcAddress` 후크 함수는 다음을 반환할 수 있습니다.

- 0-정보 알림이 필요한 경우

- 후크 함수가 주소 자체를 가져오는 경우 가져온 함수의 주소입니다.

알림이 이면 `dliNoteEndProcessing` 후크 함수의 반환 값은 무시 됩니다.

이 포인터가 초기화 되지 않은 경우 (0이 아닌) 지연 로드 도우미는 실행 전체에서 특정 알림 지점에 함수를 호출 합니다. 함수 포인터의 정의는 다음과 같습니다.

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

알림은 `DelayLoadInfo` 알림 값과 함께 후크 함수에 대 한 구조를 전달 합니다. 이 데이터는 지연 로드 도우미 루틴이 사용 하는 데이터와 동일 합니다. 알림 값은 [구조 및 상수 정의](understanding-the-helper-function.md#structure-and-constant-definitions)에 정의 된 값 중 하나입니다.

## <a name="failure-hooks"></a><a name="failure-hooks"></a> 실패 후크

오류 후크는 [알림 후크에](#notification-hooks)동일한 방식으로 사용 하도록 설정 됩니다. 후크 루틴은 처리를 계속할 수 있도록 적합 한 값을 반환 해야 합니다 ( `HINSTANCE` 또는 `FARPROC` ). 또는 0을 통해 예외가 throw 되어야 함을 나타낼 수 있습니다.

사용자 정의 함수를 참조 하는 포인터 변수는 다음과 같습니다.

```C
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

구조에는 **`DelayLoadInfo`** 의 값을 포함 하 여 오류에 대 한 상세 보고에 필요한 모든 관련 데이터가 포함 `GetLastError` 됩니다.

알림이 인 경우 **`dliFailLoadLib`** 후크 함수는 다음을 반환할 수 있습니다.

- 오류를 처리할 수 없는 경우 0입니다.

- `HMODULE`오류 후크가 문제를 해결 하 고 라이브러리 자체를 로드 한 경우입니다.

알림이 인 경우 **`dliFailGetProc`** 후크 함수는 다음을 반환할 수 있습니다.

- 오류를 처리할 수 없는 경우 0입니다.

- 오류 후크가 주소 자체를 가져오는 데 성공한 경우 유효한 프로시저 주소 (가져오기 함수 주소)입니다.

## <a name="report-by-using-an-exception"></a>예외를 사용 하 여 보고

오류를 처리 하는 데 필요한 모든 것이 프로시저를 중단 하는 것 이라면 사용자 코드에서 예외를 처리할 수 있다면 후크가 필요 하지 않습니다.

## <a name="delay-load-exception-codes"></a><a name="delay-load-exception-codes"></a> 로드 예외 코드 지연

부하를 지연 하는 동안 오류가 발생 하면 구조화 된 예외 코드가 발생할 수 있습니다. 예외 값은 매크로를 사용 하 여 지정 합니다 `VcppException` .

```C
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

오류의 경우 `LoadLibrary` 표준이 `VcppException(ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND)` throw 됩니다. 오류의 경우 `GetProcAddress` throw 되는 오류는 `VcppException(ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND)` 입니다. 예외는 구조체에 대 한 포인터를 전달 합니다 `DelayLoadInfo` . 이 `LPDWORD` 값은 구조체의 필드에서로 검색 되는 값에 `GetExceptionInformation` [`EXCEPTION_RECORD`](/windows/win32/api/winnt/ns-winnt-exception_record) `ExceptionInformation[0]` 있습니다.

필드에 잘못 된 비트가 설정 되어 있으면 `grAttrs` 예외가 `ERROR_INVALID_PARAMETER` throw 됩니다. 이 예외는 모든 의도 및 목적을 위해 치명적입니다.

자세한 내용은 [구조체 및 상수 정의](understanding-the-helper-function.md#structure-and-constant-definitions)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)
