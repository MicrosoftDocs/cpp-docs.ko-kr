---
description: '자세히 알아보기: CAnimationVariableIntegerChangeHandler 클래스'
title: CAnimationVariableIntegerChangeHandler 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: 53a0a1838e021294b4ccc870e6f01b873233a0c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336737"
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler 클래스

애니메이션 변수 값이 변경될 때 애니메이션 API에서 호출하는 콜백을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler:: CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|`CAnimationVariableIntegerChangeHandler` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler:: CreateInstance](#createinstance)|콜백 인스턴스를 만듭니다 `CAnimationVariableIntegerChangeHandler` .|
|[CAnimationVariableIntegerChangeHandler:: OnIntegerValueChanged](#onintegervaluechanged)|애니메이션 변수 값이 변경 되 면 호출 됩니다. ( `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`을 재정의합니다.)|
|[CAnimationVariableIntegerChangeHandler:: Set애니메이션 컨트롤러](#setanimationcontroller)|애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.|

## <a name="remarks"></a>설명

이 이벤트 처리기는 CAnimationVariable:: EnableIntegerValueChangedEvent 또는 CAnimationBaseObject:: EnableIntegerValueChangedEvent (애니메이션 개체에 캡슐화 된 모든 애니메이션 변수에 대해이 이벤트를 사용 하도록 설정)를 호출 하는 경우 생성 되어 IuiSetVariableIntegerChangeHandler Variable:: 메서드에 전달 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[MFC 클래스](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a> CAnimationVariableIntegerChangeHandler:: CAnimationVariableIntegerChangeHandler

CAnimationVariableIntegerChangeHandler 개체를 생성 합니다.

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a> CAnimationVariableIntegerChangeHandler:: CreateInstance

CAnimationVariableIntegerChangeHandler callback의 인스턴스를 만듭니다.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

*ppHandler*

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a> CAnimationVariableIntegerChangeHandler:: OnIntegerValueChanged

애니메이션 변수 값이 변경 되 면 호출 됩니다.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>매개 변수

*storyboard*<br/>
변수에 애니메이션 효과를 주는 storyboard입니다.

*variable*<br/>
업데이트 된 애니메이션 변수입니다.

*newValue*<br/>
반올림 된 새 값입니다.

*previousValue*<br/>
이전 반올림 값입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 합니다.

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> CAnimationVariableIntegerChangeHandler:: Set애니메이션 컨트롤러

애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
