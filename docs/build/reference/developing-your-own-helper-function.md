---
description: '자세한 정보: 자체 도우미 함수 개발'
title: 사용자 도우미 함수 개발
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: da536d13da9a596c5667c3fa84311b73e66d71ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201458"
---
# <a name="developing-your-own-helper-function"></a>사용자 도우미 함수 개발

DLL 또는 가져오기의 이름을 기준으로 특정 처리를 수행 하는 루틴의 고유한 버전을 제공할 수 있습니다. 이 작업을 수행 하는 방법에는 두 가지가 있습니다. 제공 된 코드를 기반으로 하 여 직접 코딩 하거나 앞에서 설명한 알림 후크를 사용 하 여 제공 된 버전을 단순히 후크 합니다.

## <a name="code-your-own"></a>직접 코딩

기본적으로 제공 된 코드를 새 항목에 대 한 지침으로 사용할 수 있기 때문에이 방법은 매우 간단 합니다. 물론 호출 규칙을 따라야 하며 링커 생성 썽크로 반환 되는 경우 적절 한 함수 포인터를 반환 해야 합니다. 코드에 한 번 호출을 충족 하거나 호출을 가져오기 위해 원하는 것을 원하는 대로 수행할 수 있습니다.

## <a name="use-the-start-processing-notification-hook"></a>처리 시작 알림 후크 사용

사용자가 제공 하는 알림 후크 함수에 대 한 새 포인터를 제공 하는 것이 가장 간편 합니다. 이 시점에서 후크 함수는 기본적으로 새 도우미 함수가 될 수 있습니다. 기본 도우미가 성공적으로 반환 되 면 기본 도우미의 모든 추가 처리를 무시 하기 때문입니다.

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)
