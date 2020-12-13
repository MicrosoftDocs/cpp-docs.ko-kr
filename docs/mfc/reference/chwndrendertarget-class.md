---
description: '자세히 알아보기: CHwndRenderTarget 클래스'
title: CHwndRenderTarget 클래스
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: 3a3058105fff5e5ac304f2cc980cd93f2bac70a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143639"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 클래스

ID2D1HwndRenderTarget에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHwndRenderTarget:: CHwndRenderTarget](#chwndrendertarget)|HWND에서 CHwndRenderTarget 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHwndRenderTarget:: Attach](#attach)|기존 렌더링 대상 인터페이스를 개체에 연결 합니다.|
|[CHwndRenderTarget:: CheckWindowState](#checkwindowstate)|이 렌더링 대상과 연결 된 HWND가 폐색 여부를 나타냅니다.|
|[CHwndRenderTarget:: Create](#create)|창과 연결 된 렌더링 대상을 만듭니다.|
|[CHwndRenderTarget::D etach](#detach)|개체에서 렌더링 대상 인터페이스를 분리 합니다.|
|[CHwndRenderTarget:: GetHwnd](#gethwnd)|이 렌더링 대상과 연결 된 HWND를 반환 합니다.|
|[CHwndRenderTarget:: GetHwndRenderTarget](#gethwndrendertarget)|ID2D1HwndRenderTarget 인터페이스를 반환 합니다.|
|[CHwndRenderTarget:: 다시 만들기](#recreate)|창과 연결 된 렌더링 대상을 다시 만듭니다.|
|[CHwndRenderTarget:: Resize](#resize)|렌더링 대상의 크기를 지정 된 픽셀 크기로 변경 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CHwndRenderTarget:: operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|ID2D1HwndRenderTarget 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CHwndRenderTarget:: m_pHwndRenderTarget](#m_phwndrendertarget)|ID2D1HwndRenderTarget 개체에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="chwndrendertargetattach"></a><a name="attach"></a> CHwndRenderTarget:: Attach

기존 렌더링 대상 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>매개 변수

*pTarget*<br/>
기존 렌더링 대상 인터페이스입니다. NULL 일 수 없음

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a> CHwndRenderTarget:: CheckWindowState

이 렌더링 대상과 연결 된 HWND가 폐색 여부를 나타냅니다.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>반환 값

이 렌더링 대상과 연결 된 HWND가 폐색 여부를 나타내는 값입니다.

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a> CHwndRenderTarget:: CHwndRenderTarget

HWND에서 CHwndRenderTarget 개체를 생성 합니다.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>매개 변수

*hwnd*<br/>
이 렌더링 대상과 연결 된 HWND입니다.

## <a name="chwndrendertargetcreate"></a><a name="create"></a> CHwndRenderTarget:: Create

창과 연결 된 렌더링 대상을 만듭니다.

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
이 렌더링 대상과 연결 된 HWND입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="chwndrendertargetdetach"></a><a name="detach"></a> CHwndRenderTarget::D etach

개체에서 렌더링 대상 인터페이스를 분리 합니다.

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 렌더링 대상 인터페이스에 대 한 포인터입니다.

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a> CHwndRenderTarget:: GetHwnd

이 렌더링 대상과 연결 된 HWND를 반환 합니다.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>반환 값

이 렌더링 대상과 연결 된 HWND입니다.

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a> CHwndRenderTarget:: GetHwndRenderTarget

ID2D1HwndRenderTarget 인터페이스를 반환 합니다.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>반환 값

ID2D1HwndRenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a> CHwndRenderTarget:: m_pHwndRenderTarget

ID2D1HwndRenderTarget 개체에 대 한 포인터입니다.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a> CHwndRenderTarget:: operator ID2D1HwndRenderTarget *

ID2D1HwndRenderTarget 인터페이스를 반환 합니다.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>반환 값

ID2D1HwndRenderTarget 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a> CHwndRenderTarget:: 다시 만들기

창과 연결 된 렌더링 대상을 다시 만듭니다.

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>매개 변수

*hWnd*<br/>
이 렌더링 대상과 연결 된 HWND입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="chwndrendertargetresize"></a><a name="resize"></a> CHwndRenderTarget:: Resize

렌더링 대상의 크기를 지정 된 픽셀 크기로 변경 합니다.

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
장치 픽셀에서 렌더링 대상의 새 크기

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
