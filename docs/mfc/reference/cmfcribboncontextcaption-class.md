---
description: '자세한 정보: Cmfc리본 Contextcaption 클래스'
title: Cmfc리본 Contextcaption 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: fa4134b89055274e4f44bef1150518207e06143e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293627"
---
# <a name="cmfcribboncontextcaption-class"></a>Cmfc리본 Contextcaption 클래스

리본 범주 맨 위 또는 컨텍스트 범주에 나타나는 색 지정된 캡션을 구현합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|캡션 색을 반환합니다.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|

## <a name="remarks"></a>설명

이 클래스는 직접 인스턴스화할 수 없습니다. [Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md) 클래스는이 클래스를 내부적으로 사용 하 여 리본 범주에 색을 추가 합니다.

리본 범주에 대 한 색을 설정 하려면 [Cmfcribbon category:: SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)를 호출 합니다. 컨텍스트 범주에 대 한 색을 설정 하려면 [Cmfc리본 표시줄:: AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)를 호출 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonbar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a> Cmfc리본 Contextcaption:: GetColor

캡션의 배경색을 반환 합니다.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>반환 값

반환 되는 값은 다음 열거형 값 중 하나일 수 있습니다.

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>설명

이 캡션의 색은 [Cmfc리본 category:: SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) 또는 [Cmfc리본 표시줄:: addcontextcategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)를 호출 하 여 설정할 수 있습니다.

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a> Cmfc리본 Contextcaption:: GetRightTabX

범주의 리본 탭 오른쪽 가장자리의 위치를 검색 합니다.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>반환 값

개체의 리본 탭에서 바깥쪽 사각형의 오른쪽 X 값을 반환 `CMFCRibbonCategory` 하거나, 탭이 잘린 경우 값-1을 반환 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 단추 클래스](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Cmfc리본 범주 클래스](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md)
