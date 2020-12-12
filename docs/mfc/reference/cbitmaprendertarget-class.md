---
description: '자세히 알아보기: CBitmapRenderTarget 클래스'
title: CBitmapRenderTarget 클래스
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: a7987651c988dcf7fcd4c4decf4a2bd474ab8619
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122683"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget 클래스

ID2D1BitmapRenderTarget에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|CBitmapRenderTarget 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBitmapRenderTarget:: Attach](#attach)|기존 렌더링 대상 인터페이스를 개체에 연결 합니다.|
|[CBitmapRenderTarget::D etach](#detach)|개체에서 렌더링 대상 인터페이스를 분리 합니다.|
|[CBitmapRenderTarget:: GetBitmap](#getbitmap)|이 렌더링 대상에 대 한 비트맵을 검색 합니다. 반환 된 비트맵은 그리기 작업에 사용할 수 있습니다.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|ID2D1BitmapRenderTarget 인터페이스를 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CBitmapRenderTarget:: operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|ID2D1BitmapRenderTarget 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CBitmapRenderTarget:: m_pBitmapRenderTarget](#m_pbitmaprendertarget)|ID2D1BitmapRenderTarget 개체에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a> CBitmapRenderTarget:: Attach

기존 렌더링 대상 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>매개 변수

*pTarget*<br/>
기존 렌더링 대상 인터페이스입니다. NULL 일 수 없음

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a> CBitmapRenderTarget::CBitmapRenderTarget

CBitmapRenderTarget 개체를 생성 합니다.

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a> CBitmapRenderTarget::D etach

개체에서 렌더링 대상 인터페이스를 분리 합니다.

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 렌더링 대상 인터페이스에 대 한 포인터입니다.

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a> CBitmapRenderTarget:: GetBitmap

이 렌더링 대상에 대 한 비트맵을 검색 합니다. 반환 된 비트맵은 그리기 작업에 사용할 수 있습니다.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>매개 변수

*bitmap*<br/>
이 메서드는 반환 될 때이 렌더링 대상에 대 한 유효한 비트맵을 포함 합니다. 이 비트맵은 그리기 작업에 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a> CBitmapRenderTarget::GetBitmapRenderTarget

ID2D1BitmapRenderTarget 인터페이스를 반환 합니다.

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>반환 값

ID2D1BitmapRenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a> CBitmapRenderTarget:: m_pBitmapRenderTarget

ID2D1BitmapRenderTarget 개체에 대 한 포인터입니다.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a> CBitmapRenderTarget:: operator ID2D1BitmapRenderTarget *

ID2D1BitmapRenderTarget 인터페이스를 반환 합니다.

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>반환 값

ID2D1BitmapRenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
