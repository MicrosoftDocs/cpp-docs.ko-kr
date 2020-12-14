---
description: '자세히 알아보기: 컨트롤 클래스'
title: 컨트롤 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: eb0bee6d865867a052b5f49408bdaa1b70da343f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310124"
---
# <a name="control-classes"></a>컨트롤 클래스

컨트롤 클래스는 정적 텍스트 컨트롤에서 트리 컨트롤에 이르는 다양 한 표준 Windows 컨트롤을 캡슐화 합니다. 또한 MFC는 비트맵 및 컨트롤 막대를 포함 하는 단추를 비롯 한 몇 가지 새로운 컨트롤을 제공 합니다.

클래스 이름이 "**Ctrl**"로 끝나는 컨트롤은 windows 95 및 windows NT 버전 3.51에서 새로 추가한 것입니다.

## <a name="static-display-controls"></a>정적 디스플레이 컨트롤

[CStatic](reference/cstatic-class.md)<br/>
정적 디스플레이 창입니다. 정적 컨트롤은 대화 상자 또는 창에서 다른 컨트롤의 레이블을 가져오거나, 상자를 구분 하는 데 사용 됩니다. 텍스트 또는 상자가 아닌 그래픽 이미지를 표시할 수도 있습니다.

## <a name="text-controls"></a>텍스트 컨트롤

[CEdit](reference/cedit-class.md)<br/>
편집 가능한 텍스트 컨트롤 창입니다. 편집 컨트롤은 사용자의 텍스트 입력을 허용 하는 데 사용 됩니다.

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
에서는 IP (인터넷 프로토콜) 주소를 조작 하기 위한 편집 상자를 지원 합니다.

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
사용자가 텍스트를 입력 하 고 편집할 수 있는 컨트롤입니다. 에서 캡슐화 된 컨트롤과는 달리 `CEdit` rich edit 컨트롤은 문자 및 단락 서식 지정 및 OLE 개체를 지원 합니다.

## <a name="controls-that-represent-numbers"></a>숫자를 나타내는 컨트롤

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
사용자가 값 또는 값 집합을 선택 하기 위해 이동 하는 슬라이더를 포함 하는 컨트롤입니다.

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
사용자가 클릭 하 여 값을 증가 시키거나 감소 시킬 수 있는 화살표 단추 쌍입니다.

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
작업의 진행률을 나타내기 위해 서서히 왼쪽에서 오른쪽으로 채워진 사각형을 표시 합니다.

[CScrollBar](reference/cscrollbar-class.md)<br/>
스크롤 막대 컨트롤 창입니다. 클래스는 사용자가 범위 내에서 위치를 지정할 수 있는 대화 상자 또는 창에서 컨트롤로 사용할 스크롤 막대의 기능을 제공 합니다.

## <a name="buttons"></a>단추

[CButton](reference/cbutton-class.md)<br/>
단추 컨트롤 창입니다. 클래스는 대화 상자 또는 창에서 누름 단추, 확인란 또는 라디오 단추에 대 한 프로그래밍 인터페이스를 제공 합니다.

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
텍스트 캡션이 아닌 비트맵을 포함 하는 단추입니다.

## <a name="lists"></a>목록

[CListBox](reference/clistbox-class.md)<br/>
목록 상자 컨트롤 창입니다. 목록 상자에는 사용자가 보고 선택할 수 있는 항목의 목록이 표시 됩니다.

[CDragListBox](reference/cdraglistbox-class.md)<br/>
Windows 목록 상자의 기능을 제공 합니다. 사용자가 목록 상자 내에서 파일 이름 및 문자열 리터럴과 같은 목록 상자 항목을 이동할 수 있습니다. 이 기능이 포함 된 목록 상자는 프로젝트에 경로 이름 또는 파일 포함과 같이 사전순이 아닌 순서로 항목 목록에 유용 합니다.

[CComboBox](reference/ccombobox-class.md)<br/>
콤보 상자 컨트롤 창입니다. 콤보 상자는 편집 컨트롤과 목록 상자로 구성 됩니다.

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
이미지 목록에 대한 지원을 제공하여 콤보 상자 컨트롤을 확장합니다.

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
사용자가 각 항목 옆의 확인란을 선택 하거나 선택을 취소할 수 있는 확인란이 있는 항목의 목록을 표시 합니다.

[CListCtrl](reference/clistctrl-class.md)<br/>
각각 아이콘과 레이블로 구성 되는 항목 컬렉션을 파일 탐색기의 오른쪽 창과 비슷한 방식으로 표시 합니다.

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
파일 탐색기의 왼쪽 창과 비슷한 방식으로 정렬 된 아이콘 및 레이블의 계층 목록을 표시 합니다.

## <a name="toolbars-and-status-bars"></a>도구 모음 및 상태 표시줄

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Windows의 도구 모음 공용 컨트롤의 기능을 제공합니다. 대부분의 MFC 프로그램은이 클래스 대신 [CToolBar](reference/ctoolbar-class.md) 를 사용 합니다.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
응용 프로그램에서 상태 정보를 표시할 수 있는 가로 창 (일반적으로 창으로 구분)입니다. 대부분의 MFC 프로그램은이 클래스 대신 [Cstatusbar](reference/cstatusbar-class.md) 를 사용 합니다.

## <a name="miscellaneous-controls"></a>기타 컨트롤

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
간단한 비디오 클립을 표시 합니다.

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
응용 프로그램에서 도구의 용도를 설명 하는 한 줄의 텍스트를 표시 하는 작은 팝업 창입니다.

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
사용자가 특정 날짜 또는 시간 값을 선택할 수 있도록 하는 확장 된 편집 컨트롤 또는 간단한 달력 인터페이스 컨트롤을 지원 합니다.

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
열의 제목이 나 레이블을 표시 합니다.

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
사용자가 날짜를 선택할 수 있는 간단한 달력 인터페이스 컨트롤을 지원 합니다.

[CTabCtrl](reference/ctabctrl-class.md)<br/>
사용자가 클릭할 수 있는 탭이 있는 컨트롤로, 노트북의 구분선과 유사 합니다.

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
사용자가 작업을 빠르게 수행 하기 위해 누를 수 있는 바로 가기 키 조합을 만들 수 있습니다.

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
사용자가 포함 된 링크를 클릭할 때 표시 되는 텍스트를 렌더링 하 고 적절 한 응용 프로그램을 시작 합니다.

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
MFC 창에서 WebBrowser ActiveX 컨트롤의 기능을 제공합니다.

## <a name="related-classes"></a>관련 클래스

[CImageList](reference/cimagelist-class.md)<br/>
Windows 이미지 목록의 기능을 제공합니다. 이미지 목록은 목록 컨트롤 및 트리 컨트롤과 함께 사용됩니다. 이러한 컨트롤은 또한 동일한 크기의 비트맵 집합을 저장하고 아카이브하는 데 사용할 수 있습니다.

[CCtrlView](reference/cctrlview-class.md)<br/>
Windows 컨트롤과 연결 된 모든 뷰의 기본 클래스입니다. 컨트롤을 기반으로 하는 뷰는 아래에 설명 되어 있습니다.

[CEditView](reference/ceditview-class.md)<br/>
Windows 표준 편집 컨트롤을 포함 하는 뷰입니다.

[CRichEditView](reference/cricheditview-class.md)<br/>
Windows rich edit 컨트롤을 포함 하는 뷰입니다.

[CListView](reference/clistview-class.md)<br/>
Windows 목록 컨트롤을 포함 하는 뷰입니다.

[CTreeView](reference/ctreeview-class.md)<br/>
Windows 트리 컨트롤을 포함 하는 뷰입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
