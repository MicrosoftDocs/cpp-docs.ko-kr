---
description: '자세히 알아보기: CD2DRadialGradientBrush 클래스'
title: CD2DRadialGradientBrush 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: c5e169a5d608edd246d5c7269c94e3b225fdd491
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118747"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush 클래스

ID2D1RadialGradientBrush에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DRadialGradientBrush:: CD2DRadialGradientBrush](#cd2dradialgradientbrush)|CD2DLinearGradientBrush 개체를 생성 합니다.|
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|소멸자입니다. D2D 방사형 그라데이션 브러시 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DRadialGradientBrush:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DRadialGradientBrush:: Create](#create)|CD2DRadialGradientBrush를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DRadialGradientBrush::D estroy](#destroy)|CD2DRadialGradientBrush 개체를 소멸 시킵니다. [CD2DGradientBrush::D estroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy)를 재정의 합니다.|
|[CD2DRadialGradientBrush::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DRadialGradientBrush:: Get](#get)|ID2D1RadialGradientBrush 인터페이스를 반환 합니다.|
|[CD2DRadialGradientBrush:: GetCenter](#getcenter)|그라데이션 타원의 중심을 검색 합니다.|
|[CD2DRadialGradientBrush:: GetGradientOriginOffset](#getgradientoriginoffset)|그라데이션 타원의 중심을 기준으로 하는 그라데이션 원점의 오프셋을 검색 합니다.|
|[CD2DRadialGradientBrush:: GetRadiusX](#getradiusx)|그라데이션 타원의 x 반지름을 검색 합니다.|
|[CD2DRadialGradientBrush:: GetRadiusY](#getradiusy)|그라데이션 타원의 y 반지름을 검색 합니다.|
|[CD2DRadialGradientBrush:: SetCenter](#setcenter)|브러시의 좌표 공간에서 그라데이션 타원의 중심을 지정 합니다.|
|[CD2DRadialGradientBrush:: SetGradientOriginOffset](#setgradientoriginoffset)|그라데이션 타원의 중심을 기준으로 하는 그라데이션 원점의 오프셋을 지정 합니다.|
|[CD2DRadialGradientBrush:: SetRadiusX](#setradiusx)|브러시의 좌표 공간에서 그라데이션 타원의 x 반지름을 지정 합니다.|
|[CD2DRadialGradientBrush:: SetRadiusY](#setradiusy)|브러시의 좌표 공간에서 그라데이션 타원의 y 반경을 지정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DRadialGradientBrush:: operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|ID2D1RadialGradientBrush 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DRadialGradientBrush:: m_pRadialGradientBrush](#m_pradialgradientbrush)|ID2D1RadialGradientBrush에 대 한 포인터입니다.|
|[CD2DRadialGradientBrush:: m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|브러시 그라데이션의 중심, 그라데이션 원점 오프셋 및 x 반지름 및 y 반지름입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a> CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush

소멸자입니다. D2D 방사형 그라데이션 브러시 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a> CD2DRadialGradientBrush:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL 일 수 없음

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a> CD2DRadialGradientBrush:: CD2DRadialGradientBrush

CD2DLinearGradientBrush 개체를 생성 합니다.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*gradientStops*<br/>
D2D1_GRADIENT_STOP 구조체의 배열에 대 한 포인터입니다.

*gradientStopsCount*<br/>
GradientStops 배열의 그라데이션 중지점 수를 지정 하는 1 보다 크거나 같은 값입니다.

*RadialGradientBrushProperties*<br/>
브러시 그라데이션의 중심, 그라데이션 원점 오프셋 및 x 반지름 및 y 반지름입니다.

*colorInterpolationGamma*<br/>
그라데이션 중지점 간의 색 보간을 수행 하는 공간입니다.

*extendMode*<br/>
[0, 1] 정규화 된 범위 밖에 있는 그라데이션의 동작입니다.

*pBrushProperties*<br/>
브러시의 불투명도 및 변형에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a> CD2DRadialGradientBrush:: Create

CD2DRadialGradientBrush를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a> CD2DRadialGradientBrush::D estroy

CD2DRadialGradientBrush 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a> CD2DRadialGradientBrush::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a> CD2DRadialGradientBrush:: Get

ID2D1RadialGradientBrush 인터페이스를 반환 합니다.

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>반환 값

ID2D1RadialGradientBrush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a> CD2DRadialGradientBrush:: GetCenter

그라데이션 타원의 중심을 검색 합니다.

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>반환 값

그라데이션 타원의 중심입니다. 이 값은 브러시의 좌표 공간으로 표현 됩니다.

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a> CD2DRadialGradientBrush:: GetGradientOriginOffset

그라데이션 타원의 중심을 기준으로 하는 그라데이션 원점의 오프셋을 검색 합니다.

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>반환 값

그라데이션 타원의 중심에서 그라데이션 원점을 기준으로 하는 오프셋입니다. 이 값은 브러시의 좌표 공간으로 표현 됩니다.

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a> CD2DRadialGradientBrush:: GetRadiusX

그라데이션 타원의 x 반지름을 검색 합니다.

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>반환 값

그라데이션 타원의 x 반지름입니다. 이 값은 브러시의 좌표 공간으로 표현 됩니다.

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a> CD2DRadialGradientBrush:: GetRadiusY

그라데이션 타원의 y 반지름을 검색 합니다.

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>반환 값

그라데이션 타원의 y 반경입니다. 이 값은 브러시의 좌표 공간으로 표현 됩니다.

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a> CD2DRadialGradientBrush:: m_pRadialGradientBrush

ID2D1RadialGradientBrush에 대 한 포인터입니다.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a> CD2DRadialGradientBrush:: m_RadialGradientBrushProperties

브러시 그라데이션의 중심, 그라데이션 원점 오프셋 및 x 반지름 및 y 반지름입니다.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a> CD2DRadialGradientBrush:: operator ID2D1RadialGradientBrush *

ID2D1RadialGradientBrush 인터페이스를 반환 합니다.

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>반환 값

ID2D1RadialGradientBrush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a> CD2DRadialGradientBrush:: SetCenter

브러시의 좌표 공간에서 그라데이션 타원의 중심을 지정 합니다.

```cpp
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
브러시의 좌표 공간에 있는 그라데이션 타원의 중심입니다.

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a> CD2DRadialGradientBrush:: SetGradientOriginOffset

그라데이션 타원의 중심을 기준으로 하는 그라데이션 원점의 오프셋을 지정 합니다.

```cpp
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>매개 변수

*gradientOriginOffset*<br/>
그라데이션 타원의 중심에서 그라데이션 원점을 기준으로 하는 오프셋입니다.

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a> CD2DRadialGradientBrush:: SetRadiusX

브러시의 좌표 공간에서 그라데이션 타원의 x 반지름을 지정 합니다.

```cpp
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>매개 변수

*radiusX*<br/>
그라데이션 타원의 x 반지름입니다. 이 값은 브러시의 좌표 공간에 있습니다.

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a> CD2DRadialGradientBrush:: SetRadiusY

브러시의 좌표 공간에서 그라데이션 타원의 y 반경을 지정 합니다.

```cpp
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>매개 변수

*radiusY*<br/>
그라데이션 타원의 y 반경입니다. 이 값은 브러시의 좌표 공간에 있습니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
