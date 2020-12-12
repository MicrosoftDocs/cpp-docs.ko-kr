---
description: '자세한 정보: Cmfc리본 레이블 클래스'
title: Cmfc리본 레이블 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: 0699e76dfe90b87cd813d18d076adf23f8512bee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321828"
---
# <a name="cmfcribbonlabel-class"></a>Cmfc리본 레이블 클래스

리본에 대해 클릭할 수 없는 텍스트 레이블을 구현합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfc리본 레이블:: Cmfc리본 레이블](#cmfcribbonlabel)|지정 된 텍스트 문자열을 사용 하 여 개체를 생성 하 고 초기화 `CMFCRibbonLabel` 합니다.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCRibbonLabel::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[Cmfc리본 레이블:: SetACCData](#setaccdata)|현재 리본 레이블 요소에 대 한 내게 필요한 옵션 데이터를 결정 합니다. [Cmfc리본 단추:: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)를 재정의 합니다.|

### <a name="remarks"></a>설명

리본 레이블을 만든 후 [Cmfcribbon panel:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)를 호출 하 여 패널에 추가 합니다.

빠른 실행 도구 모음에는 리본 레이블을 추가할 수 없습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRibbonLabel

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a> Cmfc리본 레이블:: Cmfc리본 레이블

지정 된 텍스트 문자열을 표시 하는 [Cmfc리본 레이블](../../mfc/reference/cmfcribbonlabel-class.md) 개체를 생성 하 고 초기화 합니다.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
진행 레이블에 표시할 텍스트입니다.

*bIsMultiLine*<br/>
진행 레이블이 여러 줄 레이블로 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a> Cmfc리본 레이블:: SetACCData

현재 리본 레이블 요소에 대 한 내게 필요한 옵션 데이터를 결정 합니다.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>매개 변수

*pParent*<br/>
진행 현재 리본 레이블의 부모 창을 나타냅니다.

*data*<br/>
제한이 `CAccessibilityData` 현재 리본 레이블의 내게 필요한 옵션 데이터로 채워지는 형식의 개체입니다.

### <a name="return-value"></a>반환 값

*데이터* 매개 변수가 현재 리본 레이블의 내게 필요한 옵션 데이터로 채워진 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 단추 클래스](../../mfc/reference/cmfcribbonbutton-class.md)
