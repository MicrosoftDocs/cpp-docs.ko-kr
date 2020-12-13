---
description: '자세히 알아보기: CMFCToolBarFontSizeComboBox 클래스'
title: CMFCToolBarFontSizeComboBox 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: a355e62f2ef538372d70b9b2b393bc16bff2ef4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331753"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 클래스

사용자가 글꼴 크기를 선택할 수 있는 콤보 상자 컨트롤을 포함 하는 도구 모음 단추입니다.

## <a name="syntax"></a>구문

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|`CMFCToolBarFontSizeComboBox` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|선택한 글꼴 크기를 트윕 단위로 반환 합니다.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|지정 된 글꼴에 대해 지원 되는 모든 글꼴 크기로 콤보 상자 목록을 채웁니다.|
|[CMFCToolBarFontSizeComboBox:: SetTwipSize](#settwipsize)|글꼴 크기를 트윕 단위로 설정 합니다.|

## <a name="remarks"></a>설명

`CMFCToolBarFontSizeComboBox`개체를 [cmfc기능 글꼴 콤보 상자 클래스](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 개체와 함께 사용 하 여 사용자가 글꼴 및 글꼴 크기를 선택할 수 있습니다.

글꼴 콤보 상자 단추를 추가 하는 것과 같이 도구 모음에 글꼴 크기 콤보 상자 단추를 추가할 수 있습니다. 자세한 내용은 [Cmfc의 글꼴 Combobox 클래스](../../mfc/reference/cmfctoolbarfontcombobox-class.md)를 참조 하세요.

사용자가 개체에서 새 글꼴을 선택 하는 경우 `CMFCToolBarFontComboBox` [CMFCToolBarFontSizeComboBox:: RebuildFontSizes](#rebuildfontsizes) 메서드를 사용 하 여 글꼴 크기 콤보 상자를 해당 글꼴에 대해 지원 되는 크기로 채울 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 개체를 구성 하는 방법을 보여 줍니다 `CMFCToolBarFontSizeComboBox` `CMFCToolBarFontSizeComboBox` . 이 예제에서는 텍스트 상자에서 글꼴 크기 (트윕)를 검색 하 고 글꼴 크기 콤보 상자를 지정 된 글꼴의 모든 유효한 크기로 채운 다음 글꼴 크기를 트윕 단위로 지정 하는 방법을 보여 줍니다. 이 코드 조각은 [워드 패드 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbarfontcombobox

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a> CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

`CMFCToolBarFontSizeComboBox` 개체를 생성합니다.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a> CMFCToolBarFontSizeComboBox::GetTwipSize

글꼴 크기 콤보 상자의 텍스트 상자에서 글꼴 크기 (트윕)를 검색 합니다.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>반환 값

반환 값이 양수인 경우 글꼴 크기 (트윕)입니다. 콤보 상자의 텍스트 상자가 비어 있는 경우-1입니다. 오류가 발생 하는 경우에는-2입니다.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a> CMFCToolBarFontSizeComboBox::RebuildFontSizes

글꼴 크기 콤보 상자를 지정 된 글꼴의 모든 유효한 크기로 채웁니다.

```cpp
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>매개 변수

*strFontName*<br/>
진행 글꼴 이름을 지정 합니다.

### <a name="remarks"></a>설명

글꼴 콤보 상자의 선택 항목과 Cmfc기능 글꼴 콤보 상자 (예: [Cmfc사용자 이름 Combobox 클래스](../../mfc/reference/cmfctoolbarfontcombobox-class.md))를 동기화 하려는 경우이 함수를 호출 합니다.

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a> CMFCToolBarFontSizeComboBox:: SetTwipSize

지정 된 크기 (트윕 단위)를 가장 가까운 크기로 반올림 하 고 콤보 상자에서 선택한 크기를 해당 값으로 설정 합니다.

```cpp
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>매개 변수

*nSize*<br/>
진행 설정할 글꼴 크기 (트윕)를 지정 합니다.

### <a name="remarks"></a>설명

나중에 [CMFCToolBarFontSizeComboBox:: GetTwipSize](#gettwipsize) 메서드를 호출 하 여 이전 유효한 글꼴 크기를 검색할 수 있습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 클래스](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 클래스](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)
