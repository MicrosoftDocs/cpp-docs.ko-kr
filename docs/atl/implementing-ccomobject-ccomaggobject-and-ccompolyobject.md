---
description: CComObject, CComAggObject 및 CComPolyObject 구현에 대해 자세히 알아보세요.
title: CComObject, CComAggObject 및 CComPolyObject 구현
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e0cc8a6b65ec9d85249cd47e2f43cf1bec2b8ce2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147773"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>CComObject, CComAggObject 및 CComPolyObject 구현

[CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)및 [ccompolyobject](../atl/reference/ccompolyobject-class.md) 템플릿 클래스는 항상 상속 체인에서 가장 많이 파생 된 클래스입니다. `IUnknown` `QueryInterface` , `AddRef` 및의 모든 메서드를 처리 하는 것은 사용자의 책임입니다 `Release` . 또한 `CComAggObject` 및 `CComPolyObject` (집계 된 개체에 사용 되는 경우) 내부 알려지지 않은에 필요한 특수 참조 계산 및 의미 체계를 제공 합니다 `QueryInterface` .

`CComObject`, `CComAggObject` 또는가 사용 되는지 여부는 `CComPolyObject` 다음 매크로 중 하나 (또는 없음)를 선언 하는지 여부에 따라 달라 집니다.

|매크로|효과|
|-----------|------------|
|  DECLARE_NOT_AGGREGATABLE|항상 `CComObject` 를 사용 합니다.|
|DECLARE_AGGREGATABLE|개체가 집계 된 경우를 사용 하 고 그렇지 않으면를 사용 `CComAggObject` `CComObject` 합니다. `CComCoClass` 에이 매크로가 포함 되어 있으므로 클래스에서 선언 된 DECLARE_ * _AGGREGATABLE 매크로가 없으면 기본값이 됩니다.|
|  DECLARE_ONLY_AGGREGATABLE|항상 `CComAggObject` 를 사용 합니다. 개체가 집계 되지 않으면 오류를 반환 합니다.|
|  DECLARE_POLY_AGGREGATABLE|ATL은가 호출 될 때 **\<CYourClass> Ccompolyobject** 의 인스턴스를 만듭니다 `IClassFactory::CreateInstance` . 생성 하는 동안 알 수 없는 외부 값이 확인 됩니다. NULL 인 경우 `IUnknown` 는 집계할 수 없는 개체에 대해 구현 됩니다. 외부 unknown이 NULL이 아닌 경우는 `IUnknown` 집계 된 개체에 대해 구현 됩니다.|

및를 사용 하는 경우 `CComAggObject` `CComObject` 의 이점은 `IUnknown` 생성 되는 개체의 종류에 맞게 최적화 되어 있기 때문입니다. 예를 들어, 집계할 수 없는 개체는 참조 수만 필요 하 고, 집계 된 개체에는 내부 unknown의 참조 수와 외부 unknown에 대 한 포인터가 모두 필요 합니다.

를 사용 하는 경우의 장점은 `CComPolyObject` 집계 된 사례와 집계할 수 없는 사례를 `CComAggObject` `CComObject` 처리 하기 위해 모듈에서 및를 모두 사용 하지 않도록 하는 것입니다. 단일 `CComPolyObject` 개체는 두 경우를 모두 처리 합니다. 즉, 모듈에는 vtable의 복사본 하 나와 함수의 복사본이 하나만 있습니다. Vtable이 큰 경우 모듈 크기를 크게 줄일 수 있습니다. 그러나 vtable이 작은 경우를 사용 하면 `CComPolyObject` 집계 된 개체 또는 집계할 수 없는 개체에 대해 최적화 되지 않으므로를 사용 하 여 모듈 크기가 약간 커질 수 있습니다 `CComAggObject` `CComObject` .

## <a name="see-also"></a>참고 항목

[ATL COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)<br/>
[집계 및 클래스 팩터리 매크로](../atl/reference/aggregation-and-class-factory-macros.md)
