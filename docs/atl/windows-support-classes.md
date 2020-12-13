---
description: '자세한 정보: Windows 지원 클래스'
title: Windows 지원 클래스 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: c88a6ef878a428581ca090e78b2fac3b5e02131d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138063"
---
# <a name="windows-support-classes"></a>Windows 지원 클래스

다음 클래스는 windows에 대 한 지원을 제공 합니다.

- [_U_MENUorID](../atl/reference/u-menuorid-class.md) 및에 대 한 래퍼를 제공 `CreateWindow` `CreateWindowEx` 합니다.

- [CWindow](../atl/reference/cwindow-class.md) 창을 조작 하기 위한 메서드를 포함 합니다. `CWindow`는 `CWindowImpl`, `CDialogImpl` 및 `CContainedWindow`의 기본 클래스입니다.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) 새 창 클래스를 기반으로 창을 구현 합니다. 를 사용 하 여 창을 서브클래싱하 나 슈퍼 클래스 할 수도 있습니다.

- [Cdialogimpl](../atl/reference/cdialogimpl-class.md) 대화 상자를 구현 합니다.

- [Caxdialogimpl](../atl/reference/caxdialogimpl-class.md) ActiveX 컨트롤을 호스트 하는 대화 상자 (모달 또는 모덜리스)를 구현 합니다.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) 기본 기능을 사용 하 여 대화 상자 (모달 또는 모덜리스)를 구현 합니다.

- [Caxwindow](../atl/reference/caxwindow-class.md) ActiveX 컨트롤을 호스트 하는 창을 조작 합니다.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) ActiveX 컨트롤을 호스트 하는 창을 조작 하 고 사용이 허가 된 ActiveX 컨트롤을 호스팅할 수 있도록 지 원하는 메서드를 제공 합니다.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 다른 개체 내에 포함 된 창을 구현 합니다.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 새 창 클래스의 정보를 관리 합니다.

- [Cdynamicchain](../atl/reference/cdynamicchain-class.md) 메시지 맵의 동적 체인을 지원 합니다.

- [Cmessagemap](../atl/reference/cmessagemap-class.md) 개체가 메시지 맵을 다른 개체에 노출할 수 있도록 합니다.

- [CWinTraits](../atl/reference/cwintraits-class.md) ATL 창 개체의 특성을 표준화 하는 간단한 방법을 제공 합니다.

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) 창 스타일 및 창 생성에 사용 되는 확장 스타일에 대 한 기본값을 제공 합니다. 이러한 값은 논리 OR 연산자를 사용 하 여 창을 만드는 동안 제공 된 값에 추가 됩니다.

## <a name="related-articles"></a>관련 문서

[ATL 창 클래스](../atl/atl-window-classes.md)

[ATL 자습서](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>참고 항목

[클래스 개요](../atl/atl-class-overview.md)<br/>
[메시지 맵 매크로](../atl/reference/message-map-macros-atl.md)<br/>
[창 클래스 매크로](../atl/reference/window-class-macros.md)
