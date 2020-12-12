---
description: '자세한 정보: CDialogEx 클래스'
title: CDialogEx 클래스
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: 27ec0011935871d472734cae6f0d62b402382727
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185247"
---
# <a name="cdialogex-class"></a>CDialogEx 클래스

`CDialogEx` 클래스는 대화 상자의 배경 색과 배경 이미지를 지정합니다.

## <a name="syntax"></a>구문

```
class CDialogEx : public CDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|`CDialogEx` 개체를 생성합니다.|
|`CDialogEx::~CDialogEx`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|대화 상자의 배경 색을 설정합니다.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|대화 상자의 배경 이미지를 설정합니다.|

## <a name="remarks"></a>설명

`CDialogEx` 클래스를 사용하려면 `CDialogEx` 클래스 대신 `CDialog` 클래스에서 대화 상자 클래스를 파생합니다.

대화 상자 이미지는 리소스 파일에 저장됩니다. 프레임워크는 리소스 파일에서 로드되는 모든 이미지를 자동으로 삭제합니다. 현재 배경 이미지를 프로그래밍 방식으로 삭제 하려면 [Cdialogex:: SetBackgroundImage](#setbackgroundimage) 메서드를 호출 하거나 `OnDestroy` 이벤트 처리기를 구현 합니다. [Cdialogex:: SetBackgroundImage](#setbackgroundimage) 메서드를 호출 하는 경우 `HBITMAP` 매개 변수를 이미지 핸들로 전달 합니다. `CDialogEx` 개체가 이미지의 소유권을 갖게 되며 `m_bAutoDestroyBmp` 플래그가 `TRUE`이면 삭제합니다.

`CDialogEx`개체는 [CMFCPopupMenu 클래스](../../mfc/reference/cmfcpopupmenu-class.md) 개체의 부모가 될 수 있습니다. [CMFCPopupMenu 클래스](../../mfc/reference/cmfcpopupmenu-class.md) 개체는 `CDialogEx::SetActiveMenu` [CMFCPopupMenu class](../../mfc/reference/cmfcpopupmenu-class.md) 개체가 열릴 때 메서드를 호출 합니다. 그런 다음 `CDialogEx` [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 개체가 닫힐 때까지 개체는 모든 메뉴 이벤트를 처리 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxdialogex

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a> CDialogEx:: CDialogEx

`CDialogEx` 개체를 생성합니다.

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>매개 변수

*nIDTemplate*<br/>
진행 대화 상자 템플릿의 리소스 ID입니다.

*lpszTemplateName*<br/>
진행 대화 상자 템플릿의 리소스 이름입니다.

*pParent*<br/>
진행 부모 창에 대 한 포인터입니다. 기본값은 NULL입니다.

*pParentWnd*<br/>
진행 부모 창에 대 한 포인터입니다. 기본값은 NULL입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a> CDialogEx:: SetBackgroundColor

대화 상자의 배경 색을 설정합니다.

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 RGB 색 값입니다.

*bRepaint*<br/>
진행 화면을 즉시 업데이트 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a> CDialogEx:: SetBackgroundImage

대화 상자의 배경 이미지를 설정합니다.

```cpp
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>매개 변수

*hBitmap*<br/>
진행 배경 이미지에 대 한 핸들입니다.

*uiBmpResId*<br/>
진행 배경 이미지의 리소스 ID입니다.

*location*<br/>
진행 `CDialogEx::BackgroundLocation` 이미지의 위치를 지정 하는 값 중 하나입니다. 유효한 값은 BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT 및 BACKGR_BOTTOMRIGHT입니다. 기본값은 BACKGR_TILE입니다.

*bAutoDestroy*<br/>
진행 배경 이미지를 자동으로 삭제 하려면 TRUE이 고, 그렇지 않으면 FALSE입니다.

*bRepaint*<br/>
진행 대화 상자를 즉시 다시 그리려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

두 번째 메서드 오버 로드 구문에서 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

지정 하는 이미지는 대화 상자 클라이언트 영역에 맞게 확장 되지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 클래스](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager 클래스](../../mfc/reference/ccontextmenumanager-class.md)
