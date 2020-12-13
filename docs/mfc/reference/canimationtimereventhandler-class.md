---
description: '자세한 정보: Canimationand Eventhandler 클래스'
title: CAnimationTimerEventHandler 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: 5d5f3e07eeb7ffe3f3bb226afd566330808303ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336762"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler 클래스

타이밍 이벤트가 발생할 때 애니메이션 API에서 호출하는 콜백을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Canimation타이머 Eventhandler:: CreateInstance](#createinstance)|콜백 인스턴스를 만듭니다 `CAnimationTimerEventHandler` .|
|[CAnimationTimerEventHandler:: OnPostUpdate](#onpostupdate)|애니메이션 업데이트가 완료 된 후 발생 하는 이벤트를 처리 합니다. ( `CUIAnimationTimerEventHandlerBase::OnPostUpdate`을 재정의합니다.)|
|[CAnimationTimerEventHandler:: OnPreUpdate](#onpreupdate)|애니메이션 업데이트를 시작 하기 전에 발생 하는 이벤트를 처리 합니다. ( `CUIAnimationTimerEventHandlerBase::OnPreUpdate`을 재정의합니다.)|
|[CanimationOnRenderingTooSlow Eventhandler::](#onrenderingtooslow)|애니메이션의 렌더링 프레임 비율이 원하는 최소 프레임 속도로 떨어질 때 발생 하는 이벤트를 처리 합니다. ( `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`을 재정의합니다.)|
|[Canimationand Eventhandler:: Set애니메이션 컨트롤러](#setanimationcontroller)|애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.|

## <a name="remarks"></a>설명

이 이벤트 처리기는 CAnimationController:: EnableAnimationTimerEventHandler를 호출할 때 생성 되 고 IUIAnimationTimer:: Set타이머 처리기에 전달 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a> Canimation타이머 Eventhandler:: CreateInstance

Canimationeventhandler Eventhandler 콜백의 인스턴스를 만듭니다.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

*Pp타이머 이벤트 처리기*

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a> CAnimationTimerEventHandler:: OnPostUpdate

애니메이션 업데이트가 완료 된 후 발생 하는 이벤트를 처리 합니다.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a> CAnimationTimerEventHandler:: OnPreUpdate

애니메이션 업데이트를 시작 하기 전에 발생 하는 이벤트를 처리 합니다.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a> CanimationOnRenderingTooSlow Eventhandler::

애니메이션의 렌더링 프레임 비율이 원하는 최소 프레임 속도로 떨어질 때 발생 하는 이벤트를 처리 합니다.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>매개 변수

*24*

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> Canimationand Eventhandler:: Set애니메이션 컨트롤러

애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
