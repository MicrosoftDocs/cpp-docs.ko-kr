---
description: '자세히 알아보기: CD2DLayer 클래스'
title: CD2DLayer 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: bd41cd591e6422c9434cd84d20cb6e5d778410bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306952"
---
# <a name="cd2dlayer-class"></a>CD2DLayer 클래스

ID2D1Layer에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DLayer:: CD2DLayer](#cd2dlayer)|CD2DLayer 개체를 생성 합니다.|
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|소멸자입니다. D2D 계층 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DLayer:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DLayer:: Create](#create)|CD2DLayer를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DLayer::D estroy](#destroy)|CD2DLayer 개체를 소멸 시킵니다. [CD2DResource::D estroy](../../mfc/reference/cd2dresource-class.md#destroy)를 재정의 합니다.|
|[CD2DLayer::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DLayer:: Get](#get)|ID2D1Layer 인터페이스를 반환 합니다.|
|[CD2DLayer:: GetSize](#getsize)|렌더링 대상의 크기를 장치 독립적 픽셀 단위로 반환 합니다.|
|[CD2DLayer:: IsValid](#isvalid)|리소스 유효성 검사 ( [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)재정의)|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DLayer:: operator ID2D1Layer *](#operator_id2d1layer_star)|ID2D1Layer 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DLayer:: m_pLayer](#m_player)|ID2D1Layer 개체에 대 한 포인터를 저장 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a> CD2DLayer:: ~ CD2DLayer

소멸자입니다. D2D 계층 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a> CD2DLayer:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL 일 수 없음

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a> CD2DLayer:: CD2DLayer

CD2DLayer 개체를 생성 합니다.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dlayercreate"></a><a name="create"></a> CD2DLayer:: Create

CD2DLayer를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a> CD2DLayer::D estroy

CD2DLayer 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a> CD2DLayer::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dlayerget"></a><a name="get"></a> CD2DLayer:: Get

ID2D1Layer 인터페이스를 반환 합니다.

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>반환 값

ID2D1Layer 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a> CD2DLayer:: GetSize

렌더링 대상의 크기를 장치 독립적 픽셀 단위로 반환 합니다.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>반환 값

렌더링 대상의 현재 크기 (장치 독립적 픽셀)입니다.

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a> CD2DLayer:: IsValid

리소스 유효성 검사

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a> CD2DLayer:: m_pLayer

ID2D1Layer 개체에 대 한 포인터를 저장 합니다.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a> CD2DLayer:: operator ID2D1Layer *

ID2D1Layer 인터페이스를 반환 합니다.

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>반환 값

ID2D1Layer 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
