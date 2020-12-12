---
description: '자세히 알아보기: CPageSetupDialog 클래스'
title: CPageSetupDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: 862e8c1edff04ba58efe13f471ffeee71c11ede5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264910"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog 클래스

인쇄 여백 설정과 수정이 추가로 지원되는 Windows 공용 OLE 페이지 설정 대화 상자에서 제공하는, 서비스를 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|`CPageSetupDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPageSetupDialog:: Create프린터 Dc](#createprinterdc)|인쇄용 장치 컨텍스트를 만듭니다.|
|[CPageSetupDialog::D oModal](#domodal)|대화 상자를 표시 하 고 사용자가 선택할 수 있도록 허용 합니다.|
|[CPageSetupDialog:: GetDeviceName 이름](#getdevicename)|프린터의 장치 이름을 반환 합니다.|
|[CPageSetupDialog:: GetDevMode](#getdevmode)|프린터의 현재 DEVMODE를 반환 합니다.|
|[CPageSetupDialog:: GetDriverName](#getdrivername)|프린터에서 사용 하는 드라이버를 반환 합니다.|
|[CPageSetupDialog:: GetMargins](#getmargins)|프린터의 현재 여백 설정을 반환 합니다.|
|[CPageSetupDialog:: GetPaperSize](#getpapersize)|프린터의 용지 크기를 반환 합니다.|
|[CPageSetupDialog::GetPortName](#getportname)|출력 포트 이름을 반환 합니다.|
|[CPageSetupDialog:: OnDrawPage](#ondrawpage)|인쇄 된 페이지의 화면 이미지를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.|
|[CPageSetupDialog::P reDrawPage](#predrawpage)|인쇄 된 페이지의 화면 이미지를 렌더링 하기 전에 프레임 워크에서 호출 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPageSetupDialog:: m_psd](#m_psd)|개체를 사용자 지정 하는 데 사용 되는 구조체 `CPageSetupDialog` 입니다.|

## <a name="remarks"></a>설명

이 클래스는 인쇄 설정 대화 상자를 사용 하도록 디자인 되었습니다.

개체를 사용 하려면 `CPageSetupDialog` 먼저 생성자를 사용 하 여 개체를 만듭니다 `CPageSetupDialog` . 대화 상자를 생성 한 후에는 데이터 멤버의 값을 설정 하거나 수정 `m_psd` 하 여 대화 상자의 컨트롤 값을 초기화할 수 있습니다. [M_psd](#m_psd) 구조는 PAGESETUPDLG 유형입니다.

대화 상자 컨트롤을 초기화 한 후 `DoModal` 멤버 함수를 호출 하 여 대화 상자를 표시 하 고 사용자가 인쇄 옵션을 선택할 수 있습니다. `DoModal` 사용자가 확인 (IDOK) 또는 취소 (IDCANCEL) 단추를 선택 했는지 여부를 반환 합니다.

`DoModal`에서 IDOK를 반환 하는 경우의 여러 `CPageSetupDialog` 멤버 함수를 사용 하거나 `m_psd` 데이터 멤버에 액세스 하 여 사용자가 입력 한 정보를 검색할 수 있습니다.

> [!NOTE]
> 일반 OLE 페이지 설정 대화 상자를 해제 한 후에는 사용자가 변경한 내용이 프레임 워크에 의해 저장 되지 않습니다. 응용 프로그램 자체는이 대화 상자에서 응용 프로그램의 문서 또는 응용 프로그램 클래스의 멤버와 같은 영구 위치에 값을 저장 하는 것입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a> CPageSetupDialog::CPageSetupDialog

개체를 생성 하려면이 함수를 호출 `CPageSetupDialog` 합니다.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
대화 상자의 설정을 사용자 지정 하는 데 사용할 수 있는 하나 이상의 플래그입니다. 비트 or 연산자를 사용 하 여 값을 조합할 수 있습니다. 이러한 값에는 다음과 같은 의미가 있습니다.

- PSD_DEFAULTMINMARGINS 페이지 여백에 대해 허용 되는 최소 너비를 프린터의 최소 너비와 동일 하 게 설정 합니다. PSD_MARGINS 및 PSD_MINMARGINS 플래그도 지정 된 경우이 플래그는 무시 됩니다.

- 구현 되지 PSD_INWININIINTLMEASURE.

- PSD_MINMARGINS를 사용 하면 시스템에서 멤버에 지정 된 값을 `rtMinMargin` 왼쪽, 위쪽, 오른쪽 및 아래쪽 여백에 대해 허용 되는 최소 너비로 사용 합니다. 시스템에서 사용자가 지정 된 최소값 보다 작은 너비를 입력 하지 못하게 합니다. PSD_MINMARGINS 지정 하지 않으면 시스템에서 허용 되는 최소 너비를 프린터에서 허용 하는 것으로 설정 합니다.

- PSD_MARGINS 여백 컨트롤 영역을 활성화 합니다.

- PSD_INTHOUSANDTHSOFINCHES 하면 대화 상자의 단위가 1/1000 인치 단위로 측정 됩니다.

- PSD_INHUNDREDTHSOFMILLIMETERS 하면 대화 상자의 단위가 1/100 단위로 측정 됩니다.

- PSD_DISABLEMARGINS 여백 대화 상자 컨트롤을 사용 하지 않도록 설정 합니다.

- PSD_DISABLEPRINTER 프린터 단추를 사용 하지 않도록 설정 합니다.

- PSD_NOWARNING 기본 프린터가 없으면 경고 메시지가 표시 되지 않도록 합니다.

- PSD_DISABLEORIENTATION 페이지 방향 대화 상자 컨트롤을 사용 하지 않도록 설정 합니다.

- PSD_RETURNDEFAULT 하면에서 `CPageSetupDialog` 대화 상자를 표시 하지 않고 시스템 기본 프린터에 대해 초기화 된 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 및 [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) 구조체를 반환 합니다. 및가 모두 NULL 인 것으로 가정 합니다. `hDevNames` `hDevMode` 그렇지 않으면 함수가 오류를 반환 합니다. 시스템 기본 프린터가 이전 프린터 드라이버 (Windows 버전 3.0 이전 버전)에서 지원 되는 경우에만이 `hDevNames` 반환 됩니다. `hDevMode` 는 NULL입니다.

- PSD_DISABLEPAPER 용지 선택 컨트롤을 사용 하지 않도록 설정 합니다.

- PSD_SHOWHELP 하면 대화 상자에 도움말 단추가 표시 됩니다. `hwndOwner`이 플래그가 지정 된 경우 멤버는 NULL이 아니어야 합니다.

- PSD_ENABLEPAGESETUPHOOK에 지정 된 후크 함수를 사용 하도록 설정 `lpfnSetupHook` 합니다.

- PSD_ENABLEPAGESETUPTEMPLATE를 사용 하면 운영 체제에서 및로 식별 되는 대화 상자 템플릿 상자를 사용 하 여 대화 상자를 만들 수 `hInstance` `lpSetupTemplateName` 있습니다.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE는가 `hInstance` 미리 로드 된 대화 상자 템플릿을 포함 하는 데이터 블록을 식별 함을 나타냅니다. 이 플래그가 지정 된 경우 시스템에서 무시 됩니다 `lpSetupTemplateName` .

- PSD_ENABLEPAGEPAINTHOOK에 지정 된 후크 함수를 사용 하도록 설정 `lpfnPagePaintHook` 합니다.

- PSD_DISABLEPAGEPAINTING 대화 상자의 그리기 영역을 사용 하지 않도록 설정 합니다.

*pParentWnd*<br/>
대화 상자의 부모 또는 소유자에 대 한 포인터입니다.

### <a name="remarks"></a>설명

[DoModal](../../mfc/reference/cdialog-class.md#domodal) 함수를 사용 하 여 대화 상자를 표시 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a> CPageSetupDialog:: Create프린터 Dc

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 및 [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) 구조에서 프린터 장치 컨텍스트를 만듭니다.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>반환 값

새로 만든 프린터 DC (장치 컨텍스트)에 대 한 핸들입니다.

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a> CPageSetupDialog::D oModal

이 함수를 호출 하 여 Windows 일반 OLE 페이지 설정 대화 상자를 표시 하 고 사용자가 인쇄 여백, 용지 크기 및 용지 및 대상 프린터와 같은 다양 한 인쇄 설정 옵션을 선택할 수 있습니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

IDOK 또는 IDCANCEL. IDCANCEL이 반환 되는 경우 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 호출 하 여 오류가 발생 했는지 여부를 확인 합니다.

IDOK 및 IDCANCEL는 사용자가 확인 또는 취소 단추를 선택 했는지 여부를 나타내는 상수입니다.

### <a name="remarks"></a>설명

또한 사용자는 네트워크 위치 및 선택한 프린터와 관련 된 속성 등의 프린터 설치 옵션에 액세스할 수 있습니다.

구조체의 멤버를 설정 하 여 다양 한 페이지 설정 대화 상자 옵션을 초기화 하려면를 `m_psd` 호출 하기 전에 `DoModal` , 그리고 대화 상자 개체가 생성 된 후에이 옵션을 설정 해야 합니다. 를 호출한 후에 `DoModal` 는 다른 멤버 함수를 호출 하 여 사용자가 대화 상자에 입력 한 설정이 나 정보를 검색 합니다.

사용자가 입력 한 현재 설정을 전파 하려면 [CWinApp:: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)를 호출 합니다. 이 함수는 개체의 정보를 가져오고를 `CPageSetupDialog` 초기화 하 고 적절 한 특성을 가진 새 프린터 DC를 선택 합니다.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>예제

  [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog)의 예제를 참조 하세요.

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a> CPageSetupDialog:: GetDeviceName 이름

이후에이 함수 `DoModal` 를 호출 하 여 현재 선택 된 프린터의 이름을 검색 합니다.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>반환 값

개체에서 사용 하는 장치 이름 `CPageSetupDialog` 입니다.

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a> CPageSetupDialog:: GetDevMode

를 호출한 후이 함수 `DoModal` 를 호출 하 여 개체의 프린터 장치 컨텍스트에 대 한 정보를 검색 `CPageSetupDialog` 합니다.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>반환 값

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 데이터 구조로, 장치 초기화 및 인쇄 드라이버 환경에 대 한 정보가 포함 되어 있습니다. Windows SDK에서 설명 하는 Windows [globalunlock](/windows/win32/api/winbase/nf-winbase-globalunlock) 함수를 사용 하 여이 구조에서 사용 하는 메모리의 잠금을 해제 해야 합니다.

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a> CPageSetupDialog:: GetDriverName

[DoModal](../../mfc/reference/cprintdialog-class.md#domodal) 를 호출한 후이 함수를 호출 하 여 시스템 정의 프린터 장치 드라이버의 이름을 검색 합니다.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>반환 값

`CString`시스템 정의 드라이버 이름을 지정 하는입니다.

### <a name="remarks"></a>설명

에서 반환 하는 개체에 대 한 포인터를 `CString` `GetDriverName` `lpszDriverName` [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc)에 대 한 호출에서 값으로 사용 합니다.

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a> CPageSetupDialog:: GetMargins

을 호출 하 여 `DoModal` 프린터 장치 드라이버의 여백을 검색 한 후이 함수를 호출 합니다.

```cpp
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>매개 변수

*lpRectMargins*<br/>
현재 선택 된 프린터의 인쇄 여백 (1/1000 인치 또는 1/100 mm)을 설명 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 포인터입니다. 이 사각형에 관심이 없으면이 매개 변수에 대해 NULL을 전달 합니다.

*lpRectMinMargins*<br/>
`RECT` `CRect` 현재 선택 된 프린터의 최소 인쇄 여백 (1/1000 인치 또는 1/100 mm)을 설명 하는 구조체 또는 개체에 대 한 포인터입니다. 이 사각형에 관심이 없으면이 매개 변수에 대해 NULL을 전달 합니다.

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a> CPageSetupDialog:: GetPaperSize

인쇄를 위해 선택 된 용지의 크기를 검색 하려면이 함수를 호출 합니다.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>반환 값

인쇄를 위해 선택 된 용지 크기 (1/1000 인치 또는 1/100 mm)를 포함 하는 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체입니다.

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a> CPageSetupDialog::GetPortName

를 호출한 후이 함수 `DoModal` 를 호출 하 여 현재 선택 된 프린터 포트의 이름을 검색 합니다.

```
CString GetPortName() const;
```

### <a name="return-value"></a>반환 값

현재 선택 된 프린터 포트의 이름입니다.

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a> CPageSetupDialog:: m_psd

멤버가 dialog 개체의 특성을 저장 하는 PAGESETUPDLG 형식의 구조입니다.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 `CPageSetupDialog` `m_psd` 멤버 함수를 호출 하기 전에를 사용 하 여 대화 상자의 다양 한 측면을 설정할 수 있습니다 `DoModal` .

데이터 멤버를 직접 수정 하는 경우 `m_psd` 모든 기본 동작을 재정의 합니다.

[Pagesetupdlg](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) 구조에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

[CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog)의 예제를 참조 하세요.

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a> CPageSetupDialog:: OnDrawPage

인쇄 된 페이지의 화면 이미지를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
프린터 장치 컨텍스트에 대 한 포인터입니다.

*N 메시지*<br/>
현재 그려지는 페이지의 영역을 나타내는 메시지를 지정 합니다. 다음 중 하나일 수 있습니다.

- 전체 페이지 영역을 WM_PSD_FULLPAGERECT 합니다.

- 현재 최소 여백 WM_PSD_MINMARGINRECT 합니다.

- 현재 여백을 WM_PSD_MARGINRECT 합니다.

- 페이지의 콘텐츠를 WM_PSD_GREEKTEXTRECT 합니다.

- 우표 스탬프 표시를 위해 예약 된 WM_PSD_ENVSTAMPRECT 영역입니다.

- 반환 주소 표현의 WM_PSD_YAFULLPAGERECT 영역입니다. 이 영역은 샘플 페이지 영역의 가장자리로 확장 됩니다.

*lpRect*<br/>
그리기 영역의 좌표를 포함 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

처리 되는 경우 0이 아닌 값 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 이미지는 일반 OLE 페이지 설정 대화 상자의 일부로 표시 됩니다. 기본 구현에서는 텍스트 페이지의 이미지를 그립니다.

이 함수를 재정의 하 여 이미지의 특정 영역 또는 전체 이미지의 그리기를 사용자 지정 합니다. **`switch`** **`case`** *N 메시지* 의 값을 확인 하는 문이 포함 된 문을 사용 하 여이 작업을 수행할 수 있습니다. 예를 들어 페이지 이미지 내용의 렌더링을 사용자 지정 하려면 다음 예제 코드를 사용할 수 있습니다.

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

*N 메시지* 의 모든 경우를 처리할 필요가 없습니다. 이미지의 한 구성 요소, 이미지의 여러 구성 요소 또는 전체 영역을 처리 하도록 선택할 수 있습니다.

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a> CPageSetupDialog::P reDrawPage

인쇄 된 페이지의 화면 이미지를 그리기 전에 프레임 워크에서 호출 됩니다.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>매개 변수

*wPaper*<br/>
용지 크기를 나타내는 값을 지정 합니다. 이 값은 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 구조 설명에 나열 된 **DMPAPER_** 값 중 하나일 수 있습니다.

*wFlags*<br/>
용지 또는 봉투의 방향, 프린터가 도트 매트릭스 인지 HPPCL (Hewlett Packard Printer Control Language) 장치 인지를 나타냅니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- 가로 모드의 용지 0x001 (점 행렬)

- 가로 모드의 0x003 용지 (HPPCL)

- 세로 모드의 0x005 용지 (점 행렬)

- 세로 모드의 0x007 용지 (HPPCL)

- 가로 모드의 0x00b 봉투 (HPPCL)

- 세로 모드의 0x00d 봉투 (점 행렬)

- 가로 모드의 0x019 봉투 (점 행렬)

- 세로 모드의 0x01f 봉투 (점 행렬)

*pPSD*<br/>
`PAGESETUPDLG` 구조체에 대한 포인터입니다. [Pagesetupdlg](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

### <a name="return-value"></a>반환 값

처리 되는 경우 0이 아닌 값 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이미지 그리기를 사용자 지정 하려면이 함수를 재정의 합니다. 이 함수를 재정의 하 고 TRUE를 반환 하는 경우 전체 이미지를 그려야 합니다. 이 함수를 재정의 하 고 FALSE를 반환 하는 경우 프레임 워크에서 전체 기본 이미지를 그립니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 워드 패드](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
