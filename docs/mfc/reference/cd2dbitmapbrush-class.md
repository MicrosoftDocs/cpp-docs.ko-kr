---
description: '자세히 알아보기: CD2DBitmapBrush 클래스'
title: CD2DBitmapBrush 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: a9d4c1955b1318ecb273482cd49025090bf97d3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227587"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush 클래스

ID2D1BitmapBrush에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DBitmapBrush:: CD2DBitmapBrush](#cd2dbitmapbrush)|오버로드됨. 파일에서 CD2DBitmapBrush 개체를 생성 합니다.|
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|소멸자입니다. D2D 비트맵 브러시 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DBitmapBrush:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DBitmapBrush:: Create](#create)|CD2DBitmapBrush를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DBitmapBrush::D estroy](#destroy)|CD2DBitmapBrush 개체를 소멸 시킵니다. [CD2DBrush::D estroy](../../mfc/reference/cd2dbrush-class.md#destroy)를 재정의 합니다.|
|[CD2DBitmapBrush::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DBitmapBrush:: Get](#get)|ID2D1BitmapBrush 인터페이스를 반환 합니다.|
|[CD2DBitmapBrush:: GetBitmap](#getbitmap)|이 브러시가 그릴 때 사용 하는 비트맵 소스를 가져옵니다.|
|[CD2DBitmapBrush:: GetExtendModeX](#getextendmodex)|브러시가 비트맵을 벗어나 확장 하는 영역을 가로 바둑판식으로 배열 하는 메서드를 가져옵니다.|
|[CD2DBitmapBrush:: GetExtendModeY](#getextendmodey)|브러시가 비트맵을 지 나 확장 하는 영역을 세로 바둑판식으로 배열 하는 메서드를 가져옵니다.|
|[CD2DBitmapBrush:: GetInterpolationMode](#getinterpolationmode)|브러시 비트맵의 크기를 조정 하거나 회전할 때 사용 되는 보간 방법을 가져옵니다.|
|[CD2DBitmapBrush:: SetBitmap](#setbitmap)|이 브러시가 그릴 때 사용 하는 비트맵 소스를 지정 합니다.|
|[CD2DBitmapBrush:: SetExtendModeX](#setextendmodex)|브러시가 비트맵을 벗어나 확장 하는 영역을 가로 바둑판식으로 배열 하는 방법을 지정 합니다.|
|[CD2DBitmapBrush:: SetExtendModeY](#setextendmodey)|브러시가 비트맵을 벗어나 확장 하는 영역을 세로 바둑판식으로 배열 하는 방법을 지정 합니다.|
|[CD2DBitmapBrush:: SetInterpolationMode](#setinterpolationmode)|브러시 비트맵의 크기를 조정 하거나 회전할 때 사용 되는 보간 모드를 지정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CD2DBitmapBrush:: CommonInit](#commoninit)|개체를 초기화 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DBitmapBrush:: operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|ID2D1BitmapBrush 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DBitmapBrush:: m_pBitmap](#m_pbitmap)|CD2DBitmap 개체에 대 한 포인터를 저장 합니다.|
|[CD2DBitmapBrush:: m_pBitmapBrush](#m_pbitmapbrush)|ID2D1BitmapBrush 개체에 대 한 포인터를 저장 합니다.|
|[CD2DBitmapBrush:: m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|비트맵 브러시 속성입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a> CD2DBitmapBrush:: ~ CD2DBitmapBrush

소멸자입니다. D2D 비트맵 브러시 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a> CD2DBitmapBrush:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL 일 수 없음

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a> CD2DBitmapBrush:: CD2DBitmapBrush

CD2DBitmapBrush 개체를 생성 합니다.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*pBitmapBrushProperties*<br/>
비트맵 브러시의 확장 모드 및 보간 모드에 대 한 포인터입니다.

*pBrushProperties*<br/>
브러시의 불투명도 및 변형에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

*uiResID*<br/>
리소스의 리소스 ID입니다.

*lpszType*<br/>
리소스 형식을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*sizeDest*<br/>
비트맵의 대상 크기입니다.

*lpszImagePath*<br/>
파일의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a> CD2DBitmapBrush:: CommonInit

개체를 초기화 합니다.

```cpp
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>매개 변수

*pBitmapBrushProperties*<br/>
비트맵 브러시 속성에 대 한 포인터입니다.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a> CD2DBitmapBrush:: Create

CD2DBitmapBrush를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a> CD2DBitmapBrush::D estroy

CD2DBitmapBrush 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a> CD2DBitmapBrush::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a> CD2DBitmapBrush:: Get

ID2D1BitmapBrush 인터페이스를 반환 합니다.

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>반환 값

ID2D1BitmapBrush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a> CD2DBitmapBrush:: GetBitmap

이 브러시가 그릴 때 사용 하는 비트맵 소스를 가져옵니다.

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>반환 값

CD2DBitmap 개체에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a> CD2DBitmapBrush:: GetExtendModeX

브러시가 비트맵을 벗어나 확장 하는 영역을 가로 바둑판식으로 배열 하는 메서드를 가져옵니다.

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>반환 값

브러시가 비트맵을 벗어나 확장 하는 영역을 가로 바둑판식으로 배열 하는 방법을 지정 하는 값입니다.

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a> CD2DBitmapBrush:: GetExtendModeY

브러시가 비트맵을 지 나 확장 하는 영역을 세로 바둑판식으로 배열 하는 메서드를 가져옵니다.

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>반환 값

브러시가 비트맵을 지 나 확장 하는 영역을 세로 바둑판식으로 배열 하는 방법을 지정 하는 값입니다.

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a> CD2DBitmapBrush:: GetInterpolationMode

브러시 비트맵의 크기를 조정 하거나 회전할 때 사용 되는 보간 방법을 가져옵니다.

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>반환 값

브러시 비트맵의 크기를 조정 하거나 회전할 때 사용 되는 보간 방법입니다.

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a> CD2DBitmapBrush:: m_pBitmap

CD2DBitmap 개체에 대 한 포인터를 저장 합니다.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a> CD2DBitmapBrush:: m_pBitmapBrush

ID2D1BitmapBrush 개체에 대 한 포인터를 저장 합니다.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a> CD2DBitmapBrush:: m_pBitmapBrushProperties

비트맵 브러시 속성입니다.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a> CD2DBitmapBrush:: operator ID2D1BitmapBrush *

ID2D1BitmapBrush 인터페이스를 반환 합니다.

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>반환 값

ID2D1BitmapBrush 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a> CD2DBitmapBrush:: SetBitmap

이 브러시가 그릴 때 사용 하는 비트맵 소스를 지정 합니다.

```cpp
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>매개 변수

*pBitmap*<br/>
브러시에 사용 되는 비트맵 원본입니다.

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a> CD2DBitmapBrush:: SetExtendModeX

브러시가 비트맵을 벗어나 확장 하는 영역을 가로 바둑판식으로 배열 하는 방법을 지정 합니다.

```cpp
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>매개 변수

*extendModeX*<br/>
브러시가 비트맵을 벗어나 확장 하는 영역을 가로 바둑판식으로 배열 하는 방법을 지정 하는 값입니다.

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a> CD2DBitmapBrush:: SetExtendModeY

브러시가 비트맵을 벗어나 확장 하는 영역을 세로 바둑판식으로 배열 하는 방법을 지정 합니다.

```cpp
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>매개 변수

*extendModeY*<br/>
브러시가 비트맵을 지 나 확장 하는 영역을 세로 바둑판식으로 배열 하는 방법을 지정 하는 값입니다.

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a> CD2DBitmapBrush:: SetInterpolationMode

브러시 비트맵의 크기를 조정 하거나 회전할 때 사용 되는 보간 모드를 지정 합니다.

```cpp
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>매개 변수

*interpolationMode*<br/>
브러시 비트맵의 크기를 조정 하거나 회전할 때 사용 되는 보간 모드입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
