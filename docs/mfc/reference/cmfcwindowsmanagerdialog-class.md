---
description: '자세한 정보: CMFCWindowsManagerDialog 클래스'
title: CMFCWindowsManagerDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 526cf731e049ffd267382b0c3895b5d29792dcb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331623"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 클래스

`CMFCWindowsManagerDialog`사용자는 개체를 사용 하 여 mdi 응용 프로그램에서 mdi 자식 창을 관리할 수 있습니다.

## <a name="syntax"></a>구문

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCWindowsManagerDialog:: CMFCWindowsManagerDialog 대화 상자](#cmfcwindowsmanagerdialog)|`CMFCWindowsManagerDialog` 개체를 생성합니다.|

## <a name="remarks"></a>설명

에는 `CMFCWindowsManagerDialog` 현재 응용 프로그램에 열려 있는 MDI 자식 창의 목록이 포함 되어 있습니다. 사용자는이 대화 상자를 사용 하 여 MDI 자식 창의 상태를 수동으로 제어할 수 있습니다.

`CMFCWindowsManagerDialog` 은 [CMDIFrameWndEx 클래스](../../mfc/reference/cmdiframewndex-class.md)안에 포함 됩니다. 는 `CMFCWindowsManagerDialog` 수동으로 만들어야 하는 클래스가 아닙니다. 대신 [CMDIFrameWndEx:: ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)함수를 호출 하면 개체가 생성 되 고 표시 됩니다 `CMFCWindowsManagerDialog` .

## <a name="example"></a>예제

다음 예제에서는를 호출 하 여 개체를 생성 하는 방법을 보여 줍니다 `CMFCWindowsManagerDialog` `CMDIFrameWndEx::ShowWindowsDialog` . 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxWindowsManagerDialog

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a> CMFCWindowsManagerDialog:: CMFCWindowsManagerDialog 대화 상자

[Cmfcwindowsmanagerdialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 개체를 생성 합니다.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>매개 변수

*pMDIFrame*<br/>
진행 부모 또는 소유자 창에 대 한 포인터입니다.

*bHelpButton*<br/>
진행 프레임 워크에서 **도움말** 단추를 표시할지 여부를 지정 하는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

시각적 관리자에 대 한 자세한 내용은 [시각화 관리자](../../mfc/visualization-manager.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx 클래스](../../mfc/reference/cmdiframewndex-class.md)
