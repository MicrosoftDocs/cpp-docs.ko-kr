---
description: '자세한 정보: 로드 실패 후크 지연'
title: 오류 후크
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.openlocfilehash: 46cec6c66169ebe589bb5f0c912b2d8239e69da1
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667179"
---
# <a name="failure-hooks"></a>오류 후크

오류 후크는 [알림 후크에](notification-hooks.md)동일한 방식으로 사용 하도록 설정 됩니다. 후크 루틴은 처리를 계속할 수 있도록 적합 한 값을 반환 해야 합니다 ( `HINSTANCE` 또는 `FARPROC` ). 또는 0을 통해 예외가 throw 되어야 함을 나타낼 수 있습니다.

사용자 정의 함수를 참조 하는 포인터 변수는 다음과 같습니다.

```C
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

구조에는 **`DelayLoadInfo`** 의 값을 포함 하 여 오류를 정확 하 게 보고 하는 데 필요한 모든 관련 데이터가 포함 `GetLastError` 됩니다.

알림이 인 경우 **`dliFailLoadLib`** 후크 함수는 다음을 반환할 수 있습니다.

- 오류를 처리할 수 없는 경우 0입니다.

- `HMODULE`오류 후크가 문제를 해결 하 고 라이브러리 자체를 로드 한 경우입니다.

알림이 인 경우 **`dliFailGetProc`** 후크 함수는 다음을 반환할 수 있습니다.

- 오류를 처리할 수 없는 경우 0입니다.

- 오류 후크가 주소 자체를 가져오는 데 성공한 경우 유효한 프로시저 주소 (가져오기 함수 주소)입니다.

## <a name="see-also"></a>참고 항목

[오류 처리 및 알림](error-handling-and-notification.md)
