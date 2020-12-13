---
description: '자세한 정보: 이벤트 처리 인터페이스 구현'
title: 이벤트 처리 인터페이스 구현
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
ms.openlocfilehash: 109fbb1fbdd4f18d0eb4c295fbc08de2b7cc3a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152765"
---
# <a name="implementing-the-event-handling-interface"></a>이벤트 처리 인터페이스 구현

ATL을 사용 하면 이벤트를 처리 하는 데 필요한 세 가지 요소인 이벤트 인터페이스를 구현 하 고 이벤트 소스를 unadvising 이벤트 소스를 수 있습니다. 수행 해야 하는 정확한 단계는 이벤트 인터페이스의 유형과 응용 프로그램의 성능 요구 사항에 따라 달라 집니다.

ATL을 사용 하 여 인터페이스를 구현 하는 가장 일반적인 방법은 다음과 같습니다.

- 사용자 지정 인터페이스에서 직접 파생.

- 형식 라이브러리에 설명 된 이중 인터페이스에 대해 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 에서 파생 됩니다.

- 형식 라이브러리에 설명 된 dispinterface에 대해 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 에서 파생 됩니다.

- 형식 라이브러리에 설명 되지 않은 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) for dispinterface에서 파생 되거나 런타임에 형식 정보를 로드 하지 않음으로써 효율성을 개선 하려는 경우

사용자 지정 또는 이중 인터페이스를 구현 하는 경우에는 사용자 지정 [advise](reference/connection-point-global-functions.md#atladvise) 또는 [Ccomptrbase:: advise](../atl/reference/ccomptrbase-class.md#advise)를 호출 하 여 이벤트 소스에 대 한 조언을 지정 해야 합니다. 호출에서 반환 된 쿠키를 직접 추적 해야 합니다. [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) 를 호출 하 여 연결을 중단 합니다.

또는를 사용 하 여 서 수를 구현 하는 경우 `IDispEventImpl` `IDispEventSimpleImpl` [IDispEventSimpleImpl::D ispeventadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)를 호출 하 여 이벤트 소스에 대 한 조언을 지정 해야 합니다. [IDispEventSimpleImpl::D ispeventunadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) 를 호출 하 여 연결을 중단 합니다.

`IDispEventImpl`복합 컨트롤의 기본 클래스로를 사용 하는 경우 싱크 맵에 나열 된 이벤트 소스가 권장 되며 [CComCompositeControl:: AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)를 사용 하 여 자동으로 advise 되지 않습니다.

`IDispEventImpl`및 `IDispEventSimpleImpl` 클래스는 쿠키를 관리 합니다.

## <a name="see-also"></a>참고 항목

[이벤트 처리](../atl/event-handling-and-atl.md)
