---
description: '자세한 정보: 이중 인터페이스 구현'
title: 이중 인터페이스 구현 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: e20bbe293cb7d6e7ae0f4d0482f1003571178ab9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147799"
---
# <a name="implementing-a-dual-interface"></a>이중 인터페이스 구현

이중 인터페이스에서 메서드의 기본 구현을 제공 하는 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 클래스를 사용 하 여 이중 인터페이스를 구현할 수 있습니다 `IDispatch` . 자세한 내용은 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)을 참조하십시오.

이 클래스를 사용 하려면 다음을 수행 합니다.

- 형식 라이브러리에서 이중 인터페이스를 정의 합니다.

- 의 특수화에서 클래스를 파생 시킵니다 `IDispatchImpl` (인터페이스 및 형식 라이브러리에 대 한 정보를 템플릿 인수로 전달).

- 를 통해 이중 인터페이스를 노출 하도록 COM 맵에 항목 (또는 항목)을 추가 `QueryInterface` 합니다.

- 클래스에서 인터페이스의 vtable 부분을 구현 합니다.

- 런타임에 개체에서 인터페이스 정의를 포함 하는 형식 라이브러리를 사용할 수 있는지 확인 합니다.

## <a name="atl-simple-object-wizard"></a>ATL 단순 개체 마법사

새 인터페이스와이 인터페이스를 구현 하는 새 클래스를 만들려는 경우 [Atl 클래스 추가 대화 상자](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)를 사용 하 고 [Atl 단순 개체 마법사](../atl/reference/atl-simple-object-wizard.md)를 사용할 수 있습니다.

## <a name="implement-interface-wizard"></a>인터페이스 구현 마법사

기존 인터페이스를 사용 하는 경우 [인터페이스 구현 마법사](../atl/reference/adding-a-new-interface-in-an-atl-project.md) 를 사용 하 여 필요한 기본 클래스, COM 맵 항목 및 기본 메서드 구현을 기존 클래스에 추가할 수 있습니다.

> [!NOTE]
> 형식 라이브러리의 주 및 부 버전 번호가 기본 클래스에 템플릿 인수로 전달 되도록 생성 된 기본 클래스를 조정 해야 할 수 있습니다 `IDispatchImpl` . 인터페이스 구현 마법사는 형식 라이브러리 버전 번호를 확인 하지 않습니다.

## <a name="implementing-idispatch"></a>IDispatch 구현

해당 하는 `IDispatchImpl` 이중 인터페이스를 설명 하는 형식 라이브러리를 사용 하는 경우 기본 클래스를 사용 하 여 COM 맵에 적절 한 항목을 지정 하 여 ( [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) 또는 [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) 매크로 사용) 인터페이스의 구현을 제공할 수 있습니다. 예를 들어이 방식으로 인터페이스를 구현 하는 것이 매우 일반적입니다 `IDispatch` . ATL 단순 개체 마법사 및 인터페이스 구현 마법사는 모두 이러한 방식으로를 구현 한다고 가정 `IDispatch` 하므로 맵에 적절 한 항목을 추가 합니다.

> [!NOTE]
> ATL은 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 및 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 클래스를 제공 하 여 호환 되는 이중 인터페이스의 정의가 포함 된 형식 라이브러리를 요구 하지 않고 dispinterface를 구현할 수 있도록 합니다.

## <a name="see-also"></a>참고 항목

[이중 인터페이스 및 ATL](../atl/dual-interfaces-and-atl.md)
