---
description: '자세히 알아보기: 컨트롤 막대 클래스'
title: 컨트롤 막대 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: 9ccb22a90799d7af7db49cd0a1a65a1009e9f36e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310228"
---
# <a name="control-bar-classes"></a>컨트롤 막대 클래스

컨트롤 막대는 프레임 창에 연결 됩니다. 여기에는 단추, 상태 창 또는 대화 상자 템플릿이 포함 되어 있습니다. 도구 팔레트 라고도 하는 자유 부동 컨트롤 막대는 [CMiniFrameWnd](reference/cminiframewnd-class.md) 개체에 연결 하 여 구현 됩니다.

## <a name="framework-control-bars"></a>프레임 워크 컨트롤 막대

이러한 컨트롤 막대는 MFC 프레임 워크의 필수적인 부분입니다. 이러한 컨트롤은 프레임 워크와 통합 되기 때문에 Windows 컨트롤 막대 보다 사용 하기 쉽고 강력 합니다. 대부분의 MFC 응용 프로그램은 Windows 컨트롤 막대가 아닌 이러한 컨트롤 막대를 사용 합니다.

[CControlBar](reference/ccontrolbar-class.md)<br/>
이 섹션에 나열 된 MFC 컨트롤 막대의 기본 클래스입니다. 컨트롤 막대는 프레임 창의 가장자리에 맞춰진 창입니다. 컨트롤 막대에 `HWND` 는 `HWND` 도구 모음 단추와 같은를 기반으로 하지 않는 컨트롤 또는 컨트롤이 포함 됩니다.

[CDialogBar](reference/cdialogbar-class.md)<br/>
대화 상자 템플릿을 기반으로 하는 컨트롤 막대입니다.

[CReBar](reference/crebar-class.md)<br/>
컨트롤 형식으로 추가 자식 창을 포함할 수 있는 도구 모음을 지원 합니다.

[CToolBar](reference/ctoolbar-class.md)<br/>
을 기반으로 하지 않는 비트맵 명령 단추가 포함 된 도구 모음 컨트롤 창입니다 `HWND` . 대부분의 MFC 응용 프로그램은 대신이 클래스 `CToolBarCtrl` 를 사용 합니다.

[CStatusBar](reference/cstatusbar-class.md)<br/>
상태 표시줄 컨트롤 창에 대 한 기본 클래스입니다. 대부분의 MFC 응용 프로그램은 대신이 클래스 `CStatusBarCtrl` 를 사용 합니다.

## <a name="windows-control-bars"></a>Windows 컨트롤 막대

이러한 컨트롤 막대는 해당 Windows 컨트롤에 대 한 씬 래퍼입니다. 프레임 워크는 프레임 워크와 통합 되지 않으므로 이전에 나열 된 컨트롤 막대 보다 사용 하기 어렵습니다. 대부분의 MFC 응용 프로그램은 이전에 나열 된 컨트롤 막대를 사용 합니다.

[CRebarCtrl](reference/crebarctrl-class.md)<br/>
개체의 내부 컨트롤을 구현 합니다 `CRebar` .

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
응용 프로그램에서 상태 정보를 표시할 수 있는 가로 창 (일반적으로 창으로 구분)입니다.

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Windows의 도구 모음 공용 컨트롤의 기능을 제공합니다.

## <a name="related-classes"></a>관련 클래스

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
응용 프로그램에서 도구의 용도를 설명 하는 한 줄의 텍스트를 표시 하는 작은 팝업 창입니다.

[CDockState](reference/cdockstate-class.md)<br/>
컨트롤 막대에 대 한 고정 상태 데이터의 영구 저장소를 처리 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
