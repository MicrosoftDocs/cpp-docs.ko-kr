---
description: '다음에 대 한 자세한 정보: CDCRenderTarget 클래스'
title: CDCRenderTarget 클래스
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 3959321bbd6274c821b1f02be5962b23ec9dbc95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185325"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 클래스

ID2D1DCRenderTarget에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDCRenderTarget:: CDCRenderTarget](#cdcrendertarget)|CDCRenderTarget 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDCRenderTarget:: Attach](#attach)|기존 렌더링 대상 인터페이스를 개체에 연결 합니다.|
|[CDCRenderTarget:: BindDC](#binddc)|렌더링 대상을 그리기 명령이 실행 되는 장치 컨텍스트에 바인딩합니다.|
|[CDCRenderTarget:: Create](#create)|CDCRenderTarget을 만듭니다.|
|[CDCRenderTarget::D etach](#detach)|개체에서 렌더링 대상 인터페이스를 분리 합니다.|
|[CDCRenderTarget:: GetDCRenderTarget](#getdcrendertarget)|ID2D1DCRenderTarget 인터페이스를 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CDCRenderTarget:: operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|ID2D1DCRenderTarget 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDCRenderTarget:: m_pDCRenderTarget](#m_pdcrendertarget)|ID2D1DCRenderTarget 개체에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cdcrendertargetattach"></a><a name="attach"></a> CDCRenderTarget:: Attach

기존 렌더링 대상 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>매개 변수

*pTarget*<br/>
기존 렌더링 대상 인터페이스입니다. NULL 일 수 없음

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a> CDCRenderTarget:: BindDC

렌더링 대상을 그리기 명령이 실행 되는 장치 컨텍스트에 바인딩합니다.

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
렌더링 대상에서 그리기 명령이 실행 되는 장치 컨텍스트입니다.

*rect*<br/>
렌더링 대상이 바인딩되는 장치 컨텍스트 (HDC)에 대 한 핸들의 크기입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a> CDCRenderTarget:: CDCRenderTarget

CDCRenderTarget 개체를 생성 합니다.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a> CDCRenderTarget:: Create

CDCRenderTarget을 만듭니다.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>매개 변수

*.props*<br/>
렌더링 모드, 픽셀 형식, 원격 옵션, DPI 정보 및 하드웨어 렌더링에 필요한 최소 DirectX 지원입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a> CDCRenderTarget::D etach

개체에서 렌더링 대상 인터페이스를 분리 합니다.

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 렌더링 대상 인터페이스에 대 한 포인터입니다.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a> CDCRenderTarget:: GetDCRenderTarget

ID2D1DCRenderTarget 인터페이스를 반환 합니다.

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>반환 값

ID2D1DCRenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a> CDCRenderTarget:: m_pDCRenderTarget

ID2D1DCRenderTarget 개체에 대 한 포인터입니다.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a> CDCRenderTarget:: operator ID2D1DCRenderTarget *

ID2D1DCRenderTarget 인터페이스를 반환 합니다.

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>반환 값

ID2D1DCRenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
