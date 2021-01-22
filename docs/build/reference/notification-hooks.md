---
description: '자세한 정보: 지연 로드 알림 후크'
title: 알림 후크
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.openlocfilehash: 401ae9099afcf00dc280bb4f9e5f7016a4cbc640
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667543"
---
# <a name="notification-hooks"></a>알림 후크

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

알림은 `DelayLoadInfo` 알림 값과 함께 후크 함수에 대 한 구조를 전달 합니다. 이 데이터는 지연 로드 도우미 루틴이 사용 하는 데이터와 동일 합니다. 알림 값은 [구조 및 상수 정의](structure-and-constant-definitions.md)에 정의 된 값 중 하나입니다.

## <a name="see-also"></a>참고 항목

[오류 처리 및 알림](error-handling-and-notification.md)
