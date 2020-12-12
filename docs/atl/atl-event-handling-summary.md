---
description: '자세한 정보: ATL 이벤트 처리 요약'
title: ATL 이벤트 처리 요약
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: c041de6cbd0e0852d5ce0e51d892c21c7d9a23d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148657"
---
# <a name="atl-event-handling-summary"></a>ATL 이벤트 처리 요약

일반적으로 COM 이벤트를 처리 하는 과정은 비교적 간단 합니다. 세 가지 주요 단계가 있습니다.

- 개체에 이벤트 인터페이스를 구현 합니다.

- 개체에서 이벤트를 수신 하려고 하는 이벤트 소스에 대해 알립니다.

- 개체가 더 이상 이벤트를 수신 하지 않아도 되는 경우 이벤트 소스를 Unadvise 합니다.

## <a name="implementing-the-interface"></a>인터페이스 구현

ATL을 사용 하 여 인터페이스를 구현 하는 네 가지 주요 방법이 있습니다.

|에서 파생|인터페이스 유형에 적합|모든 메서드를 구현 해야 합니다. *|런타임에 형식 라이브러리가 필요 합니다.|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|인터페이스|Vtable|예|아니요|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|이중|예|예|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|아니요|예|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|아니요|아니요|

\* ATL 지원 클래스를 사용 하는 경우 또는 메서드를 수동으로 구현 하지 않아도 됩니다 `IUnknown` `IDispatch` .

## <a name="advising-and-unadvising-the-event-source"></a>이벤트 원본에 대 한 Unadvising

ATL을 사용 하 여 이벤트 소스를 unadvising 하는 세 가지 주요 방법이 있습니다.

|Advise 함수|Unadvise 함수|에서 사용 하기에 가장 적합 합니다.|쿠키를 추적 해야 합니다.|의견|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[](reference/connection-point-global-functions.md#atladvise) [Ccomptrbase:: Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable 또는 이중 인터페이스|예|`AtlAdvise` 는 전역 ATL 함수입니다. `CComPtrBase::Advise`[CComPtr](../atl/reference/ccomptr-class.md) 및 [CComQIPtr](../atl/reference/ccomqiptr-class.md)에서 사용 됩니다.|
|[IDispEventSimpleImpl::D ispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::D ispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) 또는 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|아니요|`AtlAdvise`기본 클래스에서 더 많은 작업을 수행 하므로 매개 변수가 줄어듭니다.|
|[CComCompositeControl:: AdviseSinkMap (TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl:: AdviseSinkMap (FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|복합 컨트롤의 ActiveX 컨트롤|아니요|`CComCompositeControl::AdviseSinkMap` 이벤트 싱크 맵의 모든 항목에 대해 조언 합니다. 동일한 함수가 항목을 제안 하지 않습니다. 이 메서드는 클래스에 의해 자동으로 호출 됩니다 `CComCompositeControl` .|
|[CAxDialogImpl:: AdviseSinkMap (TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl:: AdviseSinkMap (FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|대화 상자의 ActiveX 컨트롤|아니요|`CAxDialogImpl::AdviseSinkMap` 대화 상자 리소스의 모든 ActiveX 컨트롤에 대 한 권장을 제안 합니다. 자동으로 수행 됩니다.|

## <a name="see-also"></a>참고 항목

[이벤트 처리](../atl/event-handling-and-atl.md)<br/>
[IDispEventImpl 지원](../atl/supporting-idispeventimpl.md)
