---
description: '자세히 알아보기: 여러 이중 인터페이스'
title: 여러 이중 인터페이스
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
ms.openlocfilehash: d90c0176b3165cc0e5b976a29ec58b58fd3a7a56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159417"
---
# <a name="multiple-dual-interfaces"></a>여러 이중 인터페이스

이중 인터페이스의 장점 (즉, vtable 및 런타임에 바인딩 모두의 유연성)을 결합 하 여 다중 상속 기술을 통해 클래스를 스크립팅 언어와 c + +에서 사용할 수 있도록 하는 것이 좋습니다.

단일 COM 개체에 여러 이중 인터페이스를 노출할 수는 있지만 권장 되지는 않습니다. 이중 인터페이스가 여러 개 있는 경우에는 하나의 `IDispatch` 인터페이스만 노출 되어야 합니다. 이로 인해 함수 손실 또는 코드 복잡성 증가와 같은 저하를 방지할 수 있습니다. 이 방법을 고려 하는 개발자는 장점과 단점을 신중 하 게 평가 해야 합니다.

## <a name="exposing-a-single-idispatch-interface"></a>단일 IDispatch 인터페이스 노출

의 두 개 이상의 특수화에서 파생 하 여 단일 개체에 여러 개의 이중 인터페이스를 노출할 수 있습니다 `IDispatchImpl` . 그러나 클라이언트가 인터페이스를 쿼리할 수 있도록 허용 하는 경우 `IDispatch` [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) 매크로 (또는 [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)))를 사용 하 여의 구현에 사용할 기본 클래스를 지정 해야 `IDispatch` 합니다.

[!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]

`IDispatch`인터페이스는 하나만 노출 되므로 인터페이스를 통해 개체에 액세스할 수 있는 클라이언트는 `IDispatch` 다른 인터페이스의 메서드나 속성에 액세스할 수 없습니다.

## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>여러 이중 인터페이스를 IDispatch의 단일 구현으로 결합

ATL은 여러 이중 인터페이스를의 단일 구현으로 결합 하는 지원을 제공 하지 않습니다 `IDispatch` . 그러나 개별 인터페이스의 합집합을 포함 하는 템플릿 클래스를 만들거나 `IDispatch` , 함수를 수행 하는 새 개체를 만들거나, `QueryInterface` 중첩 된 개체의 typeinfo 기반 구현을 사용 하 여 인터페이스를 만드는 등 여러 가지 알려진 방법으로 인터페이스를 수동으로 결합할 수 있습니다 `IDispatch` .

이러한 접근 방식에는 잠재적 네임 스페이스 충돌과 관련 된 문제가 있으며 코드 복잡성 및 유지 관리도 가능 합니다. 여러 이중 인터페이스를 만드는 것은 좋지 않습니다.

## <a name="see-also"></a>참고 항목

[이중 인터페이스 및 ATL](../atl/dual-interfaces-and-atl.md)
