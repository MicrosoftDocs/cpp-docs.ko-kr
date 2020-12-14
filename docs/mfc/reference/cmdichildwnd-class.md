---
description: '자세히 알아보기: CMDIChildWnd 클래스'
title: CMDIChildWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 4e9bf936cbb4f07401e8d54c56516f8846f2fc0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336694"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 클래스

창 관리 멤버와 함께 Windows MDI(다중 문서 인터페이스) 자식 창 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMDIChildWnd:: CMDIChildWnd](#cmdichildwnd)|`CMDIChildWnd` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMDIChildWnd:: Create](#create)|개체와 연결 된 Windows MDI 자식 창을 만듭니다 `CMDIChildWnd` .|
|[CMDIChildWnd:: GetMDIFrame](#getmdiframe)|MDI 클라이언트 창의 부모 MDI 프레임을 반환 합니다.|
|[CMDIChildWnd:: MDIActivate](#mdiactivate)|이 MDI 자식 창을 활성화 합니다.|
|[CMDIChildWnd:: MDIDestroy](#mdidestroy)|이 MDI 자식 창을 소멸 시킵니다.|
|[CMDIChildWnd:: MDIMaximize](#mdimaximize)|이 MDI 자식 창을 최대화 합니다.|
|[CMDIChildWnd:: MDIRestore](#mdirestore)|이 MDI 자식 창을 최대화 하거나 최소화 된 크기로 복원 합니다.|
|[CMDIChildWnd:: SetHandles](#sethandles)|메뉴 및 액셀러레이터 리소스에 대 한 핸들을 설정 합니다.|

## <a name="remarks"></a>설명

Mdi 자식 창은 데스크톱이 아닌 MDI 프레임 창 내부에 표시 된다는 점을 제외 하면 일반적인 프레임 창과 매우 유사 합니다. MDI 자식 창에는 자체의 메뉴 모음이 없고 대신 MDI 프레임 창의 메뉴가 공유 됩니다. 프레임 워크는 MDI 프레임 메뉴를 자동으로 변경 하 여 현재 활성화 된 MDI 자식 창을 표시 합니다.

응용 프로그램에 대 한 유용한 MDI 자식 창을 만들려면에서 클래스를 파생 시킵니다 `CMDIChildWnd` . 파생 클래스에 멤버 변수를 추가 하 여 응용 프로그램에 특정 한 데이터를 저장 합니다. 파생 클래스에서 메시지 처리기 멤버 함수 및 메시지 맵을 구현하여 메시지가 창에 전달될 때 수행되는 작업을 지정합니다.

MDI 자식 창을 생성 하는 방법에는 다음 세 가지가 있습니다.

- 을 사용 하 여 직접 구성 `Create` 합니다.

- 을 사용 하 여 직접 구성 `LoadFrame` 합니다.

- 문서 템플릿을 통해 간접적으로 구성 합니다.

또는를 호출 하기 전에 `Create` `LoadFrame` c + + 연산자를 사용 하 여 힙에서 프레임 창 개체를 구성 해야 합니다 **`new`** . 를 호출 하기 전에 `Create` [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) global 함수를 사용 하 여 창 클래스를 등록 하 여 프레임에 대 한 아이콘 및 클래스 스타일을 설정할 수도 있습니다.

`Create`멤버 함수를 사용 하 여 프레임의 생성 매개 변수를 즉각적인 인수로 전달 합니다.

`LoadFrame` 는 보다 작은 인수 `Create` 를 사용 하며, 대신 프레임의 캡션, 아이콘, 액셀러레이터 키 테이블 및 메뉴를 포함 하 여 리소스에서 대부분의 기본값을 검색 합니다. 에서 액세스할 수 있도록 하려면 `LoadFrame` 이러한 모든 리소스의 리소스 ID가 같아야 합니다 (예: IDR_MAINFRAME).

개체는 `CMDIChildWnd` 뷰 및 문서를 포함 하는 경우 프로그래머가 직접 생성 하지 않고 프레임 워크에 의해 간접적으로 생성 됩니다. `CDocTemplate`개체는 프레임 생성, 포함 하는 뷰의 생성 및 해당 문서에 대 한 뷰 연결을 오케스트레이션 합니다. 생성자의 매개 변수는 `CDocTemplate` 관련 된 `CRuntimeClass` 세 가지 클래스 (문서, 프레임 및 뷰)의를 지정 합니다. `CRuntimeClass`개체는 사용자가 지정 하는 경우 (예: 새 파일 명령 또는 MDI 창 새 명령 사용) 프레임 워크에서 동적으로 새 프레임을 만드는 데 사용 됩니다.

위의 RUNTIME_CLASS 메커니즘이 제대로 작동 하려면에서 파생 된 프레임 창 클래스를 `CMDIChildWnd` DECLARE_DYNCREATE으로 선언 해야 합니다.

`CMDIChildWnd`클래스는에서 대부분의 기본 구현을 상속 `CFrameWnd` 합니다. 이러한 기능의 자세한 목록은 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 클래스 설명을 참조 하세요. 클래스에는 `CMDIChildWnd` 다음과 같은 추가 기능이 있습니다.

- 클래스와 함께 `CMultiDocTemplate` `CMDIChildWnd` 동일한 문서 템플릿의 여러 개체가 동일한 메뉴를 공유 하 여 Windows 시스템 리소스를 저장 합니다.

- 현재 활성화 된 MDI 자식 창 메뉴는 MDI 프레임 창의 메뉴를 완전히 바꾸고 현재 활성화 된 MDI 자식 창의 캡션은 MDI 프레임 창의 캡션에 추가 됩니다. Mdi 프레임 창과 함께 구현 되는 MDI 자식 창 함수의 추가 예제는 `CMDIFrameWnd` 클래스 설명을 참조 하십시오.

C + + 연산자를 사용 **`delete`** 하 여 프레임 창을 제거 하지 마십시오. 대신 `CWnd::DestroyWindow`를 사용하세요. `CFrameWnd`의 구현은 `PostNcDestroy` 창이 소멸 될 때 c + + 개체를 삭제 합니다. 사용자가 프레임 창을 닫으면 기본 `OnClose` 처리기가를 호출 `DestroyWindow` 합니다.

에 대 한 자세한 내용은 `CMDIChildWnd` [프레임 창](../../mfc/frame-windows.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a> CMDIChildWnd:: CMDIChildWnd

를 호출 하 여 `CMDIChildWnd` 개체를 생성 합니다.

```
CMDIChildWnd();
```

### <a name="remarks"></a>설명

`Create`을 호출 하 여 표시 되는 창을 만듭니다.

### <a name="example"></a>예제

  [CMDIChildWnd:: Create](#create)의 예제를 참조 하세요.

## <a name="cmdichildwndcreate"></a><a name="create"></a> CMDIChildWnd:: Create

이 멤버 함수를 호출 하 여 Windows MDI 자식 창을 만들고 개체에 연결 `CMDIChildWnd` 합니다.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
Windows 클래스 ( [예: wndclassa](/windows/win32/api/winuser/ns-winuser-wndclassw) 구조체)의 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 클래스 이름은 [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) global 함수에 등록 된 모든 이름일 수 있습니다. 표준의 경우 NULL 이어야 합니다 `CMDIChildWnd` .

*lpszWindowName*<br/>
창 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 제목 표시줄의 텍스트로 사용 됩니다.

*dwStyle*<br/>
창 [스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 특성을 지정 합니다. WS_CHILD 스타일이 필요 합니다.

*rect*<br/>
창의 크기와 위치를 포함 합니다. `rectDefault`값을 사용 하면 창에서 새의 크기와 위치를 지정할 수 있습니다 `CMDIChildWnd` .

*pParentWnd*<br/>
창의 부모를 지정 합니다. NULL 인 경우 주 응용 프로그램 창이 사용 됩니다.

*pContext*<br/>
[Ccreatecontext](../../mfc/reference/ccreatecontext-structure.md) 구조체를 지정 합니다. 이 매개 변수는 NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

현재 활성화 된 MDI 자식 프레임 창에서 부모 프레임 창의 캡션을 확인할 수 있습니다. 자식 프레임 창의 FWS_ADDTOTITLE 스타일 비트를 해제 하면이 기능을 사용할 수 없습니다.

프레임 워크는 사용자 명령에 대 한 응답으로이 멤버 함수를 호출 하 여 자식 창을 만들며, 프레임 워크는 *pContext* 매개 변수를 사용 하 여 자식 창을 응용 프로그램에 올바르게 연결 합니다. 를 호출 하 `Create` 는 경우 *PCONTEXT* 는 NULL 일 수 있습니다.

### <a name="example"></a>예제

예제 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>예제

예제 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a> CMDIChildWnd:: GetMDIFrame

이 함수를 호출 하 여 MDI 부모 프레임을 반환 합니다.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>반환 값

MDI 부모 프레임 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

반환 되는 프레임은에서 제거 되는 두 개의 부모 이며 `CMDIChildWnd` 개체를 관리 하는 MDICLIENT 형식의 창 부모입니다 `CMDIChildWnd` . [Getparent](../../mfc/reference/cwnd-class.md#getparent) 멤버 함수를 호출 하 여 `CMDIChildWnd` 개체의 직계 MDICLIENT 부모를 임시 포인터로 반환 합니다 `CWnd` .

### <a name="example"></a>예제

  [CMDIFrameWnd:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)의 예제를 참조 하세요.

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a> CMDIChildWnd:: MDIActivate

MDI 프레임 창과 별개로 MDI 자식 창을 활성화 하려면이 멤버 함수를 호출 합니다.

```cpp
void MDIActivate();
```

### <a name="remarks"></a>설명

프레임이 활성화 되 면 마지막으로 활성화 된 자식 창도 활성화 됩니다.

### <a name="example"></a>예제

  [CMDIFrameWnd:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)의 예제를 참조 하세요.

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a> CMDIChildWnd:: MDIDestroy

이 멤버 함수를 호출 하 여 MDI 자식 창을 제거 합니다.

```cpp
void MDIDestroy();
```

### <a name="remarks"></a>설명

멤버 함수는 프레임 창에서 자식 창의 제목을 제거 하 고 자식 창을 비활성화 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a> CMDIChildWnd:: MDIMaximize

MDI 자식 창을 최대화 하려면이 멤버 함수를 호출 합니다.

```cpp
void MDIMaximize();
```

### <a name="remarks"></a>설명

자식 창이 최대화 된 경우 창의 크기를 조정 하 여 해당 클라이언트 영역이 프레임 창의 클라이언트 영역을 채우도록 합니다. 창에서 자식 창의 컨트롤 메뉴를 프레임의 메뉴 모음에 배치 하 여 사용자가 자식 창을 복원 하거나 닫고 자식 창의 제목을 프레임 창 제목에 추가할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a> CMDIChildWnd:: MDIRestore

MDI 자식 창을 최대화 또는 최소화 된 크기로 복원 하려면이 멤버 함수를 호출 합니다.

```cpp
void MDIRestore();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a> CMDIChildWnd:: SetHandles

메뉴 및 액셀러레이터 리소스에 대 한 핸들을 설정 합니다.

```cpp
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>매개 변수

*hMenu*<br/>
메뉴 리소스의 핸들입니다.

*hAccel*<br/>
액셀러레이터 키 리소스의 핸들입니다.

### <a name="remarks"></a>설명

MDI 자식 창 개체에서 사용 하는 메뉴 및 액셀러레이터 리소스를 설정 하려면이 함수를 호출 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 클래스](../../mfc/reference/cmdiframewnd-class.md)
