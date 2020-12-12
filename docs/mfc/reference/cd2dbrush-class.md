---
description: '자세히 알아보기: CD2DBrush 클래스'
title: CD2DBrush 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: 6d19601258951a297a734aa304e2a22c98baf5c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227574"
---
# <a name="cd2dbrush-class"></a>CD2DBrush 클래스

ID2D1Brush에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CD2DBrush:: CD2DBrush](#cd2dbrush)|CD2DBrush 개체를 생성 합니다.|
|[CD2DBrush:: ~ CD2DBrush](#_dtorcd2dbrush)|소멸자입니다. D2D 브러시 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DBrush:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DBrush::D estroy](#destroy)|CD2DBrush 개체를 소멸 시킵니다. [CD2DResource::D estroy](../../mfc/reference/cd2dresource-class.md#destroy)를 재정의 합니다.|
|[CD2DBrush::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DBrush:: Get](#get)|ID2D1Brush 인터페이스를 반환 합니다.|
|[CD2DBrush:: GetOpacity](#getopacity)|이 브러시의 불투명도 수준을 가져옵니다.|
|[CD2DBrush:: GetTransform](#gettransform)|렌더링 대상의 현재 변환을 가져옵니다.|
|[CD2DBrush:: IsValid](#isvalid)|리소스 유효성 검사 ( [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)재정의)|
|[CD2DBrush:: SetOpacity](#setopacity)|이 브러시의 불투명도 수준을 설정 합니다.|
|[CD2DBrush:: SetTransform](#settransform)|지정 된 변환을 렌더링 대상에 적용 하 여 기존 변환을 바꿉니다. 모든 후속 그리기 작업은 변환 된 공간에서 발생 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DBrush:: operator ID2D1Brush *](#operator_id2d1brush_star)|ID2D1Brush 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DBrush:: m_pBrush](#m_pbrush)|ID2D1Brush 개체에 대 한 포인터를 저장 합니다.|
|[CD2DBrush:: m_pBrushProperties](#m_pbrushproperties)|브러시 속성입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a> CD2DBrush:: ~ CD2DBrush

소멸자입니다. D2D 브러시 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a> CD2DBrush:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL이 될 수 없습니다.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a> CD2DBrush:: CD2DBrush

CD2DBrush 개체를 생성 합니다.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*pBrushProperties*<br/>
브러시의 불투명도 및 변형에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a> CD2DBrush::D estroy

CD2DBrush 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a> CD2DBrush::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dbrushget"></a><a name="get"></a> CD2DBrush:: Get

ID2D1Brush 인터페이스를 반환 합니다.

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>반환 값

ID2D1Brush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a> CD2DBrush:: GetOpacity

이 브러시의 불투명도 수준을 가져옵니다.

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>반환 값

브러시의 불투명도를 나타내는 0과 1 사이의 값입니다. 이 값은 브러시로 채워진 모든 픽셀의 알파 값을 선형으로 조정 하는 상수 승수입니다. 불투명도 값은 0에서 1 사이의 범위에서 고정 합니다.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a> CD2DBrush:: GetTransform

렌더링 대상의 현재 변환을 가져옵니다.

```cpp
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>매개 변수

*transform*<br/>
이 값이 반환 되 면 렌더링 대상의 현재 변환이 포함 됩니다. 이 매개 변수는 초기화되지 않은 상태로 전달됩니다.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a> CD2DBrush:: IsValid

리소스 유효성 검사

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a> CD2DBrush:: m_pBrush

ID2D1Brush 개체에 대 한 포인터를 저장 합니다.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a> CD2DBrush:: m_pBrushProperties

브러시 속성입니다.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a> CD2DBrush:: operator ID2D1Brush *

ID2D1Brush 인터페이스를 반환 합니다.

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>반환 값

ID2D1Brush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a> CD2DBrush:: SetOpacity

이 브러시의 불투명도 수준을 설정 합니다.

```cpp
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>매개 변수

*별*<br/>
브러시의 불투명도를 나타내는 0과 1 사이의 값입니다. 이 값은 브러시로 채워진 모든 픽셀의 알파 값을 선형으로 조정 하는 상수 승수입니다. 불투명도 값은 0에서 1 사이의 범위에서 고정 합니다.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a> CD2DBrush:: SetTransform

지정 된 변환을 렌더링 대상에 적용 하 여 기존 변환을 바꿉니다. 모든 후속 그리기 작업은 변환 된 공간에서 발생 합니다.

```cpp
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>매개 변수

*transform*<br/>
렌더링 대상에 적용할 변환입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
