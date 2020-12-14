---
description: '자세히 알아보기: CWinFormsDialog 클래스'
title: CWinFormsDialog 클래스
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 501f9c354bd6f0b7a628aabb93f4680155f74a69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342623"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog 클래스

Windows Forms 사용자 정의 컨트롤을 호스팅하는 MFC 대화 상자 클래스의 래퍼입니다.

## <a name="syntax"></a>구문

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>매개 변수

*TManagedControl*<br/>
MFC 응용 프로그램에 표시 되는 .NET Framework 사용자 정의 컨트롤입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWinFormsDialog:: CWinFormsDialog](#cwinformsdialog)|`CWinFormsDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWinFormsDialog:: GetControl](#getcontrol)|Windows Forms 사용자 정의 컨트롤에 대 한 참조를 검색 합니다.|
|[CWinFormsDialog:: GetControlHandle](#getcontrolhandle)|Windows Forms 사용자 정의 컨트롤에 대 한 창 핸들을 검색 합니다.|
|[CWinFormsDialog:: OnInitDialog](#oninitdialog)|Windows Forms 사용자 정의 컨트롤을 만들고 호스팅하여 MFC 대화 상자를 초기화 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-|
|[CWinFormsDialog:: operator-&gt;](#operator_-_gt)|식에서 [CWinFormsDialog:: GetControl](#getcontrol) 을 바꿉니다.|
|[CWinFormsDialog:: operator TManagedControl ^](#operator-tmanagedcontrol-hat)|형식을 Windows Forms 사용자 정의 컨트롤에 대 한 참조로 캐스팅 합니다.|

## <a name="remarks"></a>설명

`CWinFormsDialog` 는 Windows Forms 사용자 정의 컨트롤을 호스팅하는 [CDialog](../../mfc/reference/cdialog-class.md)(MFC 대화 상자 클래스)의 래퍼입니다. 이렇게 하면 모달 또는 모덜리스 MFC 대화 상자에서 .NET Framework 컨트롤을 표시할 수 있습니다.

Windows Forms 사용에 대 한 자세한 내용은 [mfc에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md) 및 [Windows Form 사용자 정의 컨트롤을 Mfc 대화 상자로 호스팅](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)을 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** afxwinforms

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a> CWinFormsDialog:: CWinFormsDialog

`CWinFormsDialog` 개체를 생성합니다.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>매개 변수

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID를 포함 합니다. 대화 상자 편집기를 사용 하 여 대화 상자 템플릿을 만들고 응용 프로그램의 리소스 스크립트 파일에 저장 합니다. 대화 상자 템플릿에 대 한 자세한 내용은 [CDialog 클래스](../../mfc/reference/cdialog-class.md)를 참조 하세요.

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a> CWinFormsDialog:: GetControl

Windows Forms 사용자 정의 컨트롤에 대 한 참조를 검색 합니다.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>반환 값

MFC 대화 상자의 Windows Forms 컨트롤에 대 한 참조를 반환 합니다.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsDialog:: GetControlHandle

Windows Forms 사용자 정의 컨트롤에 대 한 창 핸들을 검색 합니다.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>반환 값

Windows Forms 사용자 정의 컨트롤에 대 한 창 핸들을 반환 합니다.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a> CWinFormsDialog:: OnInitDialog

Windows Forms 사용자 정의 컨트롤을 만들고 호스팅하여 MFC 대화 상자를 초기화 합니다.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>반환 값

응용 프로그램에서 대화 상자의 컨트롤 중 하나에 입력 포커스를 설정 했는지 여부를 지정 하는 부울 값입니다. `OnInitDialog`가 0이 아닌 값을 반환 하는 경우 Windows에서 입력 포커스를 대화 상자의 첫 번째 컨트롤로 설정 합니다. 이 메서드는 응용 프로그램에서 명시적으로 입력 포커스를 대화 상자의 컨트롤 중 하나로 설정한 경우에만 0을 반환할 수 있습니다.

### <a name="remarks"></a>설명

DoModal [에서 상속](../../mfc/reference/cdialog-class.md)된 [Create](../../mfc/reference/cdialog-class.md#create), [createindirect](../../mfc/reference/cdialog-class.md#createindirect)또는 [](../../mfc/reference/cdialog-class.md#domodal) 메서드를 사용 하 여 MFC 대화 상자를 만들면 WM_INITDIALOG 메시지가 전송 되 고이 메서드가 호출 됩니다. 대화 상자에 Windows Forms 컨트롤의 인스턴스를 만들고 사용자 정의 컨트롤의 크기에 맞게 대화 상자의 크기를 조정 합니다. 그런 다음 MFC 대화 상자에서 새 컨트롤을 호스팅합니다.

대화 상자가 초기화 될 때 특수 처리를 수행 해야 하는 경우이 멤버 함수를 재정의 합니다. 이 메서드를 사용 하는 방법에 대 한 자세한 내용은 [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)를 참조 하세요.

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a> CWinFormsDialog:: operator-&gt;

식에서 [CWinFormsDialog:: GetControl](#getcontrol) 을 바꿉니다.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>설명

이 연산자는 식에서를 대체 하는 편리한 구문을 제공 합니다 `GetControl` .

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a> CWinFormsDialog:: operator TManagedControl ^

형식을 Windows Forms 사용자 정의 컨트롤에 대 한 참조로 캐스팅 합니다.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>설명

이 연산자는 형식을 Windows Forms 컨트롤에 대 한 참조로 캐스팅 합니다. 이 클래스는 `CWinFormsDialog<TManagedControl>` Windows Forms 사용자 정의 컨트롤 개체에 대 한 포인터를 허용 하는 함수에 대화 상자를 전달 하는 데 사용 됩니다.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView 클래스](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)
