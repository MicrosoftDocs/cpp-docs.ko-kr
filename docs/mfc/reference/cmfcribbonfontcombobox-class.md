---
description: '자세한 정보: Cmfc리본 글꼴 콤보 상자 클래스'
title: Cmfc리본 글꼴 콤보 상자 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 8a91f13f4e478512dfab3b9fcb942f96be0b9d9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333467"
---
# <a name="cmfcribbonfontcombobox-class"></a>Cmfc리본 글꼴 콤보 상자 클래스

글꼴 목록이 포함된 콤보 상자를 구현합니다. 콤보 상자를 리본 패널에 배치합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|소멸자|

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|`CMFCRibbonFontComboBox` 개체를 생성하고 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|지정된 글꼴 종류, 문자 집합, 피치 및 패밀리의 글꼴로 리본 글꼴 콤보 상자를 채웁니다.|
|`CMFCRibbonFontComboBox::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|지정된 문자 집합을 반환합니다.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|콤보 상자에 표시할 글꼴 종류를 반환합니다. 유효한 옵션 DEVICE_FONTTYPE, RASTER_FONTTYPE, TRUETYPE_FONTTYPE 또는 이러한 옵션의 비트 조합입니다.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|콤보 상자에 표시되는 글꼴의 피치 및 패밀리를 반환합니다.|
|`CMFCRibbonFontComboBox::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|이전에 지정한 글꼴 종류, 문자 집합, 피치 및 패밀리의 글꼴로 리본 글꼴 콤보 상자를 채웁니다.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|콤보 상자에서 지정된 글꼴을 선택합니다.|

## <a name="remarks"></a>설명

개체를 만든 후에는 `CMFCRibbonFontComboBox` [cmfc리본 패널:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)를 호출 하 여 리본 패널에 추가 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRibbonComboBox

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a> Cmfc리본 글꼴 Combobox:: BuildFonts

리본 메뉴의 콤보 상자를 글꼴로 채웁니다.

```cpp
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>매개 변수

*nFontType*<br/>
진행 추가할 글꼴의 글꼴 유형을 지정 합니다.

*nCharSet*<br/>
진행 추가할 글꼴의 문자 집합을 지정 합니다.

*nPitchAndFamily*<br/>
진행 추가할 글꼴의 피치와 패밀리를 지정 합니다.

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a> Cmfc리본 글꼴 Combobox:: Cmfc리본 글꼴 콤보 상자

[Cmfc리본 글꼴 콤보 상자](../../mfc/reference/cmfcribbonfontcombobox-class.md) 개체를 생성 하 고 초기화 합니다.

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 사용자가 콤보 상자에서 항목을 선택할 때 실행 되는 명령의 명령 ID입니다.

*nFontType*<br/>
진행 콤보 상자에 표시할 글꼴 유형을 지정 합니다. 유효한 옵션 DEVICE_FONTTYPE, RASTER_FONTTYPE, TRUETYPE_FONTTYPE 또는 이러한 옵션의 비트 조합입니다.

*nCharSet*<br/>
진행 콤보 상자의 글꼴을 지정 된 문자 집합에 속하는 글꼴로 필터링 합니다.

*nPitchAndFamily*<br/>
진행 콤보 상자에 표시 되는 글꼴의 피치와 패밀리를 지정 합니다.

*nWidth*<br/>
진행 콤보 상자의 너비를 픽셀 단위로 지정 합니다.

### <a name="remarks"></a>설명

가능한 *N글꼴 형식* 매개 변수 값에 대 한 자세한 내용은 Windows SDK 설명서에서 [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) 를 참조 하세요.

*Ncharset* 에 할당할 수 있는 유효한 문자 집합 및 *nPitchAndFamily* 에 할당할 수 있는 유효한 값에 대 한 자세한 내용은 Windows SDK 설명서의 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 를 참조 하세요.

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a> Cmfc리본 글꼴 Combobox:: Get글꼴 Desc

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>매개 변수

진행 *Iindex*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a> Cmfc리본 글꼴:: RebuildFonts

리본 메뉴의 콤보 상자를 이전에 지정 된 글꼴 형식, 문자 집합, 피치 및 패밀리의 글꼴로 채웁니다.

```cpp
void RebuildFonts();
```

### <a name="remarks"></a>설명

이 클래스의 [생성자](#cmfcribbonfontcombobox) 에서 리본 글꼴 콤보 상자에 포함할 글꼴의 글꼴 종류, 문자 집합, 피치 및 패밀리를 지정 하거나 [cmfcribbon 글꼴 콤보 상자:: buildfonts](#buildfonts)를 호출 하 여 지정할 수 있습니다.

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a> Cmfc리본 글꼴 Combobox:: SetFont

콤보 상자에서 지정된 글꼴을 선택합니다.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>매개 변수

' lpszName *은 선택할 글꼴의 이름을 지정 합니다.

*nCharSet*<br/>
선택한 글꼴의 문자 집합을 지정 합니다.

*bExact*<br/>
글꼴을 선택할 때 문자 집합이 일치 하도록 지정 하려면 TRUE로 설정 합니다. 글꼴을 선택할 때 문자 집합을 무시할 수 있도록 지정 하려면 FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

지정 된 글꼴을 찾아 선택한 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a> Cmfc리본 글꼴 Combobox:: GetCharSet

지정된 문자 집합을 반환합니다.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>반환 값

문자 집합 (Windows SDK 설명서의 LOGFONT 참조).

### <a name="remarks"></a>설명

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a> Cmfc리본 글꼴 Combobox:: Get글꼴 형식

콤보 상자에 표시할 글꼴 종류를 반환합니다. 유효한 옵션 DEVICE_FONTTYPE, RASTER_FONTTYPE, TRUETYPE_FONTTYPE 또는 이러한 옵션의 비트 조합입니다.

```
int GetFontType() const;
```

### <a name="return-value"></a>반환 값

글꼴 형식 (Windows SDK 설명서의 EnumFontFamProc 참조).

### <a name="remarks"></a>설명

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a> Cmfc리본 글꼴:: GetPitchAndFamily

콤보 상자에 표시되는 글꼴의 피치 및 패밀리를 반환합니다.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>반환 값

피치와 제품군 (Windows SDK 설명서의 LOGFONT 참조).

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 Combobox 클래스](../../mfc/reference/cmfcribboncombobox-class.md)
