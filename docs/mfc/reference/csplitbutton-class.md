---
description: '자세히 알아보기: CSplitButton 클래스'
title: CSplitButton 클래스
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: e73273bbeb0d03dc5ca2a3a2e6daa1be05936280
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345123"
---
# <a name="csplitbutton-class"></a>CSplitButton 클래스

`CSplitButton`클래스는 분할 단추 컨트롤을 나타냅니다. 분할 단추 컨트롤은 사용자가 단추의 주요 부분을 클릭할 때 기본 동작을 수행하고 사용자가 단추의 드롭다운 화살표를 클릭하면 드롭다운 메뉴를 표시합니다.

## <a name="syntax"></a>구문

```
class CSplitButton : public CButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSplitButton:: CSplitButton](#csplitbutton)|`CSplitButton` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSplitButton:: Create](#create)|지정 된 스타일을 사용 하 여 분할 단추 컨트롤을 만들고 현재 개체에 연결 `CSplitButton` 합니다.|
|[CSplitButton:: SetDropDownMenu](#setdropdownmenu)|사용자가 현재 분할 단추 컨트롤의 드롭다운 화살표를 클릭할 때 표시 되는 드롭다운 메뉴를 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CSplitButton:: OnDropDown](#ondropdown)|사용자가 현재 분할 단추 컨트롤의 드롭다운 화살표를 클릭할 때 시스템이 보내는 BCN_DROPDOWN 알림을 처리 합니다.|

## <a name="remarks"></a>설명

`CSplitButton`클래스는 [cbutton](../../mfc/reference/cbutton-class.md) 클래스에서 파생 됩니다. 분할 단추 컨트롤은 BS_SPLITBUTTON 스타일이 있는 단추 컨트롤입니다. 사용자가 드롭다운 화살표를 클릭할 때 사용자 지정 메뉴를 표시 합니다. 자세한 내용은 [단추 스타일](/windows/win32/Controls/button-styles)의 BS_SPLITBUTTON 및 BS_DEFSPLITBUTTON 스타일을 참조 하세요.

다음 그림에서는 페이저 컨트롤과 (1) 분할 단추 컨트롤을 포함 하는 대화 상자를 보여 줍니다. (2) 드롭다운 화살표가 이미 클릭 되었으며 (3) 하위 메뉴가 표시 됩니다.

![splitbutton 및 pager 컨트롤이 있는 대화 상자](../../mfc/reference/media/splitbutton_pager.png "splitbutton 및 pager 컨트롤이 있는 대화 상자")

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

이 클래스는 Windows Vista 이상에서 지원 됩니다.

이 클래스에 대 한 추가 요구 사항은 [Windows Vista 공용 컨트롤의 빌드 요구](../../mfc/build-requirements-for-windows-vista-common-controls.md)사항에 설명 되어 있습니다.

## <a name="csplitbuttoncreate"></a><a name="create"></a> CSplitButton:: Create

지정 된 스타일을 사용 하 여 분할 단추 컨트롤을 만들고 현재 개체에 연결 `CSplitButton` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*\
진행 컨트롤에 적용할 스타일의 비트 조합 (또는)입니다. 자세한 내용은 [단추 스타일](../../mfc/reference/styles-used-by-mfc.md#button-styles)을 참조 하세요.

*직교*\
진행 컨트롤의 위치와 크기를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*\
진행 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 null이 아닌 포인터입니다.

*nID*\
진행 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a> CSplitButton:: CSplitButton

`CSplitButton` 개체를 생성합니다. 생성자의 매개 변수는 사용자가 분할 단추 컨트롤의 드롭다운 화살표를 클릭할 때 표시 되는 하위 메뉴를 지정 합니다.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>매개 변수

*nMenuId*\
진행 메뉴 모음의 리소스 ID입니다.

*nSubMenuId*\
진행 하위 메뉴의 리소스 ID입니다.

*pMenu*\
진행 하위 메뉴를 지정 하는 [CMenu](../../mfc/reference/cmenu-class.md) 개체에 대 한 포인터입니다. 개체는 개체가 `CSplitButton` `CMenu` 범위를 벗어나면 개체와 연결 된 HMENU를 삭제 합니다 `CSplitButton` .

### <a name="remarks"></a>설명

[CSplitButton:: Create](#create) 메서드를 사용 하 여 분할 단추 컨트롤을 만들고이를 개체에 연결 `CSplitButton` 합니다.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a> CSplitButton:: OnDropDown

사용자가 현재 분할 단추 컨트롤의 드롭다운 화살표를 클릭할 때 시스템이 보내는 BCN_DROPDOWN 알림을 처리 합니다.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>매개 변수

*pNMHDR*\
진행 [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) 알림에 대 한 정보를 포함 하는 [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) 구조체에 대 한 포인터입니다.

*pResult*\
제한이 사용 되지 않습니다. 값이 반환 되지 않습니다. [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) 알림의 반환 값입니다.

### <a name="remarks"></a>설명

사용자가 분할 단추 컨트롤에서 드롭다운 화살표를 클릭 하면 시스템에서 BCN_DROPDOWN 알림 메시지를 보냅니다 .이 메시지는 `OnDropDown` 메서드가 처리 합니다. 그러나 `CSplitButton` 개체가 분할 단추 컨트롤을 포함 하는 컨트롤로 BCN_DROPDOWN 알림을 전달 하지 않습니다. 따라서 포함 하는 컨트롤은 알림에 대 한 응답으로 사용자 지정 작업을 지원할 수 없습니다.

포함 하는 컨트롤에서 지 원하는 사용자 지정 작업을 구현 하려면 개체가 아닌 BS_SPLITBUTTON 스타일의 [Cbutton](../../mfc/reference/cbutton-class.md) 개체를 사용 `CSplitButton` 합니다. 그런 다음 개체의 BCN_DROPDOWN 알림에 대 한 처리기를 구현 `CButton` 합니다. 자세한 내용은 [단추 스타일](../../mfc/reference/styles-used-by-mfc.md#button-styles)을 참조 하세요.

분할 단추 컨트롤 자체에서 지 원하는 사용자 지정 작업을 구현 하려면 [메시지 리플렉션을](../../mfc/tn062-message-reflection-for-windows-controls.md)사용 합니다. 클래스에서 고유한 클래스를 파생 시키고 `CSplitButton` 이름을 CMySplitButton과 같이 지정 합니다. 그런 다음 응용 프로그램에 다음 메시지 맵을 추가 하 여 BCN_DROPDOWN 알림을 처리 합니다.

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a> CSplitButton:: SetDropDownMenu

사용자가 현재 분할 단추 컨트롤의 드롭다운 화살표를 클릭할 때 표시 되는 드롭다운 메뉴를 설정 합니다.

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>매개 변수

*nMenuId*\
진행 메뉴 모음의 리소스 ID입니다.

*nSubMenuId*\
진행 하위 메뉴의 리소스 ID입니다.

*pMenu*\
진행 하위 메뉴를 지정 하는 [CMenu](../../mfc/reference/cmenu-class.md) 개체에 대 한 포인터입니다. 개체는 개체가 `CSplitButton` `CMenu` 범위를 벗어나면 개체와 연결 된 HMENU를 삭제 합니다 `CSplitButton` .

### <a name="remarks"></a>설명

*NMenuId* 매개 변수는 메뉴 모음 항목의 가로 목록 인 메뉴 모음을 식별 합니다. *NSubMenuId* 매개 변수는 0부터 시작 하는 인덱스 번호입니다. 하위 메뉴는 각 메뉴 모음 항목과 연결 된 메뉴 항목의 드롭다운 목록입니다. 예를 들어 일반적인 응용 프로그램에는 메뉴 모음 항목 "File", "Edit" 및 "Help"를 포함 하는 메뉴가 있습니다. "파일" 메뉴 모음 항목에는 "열기", "닫기" 및 "종료" 메뉴 항목이 포함 된 하위 메뉴가 있습니다. 분할 단추 컨트롤의 드롭다운 화살표를 클릭 하면 컨트롤은 메뉴 모음이 아니라 지정 된 하위 메뉴를 표시 합니다.

다음 그림에서는 페이저 컨트롤과 (1) 분할 단추 컨트롤을 포함 하는 대화 상자를 보여 줍니다. (2) 드롭다운 화살표가 이미 클릭 되었으며 (3) 하위 메뉴가 표시 됩니다.

![splitbutton 및 pager 컨트롤이 있는 대화 상자](../../mfc/reference/media/splitbutton_pager.png "splitbutton 및 pager 컨트롤이 있는 대화 상자")

### <a name="example"></a>예제

다음 코드 예제의 첫 번째 문은 [CSplitButton:: SetDropDownMenu](#setdropdownmenu) 메서드를 보여 줍니다. 메뉴 모음 ID IDR_MENU1 자동으로 지정 되는 Visual Studio 리소스 편집기를 사용 하 여 메뉴를 만들었습니다. *NSubMenuId* 매개 변수 (0)는 메뉴 모음의 유일한 하위 메뉴를 참조 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>참고 항목

[CSplitButton 클래스](../../mfc/reference/csplitbutton-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CButton 클래스](../../mfc/reference/cbutton-class.md)
