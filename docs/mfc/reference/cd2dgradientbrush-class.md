---
description: '자세히 알아보기: CD2DGradientBrush 클래스'
title: CD2DGradientBrush 클래스
ms.date: 03/27/2019
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: c1af08ae27bd2cbee48c4abe22f413ffeb85cd1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193398"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush 클래스

CD2DLinearGradientBrush 및 CD2DRadialGradientBrush 클래스의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DGradientBrush:: CD2DGradientBrush](#cd2dgradientbrush)|CD2DGradientBrush 개체를 생성 합니다.|
|[CD2DGradientBrush:: ~ CD2DGradientBrush](#_dtorcd2dgradientbrush)|소멸자입니다. D2D 그라데이션 브러시 개체가 제거 될 때 호출 됩니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CD2DGradientBrush::D estroy](#destroy)|CD2DGradientBrush 개체를 소멸 시킵니다. [CD2DBrush::D estroy](../../mfc/reference/cd2dbrush-class.md#destroy)를 재정의 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DGradientBrush:: m_arGradientStops](#m_argradientstops)|D2D1_GRADIENT_STOP 구조체의 배열입니다.|
|[CD2DGradientBrush:: m_colorInterpolationGamma](#m_colorinterpolationgamma)|그라데이션 중지점 간의 색 보간을 수행 하는 공간입니다.|
|[CD2DGradientBrush:: m_extendMode](#m_extendmode)|[0, 1] 정규화 된 범위 밖에 있는 그라데이션의 동작입니다.|
|[CD2DGradientBrush:: m_pGradientStops](#m_pgradientstops)|D2D1_GRADIENT_STOP 구조체의 배열에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a> CD2DGradientBrush:: ~ CD2DGradientBrush

소멸자입니다. D2D 그라데이션 브러시 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a> CD2DGradientBrush:: CD2DGradientBrush

CD2DGradientBrush 개체를 생성 합니다.

```
CD2DGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
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

*colorInterpolationGamma*<br/>
그라데이션 중지점 간의 색 보간을 수행 하는 공간입니다.

*extendMode*<br/>
[0, 1] 정규화 된 범위 밖에 있는 그라데이션의 동작입니다.

*pBrushProperties*<br/>
브러시의 불투명도 및 변형에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a> CD2DGradientBrush::D estroy

CD2DGradientBrush 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a> CD2DGradientBrush:: m_arGradientStops

D2D1_GRADIENT_STOP 구조체의 배열입니다.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a> CD2DGradientBrush:: m_colorInterpolationGamma

그라데이션 중지점 간의 색 보간을 수행 하는 공간입니다.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a> CD2DGradientBrush:: m_extendMode

[0, 1] 정규화 된 범위 밖에 있는 그라데이션의 동작입니다.

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a> CD2DGradientBrush:: m_pGradientStops

D2D1_GRADIENT_STOP 구조체의 배열에 대 한 포인터입니다.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
