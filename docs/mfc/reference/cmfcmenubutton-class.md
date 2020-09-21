---
title: CMFCMenuButton 클래스
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: 2f8ef341d7f460ed6b0ec23cb8a490842eb67cbc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743271"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 클래스

사용자가 선택한 메뉴에 팝업 메뉴와 보고서를 표시하는 단추입니다.

## <a name="syntax"></a>구문

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CMFCMenuButton:: CMFCMenuButton](#cmfcmenubutton)|`CMFCMenuButton` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|디스패치 되기 전에 창 메시지를 변환 하기 위해 프레임 워크에서 호출 됩니다. ( `CMFCButton::PreTranslateMessage`을 재정의합니다.)|
|[CMFCMenuButton:: System.windows.window.sizetocontent](#sizetocontent)|텍스트 및 이미지 크기에 따라 단추의 크기를 변경 합니다.|

### <a name="data-members"></a>데이터 멤버

|속성|Description|
|----------|-----------------|
|[CMFCMenuButton:: m_bOSMenu](#m_bosmenu)|기본 시스템 팝업 메뉴를 표시할지 아니면 [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)를 사용할지를 지정 합니다.|
|[CMFCMenuButton:: m_bRightArrow](#m_brightarrow)|팝업 메뉴가 단추의 오른쪽 아래에 표시될지 여부를 지정 합니다.|
|[CMFCMenuButton:: m_bStayPressed](#m_bstaypressed)|사용자가 단추를 놓으면 메뉴 단추가 해당 상태를 변경 하는지 여부를 지정 합니다.|
|[CMFCMenuButton:: m_hMenu](#m_hmenu)|연결 된 창 메뉴에 대 한 핸들입니다.|
|[CMFCMenuButton:: m_nMenuResult](#m_nmenuresult)|사용자가 팝업 메뉴에서 선택한 항목을 나타내는 식별자입니다.|
|[CMFCMenuButton:: m_bDefaultClick](#m_bdefaultclick)| 단추 텍스트/이미지에 대 한 기본 처리를 허용 합니다.|

## <a name="remarks"></a>설명

`CMFCMenuButton`클래스는 [Cbutton 클래스](../../mfc/reference/cbutton-class.md)에서 파생 된 [cmfcbutton 클래스](../../mfc/reference/cmfcbutton-class.md) 에서 파생 됩니다. 따라서 `CMFCMenuButton` 사용 하는 것과 같은 방식으로 코드에를 사용할 수 있습니다 `CButton` .

를 만들 때 `CMFCMenuButton` 연결 된 팝업 메뉴에 핸들을 전달 해야 합니다. 그런 다음 함수를 호출 `CMFCMenuButton::SizeToContent` 합니다. `CMFCMenuButton::SizeToContent` 단추 크기가 팝업 창이 표시 되는 위치를 가리키는 화살표를 포함 하는 데 충분 한지 확인 합니다. 즉, 단추의 오른쪽 아래 또는 오른쪽에 표시 됩니다.

## <a name="example"></a>예제

다음 예제에서는 단추에 연결 된 메뉴의 핸들을 설정 하 고 텍스트 및 이미지 크기에 따라 단추의 크기를 조정 하 고 프레임 워크에서 표시 되는 팝업 메뉴를 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [새 Controls 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxmenubutton

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a> CMFCMenuButton:: CMFCMenuButton

새 [Cmfcmenubutton](../../mfc/reference/cmfcmenubutton-class.md) 개체를 생성 합니다.

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a> CMFCMenuButton:: m_bOSMenu

프레임 워크에서 표시 하는 팝업 메뉴를 나타내는 부울 멤버 변수입니다.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>설명

이 `m_bOSMenu` TRUE 이면 프레임 워크는 `TrackPopupMenu` 이 개체에 대해 상속 된 메서드를 호출 합니다. 그렇지 않으면 프레임 워크는 [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)를 호출 합니다.

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a> CMFCMenuButton:: m_bRightArrow

팝업 메뉴의 위치를 나타내는 부울 멤버 변수입니다.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>설명

사용자가 메뉴 단추를 누르면 응용 프로그램에 팝업 메뉴가 표시 됩니다. 프레임 워크는 단추 또는 단추 오른쪽에 팝업 메뉴를 표시 합니다. 이 단추에는 팝업 메뉴가 표시 되는 위치를 나타내는 작은 화살표도 있습니다. `m_bRightArrow`이 TRUE 이면 프레임 워크는 단추 오른쪽에 팝업 메뉴를 표시 합니다. 그렇지 않으면 단추 아래에 팝업 메뉴가 표시 됩니다.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a> CMFCMenuButton:: m_bStayPressed

사용자가 팝업 메뉴에서 항목을 선택 하는 동안 메뉴 단추가 눌러져 있는지 여부를 나타내는 부울 멤버 변수입니다.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>설명

`m_bStayPressed`멤버가 FALSE 이면 사용에서 단추를 클릭할 때 메뉴 단추가 눌러져 있지 않습니다. 이 경우 프레임 워크는 팝업 메뉴만 표시 합니다.

`m_bStayPressed`멤버가 TRUE 이면 사용자가 단추를 클릭할 때 메뉴 단추가 눌러져 있습니다. 사용자가 선택 하거나 취소 하 여 팝업 메뉴를 닫을 때까지 계속 눌러져 있습니다.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a> CMFCMenuButton:: m_hMenu

연결 된 메뉴에 대 한 핸들입니다.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>설명

사용자가 메뉴 단추를 클릭 하면 프레임 워크에서이 멤버 변수로 표시 된 메뉴를 표시 합니다.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a> CMFCMenuButton:: m_nMenuResult

사용자가 팝업 메뉴에서 선택 하는 항목을 나타내는 정수입니다.

```
int m_nMenuResult;
```

### <a name="remarks"></a>설명

사용자가 선택 하거나 오류가 발생 하는 경우 사용자가 메뉴를 취소 하면이 멤버 변수의 값은 0입니다.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a> CMFCMenuButton:: m_bDefaultClick

단추에서 텍스트 또는 이미지의 기본 처리를 허용 합니다.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>설명

M_bDefaultClick false로 설정 하면 단추를 클릭할 때 단추가 메뉴에 표시 됩니다.

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a> CMFCMenuButton::P reTranslateMessage

디스패치 되기 전에 창 메시지를 변환 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
진행 처리할 메시지를 포함 하는 [MSG](/windows/win32/api/winuser/ns-winuser-msg) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

메시지를 변환 하 여 디스패치할 수 없으면 0이 아닙니다. 메시지가 변환 되지 않고 디스패치 되어야 하는 경우 0입니다.

### <a name="remarks"></a>설명

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCMenuButton:: System.windows.window.sizetocontent

텍스트 크기 및 이미지 크기에 따라 단추의 크기를 변경 합니다.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>매개 변수

*bCalcOnly*<br/>
진행 이 메서드가 단추의 크기를 조정 하는지 여부를 나타내는 부울 매개 변수입니다.

### <a name="return-value"></a>반환 값

단추의 새 크기를 지정 하는 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하 고 *Bcalconly* 가 TRUE 이면는 `SizeToContent` 단추의 새 크기만 계산 합니다.

단추의 새 크기는 단추 텍스트, 이미지 및 화살표에 맞게 계산 됩니다. 또한 프레임 워크는 가로 가장자리에 대 한 10 픽셀의 미리 정의 된 여백 및 세로 가장자리의 경우 5 픽셀을 추가 합니다.

## <a name="see-also"></a>추가 정보

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 클래스](../../mfc/reference/cmfcbutton-class.md)
