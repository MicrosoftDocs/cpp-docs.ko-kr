---
description: 사용자 고유의 지연 로드 도우미 함수를 개발 하는 방법에 대 한 자세한 정보
title: 사용자 고유의 지연 로드 도우미 함수 개발
ms.date: 01/19/2021
helpviewer_keywords:
- helper functions
ms.openlocfilehash: 2845a426023ed8b5e2bcfb0056c9be6b829dd23a
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667437"
---
# <a name="develop-your-own-delay-load-helper-function"></a>사용자 고유의 지연 로드 도우미 함수 개발

사용자 고유의 지연 로드 도우미 루틴을 제공 하는 것이 좋습니다. 사용자의 루틴에서 DLL 또는 가져오기의 이름을 기준으로 특정 처리를 수행할 수 있습니다. 사용자 고유의 코드를 삽입 하는 방법에는 두 가지가 있습니다. 제공 된 코드를 기반으로 사용자 고유의 도우미 함수를 코딩 합니다. 또는 제공 된 도우미를 후크하여 [알림 후크](notification-hooks.md)를 사용 하 여 고유한 함수를 호출 합니다.

## <a name="code-your-own-helper"></a>사용자 고유의 도우미 코딩

사용자 고유의 도우미 루틴을 만드는 것은 간단 합니다. 새 함수에 대 한 지침으로 기존 코드를 사용할 수 있습니다. 함수는 기존 도우미와 동일한 호출 규칙을 사용 해야 합니다. 그리고 링커 생성 썽크로 반환 되는 경우 적절 한 함수 포인터를 반환 해야 합니다. 코드를 만든 후 호출을 충족 하거나 호출을 받을 수 있습니다.

## <a name="use-the-start-processing-notification-hook"></a>처리 시작 알림 후크 사용

알림의 기본 도우미와 동일한 값을 사용 하는 사용자 제공 알림 후크 함수에 대 한 새 포인터를 제공 하는 것이 가장 쉽습니다 `dliStartProcessing` . 이 시점에서 기본 도우미가 성공적으로 반환 되 면 기본 도우미의 모든 추가 처리를 무시 하므로 후크 함수는 기본적으로 새 도우미 함수가 될 수 있습니다.

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)
