---
description: '자세히 알아보기: TN031: 컨트롤 막대'
title: 'TN031: 컨트롤 막대'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.bars
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
ms.openlocfilehash: 42dddf1afabdf2ab04ba8441208e7109eeacbd65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215549"
---
# <a name="tn031-control-bars"></a>TN031: 컨트롤 막대

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 메모는 MFC의 컨트롤 막대 클래스에 대해 설명 합니다. 일반적인 [Ccontrolbar](#_mfcnotes_ccontrolbar), [cstatusbar](#_mfcnotes_cstatusbar), [CToolBar](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)및 `CDockBar` 입니다.

## <a name="ccontrolbar"></a><a name="_mfcnotes_ccontrolbar"></a> CControlBar

는 `ControlBar` `CWnd` 다음과 같은 파생 클래스입니다.

- 프레임 창의 위쪽 또는 아래쪽에 정렬됩니다.

- HWND 기반 컨트롤(예: `CDialogBar`) 또는 비`HWND` 기반 항목(예: `CToolBar`, `CStatusBar`)인 자식 항목을 포함할 수 있습니다.

컨트롤 막대는 추가 스타일을 지원합니다.

- CBRS_TOP (기본값) 컨트롤 막대를 위쪽에 고정 합니다.

- 컨트롤 막대를 아래쪽에 고정 CBRS_BOTTOM 합니다.

- 부모의 크기가 조정 될 때 컨트롤 막대의 위치를 변경 하지 CBRS_NOALIGN 합니다.

`CControlBar` 에서 파생된 클래스는 더 흥미로운 구현을 제공합니다.

- `CStatusBar` 상태 표시줄, 항목은 텍스트를 포함하는 상태 표시줄 창입니다.

- `CToolBar` 도구 모음, 항목은 행으로 정렬되는 비트맵 단추입니다.

- `CDialogBar` 표준 Windows 컨트롤(대화 상자 템플릿 리소스에서 생성됨)을 포함하는 도구 모음 같은 프레임

- `CDockBar` 다른 파생 개체에 대 한 일반화 된 도킹 영역 `CControlBar` 입니다. 이 클래스에서 사용 가능한 특정 멤버 함수 및 변수는 이후 릴리스에서 변경될 수 있습니다.

모든 컨트롤 막대 개체/창은 일부 부모 프레임 창의 자식 창이 되며, 일반적으로 프레임의 클라이언트 영역(예: MDI 클라이언트 또는 뷰)에 형제로 추가됩니다. 컨트롤 막대의 자식 창 ID가 중요합니다. 컨트롤 막대의 기본 레이아웃은 ID가 AFX_IDW_CONTROLBAR_FIRST에서 AFX_IDW_CONTROLBAR_LAST 사이 범위에 속하는 컨트롤 막대에만 작동합니다. 256개의 컨트롤 막대 ID 범위가 있지만 이러한 컨트롤 막대 ID 중 처음 32개는 특별히 인쇄 미리 보기 아키텍처에서 지원됩니다.

`CControlBar` 클래스는 다음에 대한 표준 구현을 제공합니다.

- 프레임의 위쪽, 아래쪽 또는 옆쪽에 컨트롤 막대 정렬

- 컨트롤 항목 배열 할당

- 파생된 클래스의 구현 지원

C++ 컨트롤 막대 개체는 일반적으로 `CFrameWnd` 파생 클래스의 멤버로 포함되며, 부모 `HWND` 및 개체가 제거되면 삭제됩니다. 힙에 컨트롤 막대 개체를 할당해야 하는 경우 *가 제거될 때 컨트롤 막대에 "* delete this **"가 적용되도록** m_bAutoDestruct **멤버를** TRUE `HWND` 로 설정하기만 하면 됩니다.

> [!NOTE]
> `CControlBar`, 또는와 같은 MFC의 파생 클래스 중 하나를 사용 하는 대신 사용자가 직접 파생 된 클래스를 만드는 경우 `CStatusBar` `CToolBar` `CDialogBar` *m_dwStyle* 데이터 멤버를 설정 해야 합니다. 이 작업은 다음의 재정의에서 수행할 수 있습니다 `Create` .

```
// CMyControlBar is derived from CControlBar
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)
{
    m_dwStyle = dwStyle;

.
.
.
}
```

**컨트롤 막대 레이아웃 알고리즘**

컨트롤 막대 레이아웃 알고리즘은 매우 간단합니다. 프레임 창에서 컨트롤 막대 범위의 모든 자식 항목에 WM_SIZEPARENT 메시지를 보냅니다. 이 메시지와 함께 부모의 클라이언트 사각형에 대한 포인터가 전달됩니다. 이 메시지는 Z축의 자식 항목에 전송됩니다. 컨트롤 막대 자식 항목은 이 정보를 사용하여 배치되고 부모의 클라이언트 영역 크기를 줄입니다. 보통 크기의 클라이언트 영역(컨트롤 막대보다 작음)용으로 남겨진 마지막 사각형은 주 클라이언트 창(일반적으로 MDI 클라이언트, 뷰 또는 분할자 창)을 배치하는 데 사용됩니다.

자세한 내용은 `CWnd::RepositionBars` 및 `CFrameWnd::RecalcLayout` 을 참조하세요.

WM_SIZEPARENT를 포함 한 MFC 개인 Windows 메시지는 [기술 참고 24](../mfc/tn024-mfc-defined-messages-and-resources.md)에 설명 되어 있습니다.

## <a name="cstatusbar"></a><a name="_mfcnotes_cstatusbar"></a> CStatusBar

상태 표시줄은 텍스트 출력 창 행이 있는 컨트롤 막대입니다. 텍스트 출력 창을 사용하는 두 가지 일반적인 방법은 다음과 같습니다.

- 메시지 줄

     (예: 표준 메뉴 도움말 메시지 줄). 일반적으로 0 기반 인덱스를 통해 액세스

- 상태 표시기

     (예: CAP, NUM 및 SCRL 표시기). 일반적으로 문자열/명령 ID를 통해 액세스

상태 표시줄의 글꼴은 10포인트 MS Sans Serif(Windows 인터페이스 애플리케이션 디자인 가이드 또는 10포인트 Swiss 가변 폭 글꼴의 가장 일치하는 글꼴 매퍼 항목에 지정)입니다. 일본어 버전과 같은 특정 버전의 Windows에서는 선택되는 글꼴이 다릅니다.

상태 표시줄에 사용되는 색은 Windows 인터페이스 애플리케이션 디자인 가이드의 권장 사항과도 일치합니다. 이러한 색은 하드 코딩되지 않으며 제어판의 사용자 지정에 대한 응답으로 동적으로 변경됩니다.

|항목|Windows COLOR 값|기본 RGB|
|----------|-------------------------|-----------------|
|상태 표시줄 배경|COLOR_BTNFACE|RGB(192, 192, 192)|
|상태 표시줄 텍스트|COLOR_BTNTEXT|RGB(000, 000, 000)|
|상태 표시줄 위쪽/왼쪽 가장자리|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|상태 표시줄 아래쪽/오른쪽 가장자리|COLOR_BTNSHADOW|RGB(128, 128, 128)|

**CCmdUI의 CStatusBar 지원**

표시기는 일반적으로 ON_UPDATE_COMMAND_UI 메커니즘을 통해 업데이트 됩니다. 유휴 시간에 상태 표시줄은 표시기 창의 문자열 ID로 ON_UPDATE_COMMAND_UI 처리기를 호출 합니다.

ON_UPDATE_COMMAND_UI 처리기는 다음을 호출할 수 있습니다.

- `Enable`: 창을 활성화 하거나 비활성화 합니다. 비활성화된 창은 정확히 활성화된 창처럼 표시되지만 텍스트가 보이지 않습니다(즉, 텍스트 표시기가 해제됨).

- `SetText`: 텍스트를 변경 합니다. 이를 사용할 때는 창 크기가 자동으로 조정되지 않으므로 주의해야 합니다.

[만들기 및 사용자 지정 API에 대한 자세한 내용은](../mfc/reference/cstatusbar-class.md) 클래스 라이브러리 참조 *에서* CStatusBar `CStatusBar` 클래스를 참조하세요. 상태 표시줄의 사용자 지정은 대부분 상태 표시줄이 처음에 표시되기 전에 수행해야 합니다.

상태 표시줄은 하나의 스트레치 창(일반적으로 첫 번째 창)만 지원합니다. 이 창의 크기는 실제로 최소 크기입니다. 상태 표시줄이 모든 창의 최소 크기보다 큰 경우 스트레치 창에 임의의 추가 너비가 제공됩니다. 상태 표시줄이 있는 기본 애플리케이션은 첫 번째 창이 스트레치이므로 CAP, NUM 및 SCRL에 대한 오른쪽 맞춤 표시기가 있습니다.

## <a name="ctoolbar"></a><a name="_mfcnotes_ctoolbar"></a> CToolBar

도구 모음은 구분 기호를 포함할 수 있는 비트맵 단추 행이 있는 컨트롤 막대입니다. 두 가지 스타일의 단추, 즉 누름 단추 및 확인란 단추가 지원됩니다. 라디오 그룹 기능은 확인란 단추 및 ON_UPDATE_COMMAND_UI를 사용 하 여 빌드할 수 있습니다.

도구 모음의 모든 비트맵 단추는 하나의 비트맵에서 가져옵니다. 이 비트맵은 각 단추에 대한 하나의 이미지 또는 문자 모양을 포함해야 합니다. 일반적으로 비트맵의 이미지/문자 모양 순서는 화면에 그려지는 순서와 동일합니다. 사용자 지정 API를 사용하여 이를 변경할 수 있습니다.

각 단추는 크기가 같아야 합니다. 기본값은 표준 24x22 픽셀입니다. 각 이미지/문자 모양은 크기가 같고 비트맵에 세로로 정렬되어야 합니다. 기본 이미지/문자 모양 크기는 16x15 픽셀입니다. 따라서 표준 크기를 사용하는 10개의 단추가 있는 도구 모음에는 너비가 160픽셀이고 높이가 15픽셀인 비트맵이 필요합니다.

각 단추에는 하나의 이미지/문자 모양만 있습니다. 이 하나의 이미지/문자 모양에서 여러 단추 상태 및 스타일(예: 누름, 위쪽, 아래쪽, 사용 안 함, 누른 상태로 사용 안 함, 비활성화 상태)이 알고리즘 방식으로 생성됩니다. 이론적으로 모든 색 비트맵 또는 DIB를 사용할 수 있습니다. 여러 단추 상태를 생성하는 알고리즘은 원본 이미지가 회색 음영인 경우에 최상으로 작동합니다. 예제는 MFC 일반 샘플 [CLIPART](../overview/visual-cpp-samples.md) 에 제공된 표준 도구 모음 단추 및 도구 모음 단추 클립 아트를 참조하세요.

도구 모음에 사용되는 색은 Windows 인터페이스 애플리케이션 디자인 가이드의 권장 사항과도 일치합니다. 이러한 색은 하드 코딩되지 않으며 제어판의 사용자 지정에 대한 응답으로 동적으로 변경됩니다.

|항목|Windows COLOR 값|기본 RGB|
|----------|-------------------------|-----------------|
|도구 모음 배경|COLOR_BTNFACE|RGB(192,192,192)|
|도구 모음 단추 위쪽/왼쪽 가장자리|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|
|도구 모음 단추 아래쪽/오른쪽 가장자리|COLOR_BTNSHADOW|RGB(128,128,128)|

또한 도구 모음 비트맵 단추는 표준 Windows 단추 컨트롤인 경우에도 다시 칠해집니다. 이 다시 칠하기는 비트맵이 리소스에서 로드되는 경우에 발생하며, 제어판의 사용자 지정에 따른 시스템 색의 변경에 대한 응답으로 발생합니다. 도구 모음 비트맵의 다음 색은 자동으로 다시 칠해지므로 주의해서 사용해야 합니다. 비트맵의 일부를 다시 칠하지 않으려면 매핑된 RGB 값 중 하나와 근접한 색을 사용합니다. 매핑은 정확한 RGB 값을 기반으로 수행됩니다.

|RGB 값|동적으로 매핑된 COLOR 값|
|---------------|------------------------------------|
|RGB(000, 000, 000)|COLOR_BTNTEXT|
|RGB(128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

[만들기 및 사용자 지정 API에 대한 자세한 내용은](../mfc/reference/ctoolbar-class.md) 클래스 라이브러리 참조 *에서* CToolBar `CToolBar` 클래스를 참조하세요. 도구 모음의 사용자 지정은 대부분 도구 모음이 처음에 표시되기 전에 수행해야 합니다.

사용자 지정 API를 사용하여 단추 ID, 스타일, 스페이서 너비 및 특정 단추에 사용되는 이미지/문자 모양을 조정할 수 있습니다. 기본적으로 이러한 API는 사용할 필요가 없습니다.

## <a name="ccmdui-support-for-ctoolbar"></a>CCmdUI의 CToolBar 지원

도구 모음 단추가 항상 업데이트 되는 방식은 ON_UPDATE_COMMAND_UI 메커니즘을 통해 진행 됩니다. 유휴 시간에 도구 모음은 해당 단추의 명령 ID를 사용 하 여 ON_UPDATE_COMMAND_UI 처리기를 호출 합니다. ON_UPDATE_COMMAND_UI는 구분 기호에 대해 호출 되지 않지만 누름 단추 및 확인란 단추에 대해 호출 됩니다.

ON_UPDATE_COMMAND_UI 처리기는 다음을 호출할 수 있습니다.

- `Enable`: 단추를 사용 하거나 사용 하지 않도록 설정 합니다. 이는 누름 단추 및 확인란 단추에 대해 동일하게 작동합니다.

- `SetCheck`: 단추의 선택 상태를 설정합니다. 도구 모음 단추에 대해 이를 호출하면 확인란 단추로 전환됩니다. `SetCheck` 에서 사용할 수 있는 매개 변수는 0(선택하지 않은 상태), 1(선택한 상태) 또는 2(비활성화 상태)입니다.

- `SetRadio`: `SetCheck`의 축약형입니다.

확인란 단추는 "자동" 확인란 단추입니다. 즉, 사용자가 누르면 상태가 즉시 변경됩니다. 선택한 상태는 눌러진 상태입니다. 기본 제공 사용자 인터페이스에는 단추를 "비활성화 상태"로 변경할 방법이 없습니다. 이는 코드를 통해 수행해야 합니다.

사용자 지정 Api는 지정 된 도구 모음 단추의 상태를 변경할 수 있도록 허용 합니다. 특히 도구 모음 단추가 나타내는 명령에 대 한 ON_UPDATE_COMMAND_UI 처리기에서 이러한 상태를 변경 해야 합니다. 유휴 처리는 ON_UPDATE_COMMAND_UI 처리기를 사용 하 여 도구 모음 단추의 상태를 변경 하므로 SetButtonStyle을 통해 수행 되는 이러한 상태 변경은 다음 유휴 상태 후에 손실 될 수 있습니다.

도구 모음 단추는 일반 단추 또는 메뉴 항목과 같은 WM_COMMAND 메시지를 보내며, 일반적으로 ON_UPDATE_COMMAND_UI 처리기를 제공 하는 동일한 클래스의 ON_COMMAND 처리기에 의해 처리 됩니다.

화면 표시 상태에 사용되는 도구 모음 단추 스타일(TBBS_ 값)에는 다음 4가지가 있습니다.

- TBBS_CHECKED:   확인란이 현재 선택되어 있습니다(누름).

- TBBS_INDETERMINATE:   확인란이 현재 비활성화 상태입니다.

- TBBS_DISABLED:   단추가 현재 비활성화되어 있습니다.

- TBBS_PRESSED:   단추가 현재 눌러져 있습니다.

Windows 인터페이스 애플리케이션 디자인 가이드의 6가지 공식 단추 스타일은 다음 TBBS 값으로 표현됩니다.

- 해제 = 0

- 마우스 누름 = TBBS_PRESSED (다른 모든 스타일 &#124;)

- 사용 안 함 = TBBS_DISABLED

- 누름 = TBBS_CHECKED

- Down Disabled = TBBS_CHECKED &#124; TBBS_DISABLED

- 비활성화 상태 = TBBS_INDETERMINATE

## <a name="cdialogbar"></a><a name="_mfcnotes_cdialogbar"></a> CDialogBar

대화 상자 막대는 표준 Windows 컨트롤을 포함하는 컨트롤 막대입니다. 컨트롤을 포함하고 컨트롤 간의 탭 이동을 지원한다는 점에서 대화 상자처럼 작동합니다. 또한 대화 상자 템플릿을 사용하여 막대를 나타낸다는 점에서도 대화 상자처럼 작동합니다.

`CDialogBar` 는 표준 누름 단추 컨트롤을 포함하는 인쇄 미리 보기 도구 모음에 사용됩니다.

`CDialogBar` 를 사용하는 것은 `CFormView`를 사용하는 것과 유사합니다. 대화 상자 막대에 대한 대화 상자 템플릿을 정의하고 WS_CHILD 이외의 모든 스타일을 제거해야 합니다. 대화 상자는 표시되지 않아야 합니다.

`CDialogBar` 에 대한 컨트롤 알림은 도구 모음 단추와 마찬가지로 컨트롤 막대의 부모로 전송됩니다.

## <a name="ccmdui-support-for-cdialogbar"></a>CCmdUI의 CDialogBar 지원

대화 상자 표시줄 단추는 ON_UPDATE_COMMAND_UI 처리기 메커니즘을 통해 업데이트 해야 합니다. 유휴 시간에 대화 상자 모음은 ID >= 0x8000 (즉, 명령 Id 범위)이 있는 모든 단추의 명령 ID를 사용 하 여 ON_UPDATE_COMMAND_UI 처리기를 호출 합니다.

ON_UPDATE_COMMAND_UI 처리기는 다음을 호출할 수 있습니다.

- Enable: 단추를 활성화하거나 비활성화합니다.

- SetText: 단추의 텍스트를 변경합니다.

표준 창 관리자 API를 통해 사용자 지정을 수행할 수 있습니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
