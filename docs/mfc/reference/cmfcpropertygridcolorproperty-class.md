---
description: '자세한 정보: CMFCPropertyGridColorProperty 클래스'
title: CMFCPropertyGridColorProperty 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 7673044a149dc1b5171167ed0854918434651dc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334700"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty 클래스

`CMFCPropertyGridColorProperty` 클래스는 색 선택 항목 대화 상자를 여는 속성 목록 컨트롤 항목을 지원합니다.

## <a name="syntax"></a>구문

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|`CMFCPropertyGridColorProperty` 개체를 생성합니다.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|색 선택 대화 상자에서 *자동* 단추를 사용 하도록 설정 합니다. 표준 자동 단추는 **자동** 으로 레이블이 지정 됩니다.|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|색 선택 대화 상자에서 *기타* 단추를 사용 하도록 설정 합니다. 표준 다른 단추에는 **더 많은 색** 이 지정 됩니다.|
|`CMFCPropertyGridColorProperty::FormatProperty`|속성 값의 텍스트 표현에 서식을 지정합니다. [Cmfcpropertygridproperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)를 재정의 합니다.|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|속성의 현재 색을 가져옵니다.|
|`CMFCPropertyGridColorProperty::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|`CMFCPropertyGridColorProperty::OnClickButton`|사용자가 속성에 포함된 단추를 클릭하면 프레임워크에서 호출됩니다. [Cmfcpropertygridproperty:: On클릭 단추](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)를 재정의 합니다.|
|`CMFCPropertyGridColorProperty::OnDrawValue`|속성 값을 표시하기 위해 프레임워크에서 호출됩니다. [Cmfcpropertygridproperty:: OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue)를 재정의 합니다.|
|`CMFCPropertyGridColorProperty::OnEdit`|사용자가 속성 값을 수정하려고 할 때 프레임워크에서 호출됩니다. [Cmfcpropertygridproperty:: OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit)를 재정의 합니다.|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|편집 가능한 속성 값이 변경되었을 때 프레임워크에서 호출됩니다. [Cmfcpropertygridproperty:: OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue)를 재정의 합니다.|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|속성에 대한 새로운 색을 설정합니다.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|현재 색 속성 표의 열 수를 지정합니다.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|편집 가능한 속성의 원래 값을 설정합니다.|

## <a name="remarks"></a>설명

`CMFCPropertyGridColorProperty` 클래스는 속성 목록 컨트롤에 추가할 수 있는 색 속성을 지원합니다. 자세한 내용은 [Cmfcpropertygridctrl 클래스](../../mfc/reference/cmfcpropertygridctrl-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `CMFCPropertyGridColorProperty` 클래스의 개체를 생성하고 `CMFCPropertyGridColorProperty` 클래스의 다양한 메서드를 사용하여 이 개체를 구성하는 방법을 보여 줍니다. 코드에서는 자동 및 기타 단추를 사용하도록 설정하는 방법과 색 및 열 번호를 설정하는 방법을 설명합니다. 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpropertygridctrl

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a> CMFCPropertyGridColorProperty:: CMFCPropertyGridColorProperty

`CMFCPropertyGridColorProperty` 개체를 생성합니다.

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>매개 변수

*strName*<br/>
진행 속성의 이름입니다.

*color*<br/>
진행 속성의 색 값입니다.

*pPalette*<br/>
진행 색의 색상표에 대 한 포인터입니다. 기본값은 NULL입니다.

*lpszDescr*<br/>
진행 속성 설명입니다. 기본값은 NULL입니다.

*dwData*<br/>
진행 정수 또는 속성과 연결 된 다른 데이터에 대 한 포인터와 같은 응용 프로그램 관련 데이터입니다. 기본값은 0입니다.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCPropertyGridColorProperty:: Enable자동 단추

색 선택 대화 상자에서 *자동* 단추를 사용 하도록 설정 합니다. 표준 자동 단추는 **자동** 으로 레이블이 지정 됩니다.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 자동 단추의 레이블 텍스트입니다.

*colorAutomatic*<br/>
진행 자동 (기본) 색의 RGB 색 값입니다.

*bEnable*<br/>
진행 자동 단추를 사용 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a> CMFCPropertyGridColorProperty:: EnableOtherButton

색 선택 대화 상자에서 *기타* 단추를 사용 하도록 설정 합니다. 표준 다른 단추에는 **더 많은 색** 이 지정 됩니다.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 다른 단추의 레이블 텍스트입니다.

*bAltColorDlg*<br/>
진행 대화 상자를 표시 하려면 TRUE로 설정 합니다 `CMFCColorDialog` . FALSE 이면 표준 색 선택 대화 상자가 표시 됩니다. 기본값은 TRUE입니다.

*bEnable*<br/>
진행 다른 단추를 표시 하려면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.  기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a> CMFCPropertyGridColorProperty:: GetColor

속성의 현재 색을 가져옵니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a> CMFCPropertyGridColorProperty:: SetColor

속성에 대한 새로운 색을 설정합니다.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
진행 RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCPropertyGridColorProperty:: SetColumnsNumber

현재 색 속성 표의 열 수를 지정합니다.

```cpp
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>매개 변수

*Nconnections Number*<br/>
진행 색 속성 그리드의 기본 열 수입니다.

### <a name="remarks"></a>설명

이 메서드는 보호 된 데이터 멤버의 값을 설정 합니다 `m_nColumnsNumber` .

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a> CMFCPropertyGridColorProperty:: SetOriginalValue

편집 가능한 속성의 원래 값을 설정합니다.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>매개 변수

*varValue*<br/>
진행 값입니다.

### <a name="remarks"></a>설명

[Cmfcpropertygridproperty:: ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) 메서드를 사용 하 여 편집 된 속성의 원래 값을 다시 설정 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 클래스](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 클래스](../../mfc/reference/cmfcpropertygridproperty-class.md)
