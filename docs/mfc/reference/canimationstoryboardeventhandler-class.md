---
description: '자세히 알아보기: CAnimationStoryboardEventHandler 클래스'
title: CAnimationStoryboardEventHandler 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 7208ba91ec78a6de688699183b55a691b8e3d28d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254744"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler 클래스

스토리보드의 상태가 변경되거나 스토리보드가 업데이트될 때 애니메이션 API에서 호출하는 콜백을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationStoryboardEventHandler:: CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|`CAnimationStoryboardEventHandler` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationStoryboardEventHandler:: CreateInstance](#createinstance)|콜백 인스턴스를 만듭니다 `CAnimationStoryboardEventHandler` .|
|[CAnimationStoryboardEventHandler:: OnStoryboardStatusChanged](#onstoryboardstatuschanged)|`OnStoryboardStatusChanged`스토리 보드의 상태가 변경 될 때 발생 하는 이벤트를 처리 `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged` 합니다 (재정의).|
|[CAnimationStoryboardEventHandler:: OnStoryboardUpdated](#onstoryboardupdated)|`OnStoryboardUpdated`스토리 보드를 업데이트할 때 발생 하는 이벤트를 처리 합니다 (재정의 `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated` ).|
|[CAnimationStoryboardEventHandler:: Set애니메이션 컨트롤러](#setanimationcontroller)|애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.|

## <a name="remarks"></a>설명

이 이벤트 처리기는를 호출할 때 생성 되어 메서드에 전달 됩니다 `IUIAnimationStoryboard::SetStoryboardEventHandler` `CAnimationController::EnableStoryboardEventHandler` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a> CAnimationStoryboardEventHandler:: CAnimationStoryboardEventHandler

CAnimationStoryboardEventHandler 개체를 생성 합니다.

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a> CAnimationStoryboardEventHandler:: CreateInstance

CAnimationStoryboardEventHandler callback의 인스턴스를 만듭니다.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

*ppHandler*

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a> CAnimationStoryboardEventHandler:: OnStoryboardStatusChanged

스토리 보드의 상태가 변경 될 때 발생 하는 OnStoryboardStatusChanged 이벤트를 처리 합니다.

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>매개 변수

*storyboard*<br/>
상태가 변경 된 storyboard에 대 한 포인터입니다.

*newStatus*<br/>
새 storyboard 상태를 지정 합니다.

*previousStatus*<br/>
이전 storyboard 상태를 지정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a> CAnimationStoryboardEventHandler:: OnStoryboardUpdated

스토리 보드가 업데이트 될 때 발생 하는 OnStoryboardUpdated 이벤트를 처리 합니다.

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>매개 변수

*storyboard*<br/>
업데이트 된 storyboard에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> CAnimationStoryboardEventHandler:: Set애니메이션 컨트롤러

애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
