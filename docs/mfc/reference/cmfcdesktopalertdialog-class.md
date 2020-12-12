---
description: '자세한 정보: CMFCDesktopAlertDialog 클래스'
title: CMFCDesktopAlertDialog 클래스
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
ms.openlocfilehash: 327ec72b1e58d90e768f51c083ff9545f24f6f0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193190"
---
# <a name="cmfcdesktopalertdialog-class"></a>CMFCDesktopAlertDialog 클래스

`CMFCDesktopAlertDialog`클래스는 [CMFCDesktopAlertWnd 클래스](../../mfc/reference/cmfcdesktopalertwnd-class.md) 와 함께 사용 되어 팝업 창에 사용자 지정 대화 상자를 표시 합니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCDesktopAlertDialog : public CDialogEx
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCDesktopAlertDialog::CreateFromParams](#createfromparams)||
|[CMFCDesktopAlertDialog::GetDlgSize](#getdlgsize)||
|[CMFCDesktopAlertDialog::HasFocus](#hasfocus)||
|[CMFCDesktopAlertDialog::PreTranslateMessage](#pretranslatemessage)|( `CDialogEx::PreTranslateMessage`을 재정의합니다.)|

### <a name="remarks"></a>설명

다음 단계를 수행하여 팝업 창에 사용자 지정 대화 상자를 표시합니다.

1. `CMFCDesktopAlertDialog`에서 클래스를 파생합니다.

1. 프로젝트 리소스에서 자식 대화 상자 템플릿을 만듭니다.

1. 대화 상자 템플릿의 리소스 ID와 파생 클래스의 런타임 클래스 정보에 대 한 포인터를 매개 변수로 사용 하 여 [CMFCDesktopAlertWnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) 를 호출 합니다.

1. 호스트된 컨트롤에서 생성되는 모든 알림을 처리하는 사용자 지정 대화 상자를 프로그래밍하거나 이러한 알림을 직접 처리하는 호스트된 컨트롤을 프로그래밍합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDesktopAlertDialog

## <a name="cmfcdesktopalertdialogcreatefromparams"></a><a name="createfromparams"></a> CMFCDesktopAlertDialog:: CreateFromParams

```
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,
    CMFCDesktopAlertWnd* pParent);
```

### <a name="parameters"></a>매개 변수

진행 *params*<br/>

진행 *Pparent*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertdialoggetdlgsize"></a><a name="getdlgsize"></a> CMFCDesktopAlertDialog:: GetDlgSize

```
CSize GetDlgSize();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertdialoghasfocus"></a><a name="hasfocus"></a> CMFCDesktopAlertDialog:: HasFocus

```
BOOL HasFocus() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertdialogpretranslatemessage"></a><a name="pretranslatemessage"></a> CMFCDesktopAlertDialog::P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

[in] *pMsg*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd 클래스](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWndInfo 클래스](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CDialogEx 클래스](../../mfc/reference/cdialogex-class.md)
