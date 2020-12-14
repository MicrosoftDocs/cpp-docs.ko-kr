---
description: '자세히 알아보기: CPrintDialog 클래스'
title: CPrintDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: f662f3d2a522dc3a53ea887bb1031e9431df2e3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343403"
---
# <a name="cprintdialog-class"></a>CPrintDialog 클래스

Windows 공용 대화 상자에서 인쇄용으로 제공하는 서비스를 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|`CPrintDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPrintDialog:: Create프린터 Dc](#createprinterdc)|인쇄 대화 상자를 표시 하지 않고 프린터 장치 컨텍스트를 만듭니다.|
|[CPrintDialog::D oModal](#domodal)|대화 상자를 표시 하 고 사용자가 선택할 수 있게 합니다.|
|[CPrintDialog:: GetCopies](#getcopies)|요청 된 복사본 수를 검색 합니다.|
|[CPrintDialog:: GetDefaults](#getdefaults)|대화 상자를 표시 하지 않고 장치 기본값을 검색 합니다.|
|[CPrintDialog:: GetDeviceName 이름](#getdevicename)|현재 선택 된 프린터 장치의 이름을 검색 합니다.|
|[CPrintDialog:: GetDevMode](#getdevmode)|구조체를 검색 `DEVMODE` 합니다.|
|[CPrintDialog:: GetDriverName](#getdrivername)|현재 선택 된 프린터 드라이버의 이름을 검색 합니다.|
|[CPrintDialog:: GetFromPage](#getfrompage)|인쇄 범위의 시작 페이지를 검색 합니다.|
|[CPrintDialog::GetPortName](#getportname)|현재 선택 된 프린터 포트의 이름을 검색 합니다.|
|[CPrintDialog:: Get프린터 Dc](#getprinterdc)|프린터 장치 컨텍스트에 대 한 핸들을 검색 합니다.|
|[CPrintDialog::GetToPage](#gettopage)|인쇄 범위의 끝 페이지를 검색 합니다.|
|[CPrintDialog::P rintAll](#printall)|문서의 모든 페이지를 인쇄할지 여부를 결정 합니다.|
|[CPrintDialog::P rintCollate](#printcollate)|정렬 된 복사본이 요청 되는지 여부를 결정 합니다.|
|[CPrintDialog::P rintRange](#printrange)|지정 된 페이지 범위만 인쇄할지 여부를 결정 합니다.|
|[CPrintDialog::P rintSelection](#printselection)|현재 선택 된 항목만 인쇄할지 여부를 결정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPrintDialog:: m_pd](#m_pd)|개체를 사용자 지정 하는 데 사용 되는 구조체 `CPrintDialog` 입니다.|

## <a name="remarks"></a>설명

일반 인쇄 대화 상자를 사용 하면 Windows 표준과 일관 된 방식으로 인쇄 및 인쇄 설정 대화 상자를 쉽게 구현할 수 있습니다.

> [!NOTE]
> `CPrintDialogEx`클래스는 Windows 인쇄 속성 시트에서 제공 하는 서비스를 캡슐화 합니다. 자세한 내용은 [Cprintdialogex](../../mfc/reference/cprintdialogex-class.md) 개요를 참조 하세요.

`CPrintDialog`은 인쇄 설정 및 페이지 설정 모두에 대 한 일반 대화 상자를 제공 하도록 설계 된 [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)의 기능으로 대체 되었습니다.

프레임 워크를 사용 하 여 응용 프로그램에 대 한 인쇄 프로세스의 여러 측면을 처리할 수 있습니다. 이 경우 프레임 워크는 인쇄를 위한 Windows 일반 대화 상자를 자동으로 표시 합니다. 또한 프레임 워크에서 응용 프로그램에 대 한 인쇄를 처리할 수 있지만 사용자 고유의 인쇄 대화 상자를 사용 하 여 일반 인쇄 대화 상자를 재정의할 수 있습니다. 프레임 워크를 사용 하 여 인쇄 작업을 처리 하는 방법에 대 한 자세한 내용은 [인쇄](../../mfc/printing.md)문서를 참조 하세요.

응용 프로그램에서 프레임 워크의 개입 없이 인쇄를 처리 하려는 경우 `CPrintDialog` 제공 된 생성자를 사용 하 여 "있는 그대로" 클래스를 사용 하거나,에서 사용자의 대화 상자 클래스를 파생 시키고 `CPrintDialog` 필요에 맞게 생성자를 작성할 수 있습니다. 두 경우 모두 이러한 대화 상자는 클래스에서 파생 되므로 표준 MFC 대화 상자 처럼 동작 합니다 `CCommonDialog` .

개체를 사용 하려면 `CPrintDialog` 먼저 생성자를 사용 하 여 개체를 만듭니다 `CPrintDialog` . 대화 상자를 생성 한 후에는 [m_pd](#m_pd) 구조체의 값을 설정 하거나 수정 하 여 대화 상자의 컨트롤 값을 초기화할 수 있습니다. `m_pd`구조체는 [printdlg](/windows/win32/api/commdlg/ns-commdlg-printdlga)유형입니다. 이 구조에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

`m_pd`및 멤버에 대해 고유한 핸들을 제공 하지 않는 경우 `hDevMode` `hDevNames` `GlobalFree` 대화 상자를 사용 하 여 작업을 완료 하면 이러한 핸들에 대해 Windows 함수를 호출 해야 합니다. 에서 제공 하는 프레임 워크의 인쇄 설정 구현을 사용할 때 `CWinApp::OnFilePrintSetup` 이러한 핸들을 해제할 필요가 없습니다. 핸들은에서 유지 관리 되며 `CWinApp` 의 소멸자에서 해제 됩니다 `CWinApp` . 독립 실행형을 사용 하는 경우에만 이러한 핸들을 해제 해야 `CPrintDialog` 합니다.

대화 상자 컨트롤을 초기화 한 후 `DoModal` 멤버 함수를 호출 하 여 대화 상자를 표시 하 고 사용자가 인쇄 옵션을 선택할 수 있습니다. `DoModal` 사용자가 확인 (IDOK) 또는 취소 (IDCANCEL) 단추를 선택 했는지 여부를 반환 합니다.

`DoModal`에서 IDOK를 반환 하는 경우의 `CPrintDialog` 멤버 함수 중 하나를 사용 하 여 사용자가 입력 한 정보를 검색할 수 있습니다.

`CPrintDialog::GetDefaults`멤버 함수는 대화 상자를 표시 하지 않고 현재 프린터 기본값을 검색 하는 데 유용 합니다. 이 멤버 함수에는 사용자 조작이 필요 하지 않습니다.

Windows 함수를 사용 하 여 `CommDlgExtendedError` 대화 상자를 초기화 하는 동안 오류가 발생 했는지 확인 하 고 오류에 대해 자세히 알아볼 수 있습니다. 이 함수에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

`CPrintDialog` 는 Windows 버전 3.1 이상과 함께 제공 되는 COMMDLG.DLL 파일을 기반으로 합니다.

대화 상자를 사용자 지정 하려면에서 클래스를 파생 시키고 `CPrintDialog` , 사용자 지정 대화 상자 템플릿을 제공 하 고, 확장 된 컨트롤에서 알림 메시지를 처리 하는 메시지 맵을 추가 합니다. 처리 되지 않은 모든 메시지는 기본 클래스에 전달 되어야 합니다. 후크 함수 사용자 지정은 필요 하지 않습니다.

대화 상자를 인쇄 하거나 인쇄 하는지 여부에 따라 동일한 메시지를 다르게 처리 하려면 각 대화 상자에 대해 클래스를 파생 시켜야 합니다. 또한 `AttachOnSetup` 인쇄 대화 상자 내에서 인쇄 설정 단추를 선택 하면 새 대화 상자 생성을 처리 하는 Windows 함수를 재정의 해야 합니다.

사용에 대 한 자세한 내용은 `CPrintDialog` [일반 대화 상자 클래스](../../mfc/common-dialog-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a> CPrintDialog::CPrintDialog

Windows 인쇄 또는 인쇄 설정 대화 상자 개체를 생성 합니다.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*bPrintSetupOnly*<br/>
표준 Windows 인쇄 대화 상자 또는 인쇄 설정 대화 상자를 표시할지 여부를 지정 합니다. 표준 Windows 인쇄 설정 대화 상자를 표시 하려면이 매개 변수를 TRUE로 설정 합니다. FALSE로 설정 하 여 Windows 인쇄 대화 상자를 표시 합니다. *Bprintsetuponly* 가 FALSE 인 경우 인쇄 설정 옵션 단추는 인쇄 대화 상자에도 표시 됩니다.

*dwFlags*<br/>
비트 OR 연산자를 사용 하 여 대화 상자의 설정을 사용자 지정 하는 데 사용할 수 있는 하나 이상의 플래그입니다. 예를 들어 PD_ALLPAGES 플래그는 문서의 모든 페이지에 기본 인쇄 범위를 설정 합니다. 이러한 플래그에 대 한 자세한 내용은 Windows SDK에서 [Printdlg](/windows/win32/api/commdlg/ns-commdlg-printdlga) 구조체를 참조 하세요.

*pParentWnd*<br/>
대화 상자의 부모 또는 소유자 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 개체만 생성 합니다. `DoModal`멤버 함수를 사용 하 여 대화 상자를 표시 합니다.

*Bprintsetuponly* 를 FALSE로 설정 하 여 생성자를 호출 하면 PD_RETURNDC 플래그가 자동으로 사용 됩니다. , 또는를 호출한 후 `DoModal` `GetDefaults` 에는 `GetPrinterDC` 에서 프린터 DC가 반환 됩니다 `m_pd.hDC` . 호출자가 [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) 를 호출 하 여이 DC를 해제 해야 합니다 `CPrintDialog` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a> CPrintDialog:: Create프린터 Dc

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 및 [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) 구조에서 프린터 DC (장치 컨텍스트)를 만듭니다.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>반환 값

새로 만든 프린터 장치 컨텍스트에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 DC는 현재 프린터 DC로 간주 되며 이전에 가져온 다른 프린터 Dc는 사용자가 삭제 해야 합니다. 이 함수를 호출 하 고, 결과 DC를 사용 하 여 인쇄 대화 상자를 표시 하지 않을 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a> CPrintDialog::D oModal

Windows 공용 인쇄 대화 상자를 표시 하 고 사용자가 복사본 수, 페이지 범위 및 복사본의 정렬 여부와 같은 다양 한 인쇄 옵션을 선택할 수 있습니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

IDOK 또는 IDCANCEL. IDCANCEL이 반환 되는 경우 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 호출 하 여 오류가 발생 했는지 여부를 확인 합니다.

IDOK 및 IDCANCEL는 사용자가 확인 또는 취소 단추를 선택 했는지 여부를 나타내는 상수입니다.

### <a name="remarks"></a>설명

구조체의 멤버를 설정 하 여 다양 한 인쇄 대화 상자 옵션을 초기화 하려면 `m_pd` 를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 단, 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

를 호출한 후에 `DoModal` 는 다른 멤버 함수를 호출 하 여 사용자가 대화 상자에 입력 한 설정 또는 정보를 검색할 수 있습니다.

*Bprintsetuponly* 를 FALSE로 설정 하 여 생성자를 호출 하면 PD_RETURNDC 플래그가 자동으로 사용 됩니다. , 또는를 호출한 후 `DoModal` `GetDefaults` 에는 `GetPrinterDC` 에서 프린터 DC가 반환 됩니다 `m_pd.hDC` . 호출자가 [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) 를 호출 하 여이 DC를 해제 해야 합니다 `CPrintDialog` .

### <a name="example"></a>예제

  [CPrintDialog:: Create프린터 dc](#createprinterdc)의 예제를 참조 하세요.

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a> CPrintDialog:: GetCopies

요청 된 복사본 수를 검색 합니다.

```
int GetCopies() const;
```

### <a name="return-value"></a>반환 값

요청 된 복사본의 수입니다.

### <a name="remarks"></a>설명

`DoModal`요청 된 복사본 수를 검색 하기 위해를 호출한 후이 함수를 호출 합니다.

### <a name="example"></a>예제

  [CPrintDialog::P rintCollate](#printcollate)의 예제를 참조 하세요.

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a> CPrintDialog:: GetDefaults

대화 상자를 표시 하지 않고 기본 프린터의 장치 기본값을 검색 합니다.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

검색 된 값은 구조체에 배치 됩니다 `m_pd` .

경우에 따라이 함수를 호출 하면 [](#cprintdialog) `CPrintDialog` *BPRINTSETUPONLY* 가 FALSE로 설정 된에 대 한 생성자가 호출 됩니다. 이러한 경우에는 프린터 DC 및 `hDevNames` 및 `hDevMode` (데이터 멤버에 있는 두 개의 핸들이 `m_pd` 자동으로 할당 됨)가 자동으로 할당 됩니다.

`CPrintDialog` *Bprintsetuponly* 를 사용 하 여에 대 한 생성자가 FALSE로 설정 된 경우이 함수는 및를 호출자에 게 반환 하는 것 뿐만 아니라 `hDevNames` `hDevMode` `m_pd.hDevNames` `m_pd.hDevMode` 에서 프린터 DC도 반환 `m_pd.hDC` 합니다. 호출자가 개체를 마치면 핸들에서 프린터 DC를 삭제 하 고 Windows [Globalfree](/windows/win32/api/winbase/nf-winbase-globalfree) 함수를 호출 해야 합니다 `CPrintDialog` .

### <a name="example"></a>예제

이 코드 조각은 기본 프린터의 장치 컨텍스트를 가져오고 사용자에 게 프린터 해상도 (인치당 도트 수)를 보고 합니다. 프린터 기능의이 특성은 종종 DPI 라고도 합니다.

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a> CPrintDialog:: GetDeviceName 이름

현재 선택 된 프린터 장치의 이름을 검색 합니다.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>반환 값

현재 선택 된 프린터의 이름입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 를 호출 하 여 현재 선택 된 프린터의 이름을 검색 하거나 [getdefaults](#getdefaults) 를 호출 하 여 기본 프린터의 현재 장치 기본값을 검색 한 후이 함수를 호출 합니다. 에서 반환 하는 개체에 대 한 포인터를 `CString` `GetDeviceName` `lpszDeviceName` [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc)에 대 한 호출에서 값으로 사용 합니다.

### <a name="example"></a>예제

이 코드 조각은 프린터에서 사용 하는 스풀러 이름과 함께 사용자의 기본 프린터 이름 및 연결 된 포트를 표시 합니다. 예를 들어, 코드에 "기본 프린터가 HP LaserJet IIIP on \\ \server\share using winspool." 라는 메시지 상자가 표시 될 수 있습니다.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a> CPrintDialog:: GetDevMode

구조체를 검색 `DEVMODE` 합니다.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>반환 값

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 데이터 구조로, 장치 초기화 및 인쇄 드라이버 환경에 대 한 정보가 포함 되어 있습니다. Windows SDK에서 설명 하는 Windows [globalunlock](/windows/win32/api/winbase/nf-winbase-globalunlock) 함수를 사용 하 여이 구조에서 사용 하는 메모리의 잠금을 해제 해야 합니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 또는 [getdefaults](#getdefaults) 를 호출한 후이 함수를 호출 하 여 인쇄 장치에 대 한 정보를 검색 합니다.

### <a name="example"></a>예제

  [CPrintDialog::P rintCollate](#printcollate)의 예제를 참조 하세요.

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a> CPrintDialog:: GetDriverName

현재 선택 된 프린터 드라이버의 이름을 검색 합니다.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>반환 값

`CString`시스템 정의 드라이버 이름을 지정 하는입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 또는 [getdefaults](#getdefaults) 를 호출한 후이 함수를 호출 하 여 시스템 정의 프린터 장치 드라이버의 이름을 검색 합니다. 에서 반환 하는 개체에 대 한 포인터를 `CString` `GetDriverName` `lpszDriverName` [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc)에 대 한 호출에서 값으로 사용 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: GetDeviceName](#getdevicename)이름에 대 한 예제를 참조 하세요.

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a> CPrintDialog:: GetFromPage

인쇄 범위의 시작 페이지를 검색 합니다.

```
int GetFromPage() const;
```

### <a name="return-value"></a>반환 값

인쇄할 페이지 범위의 시작 페이지 번호입니다.

### <a name="remarks"></a>설명

`DoModal`을 호출 하 고 인쇄할 페이지 범위에서 시작 페이지 번호를 검색 하려면이 함수를 호출 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: m_pd](#m_pd)의 예제를 참조 하세요.

## <a name="cprintdialoggetportname"></a><a name="getportname"></a> CPrintDialog::GetPortName

현재 선택 된 프린터 포트의 이름을 검색 합니다.

```
CString GetPortName() const;
```

### <a name="return-value"></a>반환 값

현재 선택 된 프린터 포트의 이름입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 또는 [getdefaults](#getdefaults) 를 호출한 후이 함수를 호출 하 여 현재 선택 된 프린터 포트의 이름을 검색 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: GetDeviceName](#getdevicename)이름에 대 한 예제를 참조 하세요.

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a> CPrintDialog:: Get프린터 Dc

프린터 장치 컨텍스트에 대 한 핸들을 검색 합니다.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>반환 값

성공한 경우 프린터 장치 컨텍스트에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

생성자의 *Bprintsetuponly* 매개 변수가 `CPrintDialog` FALSE (인쇄 대화 상자를 표시 했음을 나타냄) 인 경우는 `GetPrinterDC` 프린터 장치 컨텍스트에 대 한 핸들을 반환 합니다. 장치 컨텍스트를 사용 하는 경우 장치 컨텍스트를 삭제 하려면 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) 함수를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a> CPrintDialog::GetToPage

인쇄 범위의 끝 페이지를 검색 합니다.

```
int GetToPage() const;
```

### <a name="return-value"></a>반환 값

인쇄할 페이지 범위의 끝 페이지 번호입니다.

### <a name="remarks"></a>설명

`DoModal`을 호출 하 여 인쇄할 페이지 범위에서 끝 페이지 번호를 검색 하려면이 함수를 호출 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: m_pd](#m_pd)의 예제를 참조 하세요.

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a> CPrintDialog:: m_pd

멤버가 dialog 개체의 특성을 저장 하는 구조체입니다.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 `CPrintDialog` `m_pd` [DoModal](#domodal) 멤버 함수를 호출 하기 전에를 사용 하 여 대화 상자의 다양 한 측면을 설정할 수 있습니다. 구조체에 대 한 자세한 내용은 `m_pd` Windows SDK [printdlg](/windows/win32/api/commdlg/ns-commdlg-printdlga) 를 참조 하세요.

데이터 멤버를 직접 수정 하는 경우 `m_pd` 모든 기본 동작을 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a> CPrintDialog::P rintAll

문서의 모든 페이지를 인쇄할지 여부를 결정 합니다.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>반환 값

문서의 모든 페이지를 인쇄 하려면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

를 호출한 후이 함수 `DoModal` 를 호출 하 여 문서의 모든 페이지를 인쇄할지 여부를 결정 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: m_pd](#m_pd)의 예제를 참조 하세요.

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a> CPrintDialog::P rintCollate

정렬 된 복사본이 요청 되는지 여부를 결정 합니다.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>반환 값

사용자가 대화 상자에서 collate 확인란을 선택 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

를 호출한 후이 함수 `DoModal` 를 호출 하 여 프린터에서 문서의 모든 인쇄 된 복사본을 정렬 해야 하는지 여부를 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a> CPrintDialog::P rintRange

지정 된 페이지 범위만 인쇄할지 여부를 결정 합니다.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>반환 값

문서의 페이지 범위만 인쇄 하려면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`DoModal`문서에서 페이지 범위만 인쇄할지 여부를 확인 하려면를 호출한 후이 함수를 호출 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: m_pd](#m_pd)의 예제를 참조 하세요.

## <a name="cprintdialogprintselection"></a><a name="printselection"></a> CPrintDialog::P rintSelection

현재 선택 된 항목만 인쇄할지 여부를 결정 합니다.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>반환 값

선택한 항목만 인쇄 하려면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

를 호출한 후이 함수 `DoModal` 를 호출 하 여 현재 선택 된 항목만 인쇄할지 여부를 확인 합니다.

### <a name="example"></a>예제

  [CPrintDialog:: m_pd](#m_pd)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 구조체](../../mfc/reference/cprintinfo-structure.md)
