---
description: '자세히 알아보기: CD2DPathGeometry 클래스'
title: CD2DPathGeometry 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: eb33d498436c887eb038b3312e2b98ca04d6620b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280536"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry 클래스

ID2D1PathGeometry에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DPathGeometry:: CD2DPathGeometry](#cd2dpathgeometry)|CD2DPathGeometry 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DPathGeometry:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DPathGeometry:: Create](#create)|CD2DPathGeometry를 만듭니다. [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create)를 재정의 합니다.|
|[CD2DPathGeometry::D estroy](#destroy)|CD2DPathGeometry 개체를 소멸 시킵니다. [CD2DGeometry::D estroy](../../mfc/reference/cd2dgeometry-class.md#destroy)를 재정의 합니다.|
|[CD2DPathGeometry::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DPathGeometry:: Get](#getfigurecount)|경로 기 하 도형의 그림 수를 검색 합니다.|
|[CD2DPathGeometry:: GetSegmentCount](#getsegmentcount)|경로 기 하 도형의 세그먼트 수를 검색 합니다.|
|[CD2DPathGeometry:: Open](#open)|그림 및 세그먼트로 경로 기 하 도형을 채우는 데 사용 되는 기 하 도형 싱크를 검색 합니다.|
|[CD2DPathGeometry:: Stream](#stream)|경로 기 하 도형의 내용을 지정 된 ID2D1GeometrySink에 복사 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DPathGeometry:: m_pPathGeometry](#m_ppathgeometry)|ID2D1PathGeometry에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a> CD2DPathGeometry:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL 일 수 없음

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a> CD2DPathGeometry:: CD2DPathGeometry

CD2DPathGeometry 개체를 생성 합니다.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a> CD2DPathGeometry:: Create

CD2DPathGeometry를 만듭니다.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>매개 변수

*pRenderTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a> CD2DPathGeometry::D estroy

CD2DPathGeometry 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a> CD2DPathGeometry::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a> CD2DPathGeometry:: Get

경로 기 하 도형의 그림 수를 검색 합니다.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>반환 값

경로 기 하 도형의 그림 수를 반환 합니다.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a> CD2DPathGeometry:: GetSegmentCount

경로 기 하 도형의 세그먼트 수를 검색 합니다.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>반환 값

경로 기 하 도형의 세그먼트 수를 반환 합니다.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a> CD2DPathGeometry:: m_pPathGeometry

ID2D1PathGeometry에 대 한 포인터입니다.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a> CD2DPathGeometry:: Open

그림 및 세그먼트로 경로 기 하 도형을 채우는 데 사용 되는 기 하 도형 싱크를 검색 합니다.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>반환 값

그림 및 세그먼트로 경로 기 하 도형을 채우는 데 사용 되는 ID2D1GeometrySink에 대 한 포인터입니다.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a> CD2DPathGeometry:: Stream

경로 기 하 도형의 내용을 지정 된 ID2D1GeometrySink에 복사 합니다.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>매개 변수

*geometrySink*<br/>
경로 기 하 도형의 내용이 복사 되는 싱크입니다. 이 싱크를 수정 해도이 경로 형상의 내용은 변경 되지 않습니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
