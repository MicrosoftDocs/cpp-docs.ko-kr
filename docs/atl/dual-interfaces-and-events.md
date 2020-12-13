---
description: '에 대 한 자세한 정보: 이중 인터페이스 및 이벤트'
title: 이중 인터페이스 및 이벤트
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 231df7a0dfc8376acd6a9a0f9d85d0ed68fdd0b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153029"
---
# <a name="dual-interfaces-and-events"></a>이중 인터페이스 및 이벤트

이벤트 인터페이스를 이중으로 디자인할 수 있지만 그렇게 하지 않는 것이 좋은 디자인 이유가 여러 가지가 있습니다. 기본적인 이유는 이벤트의 소스가 vtable을 통해서만 이벤트를 발생 시키는 것이 아니라를 통해서만 발생 하기 때문입니다 `Invoke` . 이벤트 소스가 직접 vtable 메서드 호출로 이벤트를 발생 시키는 경우 메서드는 사용 되지 않으며 `IDispatch` 인터페이스가 순수 vtable 인터페이스 여야 합니다. 이벤트 소스에서를 호출 하 여 이벤트를 발생 시키면 `Invoke` vtable 메서드는 사용 되지 않으며 인터페이스가 상호 연결 되어야 한다는 것을 알 수 없습니다. Duals로 이벤트 인터페이스를 정의 하는 경우 클라이언트가 사용 되지 않을 인터페이스의 일부를 구현 하도록 요구 합니다.

> [!NOTE]
> 이 인수는 일반적인 이중 인터페이스에는 적용 되지 않습니다. 구현 관점에서 duals는 광범위 한 클라이언트에서 액세스할 수 있는 인터페이스를 구현 하는 빠르고 편리 하 고 잘 지원 되는 방법입니다.

이중 이벤트 인터페이스를 피하는 추가 이유가 있습니다. Visual Basic 및 Internet Explorer는 모두 지원 하지 않습니다.

## <a name="see-also"></a>참고 항목

[이중 인터페이스 및 ATL](../atl/dual-interfaces-and-atl.md)
