---
title: ATL 프로젝트에 새 인터페이스 추가
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 8bf0138f85929e06b67e9a2e294eda8a2f385e1a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499383"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>ATL 프로젝트에 새 인터페이스 추가

개체 또는 컨트롤에 인터페이스를 추가 하는 경우 해당 인터페이스의 각 메서드에 대 한 스텁 함수를 만듭니다. 개체 또는 컨트롤에서 현재 기존 형식 라이브러리에 있는 인터페이스만 추가할 수 있습니다. 또한 인터페이스를 추가 하는 클래스는 [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) 매크로를 구현 해야 하며, 프로젝트에 특성이 지정 된 경우에는 특성이 있어야 합니다 `coclass` .

클래스 뷰에서 수동으로 또는 코드 마법사를 사용 하 여 다음 두 가지 방법 중 하나로 컨트롤에 새 인터페이스를 추가할 수 있습니다.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>클래스 뷰에서 코드 마법사를 사용 하 여 기존 개체 또는 컨트롤에 인터페이스를 추가 하려면

1. [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 컨트롤의 클래스 이름을 마우스 오른쪽 단추로 클릭 합니다. 예를 들어, 모든 컨트롤 또는 복합 컨트롤 또는 헤더 파일에서 BEGIN_COM_MAP 매크로를 구현 하는 기타 컨트롤 클래스입니다.

1. 바로 가기 메뉴에서 **추가**를 클릭 하 고 **인터페이스 구현**을 클릭 합니다.

1. [인터페이스 구현 마법사](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard)에서 구현할 인터페이스를 선택 합니다. 사용 가능한 typelib에 인터페이스가 없으면 .idl 파일에 수동으로 추가 해야 합니다.

## <a name="to-add-a-new-interface-manually"></a>수동으로 새 인터페이스를 추가 하려면

1. 새 인터페이스의 정의를 .idl 파일에 추가 합니다.

1. 인터페이스에서 개체 또는 컨트롤을 파생 시킵니다.

1. 인터페이스에 대 한 새 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 을 만들거나, 프로젝트에 특성이 지정 된 경우 특성을 추가 `coclass` 합니다.

1. 인터페이스에서 메서드를 구현 합니다.

## <a name="see-also"></a>참고 항목

[ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL 및 C 런타임 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
