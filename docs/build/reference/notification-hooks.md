---
description: '자세히 알아보기: 알림 후크'
title: 알림 후크
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 716d2b31faa71c77ec436662ce00368d15afc4b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209752"
---
# <a name="notification-hooks"></a>알림 후크

알림 후크는 도우미 루틴에서 다음 작업을 수행 하기 직전에 호출 됩니다.

- 라이브러리에 저장 된 핸들이 이미 로드 되었는지 확인 합니다.

- **LoadLibrary** 를 호출 하 여 DLL의 로드를 시도 합니다.

- **GetProcAddress** 를 호출 하 여 프로시저의 주소를 가져오려고 시도 합니다.

- 지연 가져오기 로드 썽크로 돌아갑니다.

알림 후크가 사용 됩니다.

- 알림을 수신 하는 고유한 함수를 가리키도록 초기화 된 **__pfnDliNotifyHook2** 포인터의 새 정의를 제공 합니다.

   \-또는-

- 프로그램 로드를 지연 시키는 DLL을 호출 하기 전에 포인터를 후크 함수로 **__pfnDliNotifyHook2** 설정 합니다.

이 알림이 **Dlistartprocessing** 인 경우 후크 함수는 다음을 반환할 수 있습니다.

- NULL

   기본 도우미는 DLL 로드를 처리 합니다. 이 방법은 정보 제공을 위해서만 호출 하는 데 유용 합니다.

- 함수 포인터

   기본 지연 로드 처리를 무시 합니다. 이렇게 하면 사용자 고유의 부하 처리기를 제공할 수 있습니다.

**이 알림이 다음을 수행** 하는 경우 후크 함수는 다음을 반환할 수 있습니다.

- 0-정보 알림이 필요한 경우

- DLL 자체를 로드 한 경우 로드 된 DLL에 대 한 HMODULE입니다.

**이 알림이 다음을 수행** 하는 경우 후크 함수는 다음을 반환할 수 있습니다.

- 0-정보 알림이 필요한 경우

- 후크 함수가 주소 자체를 가져오는 경우 가져온 함수의 주소입니다.

이 알림이 **Dlinoteendprocessing** 인 경우 후크 함수의 반환 값은 무시 됩니다.

이 포인터를 초기화 하는 경우 (0이 아닌) 지연 로드 도우미는 실행 전체의 특정 알림 지점에서 함수를 호출 합니다. 함수 포인터의 정의는 다음과 같습니다.

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

알림은 알림 값과 함께 후크 함수에 **Delayloadinfo** 구조를 전달 합니다. 이 데이터는 지연 로드 도우미 루틴이 사용 하는 데이터와 동일 합니다. 알림 값은 [구조 및 상수 정의](structure-and-constant-definitions.md)에 정의 된 값 중 하나입니다.

## <a name="see-also"></a>참고 항목

[오류 처리 및 알림](error-handling-and-notification.md)
