---
description: '자세히 알아보기: CMiniFrameWnd 클래스'
title: CMiniFrameWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: f4cb4b04897a2410d7fb81933e0611dde99e9f8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331604"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd 클래스

일반적으로 부동 도구 모음에 있는 절반 높이의 프레임 창을 나타냅니다.

## <a name="syntax"></a>구문

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|`CMiniFrameWnd` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMiniFrameWnd:: Create](#create)|`CMiniFrameWnd`생성 후 개체를 만듭니다.|
|[CMiniFrameWnd:: CreateEx](#createex)|`CMiniFrameWnd`생성 후 추가 옵션을 사용 하 여 개체를 만듭니다.|

## <a name="remarks"></a>설명

이러한 미니 프레임 창은 최소화/최대화 단추나 메뉴를 포함 하지 않으며 시스템 메뉴를 한 번만 클릭 하 여 해제 하는 것을 제외 하 고는 일반 프레임 창 처럼 동작 합니다.

개체를 사용 하려면 `CMiniFrameWnd` 먼저 개체를 정의 합니다. 그런 다음 [Create](#create) member 함수를 호출 하 여 미니 프레임 창을 표시 합니다.

개체를 사용 하는 방법에 대 한 자세한 내용은 `CMiniFrameWnd` [도킹 및 부동 도구 모음](../../mfc/docking-and-floating-toolbars.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a> CMiniFrameWnd::CMiniFrameWnd

개체를 생성 `CMiniFrameWnd` 하지만 창을 만들지는 않습니다.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>설명

창을 만들려면 [CMiniFrameWnd:: create](#create)를 호출 합니다.

## <a name="cminiframewndcreate"></a><a name="create"></a> CMiniFrameWnd:: Create

Windows 미니 프레임 창을 만들고 개체에 연결 `CMiniFrameWnd` 합니다.

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>매개 변수

*lpClassName*<br/>
Windows 클래스의 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 클래스 이름은 전역 [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) 함수에 등록 된 모든 이름일 수 있습니다. NULL 인 경우 창 클래스는 프레임 워크에서 등록 됩니다. MFC는 기본 클래스에 다음 스타일 및 특성을 제공 합니다.

- 사용자가 마우스를 두 번 클릭할 때 창 프로시저에 두 번 클릭 메시지를 보내는 스타일 비트 CS_DBLCLKS 설정 합니다.

- 창 크기가 변경 될 때 다시 그릴 클라이언트 영역의 내용을 지시 하는 스타일 비트 CS_HREDRAW 및 CS_VREDRAW를 설정 합니다.

- 클래스 커서를 Windows 표준 IDC_ARROW로 설정 합니다.

- 클래스 배경 브러시를 NULL로 설정 하므로 창이 배경을 지우지 않습니다.

- 클래스 아이콘을 표준 대기가 없어 Windows 로고 아이콘으로 설정 합니다.

- Windows에 표시 된 대로 창을 기본 크기와 위치로 설정 합니다.

*lpWindowName*<br/>
창 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다.

*dwStyle*<br/>
창 스타일 특성을 지정 합니다. 여기에는 표준 창 스타일 및 다음 특수 스타일 중 하나 이상이 포함 될 수 있습니다.

- MFS_MOVEFRAME를 사용 하면 캡션이 아니라 창의 가장자리를 클릭 하 여 미니 프레임 창을 이동할 수 있습니다.

- MFS_4THICKFRAME 미니 프레임 창의 크기 조정을 사용 하지 않도록 설정 합니다.

- MFS_SYNCACTIVE 미니 프레임 창을 활성화 하 여 부모 창 활성화를 동기화 합니다.

- MFS_THICKFRAME를 사용 하면 클라이언트 영역의 콘텐츠가 허용 하는 크기 만큼 미니 프레임 창의 크기를 줄일 수 있습니다.

- MFS_BLOCKSYSMENU 시스템 메뉴와 컨트롤 메뉴에 대 한 액세스를 사용 하지 않도록 설정 하 고 캡션 (제목 표시줄)의 일부로 변환 합니다.

가능한 창 스타일 값에 대 한 설명은 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 를 참조 하세요. 미니 프레임 창에 사용 되는 일반적인 조합은&#124;WS_SYSMENU WS_CAPTION&#124;WS_POPUP 됩니다.

*rect*<br/>
`RECT`원하는 창의 크기를 지정 하는 구조체입니다.

*pParentWnd*<br/>
부모 창을 가리킵니다. 최상위 수준 창에는 NULL을 사용 합니다.

*nID*<br/>
미니 프레임 창이 자식 창으로 만들어지면이는 자식 컨트롤의 식별자입니다. 그렇지 않으면 0입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Create` 창의 클래스 이름과 창 이름을 초기화 하 고 해당 스타일 및 부모에 대 한 기본값을 등록 합니다.

## <a name="cminiframewndcreateex"></a><a name="createex"></a> CMiniFrameWnd:: CreateEx

`CMiniFrameWnd` 개체를 만듭니다.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*<br/>
만들려는의 확장 스타일을 지정 합니다 `CMiniFrameWnd` . 창에 [확장 창 스타일](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) 을 적용 합니다.

*lpClassName*<br/>
Windows 클래스 ( [예: wndclassa](/windows/win32/api/winuser/ns-winuser-wndclassw) 구조체)의 이름을 나타내는 null로 끝나는 문자열을 가리킵니다. 클래스 이름은 global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) 함수 또는 미리 정의 된 컨트롤 클래스 이름에 등록 된 모든 이름일 수 있습니다. NULL이 아니어야 합니다.

*lpWindowName*<br/>
창 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다.

*dwStyle*<br/>
창 스타일 특성을 지정 합니다. 가능한 값에 대 한 설명은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 및 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 를 참조 하세요.

*rect*<br/>
*PParentWnd* 의 클라이언트 좌표에 있는 창의 크기 및 위치입니다.

*pParentWnd*<br/>
부모 창 개체를 가리킵니다.

*nID*<br/>
자식 창의 식별자입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CreateEx`매개 변수는 창의 초기 위치와 크기 (선택 사항)를 지정 하는 예: wndclassa 및 창 스타일을 지정 합니다. `CreateEx` 또한 창의 부모 (있는 경우)와 ID를 지정 합니다.

가 `CreateEx` 실행 되 면 Windows는 [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)및 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) 메시지를 창으로 보냅니다.

기본 메시지 처리를 확장 하려면에서 클래스를 파생 시키고 `CMiniFrameWnd` , 메시지 맵을 새 클래스에 추가 하 고, 위의 메시지에 대해 멤버 함수를 제공 합니다. 예를 들어를 재정의 하 `OnCreate` 여 새 클래스에 필요한 초기화를 수행 합니다.

추가 `On` *메시지* 메시지 처리기를 재정의 하 여 파생 클래스에 추가 기능을 추가 합니다.

WS_VISIBLE 스타일이 지정 된 경우 Windows는 창을 활성화 하 고 표시 하는 데 필요한 모든 메시지를 창으로 보냅니다. 창 스타일이 제목 표시줄을 지정 하는 경우 *lpszWindowName* 매개 변수가 가리키는 창 제목이 제목 표시줄에 표시 됩니다.

*Dwstyle* 매개 변수는 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 임의로 조합 하 여 사용할 수 있습니다.

이전 스타일 팔레트 도구 상자 창은 더 이상 지원 되지 않습니다. 이전 버전의 Windows에서는 MFC 응용 프로그램을 실행할 때 "X" 닫기 단추가 없는 이전 스타일이 지원 되었지만 Visual C++ .NET에서는 더 이상 지원 되지 않습니다. 이제 새 WS_EX_TOOLWINDOW 스타일만 지원 됩니다. 이 스타일에 대 한 설명은 [확장 창 스타일](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)
