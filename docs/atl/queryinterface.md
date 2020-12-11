---
description: '자세한 정보: QueryInterface'
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: b22163c9e69bd5573f8e6060df0457862813c366
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159169"
---
# <a name="queryinterface"></a>QueryInterface

개체에서 정적으로 제공 하는 기능을 표현할 수 있는 메커니즘 (인스턴스화된 후)은 있지만 기본 COM 메커니즘은 `IUnknown` [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))라는 메서드를 사용 하는 것입니다.

모든 인터페이스는에서 파생 `IUnknown` 되므로 모든 인터페이스에는의 구현이 `QueryInterface` 있습니다. 구현과 관계 없이이 메서드는 호출자가 포인터를 필요로 하는 인터페이스의 IID를 사용 하 여 개체를 쿼리 합니다. 개체가 해당 인터페이스를 지 원하는 경우는를 `QueryInterface` 호출 하는 동시에 인터페이스에 대 한 포인터를 검색 `AddRef` 합니다. 그렇지 않으면 E_NOINTERFACE 오류 코드를 반환 합니다.

[참조 횟수](../atl/reference-counting.md) 규칙은 항상 준수 해야 합니다. 인터페이스 포인터에서를 호출 하 여 `Release` 참조 횟수를 0으로 감소 하는 경우 해당 포인터를 다시 사용 하면 안 됩니다. 경우에 따라 개체에 대 한 약한 참조를 가져와야 할 수 있습니다. 즉, 참조 횟수를 증가 시 키 지 않고 해당 인터페이스 중 하나에 대 한 포인터를 가져오려고 할 수 있지만 다음에를 호출 하 여이 작업을 수행할 수는 없습니다 `QueryInterface` `Release` . 이러한 방식으로 가져온 포인터는 유효 하지 않으므로 사용 하면 안 됩니다. 이는 [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) 정의 될 때 보다 쉽게 드러나지 않으므로이 매크로를 정의 하는 것이 참조 계산 버그를 찾는 데 유용한 방법입니다.

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[QueryInterface: 개체에서 탐색](/windows/win32/com/queryinterface--navigating-in-an-object)
