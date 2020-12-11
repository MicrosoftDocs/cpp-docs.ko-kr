---
description: '자세히 알아보기: CD2DSolidColorBrush 클래스'
title: CD2DSolidColorBrush 클래스
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 57df3732a3c4239af6d9121426aa272c6f58417d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154606"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush 클래스

ID2D1SolidColorBrush에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DSolidColorBrush:: CD2DSolidColorBrush](#cd2dsolidcolorbrush)|오버로드됨. CD2DSolidColorBrush 개체를 생성 합니다.|
|[CD2DSolidColorBrush:: ~ CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|소멸자입니다. D2D solid 브러시 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DSolidColorBrush:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DSolidColorBrush:: Create](#create)|CD2DSolidColorBrush를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DSolidColorBrush::D estroy](#destroy)|CD2DSolidColorBrush 개체를 소멸 시킵니다. [CD2DBrush::D estroy](../../mfc/reference/cd2dbrush-class.md#destroy)를 재정의 합니다.|
|[CD2DSolidColorBrush::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DSolidColorBrush:: Get](#get)|ID2D1SolidColorBrush 인터페이스를 반환 합니다.|
|[CD2DSolidColorBrush:: GetColor](#getcolor)|단색 브러시의 색을 검색 합니다.|
|[CD2DSolidColorBrush:: SetColor](#setcolor)|이 단색 브러시의 색을 지정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DSolidColorBrush:: operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|ID2D1SolidColorBrush 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DSolidColorBrush:: m_colorSolid](#m_colorsolid)|브러시 단색입니다.|
|[CD2DSolidColorBrush:: m_pSolidColorBrush](#m_psolidcolorbrush)|ID2D1SolidColorBrush 개체에 대 한 포인터를 저장 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a> CD2DSolidColorBrush:: ~ CD2DSolidColorBrush

소멸자입니다. D2D solid 브러시 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a> CD2DSolidColorBrush:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL 일 수 없음

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a> CD2DSolidColorBrush:: CD2DSolidColorBrush

CD2DSolidColorBrush 개체를 생성 합니다.

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*color*<br/>
브러시 색의 빨강, 녹색, 파랑 및 알파 값입니다.

*pBrushProperties*<br/>
브러시의 불투명도 및 변형에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

*nAlpha*<br/>
브러시 색의 불투명도입니다.

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a> CD2DSolidColorBrush:: Create

CD2DSolidColorBrush를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a> CD2DSolidColorBrush::D estroy

CD2DSolidColorBrush 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a> CD2DSolidColorBrush::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a> CD2DSolidColorBrush:: Get

ID2D1SolidColorBrush 인터페이스를 반환 합니다.

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>반환 값

ID2D1SolidColorBrush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a> CD2DSolidColorBrush:: GetColor

단색 브러시의 색을 검색 합니다.

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>반환 값

이 단색 브러시의 색입니다.

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a> CD2DSolidColorBrush:: m_colorSolid

브러시 단색입니다.

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a> CD2DSolidColorBrush:: m_pSolidColorBrush

ID2D1SolidColorBrush 개체에 대 한 포인터를 저장 합니다.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a> CD2DSolidColorBrush:: operator ID2D1SolidColorBrush *

ID2D1SolidColorBrush 인터페이스를 반환 합니다.

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>반환 값

ID2D1SolidColorBrush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a> CD2DSolidColorBrush:: SetColor

이 단색 브러시의 색을 지정 합니다.

```cpp
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
이 단색 브러시의 색입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
