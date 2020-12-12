---
description: '자세히 알아보기: 집계'
title: 집계
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: fb02dd399020f8768fcdb3cc86687578e51cb3ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166098"
---
# <a name="aggregation"></a>집계

개체의 구현자 미리 작성 된 다른 개체에서 제공 하는 서비스를 활용 하는 경우가 있습니다. 또한이 두 번째 개체가 첫 번째의 자연 요소로 표시 됩니다. COM은 포함 및 집계를 통해 이러한 목표를 모두 달성 합니다.

집계는 포함 (외부) 개체가 생성 프로세스의 일부로 포함 된 (내부) 개체를 만들고 내부 개체의 인터페이스를 외부에서 노출 하는 것을 의미 합니다. 개체는 자신을 집계할 수 있습니다. 그렇다면 집계가 제대로 작동 하려면 특정 규칙을 따라야 합니다.

기본적으로 `IUnknown` 포함 된 개체에 대 한 모든 메서드 호출은 포함 하는 개체에 위임 해야 합니다.

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[개체 재사용](/windows/win32/com/reusing-objects)
