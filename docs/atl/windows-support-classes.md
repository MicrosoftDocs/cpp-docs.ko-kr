---
title: Windows 지원 클래스 (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9182241b1d33c63aae523cae0c2c9602466e4c2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090427"
---
# <a name="windows-support-classes"></a>Windows 지원 클래스

Windows에 대 한 지원을 제공 하는 다음 클래스:

- [_U_MENUorID](../atl/reference/u-menuorid-class.md) 에 대 한 래퍼를 제공 `CreateWindow` 고 `CreateWindowEx`입니다.

- [CWindow](../atl/reference/cwindow-class.md) 창 조작 하기 위한 메서드가 포함 되어 있습니다. `CWindow`는 `CWindowImpl`, `CDialogImpl` 및 `CContainedWindow`의 기본 클래스입니다.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) 가 새 창 클래스를 기반으로 창을 구현 합니다. 또한 있습니다 슈퍼 클래스 또는 서브 클래스에 창을.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) 대화 상자를 구현 합니다.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) ActiveX 컨트롤을 호스트 하는 대화 상자 (모달 또는 모덜리스)를 구현 합니다.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) 기본 기능을 사용 하 여 대화 상자 (모달 또는 모덜리스)를 구현 합니다.

- [CAxWindow](../atl/reference/caxwindow-class.md) ActiveX 컨트롤을 호스팅하는 창의 조작 합니다.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) ActiveX 컨트롤을 호스트 하는 기능도 사용이 허가 된 ActiveX 컨트롤 호스팅에 대 한 지원 창 조작 하기 위한 메서드를 제공 합니다.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 다른 개체 내에 포함 된 창을 구현 합니다.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 새 창 클래스의 정보를 관리 합니다.

- [CDynamicChain](../atl/reference/cdynamicchain-class.md) 메시지 맵의 동적 연결을 지원 합니다.

- [CMessageMap](../atl/reference/cmessagemap-class.md) 다른 개체에 매핑되는 개체가 해당 메시지를 노출할 수 있도록 허용 합니다.

- [CWinTraits](../atl/reference/cwintraits-class.md) ATL 창 개체의 특성을 표준화 하는 간단한 방법을 제공 합니다.

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) window 스타일 및 창을 만드는 데 사용 되는 확장된 스타일에 대 한 기본값을 제공 합니다. 이러한 값 창 만드는 동안 제공 된 값에는 논리 OR 연산자를 사용 하 여 추가 됩니다.

## <a name="related-articles"></a>관련 문서

[ATL 창 클래스](../atl/atl-window-classes.md)

[ATL 자습서](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>참고 항목

[클래스 개요](../atl/atl-class-overview.md)<br/>
[메시지 맵 매크로](../atl/reference/message-map-macros-atl.md)<br/>
[창 클래스 매크로](../atl/reference/window-class-macros.md)

