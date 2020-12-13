---
description: '자세히 알아보기: CMFCDesktopAlertWnd 클래스'
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
ms.openlocfilehash: 45b75bdbd24a88a7eacff124bb07ac81e7703c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330087"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

`CMFCDesktopAlertWnd`클래스는 사용자에 게 이벤트를 알리기 위해 화면에 표시 되는 모덜리스 대화 상자의 기능을 구현 합니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCDesktopAlertWnd:: Create](#create)|바탕 화면 경고 창을 만들고 초기화 합니다.|
|[CMFCDesktopAlertWnd:: Get애니메이션 속도](#getanimationspeed)|애니메이션 속도를 반환 합니다.|
|[CMFCDesktopAlertWnd:: Get애니메이션 형식](#getanimationtype)|애니메이션 유형을 반환 합니다.|
|[CMFCDesktopAlertWnd:: GetAutoCloseTime](#getautoclosetime)|자동 닫기 제한 시간을 반환 합니다.|
|[CMFCDesktopAlertWnd:: GetCaptionHeight](#getcaptionheight)|캡션의 높이를 반환 합니다.|
|[CMFCDesktopAlertWnd:: GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd:: GetLastPos](#getlastpos)|화면에서 바탕 화면 경고 창의 마지막 유효 위치를 반환 합니다.|
|[CMFCDesktopAlertWnd:: GetTransparency](#gettransparency)|투명도 수준을 반환 합니다.|
|[CMFCDesktopAlertWnd:: HasSmallCaption](#hassmallcaption)|바탕 화면 경고 창이 작은 캡션에 표시 되는지 여부를 결정 합니다.|
|[CMFCDesktopAlertWnd:: OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd:: OnClickLinkButton](#onclicklinkbutton)|사용자가 바탕 화면 경고 메뉴에 있는 링크 단추를 클릭 하면 프레임 워크에서 호출 됩니다.|
|[CMFCDesktopAlertWnd:: OnCommand](#oncommand)|프레임 워크는 사용자가 메뉴에서 항목을 선택 하거나, 자식 컨트롤이 알림 메시지를 보내거나, 액셀러레이터 키 입력이 변환 될 때이 멤버 함수를 호출 합니다. ( [CWnd:: OnCommand](../../mfc/reference/cwnd-class.md#oncommand)를 재정의 합니다.)|
|[CMFCDesktopAlertWnd:: OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::P rocessCommand](#processcommand)||
|[CMFCDesktopAlertWnd:: Set애니메이션 속도](#setanimationspeed)|새 애니메이션 속도를 설정 합니다.|
|[CMFCDesktopAlertWnd:: Set애니메이션 형식](#setanimationtype)|애니메이션 유형을 설정 합니다.|
|[CMFCDesktopAlertWnd:: SetAutoCloseTime](#setautoclosetime)|자동 닫기 제한 시간을 설정 합니다.|
|[CMFCDesktopAlertWnd:: SetSmallCaption](#setsmallcaption)|작은 캡션과 일반 캡션 사이를 전환 합니다.|
|[CMFCDesktopAlertWnd:: SetTransparency](#settransparency)|투명도 수준을 설정 합니다.|

## <a name="remarks"></a>설명

바탕 화면 경고 창은 투명 하 게 표시 될 수 있고 애니메이션 효과와 함께 표시 될 수 있으며, 지정 된 지연 이후 또는 닫기 단추를 클릭 하 여 사용자가 파일을 닫을 때 사라질 수 있습니다.

바탕 화면 경고 창에는 아이콘, 메시지 텍스트 (레이블) 및 링크를 포함 하는 기본 대화 상자도 포함 될 수 있습니다. 또는 바탕 화면 경고 창에 응용 프로그램 리소스의 사용자 지정 대화 상자가 포함 될 수 있습니다.

두 단계로 데스크톱 경고 창을 만들 수 있습니다. 먼저 생성자를 호출 하 여 개체를 생성 `CMFCDesktopAlertWnd` 합니다. 둘째, [CMFCDesktopAlertWnd:: create](#create) 멤버 함수를 호출 하 여 창을 만들고 개체에 연결 `CMFCDesktopAlertWnd` 합니다.

`CMFCDesktopAlertWnd`개체는 바탕 화면 경고 창의 클라이언트 영역을 채우는 특수 한 자식 대화 상자를 만듭니다. 대화 상자에 배치 된 모든 컨트롤을 소유 합니다.

팝업 창에 사용자 지정 대화 상자를 표시 하려면 다음 단계를 수행 합니다.

1. `CMFCDesktopAlertDialog`에서 클래스를 파생합니다.

1. 리소스에서 자식 대화 상자 템플릿을 만듭니다.

1. 대화 상자 템플릿의 리소스 ID 및 파생 클래스의 런타임 클래스 정보에 대 한 포인터를 사용 하 여 [CMFCDesktopAlertWnd:: Create](#create) 를 호출 합니다.

1. 사용자 지정 대화 상자를 프로그래밍 하 여 호스팅된 컨트롤에서 들어오는 모든 알림을 처리 하거나 호스트 된 컨트롤을 프로그래밍 하 여 이러한 알림을 직접 처리 합니다.

바탕 화면 경고 창의 동작을 제어 하려면 다음 함수를 사용 합니다.

- [CMFCDesktopAlertWnd:: setanimation type](#setanimationtype)을 호출 하 여 애니메이션 유형을 설정 합니다. 올바른 옵션에는 펼침, slide 및 페이드가 포함 됩니다.

- [CMFCDesktopAlertWnd:: setanimation speed](#setanimationspeed)를 호출 하 여 애니메이션 프레임 속도를 설정 합니다.

- [CMFCDesktopAlertWnd:: SetTransparency](#settransparency)를 호출 하 여 투명도 수준을 설정 합니다.

- [CMFCDesktopAlertWnd:: SetSmallCaption](#setsmallcaption)를 호출 하 여 캡션의 크기를 작게 변경 합니다. 작은 캡션은 7 픽셀의 수준입니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 개체를 구성 하는 방법을 보여 줍니다 `CMFCDesktopAlertWnd` `CMFCDesktopAlertWnd` . 이 예제에서는 애니메이션 유형을 설정 하 고, 팝업 창의 투명도를 설정 하 고, 경고 창에 작은 캡션이 표시 되도록 지정 하 고, 경고 창이 자동으로 닫히기 전 까지의 시간을 설정 하는 방법을 보여 줍니다. 또한이 예제에서는 바탕 화면 경고 창을 만들고 초기화 하는 방법을 보여 줍니다. 이 코드 조각은 [데스크톱 경고 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDesktopAlertWnd

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a> CMFCDesktopAlertWnd:: Create

바탕 화면 경고 창을 만들고 초기화 합니다.

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>매개 변수

*pWndOwner*<br/>
[in, out] 경고 창의 소유자를 지정 합니다. 그러면 해당 소유자가 바탕 화면 경고 창에 대 한 모든 알림을 받게 됩니다. 이 값은 NULL 일 수 없습니다.

*uiDlgResID*<br/>
진행 경고 창의 리소스 ID를 지정 합니다.

*hMenu*<br/>
진행 사용자가 메뉴 단추를 클릭할 때 표시 되는 메뉴를 지정 합니다. NULL 인 경우 메뉴 단추가 표시 되지 않습니다.

*ptPos*<br/>
진행 화면 좌표를 사용 하 여 경고 창이 표시 되는 초기 위치를 지정 합니다. 이 매개 변수가 (-1,-1) 이면 화면 오른쪽 아래 모서리에 경고 창이 표시 됩니다.

*pRTIDlgBar*<br/>
진행 경고 창의 클라이언트 영역을 포함 하는 사용자 지정 대화 상자 클래스에 대 한 런타임 클래스 정보입니다.

*params*<br/>
진행 경고 창을 만드는 데 사용 되는 매개 변수를 지정 합니다.

### <a name="return-value"></a>반환 값

경고 창이 성공적으로 생성 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

경고 창을 만들려면이 메서드를 호출 합니다. 경고 창의 클라이언트 영역에는 사용자에 게 표시 되는 모든 컨트롤을 호스트 하는 자식 대화 상자가 포함 되어 있습니다.

첫 번째 메서드 오버 로드는 응용 프로그램의 리소스에서 로드 되는 자식 대화 상자를 포함 하는 경고 창을 만듭니다. 첫 번째 메서드 오버 로드는 사용자 지정 대화 상자 클래스에 대 한 런타임 클래스 정보를 지정할 수도 있습니다.

두 번째 메서드 오버 로드는 기본 컨트롤을 포함 하는 경고 창을 만듭니다. [CMFCDesktopAlertWndInfo 클래스](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)를 수정 하 여 표시할 컨트롤을 지정할 수 있습니다.

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a> CMFCDesktopAlertWnd:: Get애니메이션 속도

애니메이션 속도를 반환 합니다.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>반환 값

경고 창의 애니메이션 속도 (밀리초)입니다.

### <a name="remarks"></a>설명

애니메이션 속도는 경고 창이 열리고 닫히는 속도를 설명 합니다.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a> CMFCDesktopAlertWnd:: Get애니메이션 형식

애니메이션 유형을 반환 합니다.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>반환 값

다음 애니메이션 형식 중 하나입니다.

- NO_ANIMATION

- 펼침

- 화면

- 인하

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a> CMFCDesktopAlertWnd:: GetAutoCloseTime

자동 닫기 제한 시간을 반환 합니다.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>반환 값

경고 창이 자동으로 종료 되는 시간 (밀리초)입니다.

### <a name="remarks"></a>설명

이 방법을 사용 하 여 경고 창이 자동으로 닫힐 때까지 경과 해야 하는 시간을 결정 합니다.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a> CMFCDesktopAlertWnd:: GetCaptionHeight

캡션의 높이를 반환 합니다.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>반환 값

캡션의 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 파생 클래스에서 재정의할 수 있습니다. 기본 구현: 팝업 창에 작은 캡션 또는 Windows API 함수에서 가져온 값을 표시 해야 하는 경우에는 작은 캡션 높이 값 (7 픽셀)을 반환 합니다 `GetSystemMetrics(SM_CYSMCAPTION)` .

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a> CMFCDesktopAlertWnd:: GetLastPos

화면에서 바탕 화면 경고 창의 마지막 위치를 반환 합니다.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>반환 값

화면 좌표에 있는 점입니다.

### <a name="remarks"></a>설명

이 메서드는 화면에서 경고 창의 마지막 유효한 위치를 반환 합니다.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a> CMFCDesktopAlertWnd:: GetTransparency

투명도 수준을 반환 합니다.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>반환 값

0과 255 (포함) 사이의 투명도 수준입니다. 값이 클수록 창이 더 불투명해 집니다.

### <a name="remarks"></a>설명

경고 창의 현재 투명도 수준을 검색 하려면이 메서드를 사용 합니다.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a> CMFCDesktopAlertWnd:: HasSmallCaption

바탕 화면 경고 창에 작은 캡션 또는 일반 크기 캡션이 있는지를 확인 합니다.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>반환 값

팝업 창이 작은 캡션으로 표시 되 면 TRUE입니다. 팝업 창이 보통 크기의 캡션으로 표시 되 면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 팝업 창에 작은 캡션 또는 일반 크기 캡션이 있는지 여부를 확인 합니다. 기본적으로 작은 캡션은 7 픽셀의 수준입니다. Windows API 함수를 호출 하 여 일반 크기 캡션의 높이를 가져올 수 있습니다 `GetSystemMetrics(SM_CYCAPTION)` .

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a> CMFCDesktopAlertWnd:: OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>매개 변수

진행 *Cpoint&*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a> CMFCDesktopAlertWnd:: OnClickLinkButton

사용자가 바탕 화면 경고 메뉴에 있는 링크 단추를 클릭 하면 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>매개 변수

*uiCmdID*<br/>
진행 이 매개 변수는 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

항상 FALSE입니다.

### <a name="remarks"></a>설명

사용자가 경고 창의 링크를 클릭할 때 알림을 받으려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a> CMFCDesktopAlertWnd:: OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

진행 *wParam*<br/>

진행 *lParam*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a> CMFCDesktopAlertWnd:: OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a> CMFCDesktopAlertWnd::P rocessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>매개 변수

진행 *hwnd*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a> CMFCDesktopAlertWnd:: Set애니메이션 속도

새 애니메이션 속도를 설정 합니다.

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>매개 변수

*nSpeed*<br/>
진행 새 애니메이션 속도 (밀리초)를 지정 합니다.

### <a name="remarks"></a>설명

경고 창의 애니메이션 속도를 설정 하려면이 메서드를 호출 합니다. 기본 애니메이션 속도는 30 밀리초입니다.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a> CMFCDesktopAlertWnd:: Set애니메이션 형식

애니메이션 유형을 설정 합니다.

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>매개 변수

*type*<br/>
진행 애니메이션 유형을 지정 합니다.

### <a name="remarks"></a>설명

애니메이션 유형을 설정 하려면이 메서드를 호출 합니다. 다음 값 중 하나를 지정할 수 있습니다.

- NO_ANIMATION

- 펼침

- 화면

- 인하

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a> CMFCDesktopAlertWnd:: SetAutoCloseTime

자동 닫기 제한 시간을 설정 합니다.

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>매개 변수

*않았습니다*<br/>
진행 경고 창이 자동으로 닫히기 전 까지의 시간 (밀리초)입니다.

### <a name="remarks"></a>설명

사용자가 창과 상호 작용 하지 않는 경우 지정 된 시간 후에 경고 창이 자동으로 닫힙니다.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a> CMFCDesktopAlertWnd:: SetSmallCaption

작은 캡션과 일반 캡션 사이를 전환 합니다.

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>매개 변수

*bSmallCaption*<br/>
진행 경고 창에 작은 캡션이 표시 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE로 설정 하 여 경고 창이 일반 크기 캡션을 표시 하도록 지정 합니다.

### <a name="remarks"></a>설명

작은 또는 보통 크기 캡션을 표시 하려면이 메서드를 호출 합니다. 기본적으로 작은 캡션은 7 픽셀의 수준입니다. Windows API 함수를 호출 하 여 일반 캡션의 크기를 가져올 수 있습니다 `GetSystemMetrics(SM_CYCAPTION)` .

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a> CMFCDesktopAlertWnd:: SetTransparency

팝업 창의 투명도 수준을 설정 합니다.

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>매개 변수

*nTransparency*<br/>
진행 투명도 수준을 지정 합니다. 이 값은 0에서 255 (포함) 사이 여야 합니다. 값이 클수록 창이 더 불투명해 집니다.

### <a name="remarks"></a>설명

팝업 창의 투명도 수준을 설정 하려면이 함수를 호출 합니다.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a> CMFCDesktopAlertWnd:: GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo 클래스](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)
