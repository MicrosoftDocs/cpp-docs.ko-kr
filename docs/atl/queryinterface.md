---
title: QueryInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c361bc9510c610f2004af9f09c061d6f4b8b8cd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057452"
---
# <a name="queryinterface"></a>QueryInterface

기본 COM 메커니즘을 사용 하는 것 메커니즘 개체는 정적으로 (해당 되 고 인스턴스화되기 전에)를 제공 하는 기능이 표현할 수 있지만, 합니다 `IUnknown` 메서드 호출 [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))합니다.

모든 인터페이스에서 파생 됩니다 `IUnknown`이므로 모든 인터페이스의 구현에 `QueryInterface`입니다. 구현에 관계 없이이 메서드는 호출자가 포인터 인터페이스의 IID를 사용 하 여 개체를 쿼리 합니다. 개체가 해당 인터페이스를 지원 하면 `QueryInterface` 인터페이스에 대 한 포인터도 호출 하는 동안 검색 `AddRef`합니다. 그렇지 않으면 E_NOINTERFACE 오류 코드를 반환합니다.

준수 해야 하는 참고 [참조 카운팅](../atl/reference-counting.md) 항상 규칙입니다. 호출 하는 경우 `Release` 에 참조 횟수를 0으로 감소 하는 인터페이스 포인터를 사용 하지 않아야 포인터 다시 합니다. 개체에 대 한 약한 참조 해야 하는 경우에 따라 (즉, 하려는 참조 횟수를 증가 하지 않고 해당 인터페이스 중 하나에 대 한 포인터를 가져올)를 호출 하 여이 작업을 수행 하려면 허용 되지 않지만 `QueryInterface` 뒤에 `Release`입니다. 이러한 방식으로 얻은 포인터를 잘못 되었으며 사용할 수 없습니다. 이 더 쉽게 드러납니다 시기 [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) 정의이 매크로 정의 하므로 찾기 참조 버그를 계산 하는 데 도움이 됩니다.

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[개체에서 QueryInterface: 탐색](/windows/desktop/com/queryinterface--navigating-in-an-object)

