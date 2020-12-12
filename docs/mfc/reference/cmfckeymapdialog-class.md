---
description: '자세한 정보: CMFCKeyMapDialog 클래스'
title: CMFCKeyMapDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: e339edb54b9c381dd2b27c9ee3ec7566308ae434
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265235"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog 클래스

`CMFCKeyMapDialog`클래스는 명령을 키보드의 키에 매핑하는 컨트롤을 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCKeyMapDialog:: CMFCKeyMapDialog](#cmfckeymapdialog)|`CMFCKeyMapDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCKeyMapDialog::D oModal](#domodal)|키보드 매핑 대화 상자를 표시 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCKeyMapDialog:: FormatItem](#formatitem)|키 매핑을 설명 하는 문자열을 빌드하기 위해 프레임 워크에서 호출 됩니다. 기본적으로 문자열에는 명령 이름, 사용 된 바로 가기 키 및 바로 가기 키 설명이 포함 되어 있습니다.|
|[CMFCKeyMapDialog:: GetCommandKeys](#getcommandkeys)|지정 된 명령과 연결 된 바로 가기 키의 목록을 포함 하는 문자열을 검색 합니다.|
|[CMFCKeyMapDialog:: OnInsertItem](#oninsertitem)|새 항목이 키보드 매핑 컨트롤을 지 원하는 내부 목록 컨트롤에 삽입 되기 전에 프레임 워크에서 호출 됩니다.|
|[CMFCKeyMapDialog:: OnPrintHeader](#onprintheader)|새 페이지에서 키보드 맵에 대 한 헤더를 인쇄 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCKeyMapDialog:: OnPrintItem](#onprintitem)|키보드 매핑 항목을 인쇄 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCKeyMapDialog:: OnSetColumns](#onsetcolumns)|키보드 매핑 컨트롤을 지 원하는 내부 목록 컨트롤의 열에 대해 캡션을 설정 하기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCKeyMapDialog::P rintKeyMap](#printkeymap)|사용자가 **인쇄** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CMFCKeyMapDialog:: Set\-width](#setcolumnswidth)|키보드 매핑 컨트롤을 지 원하는 내부 목록 컨트롤의 열 너비를 설정 하기 위해 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

클래스를 사용 `CMFCKeyMapDialog` 하 여 크기 조정 가능한 키보드 매핑 대화 상자를 구현 합니다. 대화 상자는 목록 뷰 컨트롤을 사용 하 여 바로 가기 키와 관련 된 명령을 표시 합니다.

`CMFCKeyMapDialog`응용 프로그램에서 클래스를 사용 하려면 주 프레임 창에 대 한 포인터를 생성자에 대 한 매개 변수로 전달 `CMFCKeyMapDialog` 합니다. 그런 다음 메서드를 호출 `DoModal` 하 여 모달 대화 상자를 시작 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxkeymapdialog

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a> CMFCKeyMapDialog:: CMFCKeyMapDialog

`CMFCKeyMapDialog` 개체를 생성합니다.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>매개 변수

*pWndParentFrame*<br/>
진행 개체의 부모 창에 대 한 포인터 `CMFCKeyMapDialog` 입니다.

*베 프린트*<br/>
진행 액셀러레이터 키 목록을 인쇄할 수 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다. 기본값은 FALSE입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCKeyMapDialog` . 이 예제는 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a> CMFCKeyMapDialog::D oModal

키보드 매핑 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

IDOK 또는 IDCANCEL와 같이 [CDialog:: EndDialog](../../mfc/reference/cdialog-class.md#enddialog) 메서드에 전달 되는 부호 있는 정수입니다. 그런 다음 메서드는 대화 상자를 닫습니다. 자세한 내용은 [CDialog::D oModal](../../mfc/reference/cdialog-class.md#domodal)을 참조 하세요.

### <a name="remarks"></a>설명

키보드 매핑 대화 상자를 사용 하 여 다양 한 범주의 명령에 액셀러레이터 키를 선택 하 고 할당할 수 있습니다. 또한 선택한 액셀러레이터 키와 해당 설명을 클립보드에 복사할 수 있습니다.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a> CMFCKeyMapDialog:: FormatItem

키 매핑을 설명 하는 문자열을 빌드하기 위해 프레임 워크에서 호출 됩니다. 기본적으로 문자열에는 명령 이름, 사용 된 바로 가기 키 및 바로 가기 키 설명이 포함 되어 있습니다.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>매개 변수

*nItem*<br/>
진행 키 매핑의 내부 목록에 있는 항목의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

`CString`서식이 지정 된 항목 텍스트를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a> CMFCKeyMapDialog:: GetCommandKeys

문자열 값을 검색 합니다. 문자열에는 지정 된 명령과 연결 된 바로 가기 키의 목록이 포함 되어 있습니다.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>매개 변수

*uiCmdID*<br/>
진행 명령 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 명령과 연결 된 바로 가기 키의 세미콜론으로 구분 된 ('; ') 목록입니다.

### <a name="remarks"></a>설명

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a> CMFCKeyMapDialog:: OnInsertItem

새 항목이 키보드 매핑 컨트롤을 지 원하는 내부 목록 컨트롤에 삽입 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>매개 변수

*pButton*<br/>
진행 키보드 키 조합을 명령 이름과 설명에 매핑하는 데 사용 되는 도구 모음 단추에 대 한 포인터입니다. 키 맵 항목은 내부 목록 컨트롤에 저장 됩니다.

*nItem*<br/>
진행 내부 목록 컨트롤에 새 키 맵 항목을 삽입할 위치를 지정 하는 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a> CMFCKeyMapDialog:: OnPrintHeader

새 페이지에서 키보드 맵에 대 한 헤더를 인쇄 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
진행 프린터에 대 한 장치 컨텍스트입니다.

*nPage*<br/>
진행 인쇄할 페이지 번호입니다.

*cx*<br/>
진행 헤더의 가로 오프셋 (픽셀)입니다.

### <a name="return-value"></a>반환 값

성공 하면 인쇄 된 텍스트의 높이입니다. 자세한 내용은 [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext)의 반환 값 섹션을 참조 하십시오.

### <a name="remarks"></a>설명

프레임 워크는이 메서드를 사용 하 여 키보드 맵을 인쇄 합니다. 기본적으로이 메서드는 페이지 번호, 응용 프로그램 이름 및 대화 상자 제목을 인쇄 합니다.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a> CMFCKeyMapDialog:: OnPrintItem

키보드 매핑 항목을 인쇄 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
진행 프린터의 장치 컨텍스트입니다.

*nItem*<br/>
진행 인쇄할 항목의 인덱스 (0부터 시작)입니다.

*y*<br/>
진행 페이지의 위쪽과 항목의 위치 사이의 세로 오프셋입니다.

*cx*<br/>
진행 페이지의 왼쪽과 항목의 위치 사이의 가로 오프셋입니다.

*bCalcHeight*<br/>
진행 인쇄 항목의 최적 높이를 계산 하려면 TRUE로 설정 합니다. FALSE 이면 인쇄 항목이 기본 공간에 맞게 잘립니다.

### <a name="return-value"></a>반환 값

인쇄 된 항목의 높이입니다.

### <a name="remarks"></a>설명

프레임 워크는이 메서드를 호출 하 여 키 맵 대화 상자 항목을 인쇄 합니다. 기본적으로이 메서드는 항목의 명령 이름, 바로 가기 키 및 명령 설명을 인쇄 합니다.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a> CMFCKeyMapDialog:: OnSetColumns

키보드 매핑 컨트롤을 지 원하는 내부 목록 컨트롤의 열에 대해 캡션을 설정 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>설명

기본적으로이 메서드는 세 리소스에서 열의 캡션을 가져옵니다. 명령 열 캡션은 IDS_AFXBARRES_COMMAND에서, 키 열 캡션은 IDS_AFXBARRES_KEYS에서, 설명 열 캡션은 IDS_AFXBARRES_DESCRIPTION에서 가져온 것입니다.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a> CMFCKeyMapDialog::P rintKeyMap

사용자가 **인쇄** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>설명

`PrintKeyMap`메서드는 키 맵을 인쇄 합니다. 새 인쇄 작업을 시작한 다음 모든 키 매핑이 인쇄 될 때까지 [Cmfckeymapdialog:: OnPrintHeader](#onprintheader) 및 [Cmfckeymapdialog:: onprintitem](#onprintitem) 메서드를 반복적으로 호출 합니다.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a> CMFCKeyMapDialog:: Set\-width

키보드 매핑 컨트롤을 지 원하는 내부 목록 컨트롤의 열 너비를 설정 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>설명

이 메서드는 내부 목록 컨트롤의 열을 기본 너비로 설정 합니다. 먼저 바로 가기 키 열의 너비를 계산 합니다. 그런 다음 나머지 너비의 1/3이 명령 열에 할당 되 고 나머지 2/3는 설명 열에 할당 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 클래스](../../mfc/reference/ckeyboardmanager-class.md)
