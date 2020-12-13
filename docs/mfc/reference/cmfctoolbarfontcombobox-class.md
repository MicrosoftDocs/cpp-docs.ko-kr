---
description: '자세한 정보: Cmfc추가 정보 Combobox 클래스'
title: Cmfc의 글꼴 Combobox 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 900da03bab8fdc95d93a9c92a14932d7a5bdd9ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331757"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Cmfc의 글꼴 Combobox 클래스

사용자가 시스템 글꼴 목록에서 글꼴을 선택할 수 있는 콤보 상자 컨트롤을 포함 하는 도구 모음 단추입니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[Cmfc작업 상자 글꼴 combobox:: Cmfc작업 상자 글꼴](#cmfctoolbarfontcombobox)|`CMFCToolBarFontComboBox` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc의 글꼴 Combobox:: Get글꼴 Desc](#getfontdesc)|`CMFCFontInfo`콤보 상자에서 지정 된 인덱스의 개체에 대 한 포인터를 반환 합니다.|
|[Cmfc의 글꼴 Combobox:: SetFont](#setfont)|글꼴의 이름 또는 글꼴의 접두사와 문자 집합에 따라 글꼴 콤보 상자의 글꼴을 선택 합니다.|

### <a name="data-members"></a>데이터 멤버

[Cmfc작업 상자 글꼴:: m_nFontHeight](#m_nfontheight)<br/>
글꼴 콤보 상자에 있는 문자의 높이입니다.

## <a name="remarks"></a>설명

도구 모음에 글꼴 콤보 상자 단추를 추가 하려면 다음 단계를 수행 합니다.

1. 부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다.

1. 개체를 생성 `CMFCToolBarFontComboBox` 합니다.

1. AFX_WM_RESETTOOLBAR 메시지를 처리 하는 메시지 처리기에서 [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)를 사용 하 여 원래 단추를 새 콤보 상자 단추로 바꿉니다.

1. [Cmfc: cmfc:: SetFont](#setfont) 메서드를 사용 하 여 콤보 상자에서 선택한 글꼴을 문서의 글꼴과 동기화 합니다.

문서 글꼴을 콤보 상자에서 선택한 글꼴과 동기화 하려면 [Cmfc기능 글꼴 combobox:: GetFontDesc](#getfontdesc) 메서드를 사용 하 여 선택한 글꼴의 특성을 검색 하 고 이러한 특성을 사용 하 여 [cfont 클래스](../../mfc/reference/cfont-class.md) 개체를 만듭니다.

글꼴 콤보 상자 단추는 Win32 함수 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) 를 호출 하 여 시스템에서 사용할 수 있는 화면 및 프린터 글꼴을 결정 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[Cmfc, 글꼴 콤보 상자](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbarfontcombobox

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a> Cmfc작업 상자 글꼴 combobox:: Cmfc작업 상자 글꼴

[Cmfc의 글꼴 콤보 상자](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 개체를 생성 합니다.

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>매개 변수

*uiID*<br/>
진행 콤보 상자의 명령 ID입니다.

*iImage*<br/>
진행 도구 모음 이미지의 인덱스 (0부터 시작)입니다. 이 이미지는 [Cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md) 클래스에서 유지 관리 하는 [Cmfctoolbar images 클래스](../../mfc/reference/cmfctoolbarimages-class.md) 개체에 있습니다.

*nFontType*<br/>
진행 콤보 상자에 포함 되는 글꼴 형식입니다. 이 매개 변수는 다음 값의 조합 (부울 또는)이 될 수 있습니다.

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
진행 DEFAULT_CHARSET로 설정 된 경우 콤보 상자는 모든 문자 집합에서 고유 하 게 명명 된 모든 글꼴을 포함 합니다. (이름이 같은 글꼴이 두 개 있으면 콤보 상자에 둘 중 하나가 포함 됩니다.) 유효한 문자 집합 값으로 설정 하면 콤보 상자에 지정 된 문자 집합의 글꼴만 포함 됩니다. 가능한 문자 집합 목록은 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 를 참조 하세요.

*dwStyle*<br/>
진행 콤보 상자의 스타일입니다. ( [콤보 상자 스타일](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)참조)

*iWidth*<br/>
진행 편집 컨트롤의 너비 (픽셀)입니다.

*nPitchAndFamily*<br/>
진행 DEFAULT_PITCH로 설정 하면 피치와 관계 없이 콤보 상자에 글꼴이 포함 됩니다. FIXED_PITCH 또는 VARIABLE_PITCH으로 설정 된 경우 콤보 상자에는 해당 피치 형식의 글꼴만 포함 됩니다. 글꼴 패밀리를 기준으로 필터링 하는 기능은 현재 지원 되지 않습니다.

*pLstFontsExternal*<br/>
제한이 사용 가능한 글꼴을 저장 하는 [CObList 클래스](../../mfc/reference/coblist-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

일반적으로 `CMFCToolBarFontComboBox` 개체는 사용 가능한 글꼴 목록을 단일 공유 개체에 저장 `CObList` 합니다. 생성자의 두 번째 오버 로드를 사용 하 고 *Plst글꼴* 에 대 한 유효한 포인터를 제공 하는 경우 해당 `CMFCToolBarFontComboBox` 개체는 대신 `CObList` 에 사용 가능한 글꼴을 사용 하 여에 해당 *하는* 를 채웁니다.

### <a name="example"></a>예제

다음 예제에서는 개체를 생성 하는 방법을 보여 줍니다 `CMFCToolBarFontComboBox` . 이 코드 조각은 [워드 패드 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a> Cmfc의 글꼴 Combobox:: Get글꼴 Desc

`CMFCFontInfo`콤보 상자에서 지정 된 인덱스의 개체에 대 한 포인터를 반환 합니다.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
진행 콤보 상자 항목의 인덱스 (0부터 시작)를 지정 합니다.

### <a name="return-value"></a>반환 값

`CMFCFontInfo` 개체에 대한 포인터입니다. *Iindex* 가 유효한 항목 인덱스를 지정 하지 않는 경우 반환 값은 NULL입니다.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a> Cmfc작업 상자 글꼴:: m_nFontHeight

콤보 상자에 소유자 그리기 스타일을 지정 하는 경우 글꼴 콤보 상자에서 문자의 높이 (픽셀)를 지정 합니다.

```
static int m_nFontHeight
```

### <a name="remarks"></a>설명

`m_nFontHeight`변수가 0 이면 콤보 상자의 기본 글꼴에 따라 높이가 자동으로 계산 됩니다. 높이는 기준선 위에 있는 문자의 어센더와 기준선 아래의 문자 디센더를 모두 포함 합니다.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a> Cmfc의 글꼴 Combobox:: SetFont

글꼴 이름 및 매개 변수에 지정 된 문자 집합에 따라 글꼴 콤보 상자의 글꼴을 선택 합니다.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
진행 글꼴 이름 또는 접두사를 지정 합니다.

*nCharSet*<br/>
진행 문자 집합을 지정 합니다.

*bExact*<br/>
진행 *LpszName* 에 글꼴 이름 또는 글꼴 접두사가 포함 되는지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

글꼴이 성공적으로 선택 된 경우 0이 아닌 것입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Bexact* 가 TRUE 이면이 메서드는 *lpszName* 으로 지정한 이름과 정확 하 게 일치 하는 글꼴을 선택 합니다. *Bexact* 가 FALSE 인 경우이 메서드는 *lpszName* 로 지정 된 텍스트로 시작 하 고 *ncharset* 로 지정한 문자 집합을 사용 하는 글꼴을 선택 합니다. *Ncharset* 이 DEFAULT_CHARSET로 설정 된 경우 문자 집합은 무시 되 고 *lpszName* 만 글꼴을 선택 하는 데 사용 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 클래스](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 클래스](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
