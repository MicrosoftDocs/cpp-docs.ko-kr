---
description: '다음에 대 한 자세한 정보: COccManager 클래스'
title: COccManager 클래스
ms.date: 11/04/2016
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
ms.openlocfilehash: 8acd39825f7f842a266a4b1dbf187ba4f7f9b5ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331425"
---
# <a name="coccmanager-class"></a>COccManager 클래스

`COleControlContainer` 및 `COleControlSite` 개체로 구현된 다양한 사용자 지정 컨트롤 사이트를 관리합니다.

## <a name="syntax"></a>구문

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COccManager:: CreateContainer](#createcontainer)|`COleContainer` 개체를 만듭니다.|
|[COccManager:: CreateDlgControls](#createdlgcontrols)|연결 된 개체에 의해 호스팅되는 ActiveX 컨트롤을 만듭니다 `COleContainer` .|
|[COccManager:: CreateSite](#createsite)|`COleClientSite` 개체를 만듭니다.|
|[COccManager:: GetDefBtnCode](#getdefbtncode)|기본 단추의 코드를 검색 합니다.|
|[COccManager:: IsDialogMessage](#isdialogmessage)|대화 메시지의 대상을 결정 합니다.|
|[COccManager:: IsLabelControl](#islabelcontrol)|지정 된 컨트롤이 레이블 컨트롤 인지 여부를 확인 합니다.|
|[COccManager:: IsMatchingMnemonic](#ismatchingmnemonic)|현재 니모닉이 지정 된 컨트롤의 니모닉과 일치 하는지 여부를 확인 합니다.|
|[COccManager:: OnEvent](#onevent)|지정 된 이벤트를 처리 하려고 시도 합니다.|
|[COccManager::P ostCreateDialog](#postcreatedialog)|대화 상자를 만드는 동안 할당 된 리소스를 해제 합니다.|
|[COccManager::P reCreateDialog](#precreatedialog)|ActiveX 컨트롤에 대 한 대화 상자 템플릿을 처리 합니다.|
|[COccManager:: SetDefaultButton](#setdefaultbutton)|지정 된 컨트롤의 기본 상태를 설정/해제 합니다.|
|[COccManager:: SplitDialogTemplate](#splitdialogtemplate)|지정 된 대화 상자 템플릿에서 기존 ActiveX 컨트롤을 공통 컨트롤에서 분리 합니다.|

## <a name="remarks"></a>설명

기본 클래스는 `CNoTrackObject` AFXTLS에 있는 문서화 되지 않은 기본 클래스입니다. H). MFC 프레임 워크에서 사용 하도록 디자인 된 클래스에서 파생 된 클래스 `CNoTrackObject` 는 메모리 누수 검색에서 제외 됩니다. 에서 직접 파생 하지 않는 것이 좋습니다 `CNoTrackObject` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>요구 사항

**헤더:** afxocc

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a> COccManager:: CreateContainer

컨트롤 컨테이너를 만들기 위해 프레임 워크에서 호출 됩니다.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
사용자 지정 사이트 컨테이너와 연결 된 창 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

새로 만든 컨테이너에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

사용자 지정 사이트를 만드는 방법에 대 한 자세한 내용은 [COleControlContainer:: AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)를 참조 하세요.

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a> COccManager:: CreateDlgControls

*Poccdialoginfo* 매개 변수로 지정 된 ActiveX 컨트롤을 만들려면이 함수를 호출 합니다.

```
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    LPCTSTR lpszResourceName,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    void* lpResource,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
대화 상자 개체의 부모에 대 한 포인터입니다.

*lpszResourceName*<br/>
만들려는 리소스의 이름입니다.

*pOccDialogInfo*<br/>
Dialog 개체를 만드는 데 사용 되는 대화 상자 템플릿에 대 한 포인터입니다.

*L보도 Ource*<br/>
리소스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

컨트롤을 성공적으로 만들었으면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a> COccManager:: CreateSite

*PCtrlCont* 가 가리키는 컨테이너에 의해 호스팅되는 컨트롤 사이트를 만들기 위해 프레임 워크에서 호출 됩니다.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>매개 변수

*pCtrlCont*<br/>
새 컨트롤 사이트를 호스팅하는 컨트롤 컨테이너에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

새로 만든 컨트롤 사이트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

[COleControlSite](../../mfc/reference/colecontrolsite-class.md)파생 클래스를 사용 하 여 사용자 지정 컨트롤 사이트를 만들려면이 함수를 재정의 합니다.

각 컨트롤 컨테이너는 여러 사이트를 호스팅할 수 있습니다. 를 여러 번 호출 하 여 추가 사이트를 만듭니다 `CreateSite` .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a> COccManager:: GetDefBtnCode

컨트롤이 기본 푸시 단추 인지 여부를 확인 하려면이 함수를 호출 합니다.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
Button 컨트롤을 포함 하는 window 개체입니다.

### <a name="return-value"></a>반환 값

다음 값 중 하나입니다.

- DLGC_DEFPUSHBUTTON 컨트롤은 대화 상자의 기본 단추입니다.

- DLGC_UNDEFPUSHBUTTON 컨트롤이 대화 상자의 기본 단추가 아닙니다.

- **0** 컨트롤은 단추가 아닙니다.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a> COccManager:: IsDialogMessage

지정 된 대화 상자에 대해 메시지를 사용 하는지 여부를 확인 하기 위해 프레임 워크에서 호출 되 고, 메시지를 처리 하는 경우에는 메시지를 처리 합니다.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>매개 변수

*pWndDlg*<br/>
메시지의 의도 한 대상 대화 상자에 대 한 포인터입니다.

*lpMsg*<br/>
`MSG`확인할 메시지를 포함 하는 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메시지가 처리 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

의 기본 동작은 `IsDialogMessage` 키보드 메시지를 확인 하 고 해당 대화 상자에 대 한 선택 항목으로 변환 하는 것입니다. 예를 들어 TAB 키를 누르면 다음 컨트롤이 나 컨트롤 그룹이 선택 됩니다.

지정 된 대화 상자로 보낸 메시지에 대 한 사용자 지정 동작을 제공 하려면이 함수를 재정의 합니다.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a> COccManager:: IsLabelControl

지정 된 컨트롤이 레이블 컨트롤 인지 여부를 확인 하려면이 함수를 호출 합니다.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
컨트롤을 포함 하는 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

컨트롤이 레이블 이면 0이 아닌 값입니다. 그렇지 않으면 0

### <a name="remarks"></a>설명

레이블 컨트롤은 순서에서 옆에 있는 모든 컨트롤에 대 한 레이블 처럼 동작 합니다.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a> COccManager:: IsMatchingMnemonic

이 함수를 호출 하 여 현재 니모닉이 컨트롤이 나타내는 것과 일치 하는지 확인 합니다.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
컨트롤을 포함 하는 창에 대 한 포인터입니다.

*lpMsg*<br/>
일치 시킬 니모닉이 포함 된 메시지에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

니모닉이 컨트롤과 일치 하면 0이 아닌 값입니다. 그렇지 않으면 0

### <a name="remarks"></a>설명

## <a name="coccmanageronevent"></a><a name="onevent"></a> COccManager:: OnEvent

지정 된 이벤트를 처리 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>매개 변수

*pCmdTarget*<br/>
이벤트를 처리 하려고 하는 개체에 대 한 포인터입니다. `CCmdTarget`

*idCtrl*<br/>
컨트롤의 리소스 ID입니다.

*pEvent*<br/>
처리 되는 이벤트입니다.

*pHandlerInfo*<br/>
NULL이 아닌 경우 `OnEvent` 는 `pTarget` `pmf` 명령을 발송 하는 대신 및 구조체의 멤버를 채웁니다 `AFX_CMDHANDLERINFO` . 일반적으로이 매개 변수는 NULL 이어야 합니다.

### <a name="return-value"></a>반환 값

이벤트가 처리 된 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 이벤트 처리 프로세스를 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a> COccManager::P reCreateDialog

실제 대화 상자를 만들기 전에 ActiveX 컨트롤에 대 한 대화 상자 템플릿을 처리 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>매개 변수

*pOccDialogInfo*<br/>
대화 `_AFX_OCC_DIALOG_INFO` 상자 템플릿과 대화 상자에서 호스팅하는 ActiveX 컨트롤에 대 한 정보를 포함 하는 구조체입니다.

*폰 템플릿*<br/>
대화 상자를 만드는 데 사용할 대화 상자 템플릿에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대화 상자를 만드는 데 사용 되는 대화 상자 템플릿 구조에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 동작은에 대 한 호출을 수행 하 여 `SplitDialogTemplate` ActiveX 컨트롤이 있는지 확인 한 다음 결과 대화 상자 템플릿을 반환 합니다.

ActiveX 컨트롤을 호스팅하는 대화 상자를 만드는 프로세스를 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a> COccManager::P ostCreateDialog

대화 상자 템플릿에 할당 된 메모리를 해제 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>매개 변수

*pOccDialogInfo*<br/>
대화 `_AFX_OCC_DIALOG_INFO` 상자 템플릿과 대화 상자에서 호스팅하는 ActiveX 컨트롤에 대 한 정보를 포함 하는 구조체입니다.

### <a name="remarks"></a>설명

이 메모리는에 대 한 호출로 할당 되었으며 `SplitDialogTemplate` 대화 상자의 호스팅된 ActiveX 컨트롤에 사용 되었습니다.

이 함수를 재정의 하 여 대화 상자 개체에서 사용 하는 리소스를 정리 하는 프로세스를 사용자 지정 합니다.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a> COccManager:: SetDefaultButton

컨트롤을 기본 단추로 설정 하려면이 함수를 호출 합니다.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
컨트롤을 포함 하는 창에 대 한 포인터입니다.

*bDefault*<br/>
컨트롤이 기본 단추가 되도록 하려면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤에 OLEMISC_ACTSLIKEBUTTON 상태 비트가 설정 되어 있어야 합니다. OLEMISC 플래그에 대 한 자세한 내용은 Windows SDK의 [olemisc](/windows/win32/api/oleidl/ne-oleidl-olemisc) 항목을 참조 하십시오.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a> COccManager:: SplitDialogTemplate

공용 대화 상자 컨트롤에서 ActiveX 컨트롤을 분할 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>매개 변수

*pTemplate*<br/>
검사할 대화 상자 템플릿에 대 한 포인터입니다.

*Pcgedlgitems*<br/>
ActiveX 컨트롤의 대화 상자 항목에 대 한 포인터 목록입니다.

### <a name="return-value"></a>반환 값

비 ActiveX 컨트롤만 포함 하는 대화 상자 템플릿 구조에 대 한 포인터입니다. ActiveX 컨트롤이 없는 경우 NULL이 반환 됩니다.

### <a name="remarks"></a>설명

ActiveX 컨트롤을 찾은 경우 템플릿이 분석 되 고 ActiveX 컨트롤이 아닌 새 템플릿도 만들어집니다. 이 프로세스 중 발견 된 모든 ActiveX 컨트롤은 *Ppoledlgitems* 에 추가 됩니다.

템플릿에 ActiveX 컨트롤이 없으면 NULL이 반환 됩니다 *.*

> [!NOTE]
> 새 템플릿에 할당 된 메모리는 함수에서 해제 됩니다 `PostCreateDialog` .

이 프로세스를 사용자 지정 하려면이 함수를 재정의 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 클래스](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer 클래스](../../mfc/reference/colecontrolcontainer-class.md)
