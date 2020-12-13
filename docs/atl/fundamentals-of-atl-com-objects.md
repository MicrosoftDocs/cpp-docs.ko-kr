---
description: '자세히 알아보기: ATL COM 개체의 기본 사항'
title: ATL COM 개체의 기본 사항
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 0a94d57701770b00eb2c2d5aed675b8cc19e9e58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152938"
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 개체의 기본 사항

다음 그림에서는 ATL COM 개체를 정의 하는 데 사용 되는 클래스와 인터페이스 간의 관계를 보여 줍니다.

![ATL 구조](../atl/media/vc307y1.gif "ATL 구조")

> [!NOTE]
> 이 다이어그램에서는 `CComObject` 가에서 파생 되는 `CYourClass` 반면 및를 `CComAggObject` `CComPolyObject` `CYourClass` 멤버 변수로 포함 하는 방법을 보여 줍니다.

ATL COM 개체를 정의 하는 방법에는 세 가지가 있습니다. 표준 옵션은에서 파생 된 클래스를 사용 하는 것입니다 `CComObject` `CYourClass` . 두 번째 옵션은 클래스를 사용 하 여 집계 된 개체를 만드는 것입니다 `CComAggObject` . 세 번째 옵션은 클래스를 사용 하는 것입니다 `CComPolyObject` . `CComPolyObject` 하이브리드 역할을 `CComObject` 합니다. 먼저 클래스 또는 클래스로 작동할 수 있습니다 .이를 `CComAggObject` 먼저 만드는 방법에 따라 달라 집니다. 클래스를 사용 하는 방법에 대 한 자세한 내용은 `CComPolyObject` [Ccompolyobject 클래스](../atl/reference/ccompolyobject-class.md)를 참조 하세요.

표준 ATL COM을 사용 하는 경우 외부 개체와 내부 개체의 두 개체를 사용 합니다. 외부 클라이언트는 외부 개체에 정의 된 래퍼 함수를 통해 내부 개체의 기능에 액세스 합니다. 외부 개체는 형식입니다 `CComObject` .

집계 개체를 사용 하는 경우 외부 개체는 내부 개체의 기능에 대 한 래퍼를 제공 하지 않습니다. 대신 외부 개체는 외부 클라이언트에서 직접 액세스 하는 포인터를 제공 합니다. 이 시나리오에서 외부 개체는 형식입니다 `CComAggObject` . 내부 개체는 외부 개체의 멤버 변수 이며 형식입니다 `CYourClass` .

클라이언트는 외부 개체를 거치지 않아도 내부 개체와 상호 작용할 수 있으므로 집계 된 개체는 일반적으로 더 효율적입니다. 또한 집계 된 개체의 인터페이스를 클라이언트에서 직접 사용할 수 있는 경우 외부 개체는 집계 된 개체의 기능을 알 필요가 없습니다. 그러나 모든 개체를 집계할 수 있는 것은 아닙니다. 집계할 개체의 경우 집계를 염두에 두면 디자인 해야 합니다.

ATL은 다음 두 단계로 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 합니다.

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)또는 [ccompolyobject](../atl/reference/ccompolyobject-class.md) 는 메서드를 구현 `IUnknown` 합니다.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 는의 참조 횟수 및 외부 포인터를 관리 합니다 `IUnknown` .

ATL COM 개체의 다른 측면은 다른 클래스에서 처리 됩니다.

- [CComCoClass](../atl/reference/ccomcoclass-class.md) 는 개체의 기본 클래스 팩터리 및 집계 모델을 정의 합니다.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 는 개체의 이중 인터페이스 부분에 대 한 기본 구현을 제공 `IDispatch Interface` 합니다.

- [은 isupporterrorinfoimpl](../atl/reference/isupporterrorinfoimpl-class.md) 는 `ISupportErrorInfo` 오류 정보를 호출 체인에 올바르게 전파할 수 있도록 하는 인터페이스를 구현 합니다.

## <a name="in-this-section"></a>섹션 내용

[CComObjectRootEx 구현](../atl/implementing-ccomobjectrootex.md)<br/>
구현에 대 한 예제 COM 맵 항목을 표시 `CComObjectRootEx` 합니다.

[CComObject, CComAggObject 및 CComPolyObject 구현](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
**DECLARE_ \* _AGGREGATABLE** 매크로가, 및 사용에 영향을 주는 방법에 대해 설명 합니다 `CComObject` `CComAggObject` `CComPolyObject` .

[IDispatch 및 IErrorInfo 지원](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
및 인터페이스를 지 원하는 데 사용할 ATL 구현 클래스를 나열 합니다 `IDispatch` `IErrorInfo` .

[IDispEventImpl 지원](../atl/supporting-idispeventimpl.md)<br/>
클래스에 대 한 연결 지점을 구현 하는 단계에 대해 설명 합니다.

[기본 클래스 팩터리 및 집계 모델 변경](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
기본 클래스 팩터리 및 집계 모델을 변경 하는 데 사용할 매크로를 표시 합니다.

[집계 된 개체 만들기](../atl/creating-an-aggregated-object.md)<br/>
집계 된 개체를 만드는 단계를 나열 합니다.

## <a name="related-sections"></a>관련 단원

[ATL 프로젝트 만들기](../atl/reference/creating-an-atl-project.md)<br/>
ATL COM 개체를 만드는 방법에 대 한 정보를 제공 합니다.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
액티브 템플릿 라이브러리를 사용하여 프로그래밍하는 방법에 대한 개념 항목의 링크를 제공합니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)
