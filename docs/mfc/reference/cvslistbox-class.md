---
description: '자세히 알아보기: CVSListBox 클래스'
title: CVSListBox 클래스
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 6912eccd4cc8e7c78407d0cda0a0dc1305d0bde8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344980"
---
# <a name="cvslistbox-class"></a>CVSListBox 클래스

`CVSListBox`클래스는 편집할 수 있는 목록 컨트롤을 지원 합니다.

## <a name="syntax"></a>구문

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CVSListBox:: CVSListBox](#cvslistbox)|`CVSListBox` 개체를 생성합니다.|
|`CVSListBox::~CVSListBox`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CVSListBox:: AddItem](#additem)|목록 컨트롤에 문자열을 추가 합니다. ( `CVSListBoxBase::AddItem`을 재정의합니다.)|
|[CVSListBox:: EditItem](#edititem)|목록 컨트롤 항목의 텍스트에 대 한 편집 작업을 시작 합니다. ( `CVSListBoxBase::EditItem`을 재정의합니다.)|
|[CVSListBox:: GetCount](#getcount)|편집 가능한 목록 컨트롤의 문자열 수를 검색 합니다. ( `CVSListBoxBase::GetCount`을 재정의합니다.)|
|[CVSListBox:: GetItemData](#getitemdata)|편집 가능한 목록 컨트롤 항목과 연결 된 응용 프로그램 관련 32 비트 값을 검색 합니다. ( `CVSListBoxBase::GetItemData`을 재정의합니다.)|
|[CVSListBox:: GetItemText](#getitemtext)|편집 가능한 목록 컨트롤 항목의 텍스트를 검색 합니다. ( `CVSListBoxBase::GetItemText`을 재정의합니다.)|
|[CVSListBox:: GetSelItem](#getselitem)|편집 가능한 목록 컨트롤에서 현재 선택 된 항목의 0부터 시작 하는 인덱스를 검색 합니다. ( `CVSListBoxBase::GetSelItem`을 재정의합니다.)|
|`CVSListBox::PreTranslateMessage`|창 메시지가 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수로 디스패치 되기 전에 변환 합니다. 자세한 내용 및 메서드 구문은 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 참조 하세요. ( `CVSListBoxBase::PreTranslateMessage`을 재정의합니다.)|
|[CVSListBox:: RemoveItem](#removeitem)|편집 가능한 목록 컨트롤에서 항목을 제거 합니다. ( `CVSListBoxBase::RemoveItem`을 재정의합니다.)|
|[CVSListBox:: SelectItem](#selectitem)|편집 가능한 목록 컨트롤 문자열을 선택 합니다. ( `CVSListBoxBase::SelectItem`을 재정의합니다.)|
|[CVSListBox:: SetItemData](#setitemdata)|응용 프로그램별 32 비트 값을 편집 가능한 목록 컨트롤 항목과 연결 합니다. ( `CVSListBoxBase::SetItemData`을 재정의합니다.)|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CVSListBox:: GetListHwnd](#getlisthwnd)|현재 포함 된 목록 뷰 컨트롤에 대 한 핸들을 반환 합니다.|

## <a name="remarks"></a>설명

`CVSListBox`클래스는 사용자가 목록 컨트롤에서 항목을 만들거나, 수정 하거나, 삭제 하거나, 다시 정렬할 수 있도록 하는 편집 단추 집합을 제공 합니다.

다음은 편집 가능한 목록 컨트롤의 그림입니다. "Item2" 라는 두 번째 목록 항목은 편집을 위해 선택 됩니다.

![CVSListBox 컨트롤](../../mfc/reference/media/cvslistbox.png "CVSListBox 컨트롤")

리소스 편집기를 사용 하 여 편집할 수 있는 목록 컨트롤을 추가 하는 경우 편집기의 **도구 상자** 창에서 미리 정의 된 편집 가능 목록 컨트롤을 제공 하지 않습니다. 대신 **그룹 상자** 컨트롤과 같은 정적 컨트롤을 추가 합니다. 프레임 워크는 정적 컨트롤을 자리 표시자로 사용 하 여 편집 가능한 목록 컨트롤의 크기와 위치를 지정 합니다.

대화 상자 템플릿에서 편집 가능한 목록 컨트롤을 사용 하려면 `CVSListBox` 대화 상자 클래스에서 변수를 선언 합니다. 변수와 컨트롤 간의 데이터 교환을 지원 하려면 `DDX_Control` 대화 상자의 메서드에서 매크로 항목을 정의 `DoDataExchange` 합니다. 편집 가능 목록 컨트롤은 기본적으로 편집 단추 없이 만들어집니다. 상속 된 CVSListBoxBase:: SetStandardButtons 메서드를 사용 하 여 편집 단추를 사용 하도록 설정 합니다.

자세한 내용은 Samples 디렉터리, `New Controls` sample, Page3 및 Page3 파일을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxvslistbox

## <a name="cvslistboxadditem"></a><a name="additem"></a> CVSListBox:: AddItem

목록 컨트롤에 문자열을 추가 합니다.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>매개 변수

*strIext*<br/>
진행 문자열에 대 한 참조입니다.

*dwData*<br/>
진행 문자열과 연결 된 응용 프로그램별 32 비트 값입니다. 기본값은 0입니다.

*iIndex*<br/>
진행 문자열을 보유 하는 위치의 인덱스 (0부터 시작)입니다. *Iindex* 매개 변수가-1 이면 문자열이 목록의 끝에 추가 됩니다. 기본값은 -1입니다.

### <a name="return-value"></a>반환 값

목록 컨트롤에서 문자열 위치의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

[Cvslistbox:: GetItemData](#getitemdata) 메서드를 사용 하 여 *dwdata* 매개 변수로 지정 된 값을 검색 합니다. 이 값은 응용 프로그램 특정 정수 또는 다른 데이터에 대 한 포인터 일 수 있습니다.

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a> CVSListBox:: CVSListBox

`CVSListBox` 개체를 생성합니다.

```
CVSListBox();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cvslistboxedititem"></a><a name="edititem"></a> CVSListBox:: EditItem

목록 컨트롤 항목의 텍스트에 대 한 편집 작업을 시작 합니다.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 목록 컨트롤 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

편집 작업이 성공적으로 시작 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

사용자는 항목의 레이블을 두 번 클릭 하거나 항목에 포커스가 있을 때 **F2** 또는 **스페이스바** 키를 눌러 편집 작업을 시작 합니다.

## <a name="cvslistboxgetcount"></a><a name="getcount"></a> CVSListBox:: GetCount

편집 가능한 목록 컨트롤의 문자열 수를 검색 합니다.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>반환 값

목록 컨트롤의 항목 수입니다.

### <a name="remarks"></a>설명

인덱스는 0부터 시작 하므로 카운트는 마지막 항목의 인덱스 값 보다 하나 큽니다.

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a> CVSListBox:: GetItemData

편집 가능한 목록 컨트롤 항목과 연결 된 응용 프로그램 관련 32 비트 값을 검색 합니다.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 편집 가능한 목록 컨트롤 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 항목에 연결 된 32 비트 값입니다.

### <a name="remarks"></a>설명

[Cvslistbox:: SetItemData](#setitemdata) 또는 [Cvslistbox:: AddItem](#additem) 메서드를 사용 하 여 32 비트 값을 list 컨트롤 항목과 연결 합니다. 이 값은 응용 프로그램 특정 정수 또는 다른 데이터에 대 한 포인터 일 수 있습니다.

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a> CVSListBox:: GetItemText

편집 가능한 목록 컨트롤 항목의 텍스트를 검색 합니다.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 편집 가능한 목록 컨트롤 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 항목의 텍스트를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

### <a name="remarks"></a>설명

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a> CVSListBox:: GetListHwnd

현재 포함 된 목록 뷰 컨트롤에 대 한 핸들을 반환 합니다.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>반환 값

포함 된 목록 뷰 컨트롤에 대 한 핸들입니다.

### <a name="remarks"></a>설명

클래스를 지 원하는 포함 된 목록 뷰 컨트롤에 대 한 핸들을 검색 하려면이 메서드를 사용 `CVSListBox` 합니다.

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a> CVSListBox:: GetSelItem

편집 가능한 목록 컨트롤에서 현재 선택 된 항목의 0부터 시작 하는 인덱스를 검색 합니다.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>반환 값

이 메서드가 성공적으로 수행 되 면 현재 선택 된 항목의 0부터 시작 하는 인덱스이 고, 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a> CVSListBox:: RemoveItem

편집 가능한 목록 컨트롤에서 항목을 제거 합니다.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 편집 가능한 목록 컨트롤 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 항목이 제거 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a> CVSListBox:: SelectItem

편집 가능한 목록 컨트롤 문자열을 선택 합니다.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>매개 변수

*iItem*<br/>
진행 편집 가능한 목록 컨트롤 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 항목을 선택 하 고 필요한 경우 항목을 뷰로 스크롤합니다.

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a> CVSListBox:: SetItemData

응용 프로그램별 32 비트 값을 편집 가능한 목록 컨트롤 항목과 연결 합니다.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 편집 가능한 목록 컨트롤 항목의 인덱스 (0부터 시작)입니다.

*dwData*<br/>
진행 32 비트 값입니다. 이 값은 응용 프로그램 특정 정수 또는 다른 데이터에 대 한 포인터 일 수 있습니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
