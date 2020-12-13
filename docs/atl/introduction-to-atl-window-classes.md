---
description: '자세히 알아보기: ATL 창 클래스 소개'
title: ATL 창 클래스 소개
ms.date: 11/04/2016
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
ms.openlocfilehash: 54a9d9764450025e51f9fac368a3434ca786fe09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152726"
---
# <a name="introduction-to-atl-window-classes"></a>ATL 창 클래스 소개

다음 ATL 클래스는 창을 구현 하 고 조작 하도록 설계 되었습니다.

- [CWindow](../atl/reference/cwindow-class.md) 를 사용 하면 창 핸들을 개체에 연결할 수 있습니다 `CWindow` . 그런 다음 `CWindow` 메서드를 호출 하 여 창을 조작 합니다.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) 를 사용 하면 새 창을 구현 하 고 메시지 맵을 사용 하 여 메시지를 처리할 수 있습니다. 새 Windows 클래스, 기존 클래스의 슈퍼 클래스 또는 기존 창을 기반으로 하는 창을 만들 수 있습니다.

- [Cdialogimpl](../atl/reference/cdialogimpl-class.md) 사용 하면 모달 또는 모덜리스 대화 상자를 구현 하 고 메시지 맵을 사용 하 여 메시지를 처리할 수 있습니다.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 은 메시지 맵이 다른 클래스에 포함 되어 있는 창을 구현 하는 미리 빌드된 클래스입니다. 를 사용 하면 `CContainedWindowT` 한 클래스에서 메시지 처리를 중앙 집중화할 수 있습니다.

- [Caxdialogimpl](../atl/reference/caxdialogimpl-class.md) 있으면 ActiveX 컨트롤을 호스트 하는 대화 상자 (모달 또는 모덜리스)를 구현할 수 있습니다.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) 를 사용 하면 기본 기능을 사용 하 여 모달 대화 상자를 구현할 수 있습니다.

- [Caxwindow](../atl/reference/caxwindow-class.md) 를 사용 하 여 ActiveX 컨트롤을 호스트 하는 창을 구현할 수 있습니다.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) 를 사용 하면 사용이 허가 된 ActiveX 컨트롤을 호스트 하는 창을 구현할 수 있습니다.

ATL은 특정 창 클래스 외에도 ATL 창 개체를 더 쉽게 구현할 수 있도록 설계 된 여러 클래스를 제공 합니다. 다음과 같습니다.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 는 새 창 클래스의 정보를 관리 합니다.

- [CWinTraits](../atl/reference/cwintraits-class.md) 및 [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) 는 ATL 창 개체의 특성을 표준화 하는 간단한 방법을 제공 합니다.

## <a name="see-also"></a>참고 항목

[창 클래스](../atl/atl-window-classes.md)
