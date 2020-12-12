---
description: '자세히 알아보기: CCmdUI 클래스'
title: CCmdUI 클래스
ms.date: 09/06/2019
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: d868c0dc3c9915f5300f56e5bfa5f1971d4ec3ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132992"
---
# <a name="ccmdui-class"></a>CCmdUI 클래스

는 `ON_UPDATE_COMMAND_UI` 파생 클래스의 처리기 내 에서만 사용 됩니다 `CCmdTarget` .

## <a name="syntax"></a>구문

```
class CCmdUI
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCmdUI:: ContinueRouting](#continuerouting)|현재 메시지를 처리기 체인으로 계속 라우팅하는 명령 라우팅 메커니즘에 지시 합니다.|
|[CCmdUI:: Enable](#enable)|이 명령에 대 한 사용자 인터페이스 항목을 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CCmdUI:: SetCheck](#setcheck)|이 명령에 대 한 사용자 인터페이스 항목의 확인 상태를 설정 합니다.|
|[CCmdUI:: SetRadio](#setradio)|`SetCheck`멤버 함수와 같지만 라디오 그룹에 대해 작동 합니다.|
|[CCmdUI:: SetText](#settext)|이 명령에 대 한 사용자 인터페이스 항목의 텍스트를 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CCmdUI:: m_nID](#m_nid)|사용자 인터페이스 개체의 ID입니다.|
|[CCmdUI:: m_nIndex](#m_nindex)|사용자 인터페이스 개체의 인덱스입니다.|
|[CCmdUI:: m_pMenu](#m_pmenu)|개체가 나타내는 메뉴를 가리킵니다 `CCmdUI` .|
|[CCmdUI:: m_pOther](#m_pother)|알림을 보낸 window 개체를 가리킵니다.|
|[CCmdUI:: m_pSubMenu](#m_psubmenu)|개체로 표시 되는 포함 된 하위 메뉴를 가리킵니다 `CCmdUI` .|

## <a name="remarks"></a>설명

`CCmdUI` 에 기본 클래스가 없습니다.

응용 프로그램의 사용자가 메뉴를 끌어올 때 각 메뉴 항목이 사용 또는 사용 안 함으로 표시 되어야 하는지 여부를 확인 해야 합니다. 메뉴 명령의 대상은 ON_UPDATE_COMMAND_UI 처리기를 구현 하 여이 정보를 제공 합니다. 응용 프로그램의 각 명령 사용자 인터페이스 개체에 대해 [클래스 마법사](mfc-class-wizard.md) 또는 **속성** 창 ( **클래스 뷰**)을 사용 하 여 각 처리기에 대 한 메시지 맵 항목 및 함수 프로토타입을 만듭니다.

메뉴를 끌어올 때 프레임 워크는 각 ON_UPDATE_COMMAND_UI 처리기를 검색 하 고 호출 합니다. 각 처리기는 `CCmdUI` 및와 같은 멤버 함수를 호출 `Enable` `Check` 하 고 프레임 워크는 각 메뉴 항목을 적절 하 게 표시 합니다.

메뉴 항목은 처리기 내에서 코드를 변경 하지 않고 컨트롤 막대 단추나 다른 명령 사용자 인터페이스 개체로 바꿀 수 있습니다 `ON_UPDATE_COMMAND_UI` .

다음 표에서는 `CCmdUI` 다양 한 명령 사용자 인터페이스 항목에 미치는 영향의 멤버 함수를 요약 하 여 보여 줍니다.

|User-Interface 항목|사용|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Menu item|사용 또는 사용 안 함|검사 또는 취소|점을 사용 하 여 확인|항목 텍스트를 설정 합니다.|
|도구 모음 단추|사용 또는 사용 안 함|선택, 선택 취소 또는 확정 되지 않음|`SetCheck`과 동일|(해당 없음)|
|상태 표시줄 창|텍스트를 표시 하거나 숨깁니다.|팝아웃 또는 표준 테두리를 설정 합니다.|`SetCheck`과 동일|창 텍스트를 설정 합니다.|
|표준 단추 `CDialogBar`|사용 또는 사용 안 함|검사 또는 선택 취소 확인란|`SetCheck`과 동일|단추 텍스트를 설정 합니다.|
|의 일반 컨트롤 `CDialogBar`|사용 또는 사용 안 함|(해당 없음)|(해당 없음)|창 텍스트를 설정 합니다.|

이 클래스를 사용 하는 방법에 대 한 자세한 내용은 [User-Interface 개체를 업데이트 하는 방법](../../mfc/how-to-update-user-interface-objects.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CCmdUI`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a> CCmdUI:: ContinueRouting

이 멤버 함수를 호출 하 여 명령 라우팅 메커니즘에 지시 하 여 현재 메시지를 처리기 체인으로 계속 라우팅합니다.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>설명

FALSE를 반환 하는 ON_COMMAND_EX 처리기와 함께 사용 해야 하는 고급 멤버 함수입니다. 자세한 내용은 [Technical Note 6](../../mfc/tn006-message-maps.md)을 참조 하세요.

## <a name="ccmduienable"></a><a name="enable"></a> CCmdUI:: Enable

이 명령에 대 한 사용자 인터페이스 항목을 사용 하거나 사용 하지 않도록 설정 하려면이 멤버 함수를 호출 합니다.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>매개 변수

*"Bon*<br/>
항목을 사용 하려면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a> CCmdUI:: m_nID

개체에서 나타내는 메뉴 항목, 도구 모음 단추 또는 기타 사용자 인터페이스 개체의 ID입니다 `CCmdUI` .

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a> CCmdUI:: m_nIndex

개체에서 나타내는 메뉴 항목, 도구 모음 단추 또는 기타 사용자 인터페이스 개체의 인덱스입니다 `CCmdUI` .

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a> CCmdUI:: m_pMenu

`CMenu`개체로 표시 되는 메뉴의 포인터 (형식)입니다 `CCmdUI` .

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>설명

항목이 메뉴가 아니면 NULL입니다.

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a> CCmdUI:: m_pSubMenu

`CMenu`개체로 표시 되는 포함 된 하위 메뉴에 대 한 포인터 (형식)입니다 `CCmdUI` .

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>설명

항목이 메뉴가 아니면 NULL입니다. 하위 메뉴가 팝업 인 경우 팝업 메뉴의 첫 번째 항목에 대 한 ID를 포함 *m_nID* 합니다. 자세한 내용은 [Technical Note 21](../../mfc/tn021-command-and-message-routing.md)을 참조 하세요.

## <a name="ccmduim_pother"></a><a name="m_pother"></a> CCmdUI:: m_pOther

`CWnd`알림을 보낸 도구 또는 상태 표시줄과 같은 창 개체에 대 한 포인터 (형식)입니다.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>설명

항목이 메뉴 또는 개체가 아닌 경우 NULL `CWnd` 입니다.

## <a name="ccmduisetcheck"></a><a name="setcheck"></a> CCmdUI:: SetCheck

이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 하려면이 멤버 함수를 호출 합니다.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>매개 변수

*nCheck*<br/>
설정할 확인 상태를 지정 합니다. 0 인 경우에는를 모두 취소 합니다. 1 인 경우를 확인 합니다. 2 인 경우 결정 되지 않은를 설정 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 메뉴 항목 및 도구 모음 단추에 대해 작동 합니다. 비활성화 된 상태는 도구 모음 단추에만 적용 됩니다.

## <a name="ccmduisetradio"></a><a name="setradio"></a> CCmdUI:: SetRadio

이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 하려면이 멤버 함수를 호출 합니다.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>매개 변수

*"Bon*<br/>
항목을 사용 하도록 설정 하려면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 멤버 함수 `SetCheck` 는 라디오 그룹의 일부로 작동 하는 사용자 인터페이스 항목에 대해 작동 한다는 점을 제외 하 고와 동일 하 게 작동 합니다. 항목 자체가 라디오 그룹 동작을 유지 해야 하는 경우가 아니면 그룹의 다른 항목을 선택을 취소 하는 것은 자동으로 진행 되지 않습니다.

## <a name="ccmduisettext"></a><a name="settext"></a> CCmdUI:: SetText

이 명령에 대 한 사용자 인터페이스 항목의 텍스트를 설정 하려면이 멤버 함수를 호출 합니다.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
텍스트 문자열에 대 한 포인터입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)
