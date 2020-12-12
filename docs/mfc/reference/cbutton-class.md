---
description: '자세히 알아보기: CButton 클래스'
title: CButton 클래스
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: af7b9bec8298942bcb414e83be24257dd62652cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122579"
---
# <a name="cbutton-class"></a>CButton 클래스

Windows 단추 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CButton : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CButton:: CButton](#cbutton)|`CButton` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CButton:: Create](#create)|Windows 단추 컨트롤을 만들고이를 개체에 연결 `CButton` 합니다.|
|[CButton::D rawItem](#drawitem)|소유자가 그린 개체를 그리려면를 재정의 `CButton` 합니다.|
|[CButton:: GetBitmap](#getbitmap)|[Setbitmap](#setbitmap)을 사용 하 여 이전에 설정한 비트맵의 핸들을 검색 합니다.|
|[CButton::GetButtonStyle](#getbuttonstyle)|Button 컨트롤 스타일에 대 한 정보를 검색 합니다.|
|[CButton:: GetCheck](#getcheck)|Button 컨트롤의 check 상태를 검색 합니다.|
|[CButton:: GetCursor](#getcursor)|[Setcursor](#setcursor)를 사용 하 여 이전에 설정 된 커서 이미지의 핸들을 검색 합니다.|
|[CButton::GetIcon](#geticon)|[Seticon](#seticon)으로 이전에 설정 된 아이콘의 핸들을 검색 합니다.|
|[CButton::GetIdealSize](#getidealsize)|단추 컨트롤의 이상적인 크기를 검색 합니다.|
|[CButton::GetImageList](#getimagelist)|Button 컨트롤의 이미지 목록을 검색 합니다.|
|[CButton:: GetNote](#getnote)|현재 명령 링크 컨트롤의 메모 구성 요소를 검색 합니다.|
|[CButton::GetNoteLength](#getnotelength)|현재 명령 링크 컨트롤에 대 한 메모 텍스트의 길이를 검색 합니다.|
|[CButton::GetSplitGlyph](#getsplitglyph)|현재 분할 단추 컨트롤과 연결 된 문자 모양을 검색 합니다.|
|[CButton:: GetSplitImageList](#getsplitimagelist)|현재 분할 단추 컨트롤의 이미지 목록을 검색 합니다.|
|[CButton:: GetSplitInfo](#getsplitinfo)|현재 분할 단추 컨트롤을 정의 하는 정보를 검색 합니다.|
|[CButton::GetSplitSize](#getsplitsize)|현재 분할 단추 컨트롤의 드롭다운 구성 요소에 대 한 경계 사각형을 검색 합니다.|
|[CButton::GetSplitStyle](#getsplitstyle)|현재 분할 단추 컨트롤을 정의 하는 분할 단추 스타일을 검색 합니다.|
|[CButton:: GetState](#getstate)|단추 컨트롤의 확인 상태, 강조 표시 상태 및 포커스 상태를 검색 합니다.|
|[CButton::GetTextMargin](#gettextmargin)|Button 컨트롤의 텍스트 여백을 검색 합니다.|
|[CButton::SetBitmap](#setbitmap)|단추에 표시할 비트맵을 지정 합니다.|
|[CButton:: SetButtonStyle](#setbuttonstyle)|단추의 스타일을 변경 합니다.|
|[CButton:: SetCheck](#setcheck)|단추 컨트롤의 확인 상태를 설정 합니다.|
|[CButton:: SetCursor](#setcursor)|단추에 표시할 커서 이미지를 지정 합니다.|
|[CButton:: SetDropDownState](#setdropdownstate)|현재 분할 단추 컨트롤의 드롭다운 상태를 설정 합니다.|
|[CButton:: SetIcon](#seticon)|단추에 표시 되는 아이콘을 지정 합니다.|
|[CButton:: Seon Agelist](#setimagelist)|단추 컨트롤의 이미지 목록을 설정 합니다.|
|[CButton:: SetNote](#setnote)|현재 명령 링크 컨트롤에 대 한 메모를 설정 합니다.|
|[CButton:: SetSplitGlyph](#setsplitglyph)|지정 된 문자 모양을 현재 분할 단추 컨트롤과 연결 합니다.|
|[CButton:: SetSplitImageList](#setsplitimagelist)|현재 분할 단추 컨트롤에 이미지 목록을 연결 합니다.|
|[CButton:: SetSplitInfo](#setsplitinfo)|현재 분할 단추 컨트롤을 정의 하는 정보를 지정 합니다.|
|[CButton:: SetSplitSize](#setsplitsize)|현재 분할 단추 컨트롤의 드롭다운 구성 요소에 대 한 경계 사각형을 설정 합니다.|
|[CButton:: SetSplitStyle](#setsplitstyle)|현재 분할 단추 컨트롤의 스타일을 설정 합니다.|
|[CButton:: SetState](#setstate)|단추 컨트롤의 강조 표시 상태를 설정 합니다.|
|[CButton:: SetTextMargin](#settextmargin)|Button 컨트롤의 텍스트 여백을 설정 합니다.|

## <a name="remarks"></a>설명

단추 컨트롤은 클릭 하 고 끌 수 있는 작은 사각형 자식 창입니다. 단추는 단독으로 또는 그룹에서 사용할 수 있으며, 텍스트 없이 표시 되거나 표시 될 수 있습니다. 사용자가 단추를 클릭 하면 일반적으로 모양이 변경 됩니다.

일반적인 단추는 확인란, 라디오 단추 및 누름 단추입니다. `CButton`개체는 [Create](#create) member 함수에 의해 초기화 될 때 지정 된 [단추 스타일](../../mfc/reference/styles-used-by-mfc.md#button-styles) 에 따라 이러한 개체의 일부가 될 수 있습니다.

또한에서 파생 된 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) 클래스는 `CButton` 텍스트 대신 비트맵 이미지를 사용 하 여 레이블이 지정 된 단추 컨트롤의 생성을 지원 합니다. 에는 `CBitmapButton` 단추의 위쪽, 아래쪽, 포커스 및 비활성 상태에 대해 별도의 비트맵이 있을 수 있습니다.

대화 상자 템플릿에서 또는 코드에서 직접 단추 컨트롤을 만들 수 있습니다. 두 경우 모두, 먼저 생성자를 호출 `CButton` 하 여 개체를 생성 `CButton` 한 다음 `Create` 멤버 함수를 호출 하 여 Windows 단추 컨트롤을 만들고이를 개체에 연결 `CButton` 합니다.

생성은에서 파생 된 클래스의 단일 단계 프로세스가 될 수 있습니다 `CButton` . 파생 클래스에 대 한 생성자를 작성 하 고 `Create` 생성자 내에서를 호출 합니다.

단추 컨트롤에서 부모 (일반적으로 [CDialog](../../mfc/reference/cdialog-class.md)에서 파생 된 클래스)로 보낸 Windows 알림 메시지를 처리 하려면 각 메시지의 부모 클래스에 메시지 매핑 항목 및 메시지 처리기 멤버 함수를 추가 합니다.

각 메시지 맵 항목은 다음 형식을 사용 합니다.

**설정 \_** _알림_ **(** _id_, _memberFxn_ **)**

여기서 *id* 는 알림을 보내는 컨트롤의 자식 창 id를 지정 하 고 *memberFxn* 는 알림을 처리 하기 위해 작성 한 부모 멤버 함수의 이름입니다.

부모의 함수 프로토타입은 다음과 같습니다.

`afx_msg void memberFxn();`

잠재적 메시지 맵 항목은 다음과 같습니다.

|맵 항목|다음 경우 부모로 전송 ...|
|---------------|----------------------------|
|ON_BN_CLICKED|사용자가 단추를 클릭 합니다.|
|ON_BN_DOUBLECLICKED|사용자가 단추를 두 번 클릭 합니다.|

`CButton`대화 상자 리소스에서 개체를 만드는 경우 `CButton` 사용자가 대화 상자를 닫으면 개체가 자동으로 소멸 됩니다.

`CButton`창 내에서 개체를 만드는 경우 해당 개체를 삭제 해야 할 수 있습니다. `CButton`함수를 사용 하 여 힙에서 개체를 만드는 경우 **`new`** **`delete`** 사용자가 Windows 단추 컨트롤을 닫을 때 개체에 대해를 호출 하 여 개체를 제거 해야 합니다. 스택에서 개체를 만들거나 `CButton` 부모 대화 상자 개체에 포함 하는 경우 자동으로 삭제 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a> CButton:: CButton

`CButton` 개체를 생성합니다.

```
CButton();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a> CButton:: Create

Windows 단추 컨트롤을 만들고이를 개체에 연결 `CButton` 합니다.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*lpszCaption*<br/>
단추 컨트롤의 텍스트를 지정 합니다.

*dwStyle*<br/>
Button 컨트롤의 스타일을 지정 합니다. 단추 [스타일](../../mfc/reference/styles-used-by-mfc.md#button-styles) 의 조합을 단추에 적용 합니다.

*rect*<br/>
단추 컨트롤의 크기와 위치를 지정 합니다. 개체 또는 구조 중 하나일 수 있습니다 `CRect` `RECT` .

*pParentWnd*<br/>
단추 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
단추 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CButton`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` Windows 단추 컨트롤을 만들고이를 개체에 연결 `CButton` 합니다.

WS_VISIBLE 스타일이 지정 된 경우 Windows는 단추를 활성화 하는 데 필요한 모든 메시지를 단추 컨트롤에 전송 하 고 단추를 표시 합니다.

Button 컨트롤에 다음 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 을 적용 합니다.

- 항상 WS_CHILD

- WS_VISIBLE 일반적으로

- WS_DISABLED 거의 없음

- 컨트롤을 그룹화 WS_GROUP

- 탭 순서 대로 단추를 포함 하려면 WS_TABSTOP 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a> CButton::D rawItem

소유자가 그린 단추의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
[Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 긴 포인터입니다. 구조체에는 그릴 항목에 대 한 정보와 필요한 그리기 형식이 포함 되어 있습니다.

### <a name="remarks"></a>설명

소유자가 그린 단추에 BS_OWNERDRAW 스타일이 설정 되어 있습니다. 소유자가 그린 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CButton` 합니다. 응용 프로그램은 멤버 함수가 종료 되기 전에 *Lpdrawitemstruct* 에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

또한 [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) 스타일 값을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a> CButton:: GetBitmap

이 멤버 함수를 호출 하 여 단추와 연결 된 이전에 [Setbitmap](#setbitmap)으로 설정 된 비트맵의 핸들을 가져옵니다.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>반환 값

비트맵에 대 한 핸들입니다. 이전에 비트맵을 지정 하지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a> CButton:: GetButtonStyle

Button 컨트롤 스타일에 대 한 정보를 검색 합니다.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>반환 값

이 개체의 단추 스타일을 반환 합니다 `CButton` . 이 함수는 다른 창 스타일이 아닌 [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) 스타일 값만 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a> CButton:: GetCheck

라디오 단추 또는 확인란의 확인 상태를 검색 합니다.

```
int GetCheck() const;
```

### <a name="return-value"></a>반환 값

BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON 또는 BS_3STATE 스타일을 사용 하 여 만든 단추 컨트롤의 반환 값은 다음 값 중 하나입니다.

|값|의미|
|-----------|-------------|
|BST_UNCHECKED|단추 상태가 선택 취소 되어 있습니다.|
|BST_CHECKED|단추 상태가 선택 됨입니다.|
|BST_INDETERMINATE|단추 상태가 결정 되지 않음 (단추가 BS_3STATE 또는 BS_AUTO3STATE 스타일) 인 경우에만 적용 됩니다.|

단추에 다른 스타일이 있는 경우 반환 값은 BST_UNCHECKED입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a> CButton:: GetCursor

이 멤버 함수를 호출 하 여 단추와 연결 된 이전에 [Setcursor](#setcursor)로 설정 된 커서의 핸들을 가져옵니다.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>반환 값

커서 이미지에 대 한 핸들입니다. 이전에 커서가 지정 되지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a> CButton:: GetIcon

이 멤버 함수를 호출 하 여 단추와 연결 된 이전에 [Seticon](#seticon)으로 설정 된 아이콘의 핸들을 가져옵니다.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>반환 값

아이콘에 대한 핸들입니다. 이전에 아이콘이 지정 되지 않은 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a> CButton:: GetIdealSize

단추 컨트롤의 이상적인 크기를 검색 합니다.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>매개 변수

*psize*<br/>
단추의 현재 크기에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK의 [Buttons](/windows/win32/controls/buttons) 섹션에 설명 된 대로 BCM_GETIDEALSIZE 메시지의 기능을 에뮬레이트합니다.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a> CButton:: GetImageList

Button 컨트롤에서 이미지 목록을 가져오려면이 메서드를 호출 합니다.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>매개 변수

*pbuttonImagelist*<br/>
개체의 이미지 목록에 대 한 포인터 `CButton` 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK의 [Buttons](/windows/win32/controls/buttons) 섹션에 설명 된 대로 BCM_GETIMAGELIST 메시지의 기능을 에뮬레이트합니다.

## <a name="cbuttongetnote"></a><a name="getnote"></a> CButton:: GetNote

현재 명령 링크 컨트롤과 연결 된 메모 텍스트를 검색 합니다.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>매개 변수

*lpszNote*\
제한이 호출자가 할당 및 할당 취소를 담당 하는 버퍼에 대 한 포인터입니다. 반환 값이 TRUE 이면 버퍼에는 현재 명령 링크 컨트롤과 연결 된 메모 텍스트가 포함 됩니다. 그렇지 않으면 버퍼는 변경 되지 않습니다.

*cchNote*\
[in, out] 부호 없는 정수 변수에 대 한 포인터입니다. 이 메서드가 호출 되 면 변수는 *lpszNote* 매개 변수로 지정 된 버퍼의 크기를 포함 합니다. 이 메서드가 반환 될 때 반환 값이 TRUE 이면 변수는 현재 명령 링크 컨트롤과 연결 된 메모의 크기를 포함 합니다. 반환 값이 FALSE 이면 변수는 메모를 포함 하는 데 필요한 버퍼 크기를 포함 합니다.

### <a name="return-value"></a>반환 값

첫 번째 오버 로드에서 현재 명령 링크 컨트롤과 연결 된 메모 텍스트를 포함 하는 [CString](../../atl-mfc-shared/using-cstring.md) 개체입니다.

또는

두 번째 오버 로드에서이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_COMMANDLINK 또는 BS_DEFCOMMANDLINK 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 Windows SDK에서 설명 하는 [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) 메시지를 보냅니다.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a> CButton:: GetNoteLength

현재 명령 링크 컨트롤에 대 한 메모 텍스트의 길이를 검색 합니다.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>반환 값

현재 명령 링크 컨트롤에 대 한 메모 텍스트의 길이 (16 비트 유니코드 문자)입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_COMMANDLINK 또는 BS_DEFCOMMANDLINK 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 Windows SDK에서 설명 하는 [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) 메시지를 보냅니다.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a> CButton:: GetSplitGlyph

현재 분할 단추 컨트롤과 연결 된 문자 모양을 검색 합니다.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>반환 값

현재 분할 단추 컨트롤과 연결 된 문자 모양 문자입니다.

### <a name="remarks"></a>설명

문자 모양은 특정 글꼴의 문자를 물리적으로 표현한 것입니다. 예를 들어 분할 단추 컨트롤은 유니코드 확인 표시 문자 (U + 2713)의 문자 모양으로 데코레이팅 될 수 있습니다.

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 `mask` BCSIF_GLYPH 플래그를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 메시지 함수가 반환 될 때이 메서드는 구조체의 멤버에서 문자 모양을 검색 `himlGlyph` 합니다.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a> CButton:: GetSplitImageList

현재 분할 단추 컨트롤의 [이미지 목록을](../../mfc/reference/cimagelist-class.md) 검색 합니다.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>반환 값

[CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 `mask` BCSIF_IMAGE 플래그를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 메시지 함수가 반환 될 때이 메서드는 구조체의 멤버에서 이미지 목록을 검색 합니다 `himlGlyph` .

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a> CButton:: GetSplitInfo

Windows에서 현재 분할 단추 컨트롤을 그리는 방법을 결정 하는 매개 변수를 검색 합니다.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>매개 변수

*pInfo*\
제한이 현재 분할 단추 컨트롤에 대 한 정보를 수신 하는 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체에 대 한 포인터입니다. 호출자는 구조체를 할당 해야 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 Windows SDK에서 설명 하는 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지를 보냅니다.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a> CButton:: GetSplitSize

현재 분할 단추 컨트롤의 드롭다운 구성 요소에 대 한 경계 사각형을 검색 합니다.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>매개 변수

*pSize*\
제한이 사각형에 대 한 설명을 받는 [크기](/windows/win32/api/windef/ns-windef-size) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

분할 단추 컨트롤이 확장 되 면 목록 컨트롤이 나 페이저 컨트롤과 같은 드롭다운 구성 요소를 표시할 수 있습니다. 이 메서드는 드롭다운 구성 요소를 포함 하는 경계 사각형을 검색 합니다.

이 메서드는 `mask` BCSIF_SIZE 플래그를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 메시지 함수가 반환 될 때이 메서드는 구조체의 멤버에서 경계 사각형을 검색 `size` 합니다.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a> CButton:: GetSplitStyle

현재 분할 단추 컨트롤을 정의 하는 분할 단추 스타일을 검색 합니다.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>반환 값

분할 단추 스타일의 비트 조합입니다. 자세한 내용은 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 참조 하십시오.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

분할 단추 스타일은 창에 분할 단추 아이콘이 그려지는 맞춤, 가로 세로 비율 및 그래픽 형식을 지정 합니다.

이 메서드는 `mask` BCSIF_STYLE 플래그를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 메시지 함수가 반환 될 때이 메서드는 구조체의 멤버에서 분할 단추 스타일을 검색 `uSplitStyle` 합니다.

## <a name="cbuttongetstate"></a><a name="getstate"></a> CButton:: GetState

Button 컨트롤의 상태를 검색 합니다.

```
UINT GetState() const;
```

### <a name="return-value"></a>반환 값

단추 컨트롤의 현재 상태를 나타내는 값의 조합을 포함 하는 비트 필드입니다. 다음 표에서는 가능한 값을 나열 합니다.

|단추 상태|값|설명|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|초기 상태입니다.|
|BST_CHECKED|0x0001|단추 컨트롤이 선택 됩니다.|
|BST_INDETERMINATE|0x0002|상태는 결정 되지 않음 (단추 컨트롤에 세 개의 상태가 있는 경우에만 가능)입니다.|
|BST_PUSHED|0x0004|단추 컨트롤이 눌러져 있습니다.|
|BST_FOCUS|0x0008|단추 컨트롤에 포커스가 있습니다.|

### <a name="remarks"></a>설명

BS_3STATE 또는 BS_AUTO3STATE 단추 스타일을 사용 하는 단추 컨트롤은 확정 되지 않은 상태의 세 번째 상태 라는 확인란을 만듭니다. 확정 되지 않은 상태는 확인란이 선택 되지 않았거나 선택 취소 되지 않았음을 나타냅니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a> CButton:: GetTextMargin

개체의 텍스트 여백을 가져오려면이 메서드를 호출 `CButton` 합니다.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>매개 변수

*pmargin*<br/>
개체의 텍스트 여백에 대 한 포인터 `CButton` 입니다.

### <a name="return-value"></a>반환 값

텍스트 여백을 반환 합니다.

### <a name="remarks"></a>설명

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK의 [Buttons](/windows/win32/controls/buttons) 섹션에 설명 된 대로 BCM_GETTEXTMARGIN 메시지의 기능을 에뮬레이트합니다.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a> CButton:: SetBitmap

이 멤버 함수를 호출 하 여 새 비트맵과 단추를 연결 합니다.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>매개 변수

*hBitmap*<br/>
비트맵 핸들입니다.

### <a name="return-value"></a>반환 값

단추와 이전에 연결 된 비트맵의 핸들입니다.

### <a name="remarks"></a>설명

비트맵은 기본적으로 가운데 맞춤 된 단추의 표면에 자동으로 배치 됩니다. 비트맵이 너무 커서 단추를 사용할 수 없는 경우 양쪽에 클리핑 됩니다. 다음을 포함 하 여 다른 맞춤 옵션을 선택할 수 있습니다.

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

단추 당 4 개의 비트맵을 사용하는 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)와 달리 `SetBitmap`에서는 단추 당 하나의 비트맵만 사용합니다. 단추를 누르면 비트맵이 오른쪽 아래로 이동 하는 것 처럼 보입니다.

사용자가 작업을 완료 하면 비트맵을 해제 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a> CButton:: SetButtonStyle

단추의 스타일을 변경 합니다.

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*nStyle*<br/>
[단추 스타일](../../mfc/reference/styles-used-by-mfc.md#button-styles)을 지정 합니다.

*bRedraw*<br/>
단추를 다시 그릴지 여부를 지정 합니다. 0이 아닌 값은 단추를 다시 그립니다. 0 값은 단추를 다시 그려지지 않습니다. 기본적으로 단추가 다시 그려집니다.

### <a name="remarks"></a>설명

`GetButtonStyle`멤버 함수를 사용 하 여 단추 스타일을 검색 합니다. 전체 단추 스타일의 하위 단어는 단추와 관련 된 스타일입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a> CButton:: SetCheck

라디오 단추 또는 확인란의 확인 상태를 설정 하거나 다시 설정 합니다.

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>매개 변수

*nCheck*<br/>
확인 상태를 지정 합니다. 이 매개 변수는 다음 중 하나일 수 있습니다.

|값|의미|
|-----------|-------------|
|BST_UNCHECKED|단추 상태를 선택 취소 됨으로 설정 합니다.|
|BST_CHECKED|단추 상태를 선택 됨으로 설정 합니다.|
|BST_INDETERMINATE|단추 상태를 미정으로 설정 합니다. 이 값은 단추에 BS_3STATE 또는 BS_AUTO3STATE 스타일이 있는 경우에만 사용할 수 있습니다.|

### <a name="remarks"></a>설명

이 멤버 함수는 누름 단추에는 영향을 주지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a> CButton:: SetCursor

새 커서를 단추와 연결 하려면이 멤버 함수를 호출 합니다.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>매개 변수

*hCursor*<br/>
커서의 핸들입니다.

### <a name="return-value"></a>반환 값

단추와 이전에 연결 된 커서의 핸들입니다.

### <a name="remarks"></a>설명

커서는 기본적으로 가운데에 있는 단추의 표면에 자동으로 배치 됩니다. 커서가 너무 커서 단추를 사용할 수 없는 경우 양쪽에서 잘립니다. 다음을 포함 하 여 다른 맞춤 옵션을 선택할 수 있습니다.

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

단추 당 4 개의 비트맵을 사용하는 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)와 달리 `SetCursor`는 단추 마다 하나의 커서만 사용합니다. 단추를 누르면 커서가 아래쪽 및 오른쪽으로 이동 하는 것으로 나타납니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a> CButton:: SetDropDownState

현재 분할 단추 컨트롤의 드롭다운 상태를 설정 합니다.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>매개 변수

*fDropDown*\
진행 BST_DROPDOWNPUSHED 상태를 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

분할 단추 컨트롤은 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 스타일을 가지 며 단추와 오른쪽 드롭다운 화살표로 구성 됩니다. 자세한 내용은 [단추 스타일](/windows/win32/Controls/button-styles)을 참조 하세요. 일반적으로 드롭다운 상태는 사용자가 드롭다운 화살표를 클릭할 때 설정 됩니다. 컨트롤의 드롭다운 상태를 프로그래밍 방식으로 설정 하려면이 메서드를 사용 합니다. 드롭다운 화살표가 상태를 나타내기 위해 음영으로 그려집니다.

이 메서드는 Windows SDK에서 설명 하는 [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 분할 단추 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_splitButton* 를 정의 합니다. 이 변수는 다음 예제에서 사용 됩니다.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 분할 단추 컨트롤의 상태를 설정 하 여 드롭다운 화살표가 푸시 되었음을 표시 합니다.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a> CButton:: SetElevationRequired

`elevation required`컨트롤이 상승 된 보안 아이콘을 표시 하는 데 필요한 현재 단추 컨트롤의 상태를로 설정 합니다.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>매개 변수

*fElevationRequired*\
진행 상태를 설정 하려면 TRUE `elevation required` 이 고, 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 또는 명령 링크 컨트롤에서 작업을 수행 하는 데 상승 된 보안 권한이 필요한 경우 컨트롤을 `elevation required` state로 설정 합니다. 그런 다음 Windows에서 컨트롤에 UAC (사용자 계정 컨트롤) 방패 아이콘을 표시 합니다. 자세한 내용은 [사용자 계정 컨트롤](/windows/win32/uxguide/winenv-uac)을 참조하십시오.

이 메서드는 Windows SDK에서 설명 하는 [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) 메시지를 보냅니다.

## <a name="cbuttonseticon"></a><a name="seticon"></a> CButton:: SetIcon

새 아이콘을 단추와 연결 하려면이 멤버 함수를 호출 합니다.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>매개 변수

*hIcon*<br/>
아이콘 핸들입니다.

### <a name="return-value"></a>반환 값

단추와 이전에 연결 된 아이콘 핸들입니다.

### <a name="remarks"></a>설명

아이콘은 기본적으로 가운데 맞춤 된 단추 모양에 자동으로 배치 됩니다. 단추에 대 한 아이콘이 너무 크면 한쪽에 클리핑 됩니다. 다음을 포함 하 여 다른 맞춤 옵션을 선택할 수 있습니다.

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

단추 당 4 개의 비트맵을 사용하는 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)와 달리 `SetIcon`에서는 단추 당 하나의 아이콘만 사용합니다. 단추를 누르면 아이콘이 오른쪽 아래로 이동 하는 것으로 나타납니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a> CButton:: Seon Agelist

개체의 이미지 목록을 설정 하려면이 메서드를 호출 `CButton` 합니다.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>매개 변수

*pbuttonImagelist*<br/>
새 이미지 목록에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK의 [Buttons](/windows/win32/controls/buttons) 섹션에 설명 된 대로 BCM_SETIMAGELIST 메시지의 기능을 에뮬레이트합니다.

## <a name="cbuttonsetnote"></a><a name="setnote"></a> CButton:: SetNote

현재 명령 링크 컨트롤에 대 한 메모 텍스트를 설정 합니다.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>매개 변수

*lpszNote*\
진행 명령 링크 컨트롤에 대 한 메모 텍스트로 설정 된 유니코드 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_COMMANDLINK 또는 BS_DEFCOMMANDLINK 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 Windows SDK에서 설명 하는 [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 명령 링크 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_cmdLink* 를 정의 합니다. 이 변수는 다음 예제에서 사용 됩니다.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 명령 링크 컨트롤에 대 한 메모 텍스트를 설정 합니다.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a> CButton:: SetSplitGlyph

지정 된 문자 모양을 현재 분할 단추 컨트롤과 연결 합니다.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>매개 변수

*chGlyph*\
진행 분할 단추 드롭다운 화살표로 사용할 문자 모양을 지정 하는 문자입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 있는 컨트롤에만이 메서드를 사용 합니다.

문자 모양은 특정 글꼴의 문자를 물리적으로 표현한 것입니다. *Chglyph* 매개 변수는 문자 모양으로 사용 되지 않지만 시스템 정의 문자 모양 집합에서 문자 모양을 선택 하는 데 대신 사용 됩니다. 기본 드롭다운 화살표 문자 모양은 문자 ' 6 '으로 지정 되 고 유니코드 문자 검정색 아래쪽 삼각형 (U + 25BC)과 유사 합니다.

이 메서드는 `mask` BCSIF_GLYPH 플래그와 Chglyph 매개 변수가 있는 멤버를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 `himlGlyph` 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a> CButton:: SetSplitImageList

현재 분할 단추 컨트롤에 [이미지 목록을](../../mfc/reference/cimagelist-class.md) 연결 합니다.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>매개 변수

*pSplitImageList*\
진행 현재 분할 단추 컨트롤에 할당할 [CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 `mask` BCSIF_IMAGE 플래그와 pSplitImageList 매개 변수를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 `himlGlyph` 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a> CButton:: SetSplitInfo

Windows에서 현재 분할 단추 컨트롤을 그리는 방법을 결정 하는 매개 변수를 지정 합니다.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>매개 변수

*pInfo*\
진행 현재 분할 단추 컨트롤을 정의 하는 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

이 메서드는 Windows SDK에서 설명 하는 [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_splitButton` 분할 단추 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수를 정의 합니다.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 분할 단추 드롭다운 화살표에 사용 되는 문자 모양을 변경 합니다. 이 예제에서는 기본 아래쪽 삼각형 문자 모양에 대 한 위쪽 삼각형 문자 모양을 대체 합니다. 표시 되는 문자 모양은 구조체의 멤버에서 지정 하는 문자에 따라 달라 집니다 `himlGlyph` `BUTTON_SPLITINFO` . 아래쪽을 가리키는 삼각형 문자 모양은 문자 ' 6 '으로 지정 되 고 위쪽 삼각형 문자 모양은 문자 ' 5 '로 지정 됩니다. 비교를 위해 편의 메서드 [Cbutton:: SetSplitGlyph](#setsplitglyph)를 참조 하세요.

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a> CButton:: SetSplitSize

현재 분할 단추 컨트롤의 드롭다운 구성 요소에 대 한 경계 사각형을 설정 합니다.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>매개 변수

*pSize*\
진행 경계 사각형을 설명 하는 [크기](/windows/win32/api/windef/ns-windef-size) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

분할 단추 컨트롤이 확장 되 면 목록 컨트롤이 나 페이저 컨트롤과 같은 드롭다운 구성 요소를 표시할 수 있습니다. 이 메서드는 드롭다운 구성 요소를 포함 하는 경계 사각형의 크기를 지정 합니다.

이 메서드는 `mask` BCSIF_SIZE 플래그와 Psize 매개 변수를 사용 하는 멤버를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 `size` 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 

### <a name="example"></a>예제

다음 코드 예제에서는 `m_splitButton` 분할 단추 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용 됩니다.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 분할 단추 드롭다운 화살표의 크기를 두 배로 만듭니다.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a> CButton:: SetSplitStyle

현재 분할 단추 컨트롤의 스타일을 설정 합니다.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>매개 변수

*uSplitStyle*\
진행 분할 단추 스타일의 비트 조합입니다. 자세한 내용은 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 참조 하십시오.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추 스타일이 BS_SPLITBUTTON 또는 BS_DEFSPLITBUTTON 된 컨트롤에만이 메서드를 사용 합니다.

분할 단추 스타일은 창에 분할 단추 아이콘이 그려지는 맞춤, 가로 세로 비율 및 그래픽 형식을 지정 합니다. 자세한 내용은 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 참조 하십시오.

이 메서드는 `mask` BCSIF_STYLE 플래그 및 Usplitstyle 매개 변수를 사용 하는 멤버를 사용 하 여 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 구조체의 멤버를 초기화 한 `uSplitStyle` 다음 Windows SDK에 설명 된 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 메시지에 해당 구조체를 보냅니다. 

### <a name="example"></a>예제

다음 코드 예제에서는 `m_splitButton` 분할 단추 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수를 정의 합니다.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 분할 단추 드롭다운 화살표의 스타일을 설정 합니다. BCSS_ALIGNLEFT 스타일은 단추의 왼쪽에 화살표를 표시 하 고, BCSS_STRETCH 스타일은 단추의 크기를 조정할 때 드롭다운 화살표의 비율을 유지 합니다.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a> CButton:: SetState

단추 컨트롤이 강조 표시 되는지 여부를 설정 합니다.

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>매개 변수

*bHighlight*<br/>
단추를 강조 표시할지 여부를 지정 합니다. 0이 아닌 값은 단추를 강조 표시 합니다. 0 값은 강조 표시를 제거 합니다.

### <a name="remarks"></a>설명

강조 표시는 단추 컨트롤의 외부에 영향을 줍니다. 라디오 단추 또는 확인란의 선택 상태에는 영향을 주지 않습니다.

단추 컨트롤은 사용자가 마우스 왼쪽 단추를 클릭 하면 자동으로 강조 표시 됩니다. 사용자가 마우스 단추를 놓으면 강조 표시가 제거 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a> CButton:: SetTextMargin

개체의 텍스트 여백을 설정 하려면이 메서드를 호출 `CButton` 합니다.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>매개 변수

*pmargin*<br/>
새 텍스트 여백에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK의 [Buttons](/windows/win32/controls/buttons) 섹션에 설명 된 대로 BCM_SETTEXTMARGIN 메시지의 기능을 에뮬레이트합니다.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox 클래스](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)<br/>
[CListBox 클래스](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 클래스](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 클래스](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton 클래스](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)
