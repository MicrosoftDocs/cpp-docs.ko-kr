---
description: '자세한 정보: Cmfcpropertygrid 속성 클래스'
title: Cmfcpropertygrid글꼴 속성 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: cec809636c83ca6fa0e61044de971f9fbea145f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289935"
---
# <a name="cmfcpropertygridfontproperty-class"></a>Cmfcpropertygrid글꼴 속성 클래스

`CMFCPropertyGridFileProperty`클래스는 글꼴 선택 대화 상자를 여는 속성 목록 컨트롤 항목을 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfcpropertygrid글꼴 속성:: Cmfcpropertygrid\-property](#cmfcpropertygridfontproperty)|`CMFCPropertyGridFontProperty` 개체를 생성합니다.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|속성 값의 텍스트 표현에 서식을 지정합니다. [Cmfcpropertygridproperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)를 재정의 합니다.|
|[Cmfcpropertygrid글꼴 속성:: GetColor](#getcolor)|글꼴 대화 상자에서 사용자가 선택 하는 글꼴 색을 검색 합니다.|
|[Cmfcpropertygrid글꼴 속성:: GetLogFont](#getlogfont)|글꼴 대화 상자에서 사용자가 선택 하는 글꼴을 검색 합니다.|
|`CMFCPropertyGridFontProperty::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|`CMFCPropertyGridFontProperty::OnClickButton`|사용자가 속성에 포함된 단추를 클릭하면 프레임워크에서 호출됩니다. [Cmfcpropertygridproperty:: On클릭 단추](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)를 재정의 합니다.|

## <a name="remarks"></a>설명

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpropertygridctrl

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a> Cmfcpropertygrid글꼴 속성:: Cmfcpropertygrid\-property

`CMFCPropertyGridFontProperty` 개체를 생성합니다.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>매개 변수

*strName*<br/>
진행 속성의 이름입니다.

*lf*<br/>
진행 글꼴의 특성을 지정 하는 논리적 글꼴 구조입니다.

*Dw글꼴 Dialogflags*<br/>
진행 속성 값 드롭다운 단추를 클릭할 때 표시 되는 글꼴 대화 상자에 적용 되는 스타일입니다. 기본값은 CF_EFFECTS 및 CF_SCREENFONTS의 비트 조합 (OR)입니다. 자세한 내용은 [CHOOSEFONT 구조체](/windows/win32/api/commdlg/ns-commdlg-choosefontw)의 *Flags* 매개 변수를 참조 하세요.

*lpszDescr*<br/>
진행 Font 속성에 대 한 설명입니다. 기본값은 NULL입니다.

*dwData*<br/>
진행 정수 또는 속성과 연결 된 다른 데이터에 대 한 포인터와 같은 응용 프로그램 관련 데이터입니다. 기본값은 0입니다.

*color*<br/>
진행 글꼴의 색입니다. 기본값은 기본 색입니다.

### <a name="remarks"></a>설명

`CMFCPropertyGridFontProperty`개체는 속성 표 글꼴 컨트롤의 글꼴 속성을 나타냅니다.

### <a name="example"></a>예제

다음 예제에서는가 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCPropertyGridFontProperty` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a> Cmfcpropertygrid글꼴 속성:: GetColor

글꼴 대화 상자에서 사용자가 선택 하는 글꼴 색을 검색 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

선택한 글꼴 색을 나타내는 RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a> Cmfcpropertygrid글꼴 속성:: GetLogFont

글꼴 대화 상자에서 사용자가 선택 하는 글꼴을 검색 합니다.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>반환 값

선택한 글꼴을 설명 하는 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 클래스](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 클래스](../../mfc/reference/cmfcpropertygridproperty-class.md)
