---
description: '자세히 알아보기: CLinkCtrl 클래스'
title: CLinkCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: a9a106d7511757fac0abfd19194081729a7d4977
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236760"
---
# <a name="clinkctrl-class"></a>CLinkCtrl 클래스

Windows의 공용 SysLink 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CLinkCtrl:: CLinkCtrl](#clinkctrl)|`CLinkCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CLinkCtrl:: Create](#create)|링크 컨트롤을 만들고이를 개체에 연결 `CLinkCtrl` 합니다.|
|[CLinkCtrl:: CreateEx](#createex)|확장 스타일을 사용 하 여 링크 컨트롤을 만들고이를 `CLinkCtrl` 개체에 연결 합니다.|
|[CLinkCtrl:: GetIdealHeight](#getidealheight)|링크 컨트롤의 이상적인 높이를 검색 합니다.|
|[CLinkCtrl:: GetIdealSize](#getidealsize)|링크의 지정 된 너비에 따라 현재 링크 컨트롤에 대 한 링크 텍스트의 기본 설정 높이를 계산 합니다.|
|[CLinkCtrl:: GetItem](#getitem)|링크 컨트롤 항목의 상태 및 특성을 검색 합니다.|
|[CLinkCtrl:: GetItemID](#getitemid)|링크 컨트롤 항목의 ID를 검색 합니다.|
|[CLinkCtrl:: GetItemState](#getitemstate)|링크 컨트롤 항목의 상태를 검색 합니다.|
|[CLinkCtrl:: GetItemUrl](#getitemurl)|링크 컨트롤 항목이 나타내는 URL을 검색 합니다.|
|[CLinkCtrl:: System.windows.media.visualtreehelper.hittest](#hittest)|사용자가 지정 된 링크를 클릭 했는지 여부를 확인 합니다.|
|[CLinkCtrl:: SetItem](#setitem)|링크 컨트롤 항목의 상태 및 특성을 설정 합니다.|
|[CLinkCtrl:: SetItemID](#setitemid)|링크 컨트롤 항목의 ID를 설정 합니다.|
|[CLinkCtrl:: SetItemState](#setitemstate)|링크 컨트롤 항목의 상태를 설정 합니다.|
|[CLinkCtrl:: SetItemUrl](#setitemurl)|링크 컨트롤 항목으로 표시 되는 URL을 설정 합니다.|

## <a name="remarks"></a>설명

"링크 컨트롤"은 하이퍼텍스트 링크를 창에 포함 하는 편리한 방법을 제공 합니다. 실제 컨트롤은 표시 된 텍스트를 렌더링 하 고 사용자가 포함 된 링크를 클릭할 때 적절 한 응용 프로그램을 시작 하는 창입니다. 한 컨트롤 내에서 여러 링크가 지원 되며 0부터 시작 하는 인덱스를 사용 하 여 액세스할 수 있습니다.

이 컨트롤과 `CLinkCtrl` 클래스는 WINDOWS XP 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

자세한 내용은 Windows SDK의 [Syslink 컨트롤](/windows/win32/Controls/syslink-overview) 을 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a> CLinkCtrl:: CLinkCtrl

`CLinkCtrl` 개체를 생성합니다.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a> CLinkCtrl:: Create

링크 컨트롤을 만들고이를 개체에 연결 `CLinkCtrl` 합니다.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*lpszLinkMarkup*<br/>
표시할 표시 된 텍스트가 들어 있는 0으로 끝나는 문자열에 대 한 포인터입니다. 자세한 내용은 [Syslink 컨트롤 개요](/windows/win32/Controls/syslink-overview)항목의 "태그 및 링크 액세스" 섹션을 참조 하세요.

*dwStyle*<br/>
링크 컨트롤의 스타일을 지정 합니다. 컨트롤 스타일의 조합을 적용 합니다. 자세한 내용은의 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 을 참조 하십시오 `Windows SDK` .

*rect*<br/>
링크 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
링크 컨트롤의 부모 창을 지정 합니다. NULL이 아니어야 합니다.

*nID*<br/>
링크 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`CLinkCtrl`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` 링크 컨트롤을 만들고이를 개체에 연결 `CLinkCtrl` 합니다. 컨트롤과 함께 확장 된 windows 스타일을 사용 하려는 경우 대신 [Clinkctrl:: CreateEx](#createex) 를 호출 `Create` 합니다.

메서드의 두 번째 형태는 `Create` 사용 되지 않습니다. *LpszLinkMarkup* 매개 변수를 지정 하는 첫 번째 폼을 사용 합니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_Link1` `m_Link2` 두 개의 링크 컨트롤에 액세스 하는 데 사용 되는 및 라는 두 개의 변수를 정의 합니다.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 다른 링크 컨트롤의 위치를 기반으로 한 링크 컨트롤을 만듭니다. 리소스 로더는 응용 프로그램이 시작 될 때 첫 번째 링크 컨트롤을 만듭니다. 응용 프로그램이 OnInitDialog 메서드를 입력 하면 첫 번째 링크 컨트롤의 위치를 기준으로 두 번째 링크 컨트롤을 만듭니다. 그런 다음 표시 되는 텍스트에 맞게 두 번째 링크 컨트롤의 크기를 조정 합니다.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a> CLinkCtrl:: CreateEx

확장 스타일을 사용 하 여 링크 컨트롤을 만들고이를 `CLinkCtrl` 개체에 연결 합니다.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>매개 변수

*lpszLinkMarkup*<br/>
표시할 표시 된 텍스트가 들어 있는 0으로 끝나는 문자열에 대 한 포인터입니다. 자세한 내용은 [Syslink 컨트롤 개요](/windows/win32/Controls/syslink-overview)항목의 "태그 및 링크 액세스" 섹션을 참조 하세요.

*dwExStyle*<br/>
링크 컨트롤의 확장 스타일을 지정 합니다. 확장 된 Windows 스타일의 목록에 대해서는 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 에 대 한 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*<br/>
링크 컨트롤의 스타일을 지정 합니다. 컨트롤 스타일의 조합을 적용 합니다. 자세한 내용은 Windows SDK의 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 을 참조 하세요.

*rect*<br/>
링크 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
링크 컨트롤의 부모 창을 지정 합니다. NULL이 아니어야 합니다.

*nID*<br/>
링크 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`CreateEx`대신 [Create](#create) 를 사용 하 여 확장 된 Windows 스타일 상수를 적용 합니다.

메서드의 두 번째 형태는 `CreateEx` 사용 되지 않습니다. *LpszLinkMarkup* 매개 변수를 지정 하는 첫 번째 폼을 사용 합니다.

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a> CLinkCtrl:: GetIdealHeight

링크 컨트롤의 이상적인 높이를 검색 합니다.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>반환 값

컨트롤의 이상적인 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)의 동작을 구현 합니다.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a> CLinkCtrl:: GetIdealSize

링크의 지정 된 너비에 따라 현재 링크 컨트롤에 대 한 링크 텍스트의 기본 설정 높이를 계산 합니다.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>매개 변수

*cxMaxWidth*\
진행 링크의 최대 너비 (픽셀)입니다.

*pSize*\
제한이 Windows [크기](/windows/win32/api/windef/ns-windef-size) 구조체에 대 한 포인터입니다. 이 메서드가 반환 될 때 구조체의 *cy* 멤버는 `SIZE` *cxmaxwidth* 로 지정 된 링크 텍스트 너비에 이상적인 링크 텍스트 높이를 포함 합니다. 구조체의 *cx* 멤버는 실제로 필요한 링크 텍스트 너비를 포함 합니다.

### <a name="return-value"></a>반환 값

링크 텍스트의 기본 설정 높이 (픽셀)입니다. 반환 값은 구조체의 *cy* 멤버 값과 동일 합니다 `SIZE` .

### <a name="remarks"></a>설명

이 메서드에 대 한 예제 `GetIdealSize` 는 [Clinkctrl:: Create](#create)의 예제를 참조 하세요.

이 메서드는 Windows SDK에서 설명 하는 [LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize) 메시지를 보냅니다.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a> CLinkCtrl:: GetItem

링크 컨트롤 항목의 상태 및 특성을 검색 합니다.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
항목 정보를 받을 [litem](/windows/win32/api/commctrl/ns-commctrl-litem) 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [LM_GETITEM](/windows/win32/Controls/lm-getitem)의 동작을 구현 합니다.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a> CLinkCtrl:: GetItemID

링크 컨트롤 항목의 ID를 검색 합니다.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>매개 변수

*iLink*<br/>
링크 컨트롤 항목의 인덱스입니다.

*대해*<br/>
지정 된 항목의 ID를 포함 하는 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

*szID*<br/>
지정 된 항목의 ID를 포함 하는 null로 끝나는 문자열입니다.

*cchID*<br/>
*Szid* 버퍼의 문자 크기입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

> [!NOTE]
> 이 함수는 *Szid 또는 대해* 의 버퍼가 MAX_LINKID_TEXT 보다 작은 경우에도 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

특정 링크 컨트롤 항목의 ID를 검색 합니다. 자세한 내용은 Windows SDK에서 Win32 메시지 [LM_GETITEM](/windows/win32/Controls/lm-getitem) 를 참조 하세요.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a> CLinkCtrl:: GetItemState

링크 컨트롤 항목의 상태를 검색 합니다.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>매개 변수

*iLink*<br/>
링크 컨트롤 항목의 인덱스입니다.

*pnState*<br/>
지정 된 상태 항목의 값입니다.

*stateMask*<br/>
가져올 상태 항목을 설명 하는 플래그의 조합입니다. 값 목록은 `state` [litem](/windows/win32/api/commctrl/ns-commctrl-litem) 구조에서 멤버에 대 한 설명을 참조 하세요. 허용 되는 항목은에서 허용 하는 항목과 동일 `state` 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

특정 링크 컨트롤 항목의 지정 된 상태 항목 값을 검색 합니다. 자세한 내용은 Windows SDK에서 Win32 메시지 [LM_GETITEM](/windows/win32/Controls/lm-getitem) 를 참조 하세요.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a> CLinkCtrl:: GetItemUrl

링크 컨트롤 항목이 나타내는 URL을 검색 합니다.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>매개 변수

*iLink*<br/>
링크 컨트롤 항목의 인덱스입니다.

*strUrl*<br/>
지정 된 항목으로 표시 되는 URL을 포함 하는 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

*szUrl*<br/>
지정 된 항목으로 표시 되는 URL을 포함 하는 null로 끝나는 문자열입니다.

*cchUrl*<br/>
*Szurl* 버퍼의 문자 크기입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

> [!NOTE]
> 이 함수는 *Szurl 또는 strUrl* 의 버퍼가 MAX_LINKID_TEXT 보다 작은 경우에도 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

지정 된 링크 컨트롤 항목이 나타내는 URL을 검색 합니다. 자세한 내용은 Windows SDK에서 Win32 메시지 [LM_GETITEM](/windows/win32/Controls/lm-getitem) 를 참조 하세요.

## <a name="clinkctrlhittest"></a><a name="hittest"></a> CLinkCtrl:: System.windows.media.visualtreehelper.hittest

사용자가 지정 된 링크를 클릭 했는지 여부를 확인 합니다.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>매개 변수

*phti*<br/>
`LHITTESTINFO`사용자가 클릭 한 링크에 대 한 정보를 포함 하는 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [LM_HITTEST](/windows/win32/Controls/lm-hittest)의 동작을 구현 합니다.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a> CLinkCtrl:: SetItem

링크 컨트롤 항목의 상태 및 특성을 설정 합니다.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
설정할 정보를 포함 하는 [Litem](/windows/win32/api/commctrl/ns-commctrl-litem) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [LM_SETITEM](/windows/win32/Controls/lm-setitem)의 동작을 구현 합니다.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a> CLinkCtrl:: SetItemID

링크 컨트롤 항목의 ID를 검색 합니다.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>매개 변수

*iLink*<br/>
링크 컨트롤 항목의 인덱스입니다.

*szID*<br/>
지정 된 항목의 ID를 포함 하는 null로 끝나는 문자열입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

특정 링크 컨트롤 항목의 ID를 설정 합니다. 자세한 내용은 Windows SDK에서 Win32 메시지 [LM_SETITEM](/windows/win32/Controls/lm-setitem) 를 참조 하세요.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a> CLinkCtrl:: SetItemState

링크 컨트롤 항목의 상태를 검색 합니다.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>매개 변수

*iLink*<br/>
링크 컨트롤 항목의 인덱스입니다.

*pnState*<br/>
설정 되는 지정 된 상태 항목의 값입니다.

*stateMask*<br/>
설정 되는 상태 항목을 설명 하는 플래그의 조합입니다. 값 목록은 `state` [litem](/windows/win32/api/commctrl/ns-commctrl-litem) 구조에서 멤버에 대 한 설명을 참조 하세요. 허용 되는 항목은에서 허용 하는 항목과 동일 `state` 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

특정 링크 컨트롤 항목의 지정 된 상태 항목 값을 설정 합니다. 자세한 내용은 Windows SDK에서 Win32 메시지 [LM_SETITEM](/windows/win32/Controls/lm-setitem) 를 참조 하세요.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a> CLinkCtrl:: SetItemUrl

링크 컨트롤 항목으로 표시 되는 URL을 설정 합니다.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>매개 변수

*iLink*<br/>
링크 컨트롤 항목의 인덱스입니다.

*szUrl*<br/>
지정 된 항목으로 표시 되는 URL을 포함 하는 null로 끝나는 문자열입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

지정 된 링크 컨트롤 항목으로 표시 되는 URL을 설정 합니다. 자세한 내용은 Windows SDK에서 Win32 메시지 [LM_SETITEM](/windows/win32/Controls/lm-setitem) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)
