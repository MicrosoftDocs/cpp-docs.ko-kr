---
description: '자세히 알아보기: CFontDialog 클래스'
title: CFontDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: c1f8637a6106db9220721dffe67a2ed1d53b26b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184350"
---
# <a name="cfontdialog-class"></a>CFontDialog 클래스

글꼴 선택 대화 상자를 응용 프로그램에 통합할 수 있습니다.

## <a name="syntax"></a>구문

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|`CFontDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFontDialog::D oModal](#domodal)|대화 상자를 표시 하 고 사용자가 선택할 수 있게 합니다.|
|[CFontDialog::GetCharFormat](#getcharformat)|선택한 글꼴의 문자 서식을 검색 합니다.|
|[CFontDialog:: GetColor](#getcolor)|선택한 글꼴의 색을 반환 합니다.|
|[CFontDialog:: GetCurrentFont](#getcurrentfont)|현재 선택 된 글꼴의 특성을 구조에 할당 합니다 `LOGFONT` .|
|[CFontDialog::GetFaceName](#getfacename)|선택한 글꼴의 글꼴 이름을 반환 합니다.|
|[CFontDialog:: GetSize](#getsize)|선택한 글꼴의 포인트 크기를 반환 합니다.|
|[CFontDialog::GetStyleName](#getstylename)|선택한 글꼴의 스타일 이름을 반환 합니다.|
|[CFontDialog:: GetWeight](#getweight)|선택한 글꼴의 두께를 반환 합니다.|
|[CFontDialog:: IsBold](#isbold)|글꼴이 굵은 글꼴 인지 여부를 확인 합니다.|
|[CFontDialog:: IsItalic](#isitalic)|글꼴이 기울임꼴 인지 여부를 확인 합니다.|
|[CFontDialog:: IsStrikeOut](#isstrikeout)|취소선과 함께 글꼴을 표시할지 여부를 결정 합니다.|
|[CFontDialog:: IsUnderline](#isunderline)|글꼴에 밑줄이 있는지 여부를 확인 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFontDialog:: m_cf](#m_cf)|개체를 사용자 지정 하는 데 사용 되는 구조체 `CFontDialog` 입니다.|

## <a name="remarks"></a>설명

`CFontDialog`개체는 현재 시스템에 설치 된 글꼴 목록이 포함 된 대화 상자입니다. 사용자는 목록에서 특정 글꼴을 선택할 수 있으며,이 선택은 응용 프로그램에 다시 보고 됩니다.

개체를 생성 하려면 `CFontDialog` 제공 된 생성자를 사용 하거나 새 하위 클래스를 파생 시키고 사용자 지정 생성자를 사용 합니다.

`CFontDialog`개체가 생성 되 면 구조를 사용 `m_cf` 하 여 대화 상자에서 컨트롤의 값 또는 상태를 초기화할 수 있습니다. [M_cf](#m_cf) 구조체의 형식은 [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)입니다. 이 구조에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

대화 상자 개체의 컨트롤을 초기화 한 후 `DoModal` 멤버 함수를 호출 하 여 대화 상자를 표시 하 고 사용자가 글꼴을 선택할 수 있습니다. `DoModal` 사용자가 확인 (IDOK) 또는 취소 (IDCANCEL) 단추를 선택 했는지 여부를 반환 합니다.

`DoModal`에서 IDOK를 반환 하는 경우의 `CFontDialog` 멤버 함수 중 하나를 사용 하 여 사용자가 입력 한 정보를 검색할 수 있습니다.

Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 사용 하 여 대화 상자를 초기화 하는 동안 오류가 발생 했는지 확인 하 고 오류에 대해 자세히 알아볼 수 있습니다. 이 함수에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

`CFontDialog` 는 Windows 버전 3.1 이상과 함께 제공 되는 COMMDLG.DLL 파일을 기반으로 합니다.

대화 상자를 사용자 지정 하려면에서 클래스를 파생 시키고 `CFontDialog` , 사용자 지정 대화 상자 템플릿을 제공 하 고, 메시지 맵을 추가 하 여 확장 된 컨트롤에서 알림 메시지를 처리 합니다. 처리 되지 않은 모든 메시지는 기본 클래스에 전달 되어야 합니다.

후크 함수 사용자 지정은 필요 하지 않습니다.

사용에 대 한 자세한 내용은 `CFontDialog` [일반 대화 상자 클래스](../../mfc/common-dialog-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a> CFontDialog::CFontDialog

`CFontDialog` 개체를 생성합니다.

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*plfInitial*<br/>
글꼴의 일부 특성을 설정할 수 있도록 하는 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 데이터 구조에 대 한 포인터입니다.

*charFormat*<br/>
Rich edit 컨트롤에서 글꼴의 일부 특성을 설정할 수 있도록 하는 [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) 데이터 구조에 대 한 포인터입니다.

*dwFlags*<br/>
하나 이상의 글꼴 선택 플래그를 지정합니다. 비트 OR 연산자를 사용하여 하나 이상의 미리 설정된 값을 결합할 수 있습니다. `m_cf.Flag` 구조체 멤버를 수정하는 경우 기본 동작을 그대로 유지하려면 변경에서 비트 OR 연산자를 사용해야 합니다. 이러한 각 플래그에 대 한 자세한 내용은 Windows SDK [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) 구조체에 대 한 설명을 참조 하십시오.

*Ccprinter*<br/>
프린터 디바이스 컨텍스트에 대한 포인터입니다. 제공하는 경우 이 매개 변수는 글꼴을 선택할 프린터에 대한 프린터 디바이스 컨텍스트를 가리킵니다.

*pParentWnd*<br/>
글꼴 대화 상자의 부모 또는 소유자 창에 대한 포인터입니다.

### <a name="remarks"></a>설명

생성자는 `CHOOSEFONT` 구조의 멤버를 자동으로 채웁니다. 기본값과는 다른 글꼴 대화 상자를 사용하려는 경우에만 이러한 멤버를 변경해야 합니다.

> [!NOTE]
> rich edit 컨트롤이 지원되지 않는 경우에만 이 함수의 첫 번째 버전이 제공됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a> CFontDialog::D oModal

이 함수를 호출 하 여 Windows 공용 글꼴 대화 상자를 표시 하 고 사용자가 글꼴을 선택할 수 있습니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

IDOK 또는 IDCANCEL. IDCANCEL이 반환 되는 경우 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 호출 하 여 오류가 발생 했는지 여부를 확인 합니다.

IDOK 및 IDCANCEL는 사용자가 확인 또는 취소 단추를 선택 했는지 여부를 나타내는 상수입니다.

### <a name="remarks"></a>설명

[M_cf](#m_cf) 구조의 멤버를 설정 하 여 다양 한 글꼴 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

`DoModal`에서 IDOK를 반환 하는 경우 다른 멤버 함수를 호출 하 여 사용자가 대화 상자에 입력 한 설정 또는 정보를 검색할 수 있습니다.

### <a name="example"></a>예제

  [CFontDialog:: CFontDialog](#cfontdialog) 및 [CFontDialog:: getcolor](#getcolor)의 예제를 참조 하세요.

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a> CFontDialog::GetCharFormat

선택한 글꼴의 문자 서식을 검색 합니다.

```cpp
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>매개 변수

*f*<br/>
선택한 글꼴의 문자 서식에 대 한 정보를 포함 하는 [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) 구조체입니다.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a> CFontDialog:: GetColor

선택한 글꼴 색을 검색 하려면이 함수를 호출 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴의 색입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a> CFontDialog:: GetCurrentFont

[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체의 멤버에 현재 선택 된 글꼴의 특성을 할당 하려면이 함수를 호출 합니다.

```cpp
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>매개 변수

*lplf*<br/>
구조체에 대 한 포인터 `LOGFONT` 입니다.

### <a name="remarks"></a>설명

다른 `CFontDialog` 멤버 함수는 현재 글꼴의 개별 특성에 액세스 하기 위해 제공 됩니다.

[DoModal](#domodal)를 호출 하는 동안이 함수가 호출 되 면 현재 선택 항목 (사용자가 대화 상자에서 확인 하거나 변경 한 내용)을 반환 합니다. 에 대 한 호출 후에이 함수가 호출 되 면 `DoModal` ( `DoModal` 가 IDOK를 반환 하는 경우에만) 사용자가 실제로 선택한 항목을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a> CFontDialog::GetFaceName

선택한 글꼴의 글꼴 이름을 검색 하려면이 함수를 호출 합니다.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>반환 값

대화 상자에서 선택한 글꼴의 글꼴 이름 `CFontDialog` 입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a> CFontDialog:: GetSize

선택한 글꼴의 크기를 검색 하려면이 함수를 호출 합니다.

```
int GetSize() const;
```

### <a name="return-value"></a>반환 값

점의 글꼴 크기 (1/10)입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a> CFontDialog::GetStyleName

선택한 글꼴의 스타일 이름을 검색 하려면이 함수를 호출 합니다.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>반환 값

글꼴의 스타일 이름입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a> CFontDialog:: GetWeight

선택한 글꼴의 가중치를 검색 하려면이 함수를 호출 합니다.

```
int GetWeight() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴의 두께입니다.

### <a name="remarks"></a>설명

글꼴의 가중치에 대 한 자세한 내용은 [cfont:: CreateFont](../../mfc/reference/cfont-class.md#createfont)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a> CFontDialog:: IsBold

선택한 글꼴이 굵은 글꼴 인지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴에 굵은 특징이 설정 되어 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a> CFontDialog:: IsItalic

선택한 글꼴이 기울임꼴 인지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴에서 기울임꼴 특성을 사용 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a> CFontDialog:: IsStrikeOut

선택한 글꼴이 취소선과 함께 표시 되는지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴에 취소선 특징이 설정 되어 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a> CFontDialog:: IsUnderline

선택한 글꼴에 밑줄이 있는지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴에 밑줄 특징이 설정 되어 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a> CFontDialog:: m_cf

멤버가 dialog 개체의 특성을 저장 하는 구조체입니다.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>설명

개체를 생성 한 후를 `CFontDialog` 사용 `m_cf` 하 여 멤버 함수를 호출 하기 전에 대화 상자의 다양 한 측면을 수정할 수 있습니다 `DoModal` . 이 구조에 대 한 자세한 내용은 Windows SDK의 [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
