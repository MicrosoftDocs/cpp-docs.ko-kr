---
description: '자세한 정보: 오류 처리 및 알림'
title: 오류 처리 및 알림
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 234d50d0b4a7e8b81874d1926ac056f8cba23376
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200990"
---
# <a name="error-handling-and-notification"></a>오류 처리 및 알림

오류 처리 및 알림에 대 한 자세한 내용은 [도우미 함수 이해](understanding-the-helper-function.md)를 참조 하세요.

후크 함수에 대 한 자세한 내용은 [구조체 및 상수 정의](structure-and-constant-definitions.md)를 참조 하세요.

프로그램이 지연 로드 된 Dll을 사용 하는 경우 프로그램을 실행 하는 동안 발생 하는 오류로 인해 처리 되지 않은 예외가 발생 하기 때문에 오류를 강력 하 게 처리 해야 합니다. 오류 처리는 두 부분으로 구성 됩니다.

후크를 통해 복구 합니다.
코드에서 복구 하거나 대체 라이브러리 및/또는 루틴을 제공 해야 하는 경우 문제를 제공 하거나 해결할 수 있는 도우미 함수에 후크를 제공할 수 있습니다. 후크 루틴은 처리를 계속할 수 있도록 적절 한 값을 반환 해야 합니다 (HINSTANCE 또는 FARPROC). 또는 0은 예외가 throw 되어야 함을 나타내는 0입니다. 후크에서 자체 **예외 또는 옵트아웃 (out** )을 throw 할 수도 있습니다. 알림 후크 및 오류 후크가 있습니다.

예외를 통해 보고 합니다.
오류를 처리 하는 데 필요한 모든 작업은 프로시저를 중단 하는 것입니다. 사용자 코드에서 예외를 처리할 수 있는 경우에는 후크가 필요 하지 않습니다.

다음 항목에서는 오류 처리 및 알림에 대해 설명 합니다.

- [알림 후크](notification-hooks.md)

- [실패 후크](failure-hooks.md)

- [예외](exceptions-c-cpp.md)

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)
