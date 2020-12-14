---
description: '자세히 알아보기: CEdit 클래스'
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 8dbf5ffd05473720682703a9f309f8483591f143
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184688"
---
# <a name="cedit-class"></a>CEdit Class

Windows 편집 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CEdit : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CEdit:: CEdit](#cedit)|`CEdit`컨트롤 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CEdit:: CanUndo](#canundo)|편집 제어 작업을 실행 취소할 수 있는지 여부를 결정 합니다.|
|[CEdit:: CharFromPos](#charfrompos)|지정 된 위치에 가장 가까운 문자에 대 한 줄 및 문자 인덱스를 검색 합니다.|
|[CEdit:: Clear](#clear)|편집 컨트롤에서 현재 선택 영역 (있는 경우)을 삭제 (선택 취소) 합니다.|
|[CEdit:: Copy](#copy)|편집 컨트롤의 현재 선택 항목 (있는 경우)을 CF_TEXT 형식으로 클립보드에 복사 합니다.|
|[CEdit:: Create](#create)|Windows 편집 컨트롤을 만들고 개체에 연결 `CEdit` 합니다.|
|[CEdit:: Cut](#cut)|편집 컨트롤에서 현재 선택 영역 (있는 경우)을 삭제 (잘라내기) 하 고 삭제 된 텍스트를 클립보드에 CF_TEXT 형식으로 복사 합니다.|
|[CEdit:: EmptyUndoBuffer](#emptyundobuffer)|편집 컨트롤의 실행 취소 플래그를 다시 설정 (지우기) 합니다.|
|[CEdit:: FmtLines](#fmtlines)|여러 줄 편집 컨트롤에서 소프트 줄 바꿈 문자를 설정 하거나 해제 하는 기능을 설정 합니다.|
|[CEdit:: GetCueBanner](#getcuebanner)|컨트롤이 비어 있고 포커스가 없는 경우 편집 컨트롤에서 텍스트 큐 또는 팁으로 표시 되는 텍스트를 검색 합니다.|
|[CEdit:: GetFirstVisibleLine](#getfirstvisibleline)|편집 컨트롤에서 맨 위에 표시 되는 줄을 결정 합니다.|
|[CEdit:: GetHandle](#gethandle)|여러 줄 편집 컨트롤에 대해 현재 할당 된 메모리에 대 한 핸들을 검색 합니다.|
|[CEdit:: GetHighlight](#gethighlight)|현재 편집 컨트롤에 강조 표시 된 텍스트 범위에서 시작 및 끝 문자의 인덱스를 가져옵니다.|
|[CEdit:: Get 텍스트](#getlimittext)|이에 포함 될 수 있는 최대 텍스트 크기를 가져옵니다 `CEdit` .|
|[CEdit:: GetLine](#getline)|편집 컨트롤에서 텍스트 줄을 검색 합니다.|
|[CEdit:: GetLineCount](#getlinecount)|여러 줄 편집 컨트롤의 줄 수를 검색 합니다.|
|[CEdit:: GetMargins](#getmargins)|이의 왼쪽 및 오른쪽 여백을 가져옵니다 `CEdit` .|
|[CEdit:: GetModify](#getmodify)|편집 컨트롤의 내용이 수정 되었는지 여부를 확인 합니다.|
|[CEdit:: GetPasswordChar](#getpasswordchar)|사용자가 텍스트를 입력할 때 편집 컨트롤에 표시 되는 암호 문자를 검색 합니다.|
|[CEdit:: GetRect](#getrect)|편집 컨트롤의 서식 지정 사각형을 가져옵니다.|
|[CEdit:: GetSel](#getsel)|편집 컨트롤에서 현재 선택 영역에 대 한 첫 번째 및 마지막 문자 위치를 가져옵니다.|
|[CEdit:: HideBalloonTip](#hideballoontip)|현재 편집 컨트롤과 연결 된 풍선 팁을 숨깁니다.|
|[CEdit:: 텍스트](#limittext)|사용자가 편집 컨트롤에 입력할 수 있는 텍스트의 길이를 제한 합니다.|
|[CEdit:: LineFromChar](#linefromchar)|지정 된 문자 인덱스를 포함 하는 줄의 줄 번호를 검색 합니다.|
|[CEdit:: LineIndex](#lineindex)|여러 줄 편집 컨트롤에서 줄의 문자 인덱스를 검색 합니다.|
|[CEdit:: LineLength](#linelength)|편집 컨트롤에서 줄의 길이를 검색 합니다.|
|[CEdit:: LineScroll](#linescroll)|여러 줄 편집 컨트롤의 텍스트를 스크롤합니다.|
|[CEdit::P aste](#paste)|클립보드의 데이터를 편집 컨트롤의 현재 커서 위치에 삽입 합니다. 클립보드에 CF_TEXT 형식의 데이터가 포함 되어 있는 경우에만 데이터가 삽입 됩니다.|
|[CEdit::P osFromChar](#posfromchar)|지정 된 문자 인덱스의 왼쪽 위 모퉁이의 좌표를 검색 합니다.|
|[CEdit:: ReplaceSel](#replacesel)|편집 컨트롤의 현재 선택 영역을 지정 된 텍스트로 바꿉니다.|
|[CEdit:: SetCueBanner](#setcuebanner)|컨트롤이 비어 있고 포커스가 없는 경우 편집 컨트롤에서 텍스트 큐 또는 팁으로 표시 되는 텍스트를 설정 합니다.|
|[CEdit:: SetHandle](#sethandle)|여러 줄 편집 컨트롤에서 사용 되는 로컬 메모리에 대 한 핸들을 설정 합니다.|
|[CEdit:: SetHighlight](#sethighlight)|현재 편집 컨트롤에 표시 되는 텍스트 범위를 강조 표시 합니다.|
|[CEdit:: Set 텍스트](#setlimittext)|이에 포함할 수 있는 최대 텍스트 크기를 설정 `CEdit` 합니다.|
|[CEdit:: SetMargins](#setmargins)|이의 왼쪽 및 오른쪽 여백을 설정 `CEdit` 합니다.|
|[CEdit:: SetModify](#setmodify)|편집 컨트롤에 대 한 수정 플래그를 설정 하거나 취소 합니다.|
|[CEdit:: SetPasswordChar](#setpasswordchar)|사용자가 텍스트를 입력할 때 편집 컨트롤에 표시 되는 암호 문자를 설정 하거나 제거 합니다.|
|[CEdit:: SetReadOnly](#setreadonly)|편집 컨트롤의 읽기 전용 상태를 설정 합니다.|
|[CEdit:: SetRect](#setrect)|여러 줄 편집 컨트롤의 서식 지정 사각형을 설정 하 고 컨트롤을 업데이트 합니다.|
|[CEdit:: SetRectNP](#setrectnp)|컨트롤 창을 다시 그려야 하지 않고 여러 줄 편집 컨트롤의 서식 지정 사각형을 설정 합니다.|
|[CEdit:: SetSel](#setsel)|편집 컨트롤에서 문자 범위를 선택 합니다.|
|[CEdit:: SetTabStops](#settabstops)|여러 줄 편집 컨트롤에서 탭 정지를 설정 합니다.|
|[CEdit:: ShowBalloonTip](#showballoontip)|현재 편집 컨트롤과 연결 된 풍선 설명을 표시 합니다.|
|[CEdit:: Undo](#undo)|마지막 편집 제어 작업을 반대로 바꿉니다.|

## <a name="remarks"></a>설명

편집 컨트롤은 사용자가 텍스트를 입력할 수 있는 사각형 자식 창입니다.

대화 상자 템플릿에서 또는 코드에서 직접 편집 컨트롤을 만들 수 있습니다. 두 경우 모두, 먼저 생성자를 호출 `CEdit` 하 여 개체를 생성 `CEdit` 한 다음 [create](#create) member 함수를 호출 하 여 Windows 편집 컨트롤을 만들고이를 개체에 연결 `CEdit` 합니다.

생성은에서 파생 된 클래스의 단일 단계 프로세스가 될 수 있습니다 `CEdit` . 파생 클래스에 대 한 생성자를 작성 하 고 `Create` 생성자 내에서를 호출 합니다.

`CEdit` 는에서 중요 한 기능을 상속 `CWnd` 합니다. 개체에서 텍스트를 설정 하 고 검색 하려면 `CEdit` `CWnd` 여러 줄을 포함 하는 경우에도 편집 컨트롤의 전체 내용을 설정 하거나 가져오는 멤버 함수 [setwindowtext](cwnd-class.md#setwindowtext) 및 [getwindowtext](cwnd-class.md#getwindowtext)를 사용 합니다. 여러 줄로 된 컨트롤의 텍스트 줄은 ' \r\n ' 문자 시퀀스로 구분 됩니다. 또한 편집 컨트롤이 여러 줄 인 경우에는 `CEdit` [getline](#getline), [setsel](#setsel), [getline](#getsel)및 [ReplaceSel](#replacesel)멤버 함수를 호출 하 여 컨트롤의 텍스트 부분을 가져오고 설정 합니다.

편집 컨트롤에서 해당 부모 (일반적으로에서 파생 된 클래스)로 보낸 Windows 알림 메시지를 처리 하려면 `CDialog` 각 메시지의 부모 클래스에 메시지 매핑 항목과 메시지 처리기 멤버 함수를 추가 합니다.

각 메시지 맵 항목은 다음 형식을 사용 합니다.

  **ON_**_알림_**(** _id_**,** _memberFxn_ **)**

여기서는 `id` 알림을 보내는 편집 컨트롤의 자식 창 ID를 지정 하 고 `memberFxn` 는 알림을 처리 하기 위해 작성 한 부모 멤버 함수의 이름입니다.

부모의 함수 프로토타입은 다음과 같습니다.

**afx_msg** void memberFxn **();**

다음은 잠재적 메시지 맵 항목과 부모 항목으로 전송 되는 사례에 대 한 설명 목록입니다.

- 사용자가 편집 컨트롤에서 텍스트를 변경 했을 수 있는 작업을 수행 ON_EN_CHANGE 합니다. EN_UPDATE 알림 메시지와 달리이 알림 메시지는 Windows에서 디스플레이를 업데이트 한 후에 전송 됩니다.

- ON_EN_ERRSPACE 편집 컨트롤은 특정 요청을 충족 하기에 충분 한 메모리를 할당할 수 없습니다.

- 사용자가 편집 컨트롤의 가로 스크롤 막대를 클릭 ON_EN_HSCROLL 합니다. 화면이 업데이트 되기 전에 부모 창에 알림이 표시 됩니다.

- 편집 컨트롤 ON_EN_KILLFOCUS 입력 포커스가 손실 됩니다.

- ON_EN_MAXTEXT 현재 삽입 내용이 편집 컨트롤에 대해 지정 된 문자 수를 초과 하 여 잘렸습니다. 편집 컨트롤에 ES_AUTOHSCROLL 스타일이 없고 삽입할 문자 수가 편집 컨트롤의 너비를 초과 하는 경우에도 전송 됩니다. 편집 컨트롤에 ES_AUTOVSCROLL 스타일이 없고 텍스트 삽입으로 인해 발생 하는 전체 줄 수가 편집 컨트롤의 높이를 초과 하는 경우에도 전송 됩니다.

- 편집 컨트롤에서 입력 포커스를 받을 때 ON_EN_SETFOCUS 전송 됩니다.

- 편집 컨트롤이 변경 된 텍스트를 표시 하려는 ON_EN_UPDATE입니다. 컨트롤에서 텍스트의 서식을 지정 하 고 텍스트를 화면에 표시 한 후 필요에 따라 창 크기를 변경할 수 있도록 합니다.

- 사용자가 편집 컨트롤의 세로 스크롤 막대를 클릭 ON_EN_VSCROLL 합니다. 화면이 업데이트 되기 전에 부모 창에 알림이 표시 됩니다.

`CEdit`대화 상자 내에서 개체를 만드는 경우 `CEdit` 사용자가 대화 상자를 닫으면 개체가 자동으로 소멸 됩니다.

대화 `CEdit` 상자 편집기를 사용 하 여 대화 상자 리소스에서 개체를 만드는 경우 `CEdit` 사용자가 대화 상자를 닫으면 개체가 자동으로 소멸 됩니다.

`CEdit`창 내에서 개체를 만드는 경우 해당 개체를 삭제 해야 할 수도 있습니다. 스택에서 개체를 만들면 `CEdit` 자동으로 제거 됩니다. `CEdit`함수를 사용 하 여 힙에서 개체를 만드는 경우 **`new`** **`delete`** 사용자가 Windows 편집 컨트롤을 종료할 때 개체에 대해를 호출 하 여 개체를 제거 해야 합니다. 개체에 메모리를 할당 하는 경우 `CEdit` 소멸자를 재정의 `CEdit` 하 여 할당을 삭제 합니다.

편집 컨트롤의 특정 스타일 (예: ES_READONLY)을 수정 하려면 [ModifyStyle](cwnd-class.md#modifystyle)를 사용 하는 대신 특정 메시지를 컨트롤에 보내야 합니다. Windows SDK에서 [컨트롤 스타일 편집](/windows/win32/Controls/edit-control-styles) 을 참조 하세요.

에 대 한 자세한 내용은 `CEdit` [컨트롤](../../mfc/controls-mfc.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a> CEdit:: CanUndo

마지막 편집 작업을 실행 취소할 수 있는지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>반환 값

멤버 함수를 호출 하 여 마지막 편집 작업을 실행 취소할 수 있는 경우 0이 아닌 `Undo` 값이 고, 실행 취소할 수 없으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [EM_CANUNDO](/windows/win32/Controls/em-canundo) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: Undo](#undo)의 예제를 참조 하세요.

## <a name="ceditcedit"></a><a name="cedit"></a> CEdit:: CEdit

`CEdit` 개체를 생성합니다.

```
CEdit();
```

### <a name="remarks"></a>설명

[Create](#create) 를 사용 하 여 Windows 편집 컨트롤을 생성 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a> CEdit:: CharFromPos

이 컨트롤에서 지정 된 지점에 가장 가까운 문자의 0부터 시작 하는 줄 및 문자 인덱스를 검색 하려면이 함수를 호출 합니다. `CEdit`

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
이 개체의 클라이언트 영역에 있는 점의 좌표 `CEdit` 입니다.

### <a name="return-value"></a>반환 값

하위 단어의 문자 인덱스 및 상위 단어의 줄 인덱스입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 이 구성원 함수는 Windows 95 및 Windows NT 4.0부터 사용할 수 있습니다.

자세한 내용은 Windows SDK [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a> CEdit:: Clear

편집 컨트롤에서 현재 선택 영역 (있는 경우)을 삭제 하려면이 함수를 호출 합니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

`Clear` [실행 취소](#undo) 멤버 함수를 호출 하 여에서 수행 하는 삭제 작업을 취소할 수 있습니다.

현재 선택 영역을 삭제 하 고 삭제 된 내용을 클립보드에 배치 하려면 [Cut](#cut) 멤버 함수를 호출 합니다.

자세한 내용은 Windows SDK [WM_CLEAR](/windows/win32/dataxchg/wm-clear) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a> CEdit:: Copy

편집 컨트롤에서 현재 선택 영역 (있는 경우)을 CF_TEXT 형식의 클립보드로 상호 연결 하려면이 함수를 호출 합니다.

```cpp
void Copy();
```

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [WM_COPY](/windows/win32/dataxchg/wm-copy) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a> CEdit:: Create

Windows 편집 컨트롤을 만들고 개체에 연결 `CEdit` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
편집 컨트롤의 스타일을 지정 합니다. [편집 스타일](styles-used-by-mfc.md#edit-styles) 의 조합을 컨트롤에 적용 합니다.

*rect*<br/>
편집 컨트롤의 크기와 위치를 지정 합니다. 는 `CRect` 개체 또는 구조체 일 수 있습니다 `RECT` .

*pParentWnd*<br/>
편집 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
편집 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CEdit`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 `CEdit` 다음을 호출 하 여 `Create` Windows 편집 컨트롤을 만들고이를 개체에 연결 `CEdit` 합니다.

가 `Create` 실행 되 면 Windows는 [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)및 [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) 메시지를 편집 컨트롤로 보냅니다.

이러한 메시지는 기본적으로 기본 클래스의 [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)및 [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) 멤버 함수에 의해 처리 됩니다 `CWnd` . 기본 메시지 처리를 확장 하려면에서 클래스를 파생 시키고 `CEdit` 메시지 맵을 새 클래스에 추가 하 고 위의 메시지 처리기 멤버 함수를 재정의 합니다. 예를 들어를 재정의 하 여 `OnCreate` 새 클래스에 필요한 초기화를 수행 합니다.

다음 [창 스타일](styles-used-by-mfc.md#window-styles) 을 편집 컨트롤에 적용 합니다.

- 항상 WS_CHILD

- WS_VISIBLE 일반적으로

- WS_DISABLED 거의 없음

- 컨트롤을 그룹화 WS_GROUP

- 탭 이동 순서에 편집 컨트롤을 포함 하려면 WS_TABSTOP 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a> CEdit:: Cut

편집 컨트롤에서 현재 선택 영역 (있는 경우)을 삭제 (잘라내기) 하 고 삭제 된 텍스트를 클립보드에 CF_TEXT 형식으로 복사 하려면이 함수를 호출 합니다.

```cpp
void Cut();
```

### <a name="remarks"></a>설명

`Cut` [실행 취소](#undo) 멤버 함수를 호출 하 여에서 수행 하는 삭제 작업을 취소할 수 있습니다.

삭제 된 텍스트를 클립보드에 넣지 않고 현재 선택 영역을 삭제 하려면 [Clear](#clear) 멤버 함수를 호출 합니다.

자세한 내용은 Windows SDK [WM_CUT](/windows/win32/dataxchg/wm-cut) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a> CEdit:: EmptyUndoBuffer

편집 컨트롤의 실행 취소 플래그를 다시 설정 하려면이 함수를 호출 합니다 (clear).

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>설명

이제 edit 컨트롤에서 마지막 작업을 실행 취소할 수 없습니다. Undo 플래그는 편집 컨트롤 내의 작업을 실행 취소할 수 있을 때마다 설정 됩니다.

실행 취소 플래그는 [Setwindowtext](../../mfc/reference/cwnd-class.md#setwindowtext) 또는 [SetHandle](#sethandle) `CWnd` 멤버 함수가 호출 될 때마다 자동으로 지워집니다.

자세한 내용은 Windows SDK [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a> CEdit:: FmtLines

여러 줄 편집 컨트롤 내에서 소프트 줄 바꿈 문자를 설정 하거나 해제 하려면이 함수를 호출 합니다.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>매개 변수

*bAddEOL*<br/>
소프트 줄 바꿈 문자를 삽입할지 여부를 지정 합니다. TRUE 값은 문자를 삽입 합니다. FALSE 값은 해당 값을 제거 합니다.

### <a name="return-value"></a>반환 값

서식 지정이 발생 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

소프트 줄 바꿈은 두 개의 캐리지 리턴과 줄 바꿈이 줄의 끝에 삽입 된 줄 바꿈으로 구성 됩니다. 하드 줄 바꿈은 하나의 캐리지 리턴과 줄 바꿈으로 구성 됩니다. 하드 줄 바꿈으로 끝나는 줄은의 영향을 받지 않습니다 `FmtLines` .

Windows는 `CEdit` 개체가 여러 줄 편집 컨트롤인 경우에만 응답 합니다.

`FmtLines`[GetHandle](#gethandle) 에서 반환 된 버퍼와 [WM_GETTEXT](/windows/win32/winmsg/wm-gettext)에서 반환 되는 텍스트에만 영향을 줍니다. 편집 컨트롤 내의 텍스트 표시에는 영향을 주지 않습니다.

자세한 내용은 Windows SDK [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a> CEdit:: GetCueBanner

컨트롤이 비어 있을 때 편집 컨트롤에서 텍스트 큐 또는 팁으로 표시 되는 텍스트를 검색 합니다.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
제한이 큐 텍스트를 포함 하는 문자열에 대 한 포인터입니다.

*cchText*<br/>
진행 받을 수 있는 문자 수입니다. 이 수는 NULL 종결 문자를 포함 합니다.

### <a name="return-value"></a>반환 값

첫 번째 오버 로드의 경우 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

두 번째 오버 로드의 경우 메서드가 성공 하는 경우 큐 텍스트를 포함 하는 [CString](../../atl-mfc-shared/using-cstring.md) 입니다. 그렇지 않으면 빈 문자열 ("")입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) 메시지를 보냅니다. 자세한 내용은 [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) 매크로를 참조 하세요.

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a> CEdit:: GetFirstVisibleLine

편집 컨트롤에서 표시 되는 맨 위 줄을 확인 하려면이 함수를 호출 합니다.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>반환 값

표시 되는 맨 위 줄의 인덱스 (0부터 시작)입니다. 한 줄 편집 컨트롤의 경우 반환 값은 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a> CEdit:: GetHandle

이 함수를 호출 하 여 여러 줄 편집 컨트롤에 현재 할당 된 메모리에 대 한 핸들을 검색 합니다.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>반환 값

편집 컨트롤의 콘텐츠를 포함 하는 버퍼를 식별 하는 로컬 메모리 핸들입니다. 한 줄 편집 컨트롤에 메시지를 보내는 것과 같은 오류가 발생 하는 경우 반환 값은 0입니다.

### <a name="remarks"></a>설명

핸들은 로컬 메모리 핸들이 고 로컬 메모리 핸들을 매개 변수로 사용 하는 **로컬** Windows 메모리 함수에서 사용 될 수 있습니다.

`GetHandle` 는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

`GetHandle`DS_LOCALEDIT 스타일 플래그 집합을 사용 하 여 대화 상자를 만든 경우에만 대화 상자에서 여러 줄 편집 컨트롤에 대해를 호출 합니다. DS_LOCALEDIT 스타일이 설정 되지 않은 경우에도 0이 아닌 반환 값을 가져오지만 반환 된 값을 사용할 수는 없습니다.

> [!NOTE]
> `GetHandle` Windows 95/98에서는 작동 하지 않습니다. `GetHandle`Windows 95/98에서를 호출 하면 NULL이 반환 됩니다. `GetHandle` 는 Windows NT 버전 3.51 이상에 설명 된 대로 작동 합니다.

자세한 내용은 Windows SDK [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a> CEdit:: GetHighlight

현재 편집 컨트롤에 강조 표시 된 텍스트 범위에 있는 첫 번째 및 마지막 문자의 인덱스를 가져옵니다.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>매개 변수

*그래픽 시작*\
제한이 강조 표시 된 텍스트 범위에 있는 첫 번째 문자의 0부터 시작 하는 인덱스입니다.

*그래픽 끝*\
제한이 강조 표시 된 텍스트 범위에서 마지막 문자의 0부터 시작 하는 인덱스입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [EM_GETHILITE](/windows/win32/Controls/em-gethilite) 메시지를 보냅니다. `SetHighlight`및 `GetHighlight` 는 현재 유니코드 빌드에서만 사용할 수 있습니다.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a> CEdit:: Get 텍스트

이 멤버 함수를 호출 하 여이 개체에 대 한 텍스트 한도를 가져옵니다 `CEdit` .

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>반환 값

이 개체의 현재 텍스트 제한 (TCHARs) `CEdit` 입니다.

### <a name="remarks"></a>설명

텍스트 제한은 편집 컨트롤이 허용할 수 있는 텍스트의 최대 크기 (TCHARs)입니다.

> [!NOTE]
> 이 구성원 함수는 Windows 95 및 Windows NT 4.0부터 사용할 수 있습니다.

자세한 내용은 Windows SDK [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a> CEdit:: GetLine

편집 컨트롤에서 텍스트 줄을 검색 하 고 *lpszbuffer 변수가* 에 배치 하려면이 함수를 호출 합니다.

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
여러 줄 편집 컨트롤에서 검색할 줄 번호를 지정 합니다. 줄 번호는 0부터 시작 합니다. 값 0은 첫 번째 줄을 지정 합니다. 이 매개 변수는 한 줄 편집 컨트롤에서 무시 됩니다.

*lpszBuffer*<br/>
줄의 복사본을 받는 버퍼를 가리킵니다. 버퍼의 첫 번째 단어는 버퍼로 복사할 수 있는 최대 TCHARs 수를 지정 해야 합니다.

*nMaxLength*<br/>
버퍼에 복사할 수 있는 최대 TCHAR.H 문자 수를 지정 합니다. `GetLine` 는 Windows에 대 한 호출을 수행 하기 전에 *lpszbuffer 변수가* 의 첫 번째 단어에이 값을 배치 합니다.

### <a name="return-value"></a>반환 값

실제로 복사된 문자 수입니다. *Nindex* 로 지정 된 줄 번호가 편집 컨트롤의 줄 수보다 큰 경우 반환 값은 0입니다.

### <a name="remarks"></a>설명

복사한 줄에 null 종료 문자가 포함 되어 있지 않습니다.

자세한 내용은 Windows SDK [EM_GETLINE](/windows/win32/Controls/em-getline) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: GetLineCount](#getlinecount)의 예제를 참조 하세요.

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a> CEdit:: GetLineCount

여러 줄 편집 컨트롤의 줄 수를 검색 하려면이 함수를 호출 합니다.

```
int GetLineCount() const;
```

### <a name="return-value"></a>반환 값

여러 줄 편집 컨트롤의 줄 수를 포함 하는 정수입니다. 편집 컨트롤에 입력 된 텍스트가 없는 경우 반환 값은 1입니다.

### <a name="remarks"></a>설명

`GetLineCount` 는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

자세한 내용은 Windows SDK [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a> CEdit:: GetMargins

이 편집 컨트롤의 왼쪽 및 오른쪽 여백을 검색 하려면이 멤버 함수를 호출 합니다.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>반환 값

하위 단어에서 왼쪽 여백의 너비 이며, 상위 단어에서 오른쪽 여백의 너비입니다.

### <a name="remarks"></a>설명

여백은 픽셀로 측정 됩니다.

> [!NOTE]
> 이 구성원 함수는 Windows 95 및 Windows NT 4.0부터 사용할 수 있습니다.

자세한 내용은 Windows SDK [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) 을 참조 하세요.

### <a name="example"></a>예제

  [Ceditview:: GetEditCtrl](ceditview-class.md#geteditctrl)의 예제를 참조 하세요.

## <a name="ceditgetmodify"></a><a name="getmodify"></a> CEdit:: GetModify

이 함수를 호출 하 여 편집 컨트롤의 내용이 수정 되었는지 여부를 확인 합니다.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>반환 값

편집 컨트롤 내용이 수정 되었으면 0이 아닌 값입니다. 변경 되지 않은 상태로 유지 되는 경우 0입니다.

### <a name="remarks"></a>설명

Windows는 편집 컨트롤의 내용이 변경 되었는지 여부를 나타내는 내부 플래그를 유지 관리 합니다. 이 플래그는 편집 컨트롤을 처음 만들 때 선택 취소 되며 [Setmodify](#setmodify) 멤버 함수를 호출 하 여 지울 수도 있습니다.

자세한 내용은 Windows SDK [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a> CEdit:: GetPasswordChar

사용자가 텍스트를 입력할 때 편집 컨트롤에 표시 되는 암호 문자를 검색 하려면이 함수를 호출 합니다.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>반환 값

사용자가 입력 한 문자 대신 표시할 문자를 지정 합니다. 암호 문자가 없는 경우 반환 값은 NULL입니다.

### <a name="remarks"></a>설명

ES_PASSWORD 스타일을 사용 하 여 편집 컨트롤을 만드는 경우 컨트롤을 지 원하는 DLL은 기본 암호 문자를 결정 합니다. 매니페스트 또는 [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) 메서드는 편집 컨트롤을 지 원하는 DLL을 결정 합니다. 편집 컨트롤을 지 원하는 user32.dll 경우 기본 암호 문자는 별표 (' * ', U + 002A)입니다. comctl32.dll 버전 6에서 편집 컨트롤을 지 원하는 경우 기본 문자는 검정색 원 (' ● ', U + 25CF)입니다. 공용 컨트롤을 지 원하는 DLL 및 버전에 대 한 자세한 내용은 [셸 및 공용 컨트롤 버전](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))을 참조 하세요.

이 메서드는 Windows SDK에서 설명 하는 [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) 메시지를 보냅니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a> CEdit:: GetRect

이 함수를 호출 하 여 편집 컨트롤의 서식 지정 사각형을 가져옵니다.

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT`서식 지정 사각형을 받는 구조체를 가리킵니다.

### <a name="remarks"></a>설명

서식 지정 사각형은 텍스트의 제한 사각형으로, 편집 컨트롤 창의 크기와는 독립적입니다.

여러 줄 편집 컨트롤의 서식 지정 사각형은 [Setrect](#setrect) 및 [SetRectNP](#setrectnp) 멤버 함수로 수정할 수 있습니다.

자세한 내용은 Windows SDK [EM_GETRECT](/windows/win32/Controls/em-getrect) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: 텍스트](#limittext)의 예제를 참조 하세요.

## <a name="ceditgetsel"></a><a name="getsel"></a> CEdit:: GetSel

반환 값 또는 매개 변수를 사용 하 여 편집 컨트롤에서 현재 선택 영역 (있는 경우)의 시작 및 끝 문자 위치를 가져오려면이 함수를 호출 합니다.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>매개 변수

*nStartChar*<br/>
현재 선택 영역에서 첫 번째 문자의 위치를 수신 하는 정수에 대 한 참조입니다.

*nEndChar*<br/>
현재 선택 영역의 끝을 지 나 첫 번째 nonselected 문자의 위치를 받는 정수에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

DWORD를 반환 하는 버전은 하위 단어에서 시작 위치를 포함 하는 값을 반환 하 고, 상위 단어에서 선택 영역 끝 다음의 첫 번째 nonselected 문자 위치를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [EM_GETSEL](/windows/win32/Controls/em-getsel) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a> CEdit:: HideBalloonTip

현재 편집 컨트롤과 연결 된 풍선 팁을 숨깁니다.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 함수는 Windows SDK에서 설명 하는 [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) 메시지를 보냅니다.

## <a name="ceditlimittext"></a><a name="limittext"></a> CEdit:: 텍스트

사용자가 편집 컨트롤에 입력할 수 있는 텍스트의 길이를 제한 하려면이 함수를 호출 합니다.

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>매개 변수

*nChars*<br/>
사용자가 입력할 수 있는 텍스트의 길이 (TCHARs)를 지정 합니다. 이 매개 변수가 0 이면 텍스트 길이가 UINT_MAX 바이트로 설정 됩니다. 이것은 기본적인 동작입니다.

### <a name="remarks"></a>설명

텍스트 제한을 변경 하면 사용자가 입력할 수 있는 텍스트만 제한 됩니다. 편집 컨트롤에 이미 있는 텍스트에는 영향을 주지 않으며의 [Setwindowtext](cwnd-class.md#setwindowtext) 멤버 함수를 통해 편집 컨트롤에 복사 되는 텍스트의 길이에도 영향을 주지 않습니다 `CWnd` . 응용 프로그램에서 함수를 사용 하 여 `SetWindowText` 에 대 한 호출에 지정 된 것 보다 더 많은 텍스트를 편집 컨트롤에 추가 하 `LimitText` 는 경우 사용자는 편집 컨트롤 내에서 텍스트를 삭제할 수 있습니다. 그러나 현재 선택 영역을 삭제 하면 텍스트가 텍스트 제한 아래에 포함 되는 경우를 제외 하 고는 텍스트 제한으로 인해 사용자가 기존 텍스트를 새 텍스트로 바꿀 수 없습니다.

> [!NOTE]
> Win32 (Windows NT 및 Windows 95/98)에서는 [set한 집합 텍스트가](#setlimittext) 이 함수를 대체 합니다.

자세한 내용은 Windows SDK [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a> CEdit:: LineFromChar

지정 된 문자 인덱스를 포함 하는 줄의 줄 번호를 검색 하려면이 함수를 호출 합니다.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
편집 컨트롤의 텍스트에 있는 원하는 문자에 대 한 0부터 시작 하는 인덱스 값을 포함 하거나-1을 포함 합니다. *Nindex* 가-1 인 경우 현재 줄, 즉 캐럿이 포함 된 줄을 지정 합니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 문자 인덱스를 포함 하는 줄의 줄 번호 (0부터 시작)입니다. *Nindex* 가-1 이면 선택의 첫 문자가 포함 된 줄 번호가 반환 됩니다. 선택 항목이 없으면 현재 줄 번호가 반환 됩니다.

### <a name="remarks"></a>설명

문자 인덱스는 편집 컨트롤의 시작 부분부터의 문자 수입니다.

이 멤버 함수는 여러 줄 편집 컨트롤 에서만 사용 됩니다.

자세한 내용은 Windows SDK [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a> CEdit:: LineIndex

여러 줄 편집 컨트롤에서 줄의 문자 인덱스를 검색 하려면이 함수를 호출 합니다.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>매개 변수

*N 줄*<br/>
편집 컨트롤의 텍스트에 있는 원하는 줄의 인덱스 값을 포함 하거나-1을 포함 합니다. *Nline* 이-1 이면 캐럿을 포함 하는 줄 인 현재 줄을 지정 합니다.

### <a name="return-value"></a>반환 값

*Nline* 에 지정 된 줄의 문자 인덱스 이거나, 지정 된 줄 번호가 편집 컨트롤의 줄 수보다 크면-1입니다.

### <a name="remarks"></a>설명

문자 인덱스는 편집 컨트롤의 시작 부분부터 지정 된 줄 까지의 문자 수입니다.

이 멤버 함수는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

자세한 내용은 Windows SDK [EM_LINEINDEX](/windows/win32/controls/em-lineindex) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a> CEdit:: LineLength

편집 컨트롤에서 줄의 길이를 검색 합니다.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>매개 변수

*N 줄*<br/>
해당 길이를 검색할 줄에 있는 문자의 인덱스 (0부터 시작)입니다. 기본값은 -1입니다.

### <a name="return-value"></a>반환 값

한 줄 편집 컨트롤의 경우 반환 값은 편집 컨트롤에 있는 텍스트의 길이 (TCHARs)입니다.

여러 줄 편집 컨트롤의 경우 반환 값은 TCHARs에서 *nline* 매개 변수로 지정 된 줄의 길이입니다. ANSI 텍스트의 경우 길이는 줄의 바이트 수입니다. 유니코드 텍스트의 경우 길이는 줄의 문자 수입니다. 줄 끝에 캐리지 리턴 문자가 포함 되지 않습니다.

*Nline* 매개 변수가 컨트롤의 문자 수보다 많은 경우 반환 값은 0입니다.

*Nline* 매개 변수가-1 인 경우 반환 값은 선택 된 문자가 포함 된 줄에서 선택 되지 않은 문자의 수입니다. 예를 들어, 선택이 한 줄의 네 번째 문자에서 다음 줄의 끝부터 여덟 번째 문자까지 확장 되는 경우 반환 값은 10입니다. 즉, 첫 번째 줄에는 세 개의 문자가, 다음에는 7 개의 문자가 있습니다.

TCHAR.H 형식에 대 한 자세한 내용은 [Windows 데이터 형식](/windows/win32/WinProg/windows-data-types)테이블의 tchar.h 행을 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [EM_LINELENGTH](/windows/win32/Controls/em-linelength) 메시지에서 지원 됩니다.

### <a name="example"></a>예제

  [CEdit:: lineindex](#lineindex)의 예제를 참조 하세요.

## <a name="ceditlinescroll"></a><a name="linescroll"></a> CEdit:: LineScroll

여러 줄 편집 컨트롤의 텍스트를 스크롤하려면이 함수를 호출 합니다.

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>매개 변수

*nLines*<br/>
세로로 스크롤할 줄 수를 지정 합니다.

*nChars*<br/>
가로로 스크롤할 문자 위치 수를 지정 합니다. 편집 컨트롤에 ES_RIGHT 또는 ES_CENTER 스타일이 있으면이 값은 무시 됩니다.

### <a name="remarks"></a>설명

이 멤버 함수는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

편집 컨트롤은 편집 컨트롤에서 텍스트의 마지막 줄을 벗어나 세로로 스크롤되지 않습니다. 현재 줄과 *nlines* 에 지정 된 줄 수가 모두 편집 컨트롤의 총 줄 수를 초과 하는 경우 편집 컨트롤의 마지막 줄이 편집 컨트롤 창의 맨 위로 스크롤 되도록 값이 조정 됩니다.

`LineScroll` 줄의 마지막 문자를 지나서 가로로 스크롤 하는 데 사용할 수 있습니다.

자세한 내용은 Windows SDK [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: GetFirstVisibleLine](#getfirstvisibleline)의 예제를 참조 하세요.

## <a name="ceditpaste"></a><a name="paste"></a> CEdit::P aste

클립보드의 데이터를 삽입 지점의에 삽입 하려면이 함수를 호출 합니다 `CEdit` .

```cpp
void Paste();
```

### <a name="remarks"></a>설명

클립보드에 CF_TEXT 형식의 데이터가 포함 되어 있는 경우에만 데이터가 삽입 됩니다.

자세한 내용은 Windows SDK [WM_PASTE](/windows/win32/dataxchg/wm-paste) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a> CEdit::P osFromChar

이 함수를 호출 하 여이 개체 내에서 지정 된 문자의 위치 (왼쪽 위 모퉁이)를 가져옵니다 `CEdit` .

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>매개 변수

*nChar*<br/>
지정 된 문자의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

*NChar* 로 지정 된 문자의 왼쪽 위 모퉁이에 대 한 좌표입니다.

### <a name="remarks"></a>설명

문자는 0부터 시작 하는 인덱스 값을 제공 하 여 지정 됩니다. *NChar* 가이 개체의 마지막 문자 인덱스 보다 큰 경우 `CEdit` 반환 값은이 개체의 마지막 문자 바로 다음에 나오는 문자 위치의 좌표를 지정 합니다 `CEdit` .

> [!NOTE]
> 이 구성원 함수는 Windows 95 및 Windows NT 4.0부터 사용할 수 있습니다.

자세한 내용은 Windows SDK [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: LineFromChar](#linefromchar)의 예제를 참조 하세요.

## <a name="ceditreplacesel"></a><a name="replacesel"></a> CEdit:: ReplaceSel

편집 컨트롤의 현재 선택 항목을 *lpszNewText* 에 지정 된 텍스트로 바꾸려면이 함수를 호출 합니다.

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszNewText*<br/>
대체 텍스트를 포함 하는 null로 끝나는 문자열을 가리킵니다.

*bCanUndo*<br/>
이 함수를 실행 취소할 수 있도록 지정 하려면이 매개 변수의 값을 TRUE로 설정 합니다. 기본값은 FALSE입니다.

### <a name="remarks"></a>설명

편집 컨트롤의 텍스트 부분만 바꿉니다. 모든 텍스트를 교체 하려면 [CWnd:: SetWindowText](cwnd-class.md#setwindowtext) 멤버 함수를 사용 합니다.

현재 선택 항목이 없으면 현재 커서 위치에 대체 텍스트가 삽입 됩니다.

자세한 내용은 Windows SDK [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: lineindex](#lineindex)의 예제를 참조 하세요.

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a> CEdit:: SetCueBanner

컨트롤이 비어 있을 때 편집 컨트롤에서 텍스트 큐 또는 팁으로 표시 되는 텍스트를 설정 합니다.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
진행 편집 컨트롤에 표시할 큐를 포함 하는 문자열에 대 한 포인터입니다.

*Fdraw... 집중*<br/>
진행 FALSE 이면 사용자가 편집 컨트롤을 클릭 하 고 컨트롤에 포커스를 부여 하는 경우 큐 배너가 그려지지 않습니다.

TRUE 이면 컨트롤에 포커스가 있을 때에도 큐 배너가 그려집니다. 사용자가 컨트롤을 입력 하기 시작 하면 큐 배너가 사라집니다.

기본값은 FALSE입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) 메시지를 보냅니다. 자세한 내용은 [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) 매크로를 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 [CEdit:: SetCueBanner](#setcuebanner) 메서드를 보여 줍니다.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a> CEdit:: SetHandle

이 함수를 호출 하 여 여러 줄 편집 컨트롤에서 사용 되는 로컬 메모리로 핸들을 설정 합니다.

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>매개 변수

*hBuffer*<br/>
로컬 메모리에 대 한 핸들을 포함 합니다. 이 핸들은 LMEM_MOVEABLE 플래그를 사용 하 여 [Localalloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows 함수를 이전에 호출 하 여 만든 것 이어야 합니다. 메모리는 null로 끝나는 문자열을 포함 하는 것으로 간주 됩니다. 그렇지 않은 경우 할당 된 메모리의 첫 번째 바이트를 0으로 설정 해야 합니다.

### <a name="remarks"></a>설명

그런 다음 편집 컨트롤은이 버퍼를 사용 하 여 자체 버퍼를 할당 하는 대신 현재 표시 된 텍스트를 저장 합니다.

이 멤버 함수는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

응용 프로그램은 새 메모리 핸들을 설정 하기 전에 [GetHandle](#gethandle) 멤버 함수를 사용 하 여 현재 메모리 버퍼에 대 한 핸들을 가져오고 Windows 함수를 사용 하 여 해당 메모리를 해제 해야 합니다 `LocalFree` .

`SetHandle` 실행 취소 버퍼 ( [Canundo](#canundo) 멤버 함수는 0을 반환)와 내부 수정 플래그를 지웁니다. [getmodify](#getmodify) 멤버 함수는 0을 반환 합니다. 편집 컨트롤 창이 다시 그려집니다.

대화 상자에서 DS_LOCALEDIT 스타일 플래그가 설정 된 대화 상자를 만든 경우에만 대화 상자의 여러 줄 편집 컨트롤에서이 멤버 함수를 사용할 수 있습니다.

> [!NOTE]
> `GetHandle` Windows 95/98에서는 작동 하지 않습니다. `GetHandle`Windows 95/98에서를 호출 하면 NULL이 반환 됩니다. `GetHandle` 는 Windows NT 버전 3.51 이상에 설명 된 대로 작동 합니다.

자세한 내용은 Windows SDK에서 [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [Localalloc](/windows/win32/api/winbase/nf-winbase-localalloc)및 [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a> CEdit:: SetHighlight

현재 편집 컨트롤에 표시 되는 텍스트 범위를 강조 표시 합니다.

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>매개 변수

*ichStart*\
진행 강조 표시할 텍스트 범위에 있는 첫 번째 문자의 0부터 시작 하는 인덱스입니다.

*ichEnd*\
진행 강조 표시할 텍스트 범위에서 마지막 문자의 0부터 시작 하는 인덱스입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [EM_SETHILITE](/windows/win32/Controls/em-sethilite) 메시지를 보냅니다.  이 메서드는 Windows SDK에서 설명 하는 [EM_SETHILITE](/windows/win32/Controls/em-sethilite) 메시지를 보냅니다. `SetHighlight`및 `GetHighlight` 는 모두 유니코드 빌드에서만 사용 됩니다.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a> CEdit:: Set 텍스트

이 멤버 함수를 호출 하 여이 개체에 대 한 텍스트 제한을 설정 합니다 `CEdit` .

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>매개 변수

*nMax*<br/>
새 텍스트 한도 (문자)입니다.

### <a name="remarks"></a>설명

텍스트 제한은 편집 컨트롤에서 허용할 수 있는 최대 텍스트 크기 (문자 수)입니다.

텍스트 제한을 변경 하면 사용자가 입력할 수 있는 텍스트만 제한 됩니다. 편집 컨트롤에 이미 있는 텍스트에는 영향을 주지 않으며의 [Setwindowtext](cwnd-class.md#setwindowtext) 멤버 함수를 통해 편집 컨트롤에 복사 되는 텍스트의 길이에도 영향을 주지 않습니다 `CWnd` . 응용 프로그램에서 함수를 사용 하 여 `SetWindowText` 에 대 한 호출에 지정 된 것 보다 더 많은 텍스트를 편집 컨트롤에 추가 하 `LimitText` 는 경우 사용자는 편집 컨트롤 내에서 텍스트를 삭제할 수 있습니다. 그러나 현재 선택 영역을 삭제 하면 텍스트가 텍스트 제한 아래에 포함 되는 경우를 제외 하 고는 텍스트 제한으로 인해 사용자가 기존 텍스트를 새 텍스트로 바꿀 수 없습니다.

이 함수는 Win32에서 대만 [텍스트](#limittext) 를 대체 합니다.

자세한 내용은 Windows SDK [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) 을 참조 하세요.

### <a name="example"></a>예제

  [Ceditview:: GetEditCtrl](ceditview-class.md#geteditctrl)의 예제를 참조 하세요.

## <a name="ceditsetmargins"></a><a name="setmargins"></a> CEdit:: SetMargins

이 편집 컨트롤의 왼쪽 및 오른쪽 여백을 설정 하려면이 메서드를 호출 합니다.

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>매개 변수

*nLeft*<br/>
새 왼쪽 여백의 너비 (픽셀)입니다.

*nRight*<br/>
새 오른쪽 여백의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 이 구성원 함수는 Windows 95 및 Windows NT 4.0부터 사용할 수 있습니다.

자세한 내용은 Windows SDK [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) 을 참조 하세요.

### <a name="example"></a>예제

  [Ceditview:: GetEditCtrl](ceditview-class.md#geteditctrl)의 예제를 참조 하세요.

## <a name="ceditsetmodify"></a><a name="setmodify"></a> CEdit:: SetModify

편집 컨트롤에 대해 수정 된 플래그를 설정 하거나 해제 하려면이 함수를 호출 합니다.

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>매개 변수

*bModified*<br/>
TRUE 값은 텍스트가 수정 되었음을 나타내고, FALSE 값은 수정 되지 않았음을 나타냅니다. 기본적으로 수정 된 플래그는 설정 되어 있습니다.

### <a name="remarks"></a>설명

수정 된 플래그는 편집 컨트롤 내의 텍스트가 수정 되었는지 여부를 나타냅니다. 사용자가 텍스트를 변경할 때마다 자동으로 설정 됩니다. [Getmodify](#getmodify) 멤버 함수를 사용 하 여 해당 값을 검색할 수 있습니다.

자세한 내용은 Windows SDK [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: GetModify](#getmodify)의 예제를 참조 하세요.

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a> CEdit:: SetPasswordChar

사용자가 텍스트를 입력 하는 경우 편집 컨트롤에 표시 되는 암호 문자를 설정 하거나 제거 하려면이 함수를 호출 합니다.

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>매개 변수

*ch*<br/>
사용자가 입력 하는 문자 대신 표시할 문자를 지정 합니다. *Ch* 가 0 이면 사용자가 입력 한 실제 문자가 표시 됩니다.

### <a name="remarks"></a>설명

암호 문자를 설정 하면 사용자가 입력 하는 각 문자에 대해 해당 문자가 표시 됩니다.

이 멤버 함수는 여러 줄 편집 컨트롤에는 영향을 주지 않습니다.

`SetPasswordChar`멤버 함수를 호출 하면에서 `CEdit` *ch* 로 지정 된 문자를 사용 하 여 표시 되는 모든 문자를 다시 그립니다.

[ES_PASSWORD](styles-used-by-mfc.md#edit-styles) 스타일을 사용 하 여 편집 컨트롤을 만드는 경우 기본 암호 문자는 별표 ()로 설정 됩니다 <strong>\*</strong> . `SetPasswordChar` *Ch* 를 0으로 설정 하 여가 호출 되는 경우이 스타일은 제거 됩니다.

자세한 내용은 Windows SDK [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a> CEdit:: SetReadOnly

이 함수를 호출 하 여 편집 컨트롤의 읽기 전용 상태를 설정 합니다.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>매개 변수

*bReadOnly*<br/>
편집 컨트롤의 읽기 전용 상태를 설정 하거나 제거할지 여부를 지정 합니다. TRUE 값은 상태를 읽기 전용으로 설정 합니다. FALSE 값은 상태를 읽기/쓰기로 설정 합니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값이 고, 오류가 발생 하는 경우 0입니다.

### <a name="remarks"></a>설명

현재 설정은 [CWnd:: GetStyle](cwnd-class.md#getstyle)의 반환 값에서 [ES_READONLY](styles-used-by-mfc.md#edit-styles) 플래그를 테스트 하 여 찾을 수 있습니다.

자세한 내용은 Windows SDK [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a> CEdit:: SetRect

지정 된 좌표를 사용 하 여 사각형의 크기를 설정 하려면이 함수를 호출 합니다.

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT` `CRect` 서식 지정 사각형의 새 크기를 지정 하는 구조체 또는 개체를 가리킵니다.

### <a name="remarks"></a>설명

이 멤버는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

`SetRect`여러 줄 편집 컨트롤의 서식 지정 사각형을 설정 하는 데 사용 합니다. 서식 지정 사각형은 텍스트의 제한 사각형으로, 편집 컨트롤 창의 크기와는 독립적입니다. 편집 컨트롤을 처음 만들 때 서식 지정 사각형은 편집 컨트롤 창의 클라이언트 영역과 동일 합니다. `SetRect`응용 프로그램은 멤버 함수를 사용 하 여 서식 지정 사각형을 편집 컨트롤 창 보다 크거나 작게 만들 수 있습니다.

편집 컨트롤에 스크롤 막대가 없는 경우 서식 지정 사각형이 창 보다 큰 경우 텍스트는 래핑되지 않고 잘립니다. 편집 컨트롤에 테두리가 포함 되어 있으면 서식 지정 사각형이 테두리의 크기로 줄어듭니다. 멤버 함수에서 반환 되는 사각형을 조정 하는 경우 `GetRect` 에는 사각형을에 전달 하기 전에 테두리의 크기를 제거 해야 합니다 `SetRect` .

`SetRect`가 호출 되 면 편집 컨트롤의 텍스트도 다시 포맷 되 고 다시 표시 됩니다.

자세한 내용은 Windows SDK [EM_SETRECT](/windows/win32/Controls/em-setrect) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a> CEdit:: SetRectNP

여러 줄 편집 컨트롤의 서식 지정 사각형을 설정 하려면이 함수를 호출 합니다.

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT` `CRect` 사각형의 새 크기를 지정 하는 구조체 또는 개체를 가리킵니다.

### <a name="remarks"></a>설명

서식 지정 사각형은 텍스트의 제한 사각형으로, 편집 컨트롤 창의 크기와는 독립적입니다.

`SetRectNP` 는 `SetRect` 편집 컨트롤 창이 다시 그려지지 않는다는 점을 제외 하 고 멤버 함수와 동일 합니다.

편집 컨트롤을 처음 만들 때 서식 지정 사각형은 편집 컨트롤 창의 클라이언트 영역과 동일 합니다. `SetRectNP`응용 프로그램은 멤버 함수를 호출 하 여 서식 지정 사각형을 편집 컨트롤 창 보다 크거나 작게 만들 수 있습니다.

편집 컨트롤에 스크롤 막대가 없는 경우 서식 지정 사각형이 창 보다 큰 경우 텍스트는 래핑되지 않고 잘립니다.

이 멤버는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

자세한 내용은 Windows SDK [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: SetRect](#setrect)의 예제를 참조 하세요.

## <a name="ceditsetsel"></a><a name="setsel"></a> CEdit:: SetSel

편집 컨트롤에서 문자 범위를 선택 하려면이 함수를 호출 합니다.

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>매개 변수

*dwSelection*<br/>
상위 단어에서 하위 단어의 시작 위치와 끝 위치를 지정 합니다. 하위 단어가 0이 고 고차 단어가-1 이면 편집 컨트롤의 모든 텍스트가 선택 됩니다. 하위 단어가-1 이면 현재 선택 항목이 제거 됩니다.

*bNoScroll*<br/>
캐럿을 스크롤하여 표시 해야 하는지 여부를 나타냅니다. FALSE 이면 캐럿이 뷰로 스크롤됩니다. TRUE 이면 캐럿이 뷰로 스크롤되지 않습니다.

*nStartChar*<br/>
시작 위치를 지정 합니다. *Nstartchar* 가 0이 고 *nendchar* 이-1 이면 편집 컨트롤의 모든 텍스트가 선택 됩니다. *Nstartchar* 가-1 이면 현재 선택 항목이 제거 됩니다.

*nEndChar*<br/>
끝 위치를 지정 합니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [EM_SETSEL](/windows/win32/Controls/em-setsel) 을 참조 하세요.

### <a name="example"></a>예제

  [CEdit:: GetSel](#getsel)의 예제를 참조 하세요.

## <a name="ceditsettabstops"></a><a name="settabstops"></a> CEdit:: SetTabStops

여러 줄 편집 컨트롤에서 탭 정지를 설정 하려면이 함수를 호출 합니다.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>매개 변수

*cxEachStop*<br/>
모든 *cxEachStop* 대화 상자 단위에서 탭 정지를 설정 하도록 지정 합니다.

*nTabStops*<br/>
*RgTabStops* 에 포함 된 탭 정지의 수를 지정 합니다. 이 수는 1 보다 커야 합니다.

*rgTabStops*<br/>
대화 상자 단위에서 탭 정지를 지정 하 여 부호 없는 정수의 배열을 가리킵니다. 대화 상자 단위는 가로 또는 세로 거리입니다. 한 개의 가로 대화 상자 단위는 현재 대화 상자 기본 너비 단위의 4 번째와 같으며 세로 대화 상자의 1 개는 현재 대화 상자 기본 높이 단위의 8-8과 같습니다. 대화 상자 기본 단위는 현재 시스템 글꼴의 높이와 너비를 기준으로 계산 됩니다. `GetDialogBaseUnits`Windows 함수는 현재 대화 상자 기본 단위 (픽셀)를 반환 합니다.

### <a name="return-value"></a>반환 값

탭이 설정 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

텍스트를 여러 줄 편집 컨트롤로 복사 하면 텍스트의 모든 탭 문자에서 다음 탭 정지까지 공간이 생성 됩니다.

탭 정지를 기본 크기인 32 대화 상자 단위로 설정 하려면이 멤버 함수의 매개 변수가 없는 버전을 호출 합니다. 탭 정지를 32 이외의 크기로 설정 하려면 *cxEachStop* 매개 변수를 사용 하 여 버전을 호출 합니다. 탭 정지를 크기 배열로 설정 하려면 두 개의 매개 변수를 사용 하 여 버전을 사용 합니다.

이 멤버 함수는 여러 줄 편집 컨트롤에 의해서만 처리 됩니다.

`SetTabStops` 는 편집 창을 자동으로 다시 그려지지 않습니다. 편집 컨트롤에 이미 있는 텍스트에 대 한 탭 정지를 변경 하는 경우 [CWnd:: InvalidateRect](cwnd-class.md#invalidaterect) 를 호출 하 여 편집 창을 다시 그립니다.

자세한 내용은 Windows SDK에서 [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) 및 [Getdialogbaseunits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) 를 참조 하세요.

### <a name="example"></a>예제

  [Ceditview:: SetTabStops](ceditview-class.md#settabstops)의 예제를 참조 하세요.

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a> CEdit:: ShowBalloonTip

현재 편집 컨트롤과 연결 된 풍선 설명을 표시 합니다.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>매개 변수

*pEditBalloonTip*\
진행 풍선 팁을 설명 하는 [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) 구조체에 대 한 포인터입니다.

*lpszTitle*\
진행 풍선 설명의 제목을 포함 하는 유니코드 문자열에 대 한 포인터입니다.

*lpszText*\
진행 풍선 팁 텍스트를 포함 하는 유니코드 문자열에 대 한 포인터입니다.

*ttiIcon*\
진행 풍선 설명에 연결할 아이콘의 유형을 지정 하는 **INT** 입니다. 기본값은 TTI_NONE입니다. 자세한 내용은 `ttiIcon` [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) 구조체의 멤버를 참조 하십시오.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 함수는 Windows SDK에서 설명 하는 [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) 메시지를 보냅니다. 자세한 내용은 [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) 매크로를 참조 하세요.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_cedit` 현재 편집 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 편집 컨트롤에 대 한 풍선 설명을 표시 합니다. [CEdit:: ShowBalloonTip](#showballoontip) 메서드는 제목 및 풍선 팁 텍스트를 지정 합니다.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a> CEdit:: Undo

마지막 편집 제어 작업을 실행 취소 하려면이 함수를 호출 합니다.

```
BOOL Undo();
```

### <a name="return-value"></a>반환 값

한 줄 편집 컨트롤의 경우 반환 값은 항상 0이 아닙니다. 여러 줄 편집 컨트롤의 경우 실행 취소 작업이 성공 하면 0이 아닌 값이 반환 되 고, 실행 취소 작업이 실패 하는 경우 0이 반환 됩니다.

### <a name="remarks"></a>설명

실행 취소 작업을 실행 취소할 수도 있습니다. 예를 들어,에 대 한 첫 번째 호출로 삭제 된 텍스트를 복원할 수 있습니다 `Undo` . 중간 편집 작업이 없는 경우에 대 한 두 번째 호출로 텍스트를 다시 제거할 수 있습니다 `Undo` .

자세한 내용은 Windows SDK [EM_UNDO](/windows/win32/Controls/em-undo) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](cwnd-class.md)<br/>
[CButton 클래스](cbutton-class.md)<br/>
[CComboBox 클래스](ccombobox-class.md)<br/>
[CListBox 클래스](clistbox-class.md)<br/>
[CScrollBar 클래스](cscrollbar-class.md)<br/>
[CStatic 클래스](cstatic-class.md)<br/>
[CDialog 클래스](cdialog-class.md)
