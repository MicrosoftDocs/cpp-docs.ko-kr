---
title: CComboBox 클래스
description: MFC Windows 콤보 상자 클래스에 대 한 API 참조 CComboBox
ms.date: 08/27/2020
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: 515a079ca4f6c3896733bbebec424f63455fb979
ms.sourcegitcommit: c8f1605354724a13566bc3b0fac3c5d98265f1d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062187"
---
# <a name="ccombobox-class"></a>CComboBox 클래스

Windows 콤보 상자의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CComboBox : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComboBox:: CComboBox](#ccombobox)|`CComboBox` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|콤보 상자의 목록 상자 또는 CBS_SORT 스타일이 있는 목록 상자의 정렬 된 위치에 문자열을 추가 합니다.|
|[CComboBox:: Clear](#clear)|편집 컨트롤에서 현재 선택 항목 (있는 경우)을 삭제 (선택 취소) 합니다.|
|[CComboBox:: CompareItem](#compareitem)|정렬 된 소유자가 그린 콤보 상자에서 새 목록 항목의 상대 위치를 확인 하기 위해 프레임 워크에서 호출 됩니다.|
|[CComboBox::Copy](#copy)|현재 선택 항목 (있는 경우)을 클립보드에 CF_TEXT 형식으로 복사 합니다.|
|[CComboBox::Create](#create)|콤보 상자를 만들고 개체에 연결 `CComboBox` 합니다.|
|[CComboBox::Cut](#cut)|편집 컨트롤에서 현재 선택 영역을 삭제 (잘라내기) 하 고 삭제 된 텍스트를 클립보드에 CF_TEXT 형식으로 복사 합니다.|
|[CComboBox::D eleteItem](#deleteitem)|소유자가 그린 콤보 상자에서 목록 항목이 삭제 될 때 프레임 워크에서 호출 됩니다.|
|[CComboBox::D eleteString](#deletestring)|콤보 상자의 목록 상자에서 문자열을 삭제 합니다.|
|[CComboBox::Dir](#dir)|콤보 상자의 목록 상자에 파일 이름 목록을 추가 합니다.|
|[CComboBox::D rawItem](#drawitem)|소유자가 그린 콤보 상자의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CComboBox:: FindString](#findstring)|콤보 상자의 목록 상자에서 지정 된 접두사를 포함 하는 첫 번째 문자열을 찾습니다.|
|[CComboBox:: FindStringExact](#findstringexact)|콤보 상자에서 지정 된 문자열과 일치 하는 첫 번째 목록 상자 문자열을 찾습니다.|
|[CComboBox:: GetComboBoxInfo](#getcomboboxinfo)|개체에 대 한 정보를 검색 `CComboBox` 합니다.|
|[CComboBox:: GetCount](#getcount)|콤보 상자의 목록 상자에 있는 항목 수를 검색 합니다.|
|[CComboBox::GetCueBanner](#getcuebanner)|콤보 상자 컨트롤에 대해 표시 되는 큐 텍스트를 가져옵니다.|
|[CComboBox:: GetCurSel](#getcursel)|콤보 상자의 목록 상자에서 현재 선택 된 항목 (있는 경우)의 인덱스를 검색 합니다.|
|[CComboBox:: GetDroppedControlRect](#getdroppedcontrolrect)|드롭다운 콤보 상자에서 표시 되는 (드롭다운) 목록 상자의 화면 좌표를 검색 합니다.|
|[CComboBox::GetDroppedState](#getdroppedstate)|드롭다운 콤보 상자의 목록 상자를 표시할지 여부를 결정 합니다.|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|콤보 상자의 드롭다운 목록 상자 부분에 대해 허용 되는 최소 너비를 검색 합니다.|
|[CComboBox:: GetEditSel](#geteditsel)|콤보 상자의 편집 컨트롤에서 현재 선택 된 항목의 시작 및 끝 문자 위치를 가져옵니다.|
|[CComboBox:: GetExtendedUI](#getextendedui)|콤보 상자에 기본 사용자 인터페이스나 확장 사용자 인터페이스가 있는지 여부를 확인 합니다.|
|[CComboBox:: GetHorizontalExtent](#gethorizontalextent)|콤보 상자의 목록 상자 부분을 가로로 스크롤할 수 있는 너비 (픽셀)를 반환 합니다.|
|[CComboBox:: GetItemData](#getitemdata)|지정 된 콤보 상자 항목과 연결 된 응용 프로그램 제공 32 비트 값을 검색 합니다.|
|[CComboBox:: GetItemDataPtr](#getitemdataptr)|지정 된 콤보 상자 항목과 연결 된 응용 프로그램에서 제공 하는 32 비트 포인터를 검색 합니다.|
|[CComboBox:: GetItemHeight](#getitemheight)|콤보 상자에서 목록 항목의 높이를 검색 합니다.|
|[CComboBox:: GetLBText](#getlbtext)|콤보 상자의 목록 상자에서 문자열을 가져옵니다.|
|[CComboBox:: GetLBTextLen](#getlbtextlen)|콤보 상자의 목록 상자에 있는 문자열의 길이를 가져옵니다.|
|[CComboBox::GetLocale](#getlocale)|콤보 상자의 로캘 식별자를 검색 합니다.|
|[CComboBox::GetMinVisible](#getminvisible)|현재 콤보 상자의 드롭다운 목록에 표시 되는 최소 항목 수를 가져옵니다.|
|[CComboBox::GetTopIndex](#gettopindex)|콤보 상자의 목록 상자 부분에서 표시 되는 첫 번째 항목의 인덱스를 반환 합니다.|
|[CComboBox::InitStorage](#initstorage)|콤보 상자의 목록 상자 부분에서 항목 및 문자열에 대 한 메모리 블록을 미리 할당 합니다.|
|[CComboBox::InsertString](#insertstring)|콤보 상자의 목록 상자에 문자열을 삽입합니다.|
|[CComboBox::LimitText](#limittext)|사용자가 콤보 상자의 편집 컨트롤에 입력할 수 있는 텍스트의 길이를 제한 합니다.|
|[CComboBox::MeasureItem](#measureitem)|소유자가 그린 콤보 상자를 만들 때 콤보 상자 차원을 결정 하기 위해 프레임 워크에서 호출 됩니다.|
|[CComboBox::P aste](#paste)|클립보드의 데이터를 편집 컨트롤의 현재 커서 위치에 삽입 합니다. 클립보드에 CF_TEXT 형식의 데이터가 포함 되어 있는 경우에만 데이터가 삽입 됩니다.|
|[CComboBox::ResetContent](#resetcontent)|콤보 상자의 목록 상자와 편집 컨트롤에서 모든 항목을 제거 합니다.|
|[CComboBox::SelectString](#selectstring)|콤보 상자의 목록 상자에서 문자열을 검색 하 고, 문자열이 있으면 목록 상자에서 문자열을 선택 하 고 편집 컨트롤에 문자열을 복사 합니다.|
|[CComboBox::SetCueBanner](#setcuebanner)|콤보 상자 컨트롤에 대해 표시 되는 큐 텍스트를 설정 합니다.|
|[CComboBox::SetCurSel](#setcursel)|콤보 상자의 목록 상자에서 문자열을 선택 합니다.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|콤보 상자의 드롭다운 목록 상자 부분에 허용 되는 최소 너비를 설정 합니다.|
|[CComboBox:: SetEditSel](#seteditsel)|콤보 상자의 편집 컨트롤에서 문자를 선택 합니다.|
|[CComboBox::SetExtendedUI](#setextendedui)|기본 사용자 인터페이스 또는 CBS_DROPDOWN 또는 CBS_DROPDOWNLIST 스타일을 포함 하는 콤보 상자의 확장 된 사용자 인터페이스 중 하나를 선택 합니다.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|콤보 상자의 목록 상자 부분을 가로로 스크롤할 수 있는 너비 (픽셀)를 설정 합니다.|
|[CComboBox::SetItemData](#setitemdata)|콤보 상자의 지정 된 항목과 연결 된 32 비트 값을 설정 합니다.|
|[CComboBox:: SetItemDataPtr](#setitemdataptr)|콤보 상자의 지정 된 항목과 연결 된 32 비트 포인터를 설정 합니다.|
|[CComboBox::SetItemHeight](#setitemheight)|콤보 상자에 있는 목록 항목의 높이 또는 콤보 상자의 편집 컨트롤 (또는 정적 텍스트) 부분 높이를 설정 합니다.|
|[CComboBox::SetLocale](#setlocale)|콤보 상자의 로캘 식별자를 설정 합니다.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|현재 콤보 상자의 드롭다운 목록에 표시 되는 최소 항목 수를 설정 합니다.|
|[CComboBox:: SetTopIndex](#settopindex)|콤보 상자의 목록 상자 부분에 지정 된 인덱스를 가진 항목이 맨 위에 표시 되도록 합니다.|
|[CComboBox::ShowDropDown](#showdropdown)|CBS_DROPDOWN 또는 CBS_DROPDOWNLIST 스타일을 포함 하는 콤보 상자의 목록 상자를 표시 하거나 숨깁니다.|

## <a name="remarks"></a>설명

콤보 상자는 정적 컨트롤 또는 편집 컨트롤과 결합 된 목록 상자로 구성 됩니다. 컨트롤의 목록 상자 부분은 항상 표시 되거나, 사용자가 컨트롤 옆의 드롭다운 화살표를 선택 하는 경우에만 드롭다운 될 수 있습니다.

목록 상자에서 현재 선택한 항목 (있는 경우)은 정적 또는 편집 컨트롤에 표시 됩니다. 또한 콤보 상자에 드롭다운 목록 스타일이 있는 경우 사용자는 목록에 있는 항목 중 하나에 대 한 초기 문자를 입력할 수 있고 목록 상자 (표시 되는 경우)는 첫 번째 문자를 사용 하 여 다음 항목을 강조 표시 합니다.

다음 표에서는 세 개의 콤보 상자 [스타일](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)을 비교 합니다.

|스타일|목록 상자가 표시 되는 경우|정적 또는 편집 컨트롤|
|-----------|-------------------------------|-----------------------------|
|단순|항상|편집|
|Drop-down|삭제 된 경우|편집|
|드롭다운 목록|삭제 된 경우|정적|

`CComboBox`대화 상자 템플릿이나 코드에서 직접 개체를 만들 수 있습니다. 두 경우 모두, 먼저 생성자를 호출 `CComboBox` 하 여 개체를 생성 `CComboBox` 한 다음 [create](#create) member 함수를 호출 하 여 컨트롤을 만들고이를 개체에 연결 `CComboBox` 합니다.

콤보 상자에서 부모 (일반적으로에서 파생 된 클래스)로 전송 되는 Windows 알림 메시지를 처리 하려면 `CDialog` 각 메시지의 부모 클래스에 메시지 매핑 항목과 메시지 처리기 멤버 함수를 추가 합니다.

각 메시지 맵 항목은 다음 형식을 사용 합니다.

`ON_Notification( id, memberFxn )`

여기서는 `id` 알림을 보내는 콤보 상자 컨트롤의 자식 창 ID를 지정 하 고 `memberFxn` 는 알림을 처리 하기 위해 작성 한 부모 멤버 함수의 이름입니다.

부모의 함수 프로토타입은 다음과 같습니다.

`afx_msg void memberFxn( );`

특정 알림이 전송 되는 순서를 예측할 수 없습니다. 특히 CBN_CLOSEUP 알림 전후에 CBN_SELCHANGE 알림이 발생할 수 있습니다.

잠재적 메시지 맵 항목은 다음과 같습니다.

- ON_CBN_CLOSEUP (Windows 3.1 이상) 콤보 상자의 목록 상자가 닫혔습니다. 이 알림 메시지는 [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있는 콤보 상자에 대해 전송 되지 않습니다.

- 사용자가 콤보 상자의 목록 상자에서 문자열을 두 번 클릭 ON_CBN_DBLCLK 합니다. 이 알림 메시지는 CBS_SIMPLE 스타일이 있는 콤보 상자에 대해서만 전송 됩니다. [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 또는 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있는 콤보 상자의 경우 한 번 클릭으로 목록 상자를 숨기 므로 두 번 클릭이 발생 하지 않습니다.

- 콤보 상자의 목록 상자가 드롭다운 될 ON_CBN_DROPDOWN (표시 됨). 이 알림 메시지는 CBS_DROPDOWN 또는 CBS_DROPDOWNLIST 스타일이 있는 콤보 상자에 대해서만 발생할 수 있습니다.

- 사용자가 콤보 상자의 편집 컨트롤 부분에 있는 텍스트를 변경 했을 수 있는 작업을 수행 ON_CBN_EDITCHANGE 합니다. CBN_EDITUPDATE 메시지와 달리이 메시지는 Windows에서 화면을 업데이트 한 후에 전송 됩니다. 콤보 상자에 CBS_DROPDOWNLIST 스타일이 있으면 전송 되지 않습니다.

- 콤보 상자의 편집 컨트롤 부분 ON_CBN_EDITUPDATE 변경 된 텍스트를 표시 하려고 합니다. 이 알림 메시지는 컨트롤의 텍스트 서식이 지정 된 후 텍스트를 표시 하기 전에 전송 됩니다. 콤보 상자에 CBS_DROPDOWNLIST 스타일이 있으면 전송 되지 않습니다.

- ON_CBN_ERRSPACE 콤보 상자는 특정 요청을 충족 하는 데 충분 한 메모리를 할당할 수 없습니다.

- ON_CBN_SELENDCANCEL (Windows 3.1 이상) 사용자의 선택이 취소 되어야 함을 나타냅니다. 사용자가 항목을 클릭 한 다음 다른 창이 나 컨트롤을 클릭 하 여 콤보 상자의 목록 상자를 숨깁니다. 이 알림 메시지는 사용자의 선택이 무시 됨을 나타내기 위해 CBN_CLOSEUP 알림 메시지 보다 먼저 전송 됩니다. CBN_SELENDCANCEL 또는 CBN_SELENDOK 알림 메시지는 CBN_CLOSEUP 알림 메시지가 전송 되지 않은 경우에도 전송 됩니다 (CBS_SIMPLE 스타일이 있는 콤보 상자의 경우와 같이).

- 사용자는 항목을 선택한 다음 ENTER 키를 누르거나 아래쪽 화살표 키를 클릭 하 여 콤보 상자의 목록 상자를 숨깁니다. ON_CBN_SELENDOK 이 알림 메시지는 사용자의 선택이 유효한 것으로 간주 됨을 나타내기 위해 CBN_CLOSEUP 메시지 보다 먼저 전송 됩니다. CBN_SELENDCANCEL 또는 CBN_SELENDOK 알림 메시지는 CBN_CLOSEUP 알림 메시지가 전송 되지 않은 경우에도 전송 됩니다 (CBS_SIMPLE 스타일이 있는 콤보 상자의 경우와 같이).

- 콤보 상자를 ON_CBN_KILLFOCUS 입력 포커스가 손실 됩니다.

- 콤보 상자의 목록 상자에서 선택한 항목은 목록 상자를 클릭 하거나 화살표 키를 사용 하 여 선택 항목을 변경 하는 경우에 변경 됩니다. ON_CBN_SELCHANGE 이 메시지를 처리할 때 콤보 상자의 편집 컨트롤에 있는 텍스트는 `GetLBText` 또는 다른 유사한 기능을 통해서만 검색할 수 있습니다. `GetWindowText` 사용할 수 없습니다.

- 콤보 상자 ON_CBN_SETFOCUS 입력 포커스를 받습니다.

대화 상자 `CComboBox` 내에서 개체를 만드는 경우 (대화 상자 리소스를 통해) `CComboBox` 사용자가 대화 상자를 닫으면 개체가 자동으로 소멸 됩니다.

다른 창 개체 내에 개체를 포함 하는 경우에는 `CComboBox` 삭제할 필요가 없습니다. 스택에서 개체를 만들면 `CComboBox` 자동으로 제거 됩니다. `CComboBox`함수를 사용 하 여 힙에서 개체를 만드는 경우 **`new`** 에는 **`delete`** 개체에 대해를 호출 하 여 Windows 콤보 상자가 소멸 될 때 개체를 제거 해야 합니다.

**참고** WM_KEYDOWN 및 WM_CHAR 메시지를 처리 하려면 콤보 상자의 편집 및 목록 상자 컨트롤을 서브클래싱하 고 및에서 클래스를 파생 시킨 `CEdit` `CListBox` 다음 이러한 메시지에 대 한 처리기를 파생 클래스에 추가 해야 합니다. 자세한 내용은 [CWnd:: SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a> CComboBox:: AddString

콤보 상자의 목록 상자에 문자열을 추가 합니다.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>매개 변수

*lpszString*<br/>
추가 될 null로 끝나는 문자열을 가리킵니다.

### <a name="return-value"></a>반환 값

반환 값이 0 보다 크거나 같으면 목록 상자에 있는 문자열의 인덱스 (0부터 시작)입니다. 오류가 발생 하는 경우 반환 값은 CB_ERR입니다. 새 문자열을 저장 하는 데 사용할 수 있는 공간이 부족 한 경우 반환 값은 CB_ERRSPACE입니다.

### <a name="remarks"></a>설명

[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일로 목록 상자를 만들지 않은 경우 문자열이 목록의 끝에 추가 됩니다. 그렇지 않으면 문자열이 목록에 삽입 되 고 목록이 정렬 됩니다.

> [!NOTE]
> 이 함수는 Windows 컨트롤에서 지원 되지 않습니다 `ComboBoxEx` . 이 컨트롤에 대 한 자세한 내용은 [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK를 참조 하세요.

목록 내의 특정 위치에 문자열을 삽입 하려면 [Insertstring](#insertstring) 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a> CComboBox:: CComboBox

`CComboBox` 개체를 생성합니다.

```
CComboBox();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a> CComboBox:: Clear

콤보 상자의 편집 컨트롤에서 현재 선택 항목 (있는 경우)을 삭제 (선택 취소) 합니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

현재 선택 영역을 삭제 하 고 삭제 된 내용을 클립보드에 배치 하려면 [Cut](#cut) 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a> CComboBox:: CompareItem

정렬 된 소유자 그리기 콤보 상자의 목록 상자 부분에서 새 항목의 상대 위치를 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpCompareItemStruct*<br/>
[Compareitemstruct](/windows/win32/api/winuser/ns-winuser-compareitemstruct) 구조체에 대 한 긴 포인터입니다.

### <a name="return-value"></a>반환 값

구조에 설명 된 두 항목의 상대 위치를 나타냅니다 `COMPAREITEMSTRUCT` . 다음 값 중 하나일 수 있습니다.

|값|의미|
|-----------|-------------|
|- 1|항목 1은 항목 2 앞에 정렬 됩니다.|
|0|항목 1과 항목 2는 동일 하 게 정렬 됩니다.|
|1|항목 1은 항목 2 뒤에 정렬 됩니다.|

에 대 한 설명은 [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) 을 참조 하십시오 `COMPAREITEMSTRUCT` .

### <a name="remarks"></a>설명

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. LBS_SORT 스타일을 사용 하 여 소유자 그리기 콤보 상자를 만드는 경우 목록 상자에 추가 된 새 항목을 정렬 하는 데 프레임 워크를 지원 하려면이 멤버 함수를 재정의 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a> CComboBox:: Copy

콤보 상자의 편집 컨트롤에서 현재 선택 항목 (있는 경우)을 CF_TEXT 형식으로 클립보드에 복사 합니다.

```cpp
void Copy();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a> CComboBox:: Create

콤보 상자를 만들고 개체에 연결 `CComboBox` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
콤보 상자의 스타일을 지정 합니다. [콤보 상자 스타일](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 의 조합을 상자에 모두 적용 합니다.

*rect*<br/>
콤보 상자의 위치와 크기를 가리킵니다. 는 [RECT 구조](/windows/win32/api/windef/ns-windef-rect) 또는 개체 일 수 있습니다 `CRect` .

*pParentWnd*<br/>
콤보 상자의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
콤보 상자의 컨트롤 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CComboBox`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` Windows 콤보 상자를 만들고 개체에 연결 `CComboBox` 합니다.

가 `Create` 실행 되 면 Windows는 [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)및 [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) 메시지를 콤보 상자로 보냅니다.

이러한 메시지는 기본적으로 기본 클래스의 [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)및 [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) 멤버 함수에 의해 처리 됩니다 `CWnd` . 기본 메시지 처리를 확장 하려면에서 클래스를 파생 시키고 `CComboBox` , 메시지 맵을 새 클래스에 추가 하 고, 앞의 메시지 처리기 멤버 함수를 재정의 합니다. 예를 들어를 재정의 하 `OnCreate` 여 새 클래스에 필요한 초기화를 수행 합니다.

다음 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 을 콤보 상자 컨트롤에 적용 합니다. :

- 항상 WS_CHILD

- WS_VISIBLE 일반적으로

- WS_DISABLED 거의 없음

- 콤보 상자의 목록 상자에 세로 스크롤을 추가 하려면 WS_VSCROLL 합니다.

- 콤보 상자의 목록 상자에 가로 스크롤을 추가 하려면 WS_HSCROLL 합니다.

- 컨트롤을 그룹화 WS_GROUP

- 탭 순서에 콤보 상자를 포함 하려면 WS_TABSTOP 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a> CComboBox:: Cut

콤보 상자 편집 컨트롤에서 현재 선택 항목 (있는 경우)을 삭제 (잘라내기) 하 고 삭제 된 텍스트를 클립보드에 CF_TEXT 형식으로 복사 합니다.

```cpp
void Cut();
```

### <a name="remarks"></a>설명

삭제 된 텍스트를 클립보드에 넣지 않고 현재 선택 영역을 삭제 하려면 [Clear](#clear) 멤버 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a> CComboBox::D eleteItem

사용자가 소유자 그리기 개체에서 항목을 삭제 `CComboBox` 하거나 콤보 상자를 소멸 시키는 경우 프레임 워크에서 호출 됩니다.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDeleteItemStruct*<br/>
삭제 된 항목에 대 한 정보를 포함 하는 Windows [Deleteitemstruct](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) 구조체에 대 한 긴 포인터입니다. 이 구조체에 대 한 설명은 [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) 을 참조 하십시오.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 아무 작업도 수행하지 않습니다. 필요에 따라 콤보 상자를 다시 그리도록이 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a> CComboBox::D eleteString

콤보 상자에서 *n 인덱스* 위치에 있는 항목을 삭제 합니다.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
삭제할 문자열의 인덱스를 지정 합니다.

### <a name="return-value"></a>반환 값

반환 값이 0 보다 크거나 같으면 목록에 남아 있는 문자열의 수입니다. *Nindex* 가 목록의 항목 수보다 많은 인덱스를 지정 하는 경우 반환 값은 CB_ERR입니다.

### <a name="remarks"></a>설명

*N 인덱스* 다음에 나오는 모든 항목은 이제 한 위치 아래로 이동 합니다. 예를 들어 콤보 상자에 두 항목이 포함 된 경우 첫 번째 항목을 삭제 하면 나머지 항목이 현재 첫 번째 위치에 있게 됩니다. 첫 번째 위치에 있는 항목의 경우 *n 인덱스*= 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a> CComboBox: ir:D

콤보 상자의 목록 상자에 파일 이름 또는 드라이브 목록을 추가 합니다.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>매개 변수

*attr*<br/>
는 **`enum`** [CFile:: GetStatus](../../mfc/reference/cfile-class.md#getstatus) 에 설명 된 값의 조합 이거나 다음 값의 조합일 수 있습니다.

- DDL_READWRITE 파일은에서 읽거나 쓸 수 있습니다.

- DDL_READONLY 파일은 읽을 수 있지만 쓸 수는 없습니다.

- DDL_HIDDEN 파일은 숨겨지고 디렉터리 목록에 표시 되지 않습니다.

- DDL_SYSTEM 파일은 시스템 파일입니다.

- *LpszWildCard* 에 지정 된 이름이 디렉터리를 지정 하는 DDL_DIRECTORY 합니다.

- DDL_ARCHIVE 파일이 보관 되었습니다.

- *LpszWildCard*으로 지정 된 이름과 일치 하는 모든 드라이브를 포함 DDL_DRIVES 합니다.

- DDL_EXCLUSIVE 배타 플래그입니다. Exclusive 플래그가 설정 된 경우 지정 된 형식의 파일만 나열 됩니다. 그렇지 않으면 지정 된 형식의 파일이 "normal" 파일 외에 나열 됩니다.

*lpszWildCard*<br/>
는 파일 사양 문자열을 가리킵니다. 문자열은 와일드 카드를 포함할 수 있습니다 (예: *. \* ).

### <a name="return-value"></a>반환 값

반환 값이 0 보다 크거나 같으면 목록에 추가 된 마지막 파일 이름의 0부터 시작 하는 인덱스입니다. 오류가 발생 하는 경우 반환 값은 CB_ERR입니다. 새 문자열을 저장 하는 데 사용할 수 있는 공간이 부족 한 경우 반환 값은 CB_ERRSPACE입니다.

### <a name="remarks"></a>설명

이 함수는 Windows 컨트롤에서 지원 되지 않습니다 `ComboBoxEx` . 이 컨트롤에 대 한 자세한 내용은 [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a> CComboBox::D rawItem

소유자 그리기 콤보 상자의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
필요한 그리기 형식에 대 한 정보를 포함 하는 [Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`itemAction`구조체의 멤버는 `DRAWITEMSTRUCT` 수행할 그리기 작업을 정의 합니다. 이 구조에 대 한 설명은 [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 를 참조 하세요.

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. 소유자 그리기 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CComboBox` 합니다. 이 멤버 함수가 종료 되기 전에 응용 프로그램은 *Lpdrawitemstruct*에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a> CComboBox:: FindString

콤보 상자의 목록 상자에서 지정 된 접두사를 포함 하는 첫 번째 문자열을 찾습니다.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>매개 변수

*nStartAfter*<br/>
검색할 첫 번째 항목 앞의 항목에 대 한 0부터 시작 하는 인덱스를 포함 합니다. 검색은 목록 상자의 아래쪽에 도달 하면 목록 상자의 맨 위에서 *Nstartafter*로 지정 된 항목으로 다시 계속 됩니다. -1 인 경우 전체 목록 상자를 처음부터 검색 합니다.

*lpszString*<br/>
검색할 접두사를 포함 하는 null로 끝나는 문자열을 가리킵니다. 검색은 대/소문자를 구분 하지 않으므로이 문자열에는 대 문자와 소문자를 조합 하 여 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

반환 값이 0 보다 크거나 같은 경우 일치 하는 항목의 인덱스 (0부터 시작)입니다. 검색에 실패 한 경우 CB_ERR 됩니다.

### <a name="remarks"></a>설명

이 함수는 Windows 컨트롤에서 지원 되지 않습니다 `ComboBoxEx` . 이 컨트롤에 대 한 자세한 내용은 [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a> CComboBox:: FindStringExact

`FindStringExact`멤버 함수를 호출 하 여 *lpszFind*에 지정 된 문자열과 일치 하는 첫 번째 목록 상자 문자열 (콤보 상자)을 찾습니다.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>매개 변수

*nIndexStart*<br/>
검색할 첫 번째 항목 앞에 있는 항목의 인덱스 (0부터 시작)를 지정 합니다. 검색은 목록 상자의 아래쪽에 도달 하면 목록 상자 맨 위에서 *Nindexstart*로 지정 된 항목으로 다시 계속 됩니다. *Nindexstart* 가-1 인 경우 전체 목록 상자를 처음부터 검색 합니다.

*lpszFind*<br/>
검색할 null로 끝나는 문자열을 가리킵니다. 이 문자열에는 확장명을 포함 하 여 전체 파일 이름이 포함 될 수 있습니다. 검색은 대/소문자를 구분 하지 않으므로이 문자열에는 대 문자와 소문자를 조합 하 여 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

일치 하는 항목의 인덱스 (0부터 시작) 이거나, 검색에 실패 한 경우 CB_ERR입니다.

### <a name="remarks"></a>설명

콤보 상자가 소유자 그리기 스타일을 사용 하 여 만들어졌지만 [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일을 사용 하지 않는 경우는 `FindStringExact` *lpszFind*의 값에 대해 더블 워드 값과 일치 시 키 려 고 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a> CComboBox:: GetComboBoxInfo

개체에 대 한 정보를 검색 `CComboBox` 합니다.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>매개 변수

*pcbi*<br/>
[COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) 메시지의 기능을 에뮬레이트합니다.

## <a name="ccomboboxgetcount"></a><a name="getcount"></a> CComboBox:: GetCount

콤보 상자의 목록 상자 부분에 있는 항목 수를 검색 하려면이 멤버 함수를 호출 합니다.

```
int GetCount() const;
```

### <a name="return-value"></a>반환 값

항목의 수입니다. 반환 된 개수는 마지막 항목의 인덱스 값 보다 하나 큽니다 (인덱스는 0부터 시작). 오류가 발생 하는 경우 CB_ERR 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a> CComboBox:: GetCueBanner

콤보 상자 컨트롤에 대해 표시 되는 큐 텍스트를 가져옵니다.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>매개 변수

*lpszText*\
제한이 큐 배너 텍스트를 받는 버퍼에 대 한 포인터입니다.

*cchText*\
진행 *LpszText* 매개 변수가 가리키는 버퍼의 크기입니다.

### <a name="return-value"></a>반환 값

첫 번째 오버 로드에서 큐 배너 텍스트가 있으면이를 포함 하는 [CString](../../atl-mfc-shared/using-cstring.md) 개체이 고, 그렇지 않으면입니다. 그렇지 않으면 `CString` 길이가 0 인 개체입니다.

또는

두 번째 오버 로드에서이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

큐 텍스트는 콤보 상자 컨트롤의 입력 영역에 표시 되는 프롬프트입니다. 사용자가 입력을 제공할 때까지 큐 텍스트가 표시 됩니다.

이 메서드는 Windows SDK에서 설명 하는 [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) 메시지를 보냅니다.

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a> CComboBox:: GetCurSel

콤보 상자에서 선택 된 항목을 확인 하려면이 멤버 함수를 호출 합니다.

```
int GetCurSel() const;
```

### <a name="return-value"></a>반환 값

콤보 상자의 목록 상자에서 현재 선택 된 항목의 0부터 시작 하는 인덱스 이거나, 선택 된 항목이 없는 경우 CB_ERR입니다.

### <a name="remarks"></a>설명

`GetCurSel` 인덱스를 목록에 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a> CComboBox:: GetDroppedControlRect

`GetDroppedControlRect`멤버 함수를 호출 하 여 드롭다운 콤보 상자에 표시 되는 (드롭다운) 목록 상자의 화면 좌표를 검색 합니다.

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>매개 변수

*lprect*<br/>
좌표를 받을 [RECT 구조체](/windows/win32/api/windef/ns-windef-rect) 를 가리킵니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a> CComboBox:: GetDroppedState

`GetDroppedState`멤버 함수를 호출 하 여 드롭다운 콤보 상자의 목록 상자가 표시 되는지 여부를 확인 합니다.

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>반환 값

목록 상자가 표시 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a> CComboBox:: GetDroppedWidth

콤보 상자의 목록 상자에 허용 되는 최소 너비 (픽셀)를 검색 하려면이 함수를 호출 합니다.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 허용 되는 최소 너비 (픽셀)입니다. 그렇지 않으면 CB_ERR 합니다.

### <a name="remarks"></a>설명

이 함수는 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 또는 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일을 사용 하는 콤보 상자에만 적용 됩니다.

기본적으로 드롭다운 목록 상자에 허용 되는 최소 너비는 0입니다. 허용 되는 최소 너비는 [Setdroppedwidth](#setdroppedwidth)를 호출 하 여 설정할 수 있습니다. 콤보 상자의 목록 상자 부분이 표시 되 면 해당 너비는 허용 되는 최소 너비 또는 콤보 상자 너비 중 더 큰 값입니다.

### <a name="example"></a>예제

  [Setdroppedwidth](#setdroppedwidth)의 예제를 참조 하세요.

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a> CComboBox:: GetEditSel

콤보 상자의 편집 컨트롤에서 현재 선택 된 항목의 시작 및 끝 문자 위치를 가져옵니다.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>반환 값

하위 단어의 시작 위치를 포함 하는 32 비트 값 이며, 상위 단어에서 선택 영역 끝 다음의 첫 번째 nonselected 문자 위치입니다. 편집 컨트롤이 없는 콤보 상자에서이 함수를 사용 하면 CB_ERR 반환 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a> CComboBox:: GetExtendedUI

`GetExtendedUI`멤버 함수를 호출 하 여 콤보 상자에 기본 사용자 인터페이스나 확장 사용자 인터페이스가 있는지 여부를 확인 합니다.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>반환 값

콤보 상자에 확장 사용자 인터페이스가 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

확장 된 사용자 인터페이스는 다음과 같은 방법으로 식별할 수 있습니다.

- 정적 컨트롤을 클릭 하면 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있는 콤보 상자에 대해서만 목록 상자가 표시 됩니다.

- 아래쪽 화살표 키를 누르면 목록 상자가 표시 됩니다 (F4를 사용 하지 않도록 설정 됨).

항목 목록이 표시 되지 않으면 (화살표 키를 사용할 수 없음) 정적 컨트롤의 스크롤이 비활성화 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a> CComboBox:: GetHorizontalExtent

콤보 상자에서 콤보 상자의 목록 상자 부분을 가로로 스크롤할 수 있는 너비 (픽셀)를 검색 합니다.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>반환 값

콤보 상자의 목록 상자 부분에 대 한 스크롤 가능한 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

이는 콤보 상자의 목록 상자 부분에 가로 스크롤 막대가 있는 경우에만 적용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a> CComboBox:: GetItemData

지정 된 콤보 상자 항목과 연결 된 응용 프로그램 제공 32 비트 값을 검색 합니다.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
콤보 상자의 목록 상자에 있는 항목의 0부터 시작 하는 인덱스를 포함 합니다.

### <a name="return-value"></a>반환 값

항목과 연결 된 32 비트 값 또는 오류가 발생 하는 경우 CB_ERR입니다.

### <a name="remarks"></a>설명

32 비트 값은 [Setitemdata](#setitemdata) 멤버 함수 호출의 *dwItemData* 매개 변수를 사용 하 여 설정할 수 있습니다. `GetItemDataPtr`검색할 32 비트 값이 포인터 () 인 경우 멤버 함수를 사용 **`void`** <strong>\*</strong> 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a> CComboBox:: GetItemDataPtr

지정 된 콤보 상자 항목과 연결 된 응용 프로그램 제공 32 비트 값을 포인터로 검색 합니다 ( **`void`** <strong>\*</strong> ).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
콤보 상자의 목록 상자에 있는 항목의 0부터 시작 하는 인덱스를 포함 합니다.

### <a name="return-value"></a>반환 값

포인터를 검색 하거나, 오류가 발생 하면-1을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a> CComboBox:: GetItemHeight

`GetItemHeight`멤버 함수를 호출 하 여 콤보 상자에서 목록 항목의 높이를 검색 합니다.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
높이를 검색할 콤보 상자의 구성 요소를 지정 합니다. *N index* 매개 변수가-1 이면 콤보 상자의 편집 컨트롤 (또는 정적 텍스트) 부분의 높이가 검색 됩니다. 콤보 상자에 [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있는 경우 *n 인덱스* 는 해당 높이를 검색할 목록 항목의 인덱스 (0부터 시작)를 지정 합니다. 그렇지 않으면 *n 인덱스* 를 0으로 설정 해야 합니다.

### <a name="return-value"></a>반환 값

콤보 상자에서 지정 된 항목의 높이 (픽셀)입니다. 오류가 발생할 경우 반환 값은 CB_ERR입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a> CComboBox:: GetLBText

콤보 상자의 목록 상자에서 문자열을 가져옵니다.

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
복사할 목록 상자 문자열의 인덱스 (0부터 시작)를 포함 합니다.

*lpszText*<br/>
는 문자열을 받을 버퍼를 가리킵니다. 버퍼에는 문자열과 종료 null 문자를 위한 충분 한 공간이 있어야 합니다.

*rString*<br/>
에 대 한 참조를 `CString`입니다.

### <a name="return-value"></a>반환 값

종료 null 문자를 제외한 문자열의 길이 (바이트)입니다. *Nindex* 가 유효한 인덱스를 지정 하지 않는 경우 반환 값은 CB_ERR입니다.

### <a name="remarks"></a>설명

이 멤버 함수의 두 번째 폼은 `CString` 항목의 텍스트를 사용 하 여 개체를 채웁니다.
*Nindex* 가 잘못 된 경우이 함수는 예외를 throw `E_INVALIDARG` 합니다 (오류 코드: `-2147024809` , `0x80070057` ).

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a> CComboBox:: GetLBTextLen

콤보 상자의 목록 상자에 있는 문자열의 길이를 가져옵니다.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
목록 상자 문자열의 인덱스 (0부터 시작)를 포함 합니다.

### <a name="return-value"></a>반환 값

종료 null 문자를 제외 하 고 문자열의 길이 (바이트)입니다. *Nindex* 가 유효한 인덱스를 지정 하지 않는 경우 반환 값은 CB_ERR입니다.

### <a name="example"></a>예제

  [Ccombobox:: GetLBText](#getlbtext)의 예제를 참조 하세요.

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a> CComboBox:: GetLocale

콤보 상자에서 사용 하는 로캘을 검색 합니다.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>반환 값

콤보 상자에 있는 문자열의 LCID (로캘 id) 값입니다.

### <a name="remarks"></a>설명

예를 들어, 로캘는 정렬 된 콤보 상자에서 문자열의 정렬 순서를 결정 하는 데 사용 됩니다.

### <a name="example"></a>예제

  [Ccombobox:: SetLocale](#setlocale)의 예제를 참조 하세요.

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a> CComboBox:: GetMinVisible

현재 콤보 상자 컨트롤의 드롭다운 목록에 표시 되는 최소 항목 수를 가져옵니다.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>반환 값

현재 드롭다운 목록에 표시 되는 최소 항목 수입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) 메시지를 보냅니다.

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a> CComboBox:: GetTopIndex

콤보 상자의 목록 상자 부분에서 표시 되는 첫 번째 항목의 0부터 시작 하는 인덱스를 검색 합니다.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>반환 값

성공 하면 콤보 상자의 목록 상자 부분에 표시 되는 첫 번째 항목의 0부터 시작 하는 인덱스이 고, 그렇지 않으면 CB_ERR입니다.

### <a name="remarks"></a>설명

처음에는 항목 0이 목록 상자의 맨 위에 있지만 목록 상자를 스크롤하면 다른 항목이 맨 위에 있을 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a> CComboBox:: InitStorage

콤보 상자의 목록 상자 부분에 목록 상자 항목을 저장할 메모리를 할당 합니다.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>매개 변수

*nItems*<br/>
추가할 항목 수를 지정 합니다.

*nBytes*<br/>
항목 문자열에 할당할 메모리 크기 (바이트)를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 메모리 재할당이 필요 하기 전에 콤보 상자의 목록 상자 부분에서 저장할 수 있는 최대 항목 수이 고, 그렇지 않으면 CB_ERRSPACE 사용 가능한 메모리가 부족 하다는 것을 의미 합니다.

### <a name="remarks"></a>설명

의 목록 상자 부분에 많은 수의 항목을 추가 하기 전에이 함수를 호출 `CComboBox` 합니다.

Windows 95/98에만 해당: *wParam* 매개 변수는 16 비트 값으로 제한 됩니다. 즉, 목록 상자에는 32767 개 이상의 항목이 포함 될 수 없습니다. 항목 수가 제한 되지만 목록 상자에 있는 항목의 총 크기는 사용 가능한 메모리에 의해서만 제한 됩니다.

이 함수는 항목 수가 많은 (100 이상) 목록 상자의 초기화 속도를 높이는 데 도움이 됩니다. 다음 [Addstring](#addstring), [Insertstring](#insertstring)및 [Dir](#dir) 함수에서 가장 짧은 시간을 사용 하도록 지정 된 메모리 양을 사전 할당 합니다. 매개 변수에 대 한 예상 값을 사용할 수 있습니다. 더 많이 추정 하면 몇 가지 추가 메모리가 할당 됩니다. 간과 하면 미리 할당 된 금액을 초과 하는 항목에 일반적인 할당이 사용 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a> CComboBox:: InsertString

콤보 상자의 목록 상자에 문자열을 삽입합니다.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
문자열을 받을 목록 상자의 위치에 대한 0부터 시작하는 인덱스를 포함합니다. 이 매개 변수가-1 이면 문자열이 목록의 끝에 추가 됩니다.

*lpszString*<br/>
삽입할 null 종료 문자열을 가리킵니다.

### <a name="return-value"></a>반환 값

문자열이 삽입된 위치의 0부터 시작하는 인덱스입니다. 오류가 발생할 경우 반환 값은 CB_ERR입니다. 공간이 부족하여 새 문자열을 저장할 수 없는 경우 반환 값은 CB_ERRSPACE입니다.

### <a name="remarks"></a>설명

[AddString](#addstring) 멤버 함수와 달리 `InsertString` 멤버 함수에서는 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일의 목록이 정렬되지 않습니다.

> [!NOTE]
> 이 함수는 Windows 컨트롤에서 지원 되지 않습니다 `ComboBoxEx` . 이 컨트롤에 대 한 자세한 내용은 [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a> CComboBox:: 개 텍스트

사용자가 콤보 상자의 편집 컨트롤에 입력할 수 있는 텍스트의 길이 (바이트)를 제한 합니다.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>매개 변수

*nMaxChars*<br/>
사용자가 입력할 수 있는 텍스트의 길이 (바이트)를 지정 합니다. 이 매개 변수가 0 이면 텍스트 길이가 65535 바이트로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값입니다. 스타일 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 또는 편집 컨트롤이 없는 콤보 상자의 콤보 상자에 대해 호출 하는 경우 반환 값은 CB_ERR 됩니다.

### <a name="remarks"></a>설명

콤보 상자에 [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)스타일이 없으면 텍스트 제한을 편집 컨트롤의 크기 보다 크게 설정 해도 아무런 효과가 없습니다.

`LimitText` 사용자가 입력할 수 있는 텍스트만 제한 합니다. 메시지가 전송 될 때 편집 컨트롤에 이미 있는 텍스트에는 영향을 주지 않으며, 목록 상자에서 문자열을 선택할 때 편집 컨트롤에 복사 되는 텍스트의 길이에도 영향을 주지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a> CComboBox:: MeasureItem

소유자 그리기 스타일을 사용 하는 콤보 상자를 만들 때 프레임 워크에서 호출 됩니다.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct) 구조체에 대 한 긴 포인터입니다.

### <a name="remarks"></a>설명

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. 이 멤버 함수를 재정의 하 고 구조를 채워서 `MEASUREITEMSTRUCT` 콤보 상자의 목록 상자 크기를 창에 알립니다. [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일을 사용 하 여 콤보 상자를 만든 경우 프레임 워크는 목록 상자의 각 항목에 대해이 멤버 함수를 호출 합니다. 그렇지 않으면이 멤버는 한 번만 호출 됩니다.

[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) 멤버 함수를 사용 하 여 만든 소유자 그리기 콤보 상자에 CBS_OWNERDRAWFIXED 스타일을 사용 하는 `CWnd` 경우 추가 프로그래밍 고려 사항이 수반 됩니다. [기술 참고 14](../../mfc/tn014-custom-controls.md)의 설명을 참조 하십시오.

구조체에 대 한 설명은 [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 를 참조 하세요 `MEASUREITEMSTRUCT` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a> CComboBox::P aste

클립보드의 데이터를 현재 커서 위치에 있는 콤보 상자의 편집 컨트롤에 삽입 합니다.

```cpp
void Paste();
```

### <a name="remarks"></a>설명

클립보드에 CF_TEXT 형식의 데이터가 포함 되어 있는 경우에만 데이터가 삽입 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a> CComboBox:: ResetContent

콤보 상자의 목록 상자와 편집 컨트롤에서 모든 항목을 제거 합니다.

```cpp
void ResetContent();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a> CComboBox:: SelectString

콤보 상자의 목록 상자에서 문자열을 검색 하 고, 문자열이 있으면 목록 상자에서 문자열을 선택 하 여 편집 컨트롤에 복사 합니다.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>매개 변수

*nStartAfter*<br/>
검색할 첫 번째 항목 앞의 항목에 대 한 0부터 시작 하는 인덱스를 포함 합니다. 검색은 목록 상자의 아래쪽에 도달 하면 목록 상자의 맨 위에서 *Nstartafter*로 지정 된 항목으로 다시 계속 됩니다. -1 인 경우 전체 목록 상자를 처음부터 검색 합니다.

*lpszString*<br/>
검색할 접두사를 포함 하는 null로 끝나는 문자열을 가리킵니다. 검색은 대/소문자를 구분 하지 않으므로이 문자열에는 대 문자와 소문자를 조합 하 여 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

문자열을 찾은 경우 선택한 항목의 인덱스 (0부터 시작)입니다. 검색에 실패 한 경우 반환 값은 CB_ERR 되며 현재 선택 항목은 변경 되지 않습니다.

### <a name="remarks"></a>설명

문자열은 처음 문자 (시작 지점)에서 접두사 문자열의 문자와 일치 하는 경우에만 선택 됩니다.

`SelectString`및 `FindString` 멤버 함수는 모두 문자열을 찾았지만 `SelectString` 멤버 함수는 문자열도 선택 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a> CComboBox:: SetCueBanner

콤보 상자 컨트롤에 대해 표시 되는 큐 텍스트를 설정 합니다.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*lpszText*\
진행 큐 텍스트를 포함 하는 null로 끝나는 버퍼에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

큐 텍스트는 콤보 상자 컨트롤의 입력 영역에 표시 되는 프롬프트입니다. 사용자가 입력을 제공할 때까지 큐 텍스트가 표시 됩니다.

이 메서드는 Windows SDK에서 설명 하는 [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 콤보 상자 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_combobox*를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 콤보 상자 컨트롤에 대 한 큐 배너를 설정 합니다.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a> CComboBox:: SetCurSel

콤보 상자의 목록 상자에서 문자열을 선택 합니다.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>매개 변수

*nSelect*<br/>
선택할 문자열의 인덱스 (0부터 시작)를 지정 합니다. -1 인 경우 목록 상자에서 현재 선택한 내용이 제거 되 고 편집 컨트롤이 지워집니다.

### <a name="return-value"></a>반환 값

메시지에 성공 하면 선택 된 항목의 0부터 시작 하는 인덱스입니다. *내보내세요* 가 목록의 항목 수보다 크거나 *내보내세요* 이-1로 설정 된 경우 반환 값은 CB_ERR입니다 .이는 선택을 취소 합니다.

### <a name="remarks"></a>설명

필요한 경우 목록 상자가 표시 되는 경우 목록 상자에서 문자열을 뷰로 스크롤합니다. 콤보 상자의 편집 컨트롤에 있는 텍스트는 새 선택 항목을 반영 하도록 변경 됩니다. 목록 상자에서 이전에 선택한 내용이 제거 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a> CComboBox:: SetDroppedWidth

콤보 상자의 목록 상자에 허용 되는 최소 너비 (픽셀)를 설정 하려면이 함수를 호출 합니다.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
콤보 상자의 목록 상자 부분에 허용 되는 최소 너비 (픽셀)입니다.

### <a name="return-value"></a>반환 값

성공 하면 목록 상자의 새 너비이 고 CB_ERR 그렇지 않으면입니다.

### <a name="remarks"></a>설명

이 함수는 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 또는 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일을 사용 하는 콤보 상자에만 적용 됩니다.

기본적으로 드롭다운 목록 상자에 허용 되는 최소 너비는 0입니다. 콤보 상자의 목록 상자 부분이 표시 되 면 해당 너비는 허용 되는 최소 너비 또는 콤보 상자 너비 중 더 큰 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a> CComboBox:: SetEditSel

콤보 상자의 편집 컨트롤에서 문자를 선택 합니다.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>매개 변수

*nStartChar*<br/>
시작 위치를 지정 합니다. 시작 위치를-1로 설정 하면 모든 기존 선택 항목이 제거 됩니다.

*nEndChar*<br/>
끝 위치를 지정 합니다. 끝 위치가-1로 설정 된 경우 편집 컨트롤에서 시작 위치부터 마지막 문자 까지의 모든 텍스트가 선택 됩니다.

### <a name="return-value"></a>반환 값

멤버 함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다. `CComboBox`이 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있거나 목록 상자가 없는 경우 CB_ERR입니다.

### <a name="remarks"></a>설명

위치는 0부터 시작 합니다. 편집 컨트롤의 첫 번째 문자를 선택 하려면 시작 위치를 0으로 지정 합니다. 끝 위치는 선택할 마지막 문자 바로 다음에 있는 문자입니다. 예를 들어 편집 컨트롤의 처음 4 개 문자를 선택 하려면 0의 시작 위치와 끝 위치 4를 사용 합니다.

> [!NOTE]
> 이 함수는 Windows 컨트롤에서 지원 되지 않습니다 `ComboBoxEx` . 이 컨트롤에 대 한 자세한 내용은 [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK를 참조 하세요.

### <a name="example"></a>예제

  [Ccombobox:: GetEditSel](#geteditsel)의 예제를 참조 하세요.

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a> CComboBox:: SetExtendedUI

`SetExtendedUI` 멤버 함수를 호출하여 기본 사용자 인터페이스 또는 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 또는 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있는 콤보 상자의 확장 사용자 인터페이스를 선택합니다.

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>매개 변수

*bExtended*<br/>
콤보 상자에서 확장 된 사용자 인터페이스를 사용할지 아니면 기본 사용자 인터페이스를 사용할지를 지정 합니다. TRUE 값은 확장 사용자 인터페이스를 선택 합니다. FALSE 값은 표준 사용자 인터페이스를 선택 합니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 CB_OKAY이 고, 오류가 발생 하면 CB_ERR입니다.

### <a name="remarks"></a>설명

확장 된 사용자 인터페이스는 다음과 같은 방법으로 식별할 수 있습니다.

- 정적 컨트롤을 클릭 하면 CBS_DROPDOWNLIST 스타일이 있는 콤보 상자에 대해서만 목록 상자가 표시 됩니다.

- 아래쪽 화살표 키를 누르면 목록 상자가 표시 됩니다 (F4를 사용 하지 않도록 설정 됨).

항목 목록이 표시 되지 않는 경우 (화살표 키를 사용할 수 없음) 정적 컨트롤의 스크롤이 비활성화 됩니다.

### <a name="example"></a>예제

  [Ccombobox:: GetExtendedUI](#getextendedui)의 예제를 참조 하세요.

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a> CComboBox:: SetHorizontalExtent

콤보 상자의 목록 상자 부분을 가로로 스크롤할 수 있는 너비 (픽셀)를 설정 합니다.

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>매개 변수

*nExtent*<br/>
콤보 상자의 목록 상자 부분을 가로로 스크롤할 수 있는 픽셀 수를 지정 합니다.

### <a name="remarks"></a>설명

목록 상자의 너비가이 값 보다 작으면 가로 스크롤 막대가 목록 상자에서 항목을 가로로 스크롤합니다. 목록 상자의 너비가이 값 보다 크거나 같으면 가로 스크롤 막대가 숨겨지거나, 콤보 상자에 [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 사용 되지 않는 경우에는이 고, 그렇지 않으면입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a> CComboBox:: SetItemData

콤보 상자의 지정 된 항목과 연결 된 32 비트 값을 설정 합니다.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
설정할 항목의 인덱스 (0부터 시작)를 포함 합니다.

*dwItemData*<br/>
항목에 연결할 새 값을 포함 합니다.

### <a name="return-value"></a>반환 값

오류가 발생 하면 CB_ERR 합니다.

### <a name="remarks"></a>설명

`SetItemDataPtr`32 비트 항목이 포인터인 경우 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a> CComboBox:: SetItemDataPtr

콤보 상자의 지정 된 항목과 연결 된 32 비트 값을 지정 된 포인터 ()로 설정 합니다 **`void`** <strong>\*</strong> .

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
항목에 대 한 0부터 시작 하는 인덱스를 포함 합니다.

*pData*<br/>
항목과 연결할 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

오류가 발생 하면 CB_ERR 합니다.

### <a name="remarks"></a>설명

항목이 추가 되거나 제거 되 면 콤보 상자 내의 항목의 상대 위치가 변경 될 수 있지만이 포인터는 콤보 상자의 수명 동안 유효한 상태로 유지 됩니다. 따라서 상자 내의 항목 인덱스는 변경 될 수 있지만 포인터는 안정적으로 유지 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a> CComboBox:: SetItemHeight

멤버 함수를 호출 하 여 콤보 `SetItemHeight` 상자에 목록 항목의 높이를 설정 하거나 콤보 상자의 편집 컨트롤 (또는 정적 텍스트) 부분의 높이를 설정 합니다.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
콤보 상자의 편집 컨트롤 (또는 정적 텍스트) 부분 또는 목록 항목의 높이가 설정 되어 있는지 여부를 지정 합니다.

콤보 상자에 [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일이 있는 경우 *n 인덱스* 는 높이가 설정 될 목록 항목의 인덱스 (0부터 시작)를 지정 합니다. 그렇지 않으면 *Nindex* 가 0 이어야 하 고 모든 목록 항목의 높이가 설정 됩니다.

*Nindex* 가-1 이면 콤보 상자의 편집 컨트롤 또는 정적 텍스트 부분의 높이가 설정 됩니다.

*cyItemHeight*<br/>
*Nindex*로 식별 되는 콤보 상자 구성 요소의 높이 (픽셀 단위)를 지정 합니다.

### <a name="return-value"></a>반환 값

인덱스 또는 높이가 잘못 된 경우를 CB_ERR 합니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

콤보 상자의 편집 컨트롤 (또는 정적 텍스트) 부분의 높이는 목록 항목의 높이와 독립적으로 설정 됩니다. 응용 프로그램은 편집 컨트롤 (또는 정적 텍스트) 부분의 높이가 특정 목록 상자 항목의 높이 보다 작은 지 확인 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a> CComboBox:: SetLocale

이 콤보 상자의 로캘 식별자를 설정 합니다.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>매개 변수

*nNewLocale*<br/>
콤보 상자에 대해 설정할 새 LCID (로캘 id) 값입니다.

### <a name="return-value"></a>반환 값

이 콤보 상자의 이전 로캘 식별자 (LCID) 값입니다.

### <a name="remarks"></a>설명

`SetLocale`가 호출 되지 않은 경우에는 시스템에서 기본 로캘을 가져옵니다. 이 시스템 기본 로캘은 제어판의 국가별 또는 국가별 응용 프로그램을 사용 하 여 수정할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a> CComboBox:: SetMinVisibleItems

현재 콤보 상자 컨트롤의 드롭다운 목록에 표시 되는 최소 항목 수를 설정 합니다.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>매개 변수

*iMinVisible 않음*\
진행 표시 되는 최소 항목 수를 지정 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 콤보 상자 컨트롤에 프로그래밍 방식으로 액세스 하는 데 사용 되는 변수 *m_combobox*를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 콤보 상자 컨트롤의 드롭다운 목록에 20 개 항목을 삽입 합니다. 그런 다음 사용자가 드롭다운 화살표를 누를 때 최소 10 개의 항목을 표시 하도록 지정 합니다.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a> CComboBox:: SetTopIndex

콤보 상자의 목록 상자 부분에 특정 항목이 표시 되는지 확인 합니다.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
목록 상자 항목의 인덱스 (0부터 시작)를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 고, 오류가 발생 하면 CB_ERR입니다.

### <a name="remarks"></a>설명

시스템은 *Nindex* 로 지정 된 항목이 목록 상자 위쪽에 나타나거나 최대 스크롤 범위에 도달할 때까지 목록 상자를 스크롤합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a> CComboBox:: ShowDropDown

[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 또는 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일을 포함 하는 콤보 상자의 목록 상자를 표시 하거나 숨깁니다.

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>매개 변수

*bShowIt*<br/>
드롭다운 목록 상자를 표시 하거나 숨길지 여부를 지정 합니다. 값이 TRUE 이면 목록 상자가 표시 됩니다. FALSE 값은 목록 상자를 숨깁니다.

### <a name="remarks"></a>설명

기본적으로이 스타일의 콤보 상자에는 목록 상자가 표시 됩니다.

이 멤버 함수는 [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 스타일을 사용 하 여 만든 콤보 상자에는 영향을 주지 않습니다.

### <a name="example"></a>예제

  [Ccombobox:: GetDroppedState](#getdroppedstate)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CButton 클래스](../../mfc/reference/cbutton-class.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)<br/>
[CListBox 클래스](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 클래스](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 클래스](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)
