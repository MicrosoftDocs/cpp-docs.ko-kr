---
title: CD2DBitmap 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
ms.openlocfilehash: 288ba5e1503a4e3eefe83624cf9a489274a10823
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253944"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap 클래스

ID2D1Bitmap에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|오버로드됨. HBITMAP CD2DBitmap 개체를 생성합니다.|
|[CD2DBitmap::~CD2DBitmap](#_dtorcd2dbitmap)|소멸자입니다. D2D 비트맵 개체 소멸 될 때 호출 됩니다.|

### <a name="protected-constructors"></a>Protected 생성자

|이름|설명|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|오버로드됨. CD2DBitmap 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|기존 개체에 대 한 리소스 인터페이스를 연결.|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|현재 비트맵으로 지정된 된 영역을 지정한 비트맵에서 복사합니다.|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|현재 비트맵으로 지정된 된 영역을 메모리에서 복사합니다.|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|복사본이 지정된 된 영역에서 지정 된 대상 현재 비트맵으로 렌더링|
|[CD2DBitmap::Create](#create)|CD2DBitmap를 만듭니다. (재정의 [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|CD2DBitmap 개체를 제거합니다. (재정의 [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|개체에서 리소스 인터페이스를 분리합니다.|
|[CD2DBitmap::Get](#get)|반환 ID2D1Bitmap 인터페이스|
|[CD2DBitmap::GetDPI](#getdpi)|dpi (인치당 도트) 비트맵의 반환|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|비트맵의 픽셀 형식 및 알파 모드 검색|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|비트맵의 크기를 장치 독립적 단위 (픽셀)를 반환합니다.|
|[CD2DBitmap::GetSize](#getsize)|비트맵의 크기를 장치 독립적 픽셀 (Dip)를 반환합니다.|
|[CD2DBitmap::IsValid](#isvalid)|리소스 유효성을 검사 (재정의 [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Protected 메서드

|이름|설명|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|개체를 초기화합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|설명|
|----------|-----------------|
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|반환 ID2D1Bitmap 인터페이스|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|이름|설명|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE 이면 m_hBmpSrc 제거 해야 합니다. 그렇지 않으면 FALSE입니다.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|원본 비트맵 핸들입니다.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|리소스 종류입니다.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|ID2D1Bitmap 개체에 대 한 포인터를 저장합니다.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|대상 크기는 비트맵입니다.|
|[CD2DBitmap::m_strPath](#m_strpath)|Botmap 파일 경로입니다.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|비트맵 리소스 id입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget.h

##  <a name="_dtorcd2dbitmap"></a>  CD2DBitmap::~CD2DBitmap

소멸자입니다. D2D 비트맵 개체 소멸 될 때 호출 됩니다.

```
virtual ~CD2DBitmap();
```

##  <a name="attach"></a>  CD2DBitmap::Attach

기존 개체에 대 한 리소스 인터페이스를 연결 합니다.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>매개 변수

*pResource*<br/>
기존 리소스 인터페이스입니다. NULL일 수 없습니다.

##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap

리소스에서 CD2DBitmap 개체를 생성합니다.

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*uiResID*<br/>
리소스의 리소스 ID.

*lpszType*<br/>
리소스 형식이 포함 된 null로 끝나는 문자열에 대 한 포인터입니다.

*sizeDest*<br/>
비트맵의 대상 크기입니다.

*bAutoDestroy*<br/>
개체 소유자 (pParentTarget)에 의해 소멸 되는 것을 나타냅니다.

*lpszPath*<br/>
파일의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*hbmpSrc*<br/>
비트맵에 대 한 핸들입니다.

##  <a name="commoninit"></a>  CD2DBitmap::CommonInit

개체를 초기화합니다.

```
void CommonInit();
```

##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap

지정한 비트맵에서 지정된 된 영역을 현재 비트맵으로 복사합니다.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>매개 변수

*pBitmap*<br/>
복사할 비트맵입니다.

*destPoint*<br/>
현재 비트맵에는 지역을 지정 srcRect 영역의 왼쪽 위 모퉁이 복사 됩니다.

*srcRect*<br/>
복사 하는 비트맵의 영역입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 HRESULT 오류 코드를 반환합니다.

##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory

메모리에서 지정된 된 영역을 현재 비트맵으로 복사합니다.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>매개 변수

*srcData*<br/>
복사할 데이터입니다.

*pitch*<br/>
SrcData에 저장 된 소스 비트맵의 피치 또는 진행 속도입니다. Stride는 스캐닝선 (메모리 내의 픽셀의 하나의 행)의 바이트 수 이며 다음 수식에서 stride를 계산할 수 있습니다: 픽셀 너비 \* 픽셀 + 메모리 안쪽 여백 당 바이트 수입니다.

*destRect*<br/>
현재 비트맵에는 지역을 지정 srcRect 영역의 왼쪽 위 모퉁이 복사 됩니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 HRESULT 오류 코드를 반환합니다.

##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget

지정 된 위치에서 지정된 된 영역 복사 대상 현재 비트맵으로 렌더링 합니다.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 복사할 영역이 포함 합니다.

*destPoint*<br/>
현재 비트맵에는 지역을 지정 srcRect 영역의 왼쪽 위 모퉁이 복사 됩니다.

*srcRect*<br/>
복사할 renderTarget의 영역입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 HRESULT 오류 코드를 반환합니다.

##  <a name="create"></a>  CD2DBitmap::Create

CD2DBitmap를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 HRESULT 오류 코드를 반환합니다.

##  <a name="destroy"></a>  CD2DBitmap::Destroy

CD2DBitmap 개체를 제거합니다.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmap::Detach

개체에서 리소스 인터페이스를 분리합니다.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

##  <a name="get"></a>  CD2DBitmap::Get

ID2D1Bitmap 인터페이스를 반환 합니다.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>반환 값

ID2D1Bitmap 인터페이스 또는 개체가 아직 초기화 되지 않은 경우 NULL 포인터입니다.

##  <a name="getdpi"></a>  CD2DBitmap::GetDPI

인치당 (DPI) 비트맵을 반환 합니다.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>반환 값

비트맵의 가로 및 세로 DPI입니다.

##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat

비트맵의 픽셀 형식 및 알파 모드 검색

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>반환 값

비트맵의 픽셀 형식 및 알파 모드입니다.

##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize

비트맵의 크기를 장치 독립적 단위 (픽셀)를 반환합니다.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>반환 값

비트맵의 픽셀에서 크기...

##  <a name="getsize"></a>  CD2DBitmap::GetSize

비트맵의 크기를 장치 독립적 픽셀 (Dip)를 반환합니다.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>반환 값

Dip는 비트맵의 크기입니다.

##  <a name="isvalid"></a>  CD2DBitmap::IsValid

리소스 유효성을 검사 합니다.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스 유효 하면 TRUE 그렇지 않으면 FALSE입니다.

##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP

TRUE 이면 m_hBmpSrc 제거 해야 합니다. 그렇지 않으면 FALSE입니다.

```
BOOL m_bAutoDestroyHBMP;
```

##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc

원본 비트맵 핸들입니다.

```
HBITMAP m_hBmpSrc;
```

##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType

리소스 종류입니다.

```
LPCTSTR m_lpszType;
```

##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap

ID2D1Bitmap 개체에 대 한 포인터를 저장합니다.

```
ID2D1Bitmap* m_pBitmap;
```

##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest

대상 크기는 비트맵입니다.

```
CD2DSizeU m_sizeDest;
```

##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath

Botmap 파일 경로입니다.

```
CString m_strPath;
```

##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID

비트맵 리소스 id입니다.

```
UINT m_uiResID;
```

##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::operator ID2D1Bitmap*

반환 ID2D1Bitmap 인터페이스

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>반환 값

ID2D1Bitmap 인터페이스 또는 개체가 아직 초기화 되지 않은 경우 NULL 포인터입니다.

## <a name="see-also"></a>참고자료

[클래스](../../mfc/reference/mfc-classes.md)
