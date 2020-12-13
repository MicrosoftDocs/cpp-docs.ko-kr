---
description: '자세한 정보: CAxDialogImpl 클래스'
title: CAxDialogImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: e84ce636642ed268ec8ca0dd25e0f3c5f3bc10c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152453"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl 클래스

이 클래스는 ActiveX 컨트롤을 호스트 하는 대화 상자 (모달 또는 모덜리스)를 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CAxDialogImpl` 입니다.

*TBase*<br/>
에 대 한 기본 창 클래스 `CDialogImplBaseT` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAxDialogImpl:: AdviseSinkMap](#advisesinkmap)|개체의 싱크 맵 이벤트 맵에 모든 항목을 advise 하거나 unadvise 하려면이 메서드를 호출 합니다.|
|[CAxDialogImpl:: Create](#create)|모덜리스 대화 상자를 만들려면이 메서드를 호출 합니다.|
|[CAxDialogImpl::D estroyWindow](#destroywindow)|모덜리스 대화 상자를 삭제 하려면이 메서드를 호출 합니다.|
|[CAxDialogImpl::D oModal](#domodal)|이 메서드를 호출 하 여 모달 대화 상자를 만듭니다.|
|[CAxDialogImpl:: EndDialog](#enddialog)|모달 대화 상자를 삭제 하려면이 메서드를 호출 합니다.|
|[CAxDialogImpl:: GetDialogProc](#getdialogproc)|콜백 함수에 대 한 포인터를 가져오려면이 메서드를 호출 `DialogProc` 합니다.|
|[CAxDialogImpl:: GetIDD](#getidd)|대화 상자 템플릿 리소스 ID를 가져오려면이 메서드를 호출 합니다.|
|[CAxDialogImpl:: IsDialogMessage](#isdialogmessage)|메시지를이 대화 상자에 사용할지 여부를 확인 하려면이 메서드를 호출 하 고 메시지를 처리 하려면 메시지를 처리 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAxDialogImpl:: m_bModal](#m_bmodal)|디버그 빌드에서만 존재 하 고 대화 상자가 모달 인 경우 true로 설정 된 변수입니다.|

## <a name="remarks"></a>설명

`CAxDialogImpl` 모달 또는 모덜리스 대화 상자를 만들 수 있습니다. `CAxDialogImpl` 기본 메시지 맵을 사용 하 여 메시지를 적절 한 처리기에 전달 하는 대화 상자 프로시저를 제공 합니다.

`CAxDialogImpl` 는에서 파생 되며 `CDialogImplBaseT` ,이는 기본적으로 및 *의 기본* 에서 파생 `CWindow` `CMessageMap` 됩니다.

클래스는 대화 상자 템플릿 리소스 ID를 지정 하는 IDD 멤버를 정의 해야 합니다. 예를 들어 **클래스 추가** 대화 상자를 사용 하 여 ATL 대화 상자 개체를 추가 하면 다음 줄이 클래스에 자동으로 추가 됩니다.

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

여기서 `MyDialog` 는 ATL 대화 상자 마법사에서 입력 한 **짧은 이름** 입니다.

자세한 내용은 [대화 상자 구현](../../atl/implementing-a-dialog-box.md) 을 참조 하세요.

로 만든 모달 대화 상자의 ActiveX 컨트롤 `CAxDialogImpl` 은 액셀러레이터 키를 지원 하지 않습니다. 를 사용 하 여 만든 대화 상자에서 액셀러레이터 키 `CAxDialogImpl` 를 지원 하려면 모덜리스 대화 상자를 만들고 사용자 고유의 메시지 루프를 사용 하 여 큐에서 메시지를 가져와 액셀러레이터 키를 처리 한 후 [Caxdialogimpl:: IsDialogMessage](#isdialogmessage) 를 사용 합니다.

에 대 한 자세한 내용은 `CAxDialogImpl` [ATL 컨트롤 포함 FAQ](../../atl/atl-control-containment-faq.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a> CAxDialogImpl:: AdviseSinkMap

개체의 싱크 맵 이벤트 맵에 모든 항목을 advise 하거나 unadvise 하려면이 메서드를 호출 합니다.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>매개 변수

*bAdvise*<br/>
모든 싱크 항목을 advise 하려면 true로 설정 합니다. 모든 싱크 항목이 advise 되지 않으면 false입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="caxdialogimplcreate"></a><a name="create"></a> CAxDialogImpl:: Create

모덜리스 대화 상자를 만들려면이 메서드를 호출 합니다.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
진행 소유자 창에 대 한 핸들입니다.

*dwInitParam*<br/>
진행 WM_INITDIALOG 메시지의 *lParam* 매개 변수에서 대화 상자에 전달할 값을 지정 합니다.

*RECT&*<br/>
이 매개 변수는 사용되지 않습니다. 이 매개 변수는에 의해 전달 됩니다 `CComControl` .

### <a name="return-value"></a>반환 값

새로 만든 대화 상자에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 대화 상자는 개체에 자동으로 연결 됩니다 `CAxDialogImpl` . 모달 대화 상자를 만들려면 [DoModal](#domodal)를 호출 합니다.

두 번째 재정의가 제공 되므로 [CComControl](../../atl/reference/ccomcontrol-class.md)에서 대화 상자를 사용할 수 있습니다.

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a> CAxDialogImpl::D estroyWindow

모덜리스 대화 상자를 삭제 하려면이 메서드를 호출 합니다.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>반환 값

창이 성공적으로 제거 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`DestroyWindow`을 호출 하 여 모달 대화 상자를 삭제 하지 마십시오. 대신 [EndDialog](#enddialog) 를 호출 합니다.

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a> CAxDialogImpl::D oModal

이 메서드를 호출 하 여 모달 대화 상자를 만듭니다.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
진행 소유자 창에 대 한 핸들입니다. 기본값은 [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 함수의 반환 값입니다.

*dwInitParam*<br/>
진행 WM_INITDIALOG 메시지의 *lParam* 매개 변수에서 대화 상자에 전달할 값을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 [EndDialog](#enddialog)호출에 지정 된 *nRetCode* 매개 변수의 값입니다. 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

이 대화 상자는 개체에 자동으로 연결 됩니다 `CAxDialogImpl` .

모덜리스 대화 상자를 만들려면 [create](#create)를 호출 합니다.

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a> CAxDialogImpl:: EndDialog

모달 대화 상자를 삭제 하려면이 메서드를 호출 합니다.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>매개 변수

*nRetCode*<br/>
진행 [DoModal](#domodal)에서 반환 하는 값입니다.

### <a name="return-value"></a>반환 값

대화 상자가 소멸 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`EndDialog` 는 대화 상자 프로시저를 통해 호출 해야 합니다. 대화 상자가 제거 되 면 Windows에서는 대화 상자를 만든의 반환 값으로 *nRetCode* 의 값을 사용 합니다 `DoModal` .

> [!NOTE]
> `EndDialog`모덜리스 대화 상자를 삭제 하려면를 호출 하지 마세요. 대신 [DestroyWindow](#destroywindow) 를 호출 합니다.

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a> CAxDialogImpl:: GetDialogProc

콜백 함수에 대 한 포인터를 가져오려면이 메서드를 호출 `DialogProc` 합니다.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>반환 값

콜백 함수에 대 한 포인터를 반환 합니다 `DialogProc` .

### <a name="remarks"></a>설명

`DialogProc`함수는 응용 프로그램에서 정의 된 콜백 함수입니다.

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a> CAxDialogImpl:: GetIDD

대화 상자 템플릿 리소스 ID를 가져오려면이 메서드를 호출 합니다.

```
int GetIDD();
```

### <a name="return-value"></a>반환 값

대화 상자 템플릿 리소스 ID를 반환 합니다.

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a> CAxDialogImpl:: IsDialogMessage

메시지를이 대화 상자에 사용할지 여부를 확인 하려면이 메서드를 호출 하 고 메시지를 처리 하려면 메시지를 처리 합니다.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
확인할 메시지를 포함 하는 [MSG](/windows/win32/api/winuser/ns-winuser-msg) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메시지가 처리 되었으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 메시지 루프 내에서 호출 됩니다.

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a> CAxDialogImpl:: m_bModal

디버그 빌드에서만 존재 하 고 대화 상자가 모달 인 경우 true로 설정 된 변수입니다.

```
bool m_bModal;
```

## <a name="see-also"></a>참고 항목

[CDialogImpl 클래스](../../atl/reference/cdialogimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
