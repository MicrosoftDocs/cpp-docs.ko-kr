---
description: '자세히 알아보기: Toolbar 컨트롤의 모양 사용자 지정'
title: 도구 모음 컨트롤의 모양 사용자 지정
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 715062484f5856da92e0668740bb6f8ac8f9d363
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336832"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>도구 모음 컨트롤의 모양 사용자 지정

클래스는 `CToolBarCtrl` toolbar 개체의 모양 (및 경우에 따라 동작)에 영향을 주는 다양 한 스타일을 제공 합니다. `dwCtrlStyle` `CToolBarCtrl::Create` `CToolBar::CreateEx` 도구 모음 컨트롤을 처음 만들 때 (또는) 멤버 함수의 매개 변수를 설정 하 여 도구 모음 개체를 수정 합니다.

다음 스타일은 도구 모음 단추의 "3D" 측면과 단추 텍스트의 배치에 영향을 줍니다.

- **TBSTYLE_FLAT** 도구 모음과 단추가 모두 투명 한 기본 도구 모음을 만듭니다. 단추 텍스트는 단추 비트맵 아래에 나타납니다. 이 스타일을 사용 하면 커서 아래의 단추가 자동으로 강조 표시 됩니다.

- **TBSTYLE_TRANSPARENT** 투명 도구 모음을 만듭니다. 투명 도구 모음에서 도구 모음은 투명 하지만 단추는 투명 하지 않습니다. 단추 텍스트는 단추 비트맵 아래에 나타납니다.

- **TBSTYLE_LIST** 단추 텍스트를 단추 비트맵의 오른쪽에 배치 합니다.

> [!NOTE]
> 다시 그리기 문제를 방지 하려면 도구 모음 개체를 표시 하기 전에 **TBSTYLE_FLAT** 및 **TBSTYLE_TRANSPARENT** 스타일을 설정 해야 합니다.

다음 스타일은 도구 모음을 통해 사용자가 끌어서 놓기를 사용 하 여 도구 모음 개체 내에서 개별 단추의 위치를 변경할 수 있는지 여부를 결정 합니다.

- **TBSTYLE_ALTDRAG** ALT 키를 누른 채 도구 모음 단추의 위치를 끌어서 변경할 수 있습니다. 이 스타일을 지정 하지 않으면 사용자가 단추를 끌 때 SHIFT 키를 누르고 있어야 합니다.

    > [!NOTE]
    >  도구 모음 단추를 끌 수 있도록 **CCS_ADJUSTABLE** 스타일을 지정 해야 합니다.

- **TBSTYLE_REGISTERDROP** 마우스 포인터를 도구 모음 단추 위로 가져갈 때 놓기 대상 개체를 요청 하는 **TBN_GETOBJECT** 알림 메시지를 생성 합니다.

나머지 스타일은 도구 모음 개체의 시각적 및 비시각적 측면에 영향을 줍니다.

- **TBSTYLE_WRAPABLE** 여러 줄의 단추를 사용할 수 있는 도구 모음을 만듭니다. 도구 모음 단추는 동일한 줄에 모든 단추를 포함 하는 것이 너무 좁아 면 다음 줄로 "줄 바꿈" 할 수 있습니다. 줄 바꿈은 분리 및 비 그룹 경계에 발생 합니다.

- **TBSTYLE_CUSTOMERASE** **WM_ERASEBKGND** 메시지를 처리할 때 **NM_CUSTOMDRAW** 알림 메시지를 생성 합니다.

- **TBSTYLE_TOOLTIPS** 응용 프로그램에서 도구 모음의 단추에 대 한 설명 텍스트를 표시 하는 데 사용할 수 있는 도구 설명 컨트롤을 만듭니다.

도구 모음 스타일 및 확장 스타일의 전체 목록은 Windows SDK [도구 모음 컨트롤 및 단추 스타일](/windows/win32/Controls/toolbar-control-and-button-styles) 및 [도구 모음 확장 스타일](/windows/win32/Controls/toolbar-extended-styles) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](using-ctoolbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
