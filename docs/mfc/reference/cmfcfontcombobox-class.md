---
description: '자세한 정보: Cmfc글꼴 Combobox 클래스'
title: Cmfc글꼴 Combobox 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: dc8e6d2a3c2c10d59cc6b7ce173d66df8b27ae62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265430"
---
# <a name="cmfcfontcombobox-class"></a>Cmfc글꼴 Combobox 클래스

`CMFCFontComboBox`클래스는 글꼴 목록이 포함 된 콤보 상자 컨트롤을 만듭니다.

## <a name="syntax"></a>구문

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfc글꼴 Combobox:: Cmfc글꼴 Combobox](#cmfcfontcombobox)|`CMFCFontComboBox` 개체를 생성합니다.|
|`CMFCFontComboBox::~CMFCFontComboBox`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|현재 글꼴 콤보 상자 컨트롤의 정렬 된 목록 상자에서 새 항목의 상대 위치를 확인 하기 위해 프레임 워크에서 호출 됩니다. ( [Ccombobox:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)을 재정의 합니다.)|
|`CMFCFontComboBox::DrawItem`|현재 글꼴 콤보 상자 컨트롤에 지정 된 항목을 그리기 위해 프레임 워크에서 호출 됩니다. ( [Ccombobox::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem)를 재정의 합니다.)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|현재 선택 된 글꼴에 대 한 정보를 검색 합니다.|
|`CMFCFontComboBox::MeasureItem`|현재 글꼴 콤보 상자 컨트롤에서 목록 상자의 크기를 창에 알리기 위해 프레임 워크에서 호출 됩니다. ( [Ccombobox:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)를 재정의 합니다.)|
|`CMFCFontComboBox::PreTranslateMessage`|창 메시지가 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수로 디스패치 되기 전에 변환 합니다. ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 재정의합니다.)|
|[Cmfc글꼴 Combobox:: SelectFont](#selectfont)|글꼴 콤보 상자에서 지정 된 조건과 일치 하는 글꼴을 선택 합니다.|
|[CMFCFontComboBox::Setup](#setup)|글꼴 콤보 상자의 항목 목록을 초기화 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|현재 글꼴 콤보 상자에서 항목 레이블을 그리는 데 사용할 글꼴을 프레임 워크에 표시 합니다.|

## <a name="remarks"></a>설명

`CMFCFontComboBox`대화 상자에서 개체를 사용 하려면 `CMFCFontComboBox` 대화 상자 클래스에 변수를 추가 합니다. 그런 다음 대화 상자 클래스의 `OnInitDialog` 메서드에서 [CMFCFontComboBox::Setup](#setup)를 호출하여 콤보상자 컨트롤의 항목목록을 초기화합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxfontcombobox

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a> Cmfc글꼴 Combobox:: Cmfc글꼴 Combobox

`CMFCFontComboBox` 개체를 생성합니다.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a> Cmfc글꼴 Combobox:: GetSelFont

현재 선택 된 글꼴에 대 한 정보를 검색 합니다.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>반환 값

글꼴을 설명 하는 [CMFCFontInfo 클래스](../../mfc/reference/cmfcfontinfo-class.md) 개체에 대 한 포인터입니다. 콤보 상자에서 글꼴을 선택 하지 않은 경우 NULL 일 수 있습니다.

### <a name="remarks"></a>설명

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a> Cmfc글꼴 Combobox:: m_bDrawUsingFont

현재 글꼴 콤보 상자에서 항목 레이블을 그리는 데 사용할 글꼴을 프레임 워크에 표시 합니다.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>설명

프레임 워크가 동일한 글꼴을 사용 하 여 각 항목 레이블을 그리려면이 멤버를 TRUE로 설정 합니다. 이 멤버를 FALSE로 설정 하 여 프레임 워크가 레이블과 동일한 이름을 가진 글꼴을 사용 하 여 각 항목 레이블을 그리도록 합니다. 이 멤버의 기본값은 FALSE입니다.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a> Cmfc글꼴 Combobox:: SelectFont

글꼴 콤보 상자에서 지정 된 조건과 일치 하는 글꼴을 선택 합니다.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>매개 변수

*pDesc*<br/>
진행 글꼴 설명 개체를 가리킵니다.

*lpszName*<br/>
진행 글꼴 이름을 지정 합니다.

*nCharSet*<br/>
진행 문자 집합을 지정 합니다. 기본값은 DEFAULT_CHARSET입니다. 자세한 내용은 `lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체의 멤버를 참조 하십시오.

### <a name="return-value"></a>반환 값

글꼴 콤보 상자의 항목이 지정 된 글꼴 설명 개체 또는 글꼴 이름과 문자 집합과 일치 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 글꼴 콤보 상자에서 지정 된 글꼴에 해당 하는 항목을 선택 하 고 스크롤합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `SelectFont` `CMFCFontComboBox` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a> Cmfc글꼴 Combobox:: 설치

글꼴 콤보 상자의 항목 목록을 초기화 합니다.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>매개 변수

*nFontType*<br/>
진행 글꼴 유형을 지정 합니다. 기본값은 DEVICE_FONTTYPE, RASTER_FONTTYPE 및 TRUETYPE_FONTTYPE의 비트 조합 (OR)입니다.

*nCharSet*<br/>
진행 글꼴 문자 집합을 지정 합니다. 기본값은 DEFAULT_CHARSET입니다.

*nPitchAndFamily*<br/>
진행 글꼴 피치 및 패밀리를 지정 합니다. 기본값은 DEFAULT_PITCH입니다.

### <a name="return-value"></a>반환 값

글꼴 콤보 상자가 성공적으로 초기화 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 매개 변수와 일치 하는 현재 설치 된 글꼴을 열거 하 고 글꼴 콤보 상자에 해당 글꼴 이름을 삽입 하 여 글꼴 콤보 상자를 초기화 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스에서 메서드를 사용 하는 방법을 보여 줍니다 `Setup` `CMFCFontComboBox` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc의 글꼴 Combobox 클래스](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo 클래스](../../mfc/reference/cmfcfontinfo-class.md)
