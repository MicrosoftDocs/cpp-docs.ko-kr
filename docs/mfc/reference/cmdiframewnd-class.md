---
description: '자세히 알아보기: CMDIFrameWnd 클래스'
title: CMDIFrameWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: 70192fb68710e54872f0aecbe862cfb00df14fcc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336678"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd 클래스

창 관리 멤버와 함께 Windows MDI(다중 문서 인터페이스) 프레임 창 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMDIFrameWnd:: CMDIFrameWnd](#cmdiframewnd)|`CMDIFrameWnd`를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMDIFrameWnd:: CreateClient](#createclient)|이에 대 한 Windows MDICLIENT 창을 만듭니다 `CMDIFrameWnd` . `OnCreate`의 멤버 함수에 의해 호출 `CWnd` 됩니다.|
|[CMDIFrameWnd:: CreateNewChild](#createnewchild)|새 자식 창을 만듭니다.|
|[CMDIFrameWnd:: GetWindowMenuPopup](#getwindowmenupopup)|창 팝업 메뉴를 반환 합니다.|
|[CMDIFrameWnd:: MDIActivate](#mdiactivate)|다른 MDI 자식 창을 활성화 합니다.|
|[CMDIFrameWnd:: MDICascade](#mdicascade)|모든 자식 창을 종속 된 형식으로 정렬 합니다.|
|[CMDIFrameWnd:: MDIGetActive](#mdigetactive)|현재 활성 상태인 MDI 자식 창을 검색 하 고, 자식이 최대화 되었는지 여부를 나타내는 플래그를 포함 합니다.|
|[CMDIFrameWnd:: MDIIconArrange](#mdiiconarrange)|모든 최소화 된 문서 자식 창을 정렬 합니다.|
|[CMDIFrameWnd:: MDIMaximize](#mdimaximize)|MDI 자식 창을 최대화 합니다.|
|[CMDIFrameWnd:: MDINext](#mdinext)|현재 활성 자식 창 바로 뒤의 자식 창을 활성화 하 고 현재 활성 자식 창을 다른 모든 자식 창 뒤에 배치 합니다.|
|[CMDIFrameWnd:: MDIPrev](#mdiprev)|이전 자식 창을 활성화 하 고 현재 활성 자식 창을 바로 뒤에 배치 합니다.|
|[CMDIFrameWnd:: MDIRestore](#mdirestore)|MDI 자식 창을 최대화 하거나 최소화 된 크기로 복원 합니다.|
|[CMDIFrameWnd:: MDISetMenu](#mdisetmenu)|MDI 프레임 창, 창 팝업 메뉴 또는 둘 다의 메뉴를 대체 합니다.|
|[CMDIFrameWnd:: MDITile](#mditile)|모든 자식 창을 바둑판식으로 정렬 합니다.|

## <a name="remarks"></a>설명

응용 프로그램에 대 한 유용한 MDI 프레임 창을 만들려면에서 클래스를 파생 시킵니다 `CMDIFrameWnd` . 파생 클래스에 멤버 변수를 추가 하 여 응용 프로그램에 특정 한 데이터를 저장 합니다. 파생 클래스에서 메시지 처리기 멤버 함수 및 메시지 맵을 구현하여 메시지가 창에 전달될 때 수행되는 작업을 지정합니다.

의 [Create](../../mfc/reference/cframewnd-class.md#create) 또는 [loadframe](../../mfc/reference/cframewnd-class.md#loadframe) 멤버 함수를 호출 하 여 MDI 프레임 창을 생성할 수 있습니다 `CFrameWnd` .

또는를 호출 하기 전에 `Create` `LoadFrame` c + + 연산자를 사용 하 여 힙에서 프레임 창 개체를 구성 해야 합니다 **`new`** . 를 호출 하기 전에 `Create` [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) global 함수를 사용 하 여 창 클래스를 등록 하 여 프레임에 대 한 아이콘 및 클래스 스타일을 설정할 수도 있습니다.

`Create`멤버 함수를 사용 하 여 프레임의 생성 매개 변수를 즉각적인 인수로 전달 합니다.

`LoadFrame` 는 보다 작은 인수 `Create` 를 사용 하며, 대신 프레임의 캡션, 아이콘, 액셀러레이터 키 테이블 및 메뉴를 포함 하 여 리소스에서 대부분의 기본값을 검색 합니다. 에서 액세스 하려면 `LoadFrame` 이러한 모든 리소스의 리소스 ID가 같아야 합니다 (예: IDR_MAINFRAME).

`MDIFrameWnd`가에서 파생 된 경우 `CFrameWnd` 에서 파생 되는 프레임 창 클래스는 `CMDIFrameWnd` 로 선언 하지 않아도 됩니다 `DECLARE_DYNCREATE` .

`CMDIFrameWnd`클래스는에서 대부분의 기본 구현을 상속 `CFrameWnd` 합니다. 이러한 기능의 자세한 목록은 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 클래스 설명을 참조 하세요. 클래스에는 `CMDIFrameWnd` 다음과 같은 추가 기능이 있습니다.

- MDI 프레임 창은 MDICLIENT 창을 관리 하 고 컨트롤 막대와 함께 위치를 조정 합니다. MDI 클라이언트 창은 MDI 자식 프레임 창의 직계 부모입니다. `CMDIFrameWnd`사용자가 mdi 클라이언트 영역을 스크롤할 수 있도록 (예: Windows 프로그램 관리자에서와 같이)에 지정 된 WS_HSCROLL 및 WS_VSCROLL 창 스타일을 주 프레임 창이 아닌 mdi 클라이언트 창에 적용 합니다.

- MDI 프레임 창은 활성 MDI 자식 창이 없는 경우 메뉴 모음으로 사용 되는 기본 메뉴를 소유 합니다. 활성 MDI 자식이 있는 경우 mdi 프레임 창의 메뉴 모음은 MDI 자식 창 메뉴로 자동으로 대체 됩니다.

- MDI 프레임 창은 현재 MDI 자식 창 (있는 경우)과 함께 작동 합니다. 예를 들어, 명령 메시지는 MDI 프레임 창 앞에 현재 활성 상태인 MDI 자식에 게 위임 됩니다.

- MDI 프레임 창에는 다음 표준 창 메뉴 명령에 대 한 기본 처리기가 있습니다.

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- MDI 프레임 창에는 현재 문서에 새 프레임과 뷰를 만드는 ID_WINDOW_NEW의 구현도 있습니다. 응용 프로그램은 이러한 기본 명령 구현을 재정의 하 여 MDI 창 처리를 사용자 지정할 수 있습니다.

C + + 연산자를 사용 **`delete`** 하 여 프레임 창을 제거 하지 마십시오. 대신 `CWnd::DestroyWindow`를 사용하세요. `CFrameWnd`의 구현은 `PostNcDestroy` 창이 소멸 될 때 c + + 개체를 삭제 합니다. 사용자가 프레임 창을 닫으면 기본 `OnClose` 처리기가를 호출 `DestroyWindow` 합니다.

에 대 한 자세한 내용은 `CMDIFrameWnd` [프레임 창](../../mfc/frame-windows.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a> CMDIFrameWnd:: CMDIFrameWnd

`CMDIFrameWnd` 개체를 생성합니다.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>설명

`Create`또는 `LoadFrame` 멤버 함수를 호출 하 여 표시 되는 MDI 프레임 창을 만듭니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a> CMDIFrameWnd:: CreateClient

개체를 관리 하는 MDI 클라이언트 창을 만듭니다 `CMDIChildWnd` .

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>매개 변수

*lpCreateStruct*<br/>
[Createstruct](/windows/win32/api/winuser/ns-winuser-createstructw) 구조체에 대 한 긴 포인터입니다.

*pWindowMenu*<br/>
창 팝업 메뉴에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

멤버 함수를 직접 재정의 하는 경우이 멤버 함수를 호출 해야 합니다 `OnCreate` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a> CMDIFrameWnd:: CreateNewChild

새 자식 창을 만듭니다.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>매개 변수

*pClass*<br/>
만들 자식 창의 런타임 클래스입니다.

*nResource*<br/>
자식 창과 연결 된 공유 리소스의 ID입니다.

*hMenu*<br/>
자식 창의 메뉴입니다.

*hAccel*<br/>
자식 창의 액셀러레이터입니다.

### <a name="remarks"></a>설명

MDI 프레임 창의 자식 창을 만들려면이 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a> CMDIFrameWnd:: GetWindowMenuPopup

이 멤버 함수를 호출 하 여 "Window" (MDI 창 관리용 메뉴 항목이 포함 된 팝업 메뉴) 라는 현재 팝업 메뉴에 대 한 핸들을 가져옵니다.

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>매개 변수

*hMenuBar*<br/>
현재 메뉴 모음입니다.

### <a name="return-value"></a>반환 값

창 팝업 메뉴가 있으면이 메뉴를 표시 합니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

기본 구현에서는 ID_WINDOW_NEW 및 ID_WINDOW_TILE_HORZ와 같은 표준 창 메뉴 명령이 포함 된 팝업 메뉴를 찾습니다.

표준 메뉴 명령 Id를 사용 하지 않는 창 메뉴가 있는 경우이 멤버 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a> CMDIFrameWnd:: MDIActivate

다른 MDI 자식 창을 활성화 합니다.

```cpp
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>매개 변수

*pWndActivate*<br/>
활성화할 MDI 자식 창을 가리킵니다.

### <a name="remarks"></a>설명

이 멤버 함수는 활성화 되는 자식 창과 비활성화 되는 자식 창 모두에 [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) 메시지를 보냅니다.

이 메시지는 사용자가 마우스나 키보드를 사용 하 여 포커스를 MDI 자식 창으로 변경 하는 경우에 전송 되는 메시지와 동일 합니다.

> [!NOTE]
> Mdi 자식 창은 MDI 프레임 창과 별개로 활성화 됩니다. 프레임이 활성화 되 면 마지막으로 활성화 된 자식 창에는 활성 창 프레임 및 캡션 표시줄을 그리기 위해 [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) 메시지가 전송 되지만 다른 WM_MDIACTIVATE 메시지는 수신 되지 않습니다.

### <a name="example"></a>예제

[CMDIFrameWnd:: GetWindowMenuPopup](#getwindowmenupopup)의 예제를 참조 하세요.

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a> CMDIFrameWnd:: MDICascade

모든 MDI 자식 창을 계단식 형식으로 정렬 합니다.

```cpp
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>매개 변수

*nType*<br/>
Cascade 플래그를 지정 합니다. 사용 하지 않도록 설정 된 MDI 자식 창이 종속 되지 않도록 방지 하는 MDITILE_SKIPDISABLED 다음 플래그만 지정할 수 있습니다.

### <a name="remarks"></a>설명

매개 변수가 없는의 첫 번째 버전은 `MDICascade` 사용 하지 않도록 설정 된 MDI 자식 창을 모두 계단식으로 배열 합니다. *NType* 매개 변수에 대 한 MDITILE_SKIPDISABLED 지정 하는 경우 두 번째 버전은 선택적으로 MDI 자식 창을 사용 하지 않도록 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a> CMDIFrameWnd:: MDIGetActive

현재 활성 MDI 자식 창 및 자식 창이 최대화 되었는지 여부를 나타내는 플래그를 검색 합니다.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>매개 변수

*P최대화*<br/>
BOOL 반환 값에 대 한 포인터입니다. 창이 최대화 된 경우 반환에 대해 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

활성 MDI 자식 창에 대 한 포인터입니다.

### <a name="example"></a>예제

[CMDIChildWnd:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)의 예제를 참조 하세요.

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a> CMDIFrameWnd:: MDIIconArrange

모든 최소화 된 문서 자식 창을 정렬 합니다.

```cpp
void MDIIconArrange();
```

### <a name="remarks"></a>설명

최소화 되지 않은 자식 창에는 영향을 주지 않습니다.

### <a name="example"></a>예제

[CMDIFrameWnd:: MDICascade](#mdicascade)의 예제를 참조 하세요.

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a> CMDIFrameWnd:: MDIMaximize

지정 된 MDI 자식 창을 최대화 합니다.

```cpp
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
최대화할 창을 가리킵니다.

### <a name="remarks"></a>설명

자식 창이 최대화 되 면 창 크기가 조정 되어 클라이언트 영역이 클라이언트 창으로 채워집니다. Windows는 사용자가 자식 창을 복원 하거나 닫을 수 있도록 프레임의 메뉴 모음에 자식 창의 컨트롤 메뉴를 배치 합니다. 또한 프레임 창 제목에 자식 창의 제목을 추가 합니다.

현재 활성화 된 MDI 자식 창이 최대화 될 때 다른 MDI 자식 창이 활성화 되 면 Windows는 현재 활성 자식을 복원 하 고 새로 활성화 된 자식 창을 최대화 합니다.

### <a name="example"></a>예제

[CMDIChildWnd:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)의 예제를 참조 하세요.

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a> CMDIFrameWnd:: MDINext

현재 활성 자식 창 바로 뒤의 자식 창을 활성화 하 고 현재 활성 자식 창을 다른 모든 자식 창 뒤에 배치 합니다.

```cpp
void MDINext();
```

### <a name="remarks"></a>설명

현재 활성화 된 MDI 자식 창이 최대화 된 경우 멤버 함수는 현재 활성 자식을 복원 하 고 새로 활성화 된 자식을 최대화 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a> CMDIFrameWnd:: MDIPrev

이전 자식 창을 활성화 하 고 현재 활성 자식 창을 바로 뒤에 배치 합니다.

```cpp
void MDIPrev();
```

### <a name="remarks"></a>설명

현재 활성화 된 MDI 자식 창이 최대화 된 경우 멤버 함수는 현재 활성 자식을 복원 하 고 새로 활성화 된 자식을 최대화 합니다.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a> CMDIFrameWnd:: MDIRestore

MDI 자식 창을 최대화 하거나 최소화 된 크기로 복원 합니다.

```cpp
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
복원할 창을 가리킵니다.

### <a name="example"></a>예제

[CMDIChildWnd:: MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore)의 예제를 참조 하세요.

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a> CMDIFrameWnd:: MDISetMenu

MDI 프레임 창, 창 팝업 메뉴 또는 둘 다의 메뉴를 대체 합니다.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>매개 변수

*pFrameMenu*<br/>
새 프레임 창 메뉴의 메뉴를 지정 합니다. NULL 인 경우에는 메뉴가 변경 되지 않습니다.

*pWindowMenu*<br/>
새 창 팝업 메뉴의 메뉴를 지정 합니다. NULL 인 경우에는 메뉴가 변경 되지 않습니다.

### <a name="return-value"></a>반환 값

이 메시지로 바뀐 프레임 창 메뉴에 대 한 포인터입니다. 해당 포인터는 임시적이며, 나중에 사용하려고 저장하면 안됩니다.

### <a name="remarks"></a>설명

를 호출한 후 `MDISetMenu` 응용 프로그램은의 [drawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar) 멤버 함수를 호출 `CWnd` 하 여 메뉴 모음을 업데이트 해야 합니다.

이 호출이 창 팝업 메뉴를 대체 하면 MDI 자식 창 메뉴 항목이 이전 창 메뉴에서 제거 되 고 새 창 팝업 메뉴에 추가 됩니다.

MDI 자식 창이 최대화 되 고이 호출이 MDI 프레임 창 메뉴를 대체 하는 경우 컨트롤 메뉴와 복원 컨트롤이 이전 프레임 창 메뉴에서 제거 되 고 새 메뉴에 추가 됩니다.

프레임 워크를 사용 하 여 MDI 자식 창을 관리 하는 경우에는이 멤버 함수를 호출 하지 마세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a> CMDIFrameWnd:: MDITile

모든 자식 창을 바둑판식으로 정렬 합니다.

```cpp
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>매개 변수

*nType*<br/>
바둑판식 배열 플래그를 지정 합니다. 이 매개 변수는 다음 플래그 중 하나일 수 있습니다.

- 타일 MDI 자식 창을 MDITILE_HORIZONTAL 한 창이 다른 창에 표시 됩니다.

- MDITILE_SKIPDISABLED 사용 하지 않도록 설정 된 MDI 자식 창을 바둑판식으로 배열 하지 못하게 합니다.

- 타일 MDI 자식 창 MDITILE_VERTICAL 다른 창 옆에 표시 됩니다.

### <a name="remarks"></a>설명

매개 변수가 없는의 첫 번째 버전은 windows `MDITile` 버전 3.1 이상에서 windows를 세로로 바둑판식으로 배열 합니다. 두 번째 버전은 *nType* 매개 변수의 값에 따라 세로 또는 가로로 창을 바둑판식으로 배열 합니다.

### <a name="example"></a>예제

[CMDIFrameWnd:: MDICascade](#mdicascade)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd 클래스](../../mfc/reference/cmdichildwnd-class.md)
