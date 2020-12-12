---
description: '자세히 알아보기: CMFCToolBarDateTimeCtrl 클래스'
title: CMFCToolBarDateTimeCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 141c2dc868f5bfc74c41cb5198daac790e23db58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306718"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 클래스

날짜 및 시간 선택 컨트롤을 포함 하는 도구 모음 단추입니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|`CMFCToolBarDateTimeCtrl` 개체를 생성합니다.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl:: CanBeStretched](#canbestretched)|사용자 지정 중에 사용자가 단추를 늘릴 수 있는지 여부를 지정 합니다. [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl:: CopyFrom](#copyfrom)|다른 도구 모음 단추의 속성을 현재 단추로 복사 합니다. [에서 CMFCToolBarButton:: copyfrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|다음에 사용하도록 예약됩니다.|
|[CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|도구 모음 단추에서 메뉴로 텍스트를 복사 합니다.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCToolBarDateTimeCtrl:: GetByCmd](#getbycmd)|`CMFCToolBarDateTimeCtrl`응용 프로그램에서 지정 된 명령 ID를 가진 첫 번째 개체를 검색 합니다.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|날짜 및 시간 선택 컨트롤에 대 한 포인터를 반환 합니다.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|도구 모음 단추와 연결 된 창 핸들을 검색 합니다. [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)를 재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)|날짜 및 시간 선택 컨트롤에서 선택한 시간을 가져와 지정 된 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 배치 합니다.|
|[CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall)|지정 된 명령 ID를 가진 시간 선택 컨트롤 단추에서 선택한 시간을 반환 합니다.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|사용자가 단추를 선택할 때 단추의 테두리를 표시할지 여부를 결정 합니다. [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|단추가 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 처리 하는지 여부를 지정 합니다. [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|**사용자 지정** 대화 상자에 단추가 추가 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)를 재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|지정 된 장치 컨텍스트 및 도킹 상태에 대 한 단추의 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl:: OnClick](#onclick)|사용자가 컨트롤을 클릭할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)을 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|부모 도구 모음이 WM_CTLCOLOR 메시지를 처리할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)를 재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::OnDraw`|지정 된 스타일 및 옵션을 사용 하 여 단추를 그리기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)를 재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|**사용자 지정** 대화 상자의 **명령** 창에 단추를 그리기 위해 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|전역 글꼴이 변경 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl:: OnMove](#onmove)|부모 도구 모음이 이동 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl:: OnShow](#onshow)|단추를 표시 하거나 숨길 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)를 재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::OnSize`|부모 도구 모음이 크기나 위치를 변경 하 고이 변경으로 인해 크기가 변경 될 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl:: OnUpdateToolTip](#onupdatetooltip)|부모 도구 모음에서 도구 설명 텍스트를 업데이트할 때 프레임 워크에서 호출 됩니다. [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)를 재정의 합니다.|
|`CMFCToolBarDateTimeCtrl::Serialize`|보관에서이 개체를 읽거나 보관 파일에 씁니다 ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)재정의).|
|`CMFCToolBarDateTimeCtrl::SetStyle`|도구 모음 단추의 스타일을 설정 합니다. [CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)를 재정의 합니다.|
|[CMFCToolBarDateTimeCtrl:: SetTime](#settime)|시간 선택 컨트롤에서 시간 및 날짜를 설정 합니다.|
|[CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall)|지정 된 명령 ID를 가진 시간 선택 컨트롤의 모든 인스턴스에 대 한 시간 및 날짜를 설정 합니다.|

## <a name="remarks"></a>설명

날짜 및 시간 선택 컨트롤을 사용 하는 방법에 대 한 예제는 ToolbarDateTimePicker 샘플 프로젝트를 참조 하세요. 도구 모음에 컨트롤 단추를 추가 하는 방법에 대 한 자세한 내용은 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbardatetimectrl

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a> CMFCToolBarDateTimeCtrl:: CanBeStretched

사용자 지정 중에 사용자가 단추를 늘릴 수 있는지 여부를 지정 합니다.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>반환 값

이 메서드는 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

기본적으로 프레임 워크는 사용자 지정 중에 사용자가 도구 모음 단추를 늘이지 못하게 합니다. 이 메서드는 사용자 지정 중에 사용자가 날짜 및 시간 도구 모음 단추를 스트레치할 수 있도록 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))을 확장 합니다.

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a> CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) 개체를 만들고 초기화 합니다.

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 컨트롤 ID입니다.

*iImage*<br/>
진행 도구 모음의 개체에 있는 이미지의 인덱스입니다 `CMFCToolBarImages` .

*dwStyle*<br/>
진행 `CMFCToolBarDateTimeCtrlImpl` 사용자가 단추를 클릭할 때 만들어지는 창의 스타일입니다.

*iWidth*<br/>
진행 컨트롤의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이 개체는 시스템 날짜 및 시간으로 초기화 됩니다. 내부 개체의 창 스타일에는 `CMFCToolBarDateTimeCtrlImpl` *dwstyle* 매개 변수와 WS_CHILD 및 WS_VISIBLE 스타일이 포함 됩니다. 을 사용 하 여 이러한 스타일을 변경할 수는 없습니다 `CMFCToolBarDateTimeCtrl::SetStyle` . `SetStyle`컨트롤의 스타일을 변경 하는 데 사용 `CMFCToolBarDateTimeCtrl` 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCToolBarDateTimeCtrl` . 이 코드 조각은 [도구 모음 날짜 시간 선택 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a> CMFCToolBarDateTimeCtrl:: CopyFrom

다른 도구 모음 단추의 속성을 현재 단추로 복사 합니다.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 복사할 원본 단추에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 다른 도구 모음 단추를이 도구 모음 단추에 복사 합니다. *src* 는 형식 이어야 합니다 `CMFCToolBarDateTimeCtrl` .

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a> CMFCToolBarDateTimeCtrl:: ExportToMenuButton

도구 모음 단추에서 메뉴로 텍스트를 복사 합니다.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>매개 변수

*menuButton*<br/>
진행 대상 메뉴 단추에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

이 메서드는 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 컨트롤의 명령 ID와 연결 된 문자열 리소스를 로드 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))을 재정의 합니다. 문자열 리소스에 대 한 자세한 내용은 [CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)을 참조 하십시오.

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a> CMFCToolBarDateTimeCtrl:: GetByCmd

`CMFCToolBarDateTimeCtrl`응용 프로그램에서 지정 된 명령 ID를 가진 첫 번째 개체를 검색 합니다.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 검색할 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 `CMFCToolBarDateTimeCtrl` 명령 id를 가진 응용 프로그램의 첫 번째 개체 이거나, `CMFCToolBarDateTimeCtrl` 지정 된 명령 id를 가진 개체가 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 공유 유틸리티 메서드는 지정 된 명령 ID를 가진 시간 선택 컨트롤의 모든 인스턴스에 대 한 시간과 날짜를 설정 하거나 가져오기 위해 [CMFCToolBarDateTimeCtrl:: settimeall](#settimeall) 및 [CMFCToolBarDateTimeCtrl:: gettimeall](#gettimeall) 등의 메서드에서 사용 됩니다.

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a> CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

날짜 및 시간 선택 컨트롤에 대 한 포인터를 반환 합니다.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>반환 값

날짜 및 시간 선택 컨트롤에 대 한 포인터입니다. 또는 컨트롤이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

`CMFCToolBarDateTimeCtrl`클래스는 `m_pWndDateTime` `CMFCToolBarDateTimeCtrl` 개체를 도구 모음에 삽입할 때 데이터 멤버를 초기화 합니다.

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a> CMFCToolBarDateTimeCtrl::GetHwnd

도구 모음 단추와 연결 된 창 핸들을 검색 합니다.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>반환 값

날짜 및 시간 도구 모음 단추와 연결 된 창 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) 메서드를 재정의 합니다.

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a> CMFCToolBarDateTimeCtrl:: GetTime

연결 된 날짜 및 시간 선택 컨트롤에서 선택한 시간을 가져와 지정 된 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 배치 합니다.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>매개 변수

*timeDest*<br/>
제한이 첫 번째 오버 로드에서 시스템 시간 정보를 수신 하는 [COleDateTime 클래스](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다. 두 번째 오버 로드에서 시스템 시간 정보를 수신 하는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체입니다.

*pTimeDest*<br/>
제한이 시스템 시간 정보를 수신 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다. NULL이 아니어야 합니다.

### <a name="return-value"></a>반환 값

첫 번째 오버 로드에서는 시간이 [COleDateTime 클래스](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 성공적으로 기록 된 경우 0이 아닌 값이 됩니다. 그렇지 않으면 0입니다. 두 번째 및 세 번째 오버 로드에서 반환 값은 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) 구조에 설정 된 dwflag 멤버와 동일한 DWORD입니다.

### <a name="remarks"></a>설명

메서드는 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Structure 멤버 dwFlags를 설정 하 여 날짜 및 시간 선택이 날짜 및 시간으로 설정 되어 있는지 여부를 나타냅니다. 값이 GDT_NONE와 같으면 컨트롤이 status로 설정 되 `no date` 고 DTS_SHOWNONE 스타일을 사용 합니다. 반환 된 값이 GDT_VALID와 같으면 시스템 시간이 대상 위치에 저장 됩니다.

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a> CMFCToolBarDateTimeCtrl:: GetTimeAll

지정 된 명령 ID를 가진 시간 선택 컨트롤 단추에서 사용자가 선택한 시간을 반환 합니다.

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 도구 모음 단추의 명령 ID를 지정 합니다.

*timeDest*<br/>
제한이 첫 번째 오버 로드에서 시스템 시간 정보를 수신 하는 [COleDateTime 클래스](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다. 두 번째 오버 로드에서 시스템 시간 정보를 수신 하는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체입니다.

*pTimeDest*<br/>
제한이 시스템 시간 정보를 수신 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다. NULL이 아니어야 합니다.

### <a name="return-value"></a>반환 값

프레임 워크에서 명령 ID *Uicmd* 와 일치 하는 도구 모음 단추를 찾을 수 없는 경우 첫 번째 오버 로드에서 반환 값은 0이 고 다른 오버 로드에서는 GDT_NONE. 도구 모음 단추가 있으면 반환 값은 해당 단추에서 [CMFCToolBarDateTimeCtrl:: GetTime](#gettime) 에 대 한 호출의 반환 값과 동일 합니다. 단추가 발견 될 때 반환 값이 0 또는 GDT_NONE 발생할 수 있습니다 .이는에 대 `GetTime` 한 호출이 다른 이유로 유효한 날짜를 반환 하지 않았음을 나타냅니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 명령 ID를 포함 하는 도구 모음 단추를 찾고 해당 단추에 대해 [CMFCToolBarDateTimeCtrl:: GetTime](#gettime) 메서드를 호출 합니다.

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a> CMFCToolBarDateTimeCtrl::HaveHotBorder

사용자가 단추를 선택할 때 단추의 테두리를 표시할지 여부를 결정 합니다.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>반환 값

선택 시 단추에 테두리가 표시 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 컨트롤이 표시 되는 경우 0이 아닌 값을 반환 합니다.

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a> CMFCToolBarDateTimeCtrl::NotifyCommand

단추가 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 처리 하는지 여부를 지정 합니다.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>매개 변수

*iNotifyCode*<br/>
진행 명령과 연결 된 알림 메시지입니다.

### <a name="return-value"></a>반환 값

단추가 WM_COMMAND 메시지를 처리 하면 TRUE이 고, 부모 도구 모음에서 메시지를 처리 해야 함을 나타내려면 FALSE입니다.

### <a name="remarks"></a>설명

프레임 워크는 부모 창에 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지를 보내려고 할 때이 메서드를 호출 합니다.

이 메서드는 [DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange) 알림을 처리 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))을 확장 합니다. 내부 시간 상태를 업데이트 하 고 동일한 명령 ID를 사용 하 여 모든 개체의 시간 속성을 업데이트 `CMFCToolBarDateTimeCtrl` 합니다.

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a> CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

**사용자 지정** 대화 상자에 단추가 추가 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>설명

이 메서드는이 개체와 동일한 명령 ID를 가진 도구 모음에 있는 첫 번째 날짜 및 시간 컨트롤에서 속성을 복사 하 여 기본 클래스 구현인 [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)를 확장 합니다. 이 개체와 동일한 명령 ID를 가진 날짜 및 시간 컨트롤이 도구 모음에 없으면이 메서드는 아무 작업도 수행 하지 않습니다.

**사용자 지정** 대화 상자에 대 한 자세한 내용은 [CMFCToolBarsCustomizeDialog 클래스](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)를 참조 하세요.

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCToolBarDateTimeCtrl::OnChangeParentWnd

단추가 새 도구 모음에 삽입 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 새 부모 창입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 개체를 다시 만들어 기본 클래스 구현 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))을 재정의 합니다 `CMFCToolBarDateTimeCtrlImpl` .

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a> CMFCToolBarDateTimeCtrl:: OnClick

사용자가 컨트롤을 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 사용 되지 않는.

*bDelay*<br/>
진행 사용 되지 않는.

### <a name="return-value"></a>반환 값

단추가 클릭 메시지를 처리 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 개체가 표시 되는 경우 0이 아닌 값을 반환 하 여 기본 클래스 구현인 [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)을 재정의 합니다 `CMFCToolBarDateTimeCtrlImpl` .

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a> CMFCToolBarDateTimeCtrl::OnCtlColor

부모 도구 모음이 WM_CTLCOLOR 메시지를 처리할 때 프레임 워크에서 호출 됩니다.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 단추를 표시 하는 장치 컨텍스트입니다.

*nCtlColor*<br/>
진행 사용 되지 않는.

### <a name="return-value"></a>반환 값

프레임 워크에서 단추의 배경을 칠하는 데 사용 하는 전역 브러시에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 제공 된 장치 컨텍스트의 텍스트와 배경색을 각각 전역 텍스트 및 배경색으로 설정 하 여 기본 클래스 구현인 [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)를 재정의 합니다.

응용 프로그램에 사용할 수 있는 전역 옵션에 대 한 자세한 내용은 [AFX_GLOBAL_DATA 구조](../../mfc/reference/afx-global-data-structure.md)를 참조 하세요.

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a> CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

전역 글꼴이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>설명

이 메서드는 컨트롤의 글꼴을 전역 글꼴의 글꼴을 변경 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))을 확장 합니다.

응용 프로그램에 사용할 수 있는 전역 옵션에 대 한 자세한 내용은 [AFX_GLOBAL_DATA 구조](../../mfc/reference/afx-global-data-structure.md)를 참조 하세요.

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a> CMFCToolBarDateTimeCtrl:: OnMove

부모 도구 모음이 이동 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnMove();
```

### <a name="remarks"></a>설명

이 메서드는 내부 개체의 위치를 업데이트 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))을 재정의 합니다 `CMFCToolBarDateTimeCtrlImpl` .

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a> CMFCToolBarDateTimeCtrl:: OnShow

단추를 표시 하거나 숨길 때 프레임 워크에서 호출 됩니다.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 단추의 표시 여부를 지정 합니다. 이 매개 변수가 TRUE 이면 단추가 표시 됩니다. 그렇지 않으면 단추가 표시 되지 않습니다.

### <a name="remarks"></a>설명

이 메서드는 *Bshow* 가 TRUE 인 경우 단추를 표시 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))을 확장 합니다. 그렇지 않으면이 메서드는 단추를 숨깁니다.

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a> CMFCToolBarDateTimeCtrl:: OnSize

부모 도구 모음이 크기나 위치를 변경 하 고이 변경으로 인해 크기가 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>매개 변수

*iSize*<br/>
진행 단추의 새 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 개체의 크기와 위치를 업데이트 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize))을 재정의 합니다 `CMFCToolBarDateTimeCtrlImpl` .

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a> CMFCToolBarDateTimeCtrl:: OnUpdateToolTip

부모 도구 모음에서 도구 설명 텍스트를 업데이트할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>매개 변수

*pWndParent*<br/>
진행 부모 창입니다.

*iButtonIndex*<br/>
진행 부모 단추 컬렉션에 있는 단추의 인덱스 (0부터 시작)입니다.

*wndToolTip*<br/>
진행 도구 설명 텍스트를 표시 하는 컨트롤입니다.

*str*<br/>
제한이 `CString` 업데이트 된 도구 설명 텍스트를 받는 개체입니다.

### <a name="return-value"></a>반환 값

메서드가 도구 설명 텍스트를 업데이트 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 단추와 연결 된 도구 설명 텍스트를 표시 하 여 기본 클래스 구현 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))을 확장 합니다. 단추가 가로로 도킹 되지 않은 경우이 메서드는 아무 작업도 수행 하지 않고 FALSE를 반환 합니다.

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a> CMFCToolBarDateTimeCtrl:: SetTime

시간 선택 컨트롤에서 시간 및 날짜를 설정 합니다.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>매개 변수

*Ti New*<br/>
진행 첫 번째 버전에서 컨트롤이 설정 되는 시간을 포함 하는 [COleDateTime 클래스](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 대 한 참조입니다. 두 번째 버전에서 컨트롤이 설정 될 시간을 포함 하는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 포인터입니다.

*Ptia*<br/>
진행 컨트롤이 설정 되는 시간을 포함 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CDateTimeCtrl:: SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)를 호출 하 여 날짜 및 시간 선택 컨트롤의 시간을 설정 합니다.

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a> CMFCToolBarDateTimeCtrl:: SetTimeAll

지정 된 명령 ID를 가진 시간 선택 컨트롤의 모든 인스턴스에 대 한 시간 및 날짜를 설정 합니다.

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>매개 변수

*uiCmd*<br/>
진행 도구 모음 단추의 명령 ID를 지정 합니다.

*Ti New*<br/>
진행 첫 번째 버전에서 컨트롤이 설정 되는 시간을 포함 하는 [COleDateTime 클래스](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다. 두 번째 버전에서 컨트롤이 설정 될 시간을 포함 하는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 포인터입니다.

*Ptia*<br/>
진행 컨트롤이 설정 되는 시간을 포함 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 명령 ID를 사용 하 여 도구 모음 단추를 찾고 [CMFCToolBarDateTimeCtrl:: SetTime](#settime)를 호출 하 여 날짜 및 시간 선택 컨트롤의 시간을 설정 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
