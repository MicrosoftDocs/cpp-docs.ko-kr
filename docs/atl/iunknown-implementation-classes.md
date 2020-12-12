---
description: '자세히 알아보기: IUnknown 구현 클래스'
title: IUnknown 구현 클래스 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: a28bd14be86501fd6566b8038b73a51efcc1c18d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147656"
---
# <a name="iunknown-implementation-classes"></a>IUnknown 구현 클래스

다음 클래스는 `IUnknown` 및 관련 메서드를 구현 합니다.

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 집계 된 개체와 집계할 않는 개체에 대 한 참조 횟수를 관리 합니다. 스레딩 모델을 지정할 수 있습니다.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 집계 된 개체와 집계할 않는 개체에 대 한 참조 횟수를 관리 합니다. 서버의 기본 스레딩 모델을 사용 합니다.

- [CComAggObject](../atl/reference/ccomaggobject-class.md) `IUnknown` 집계 된 개체에 대해를 구현 합니다.

- [CComObject](../atl/reference/ccomobject-class.md) 집계 되지 않은 `IUnknown` 개체에 대해를 구현 합니다.

- [Ccompolyobject](../atl/reference/ccompolyobject-class.md) `IUnknown` 집계 및 집계 되지 않은 개체에 대해를 구현 합니다. 를 사용 하면 `CComPolyObject` `CComAggObject` 모듈에 및가 모두 `CComObject` 포함 되지 않습니다. 단일 `CComPolyObject` 개체는 집계 된 사례와 비 집계 사례를 모두 처리 합니다.

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) `IUnknown` 모듈 잠금 횟수를 수정 하지 않고 집계할 수 없는 개체에 대해를 구현 합니다.

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) `IUnknown` 는 분리 인터페이스에 대해를 구현 합니다.

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) `IUnknown` "캐시 된" 분리 인터페이스에 대해를 구현 합니다.

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) `IUnknown` 집계 또는 분리 인터페이스의 내부 개체에 대해를 구현 합니다.

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) 모듈에서 참조 횟수를 관리 하 여 개체가 삭제 되지 않도록 합니다.

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md) 의 기초 구현을 사용 하 여 임시 COM 개체를 만듭니다 `IUnknown` .

## <a name="related-articles"></a>관련 문서

[ATL COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>참고 항목

[클래스 개요](../atl/atl-class-overview.md)<br/>
[집계 및 클래스 팩터리 매크로](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[COM 맵 매크로](../atl/reference/com-map-macros.md)<br/>
[COM 맵 전역 함수](../atl/reference/com-map-global-functions.md)
