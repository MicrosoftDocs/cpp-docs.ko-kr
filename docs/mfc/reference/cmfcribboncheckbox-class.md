---
description: '자세한 정보: Cmfc리본 Checkbox 클래스'
title: Cmfc리본 Checkbox 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 889d9e8935bb26a2a95d28697074dba973e04c21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293744"
---
# <a name="cmfcribboncheckbox-class"></a>Cmfc리본 Checkbox 클래스

`CMFCRibbonCheckBox` 클래스는 리본 패널, 빠른 실행 도구 모음 또는 팝업 메뉴에 추가할 수 있는 확인란을 구현합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|[Cmfc리본 단추:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)를 재정의 합니다.|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|[Cmfc리본 단추:: GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)를 재정의 합니다.|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|[Cmfc리본 단추:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)를 재정의 합니다.|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|( `CMFCRibbonButton::IsDrawTooltipImage`을 재정의합니다.)|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|[Cmfc리본 단추:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)를 재정의 합니다.|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|[Cmfc리본 Baseelement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)를 재정의 합니다.|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|( `CMFCRibbonButton::OnDrawOnList`을 재정의합니다.)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|[Cmfc리본 단추:: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)를 재정의 합니다.|

## <a name="remarks"></a>설명

애플리케이션에서 `CMFCRibbonCheckBox`를 사용하려면 코드에 다음 생성자를 추가합니다.

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

여기서 *nID* 은 확인란 명령 ID이 고 *lpszText* 는 확인란의 텍스트 레이블입니다.

[Cmfc리본 패널:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)를 사용 하 여 리본 패널에 확인란을 추가할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribboncheckbox

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a> Cmfc리본 확인란:: Cmfc리본 확인란

리본 확인란 개체의 생성자

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 명령 ID를 지정 합니다.

*lpszText*<br/>
진행 텍스트 레이블을 지정 합니다.

### <a name="return-value"></a>반환 값

리본 확인란 개체를 생성 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCRibbonCheckBox` .

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a> Cmfc리본 확인란:: GetCompactSize

재정의 된 경우 확인란의 컴팩트 크기를 가져옵니다.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 확인란과 연결 된 CDC에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`CSize`확인란의 컴팩트 크기를 포함 하는 개체를 반환 합니다.

### <a name="remarks"></a>설명

재정의 되지 않은 경우에는 확인란의 중간 크기를 반환 합니다.

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a> Cmfc리본 확인란:: GetIntermediateSize

확인란의 중간 크기를 가져옵니다.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 이 확인란과 연결 된 CDC에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`CSize`확인란의 중간 크기를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

재정의 되지 않은 경우는 중간 크기를 기본 확인란 크기 ()와 텍스트 크기 및 여백으로 계산 합니다 `AFX_CHECK_BOX_DEFAULT_SIZE` .

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a> Cmfc리본 확인란:: GetRegularSize

확인란의 일반 크기를 가져옵니다.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 이 확인란과 연결 된 CDC 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`CSize`확인란의 일반 크기를 포함 하는 개체를 반환 합니다.

### <a name="remarks"></a>설명

재정의 되지 않은 경우에는 확인란의 중간 크기를 반환 합니다.

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a> Cmfc리본 확인란:: IsDrawTooltipImage

확인란과 연결 된 도구 설명 이미지가 있는지 여부를 나타냅니다.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>반환 값

확인란과 연결 된 도구 설명 이미지가 있으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a> Cmfc리본 Checkbox:: OnDraw

지정 된 장치 컨텍스트를 사용 하 여 확인란을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 확인란을 그릴 CDC에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a> Cmfc리본 Checkbox:: OnDrawMenuImage

확인란의 메뉴 이미지를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>매개 변수

진행 *CDC&#42;*<br/>
확인란과 연결 된 CDC에 대 한 포인터입니다.

*CRect*<br/>
진행 `CRect` 메뉴 이미지를 그릴 사각형을 지정 하는 개체입니다.

### <a name="return-value"></a>반환 값

이미지를 그린 경우 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

재정의 되지 않으면 FALSE를 반환 합니다.

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a> Cmfc리본 Checkbox:: OnDrawOnList

명령 목록 상자에 확인란을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 확인란을 그릴 장치 컨텍스트에 대 한 포인터입니다.

*strText*<br/>
진행 표시 텍스트입니다.

*nTextOffset*<br/>
진행 목록 상자의 좌 변에 표시 텍스트 까지의 거리 (픽셀)입니다.

*rect*<br/>
진행 확인란의 표시 사각형입니다.

*bIsSelected*<br/>
진행 확인란이 선택 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

*bHighlighted 표시*<br/>
진행 확인란이 강조 표시 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a> Cmfc리본 Checkbox:: SetACCData

확인란에 대 한 내게 필요한 옵션 데이터를 설정 합니다.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>매개 변수

*pParent*<br/>
확인란의 부모 창입니다.

*data*<br/>
확인란에 대 한 내게 필요한 옵션 데이터입니다.

### <a name="return-value"></a>반환 값

항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

기본적으로이 메서드는 확인란에 대 한 내게 필요한 옵션 데이터를 설정 하 고 항상 TRUE를 반환 합니다. 내게 필요한 옵션 데이터를 설정하고 성공 또는 실패를 나타내는 값을 반환하려면 이 메서드를 재정의합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 패널 클래스](../../mfc/reference/cmfcribbonpanel-class.md)
