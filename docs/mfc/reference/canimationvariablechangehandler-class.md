---
description: '자세히 알아보기: CAnimationVariableChangeHandler 클래스'
title: CAnimationVariableChangeHandler 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 1c97bc908a29bfb7edf2222f6df117fefdaf4091
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207880"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler 클래스

애니메이션 변수 값이 변경될 때 애니메이션 API에서 호출하는 콜백을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|`CAnimationVariableChangeHandler` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|개체의 인스턴스를 만듭니다 `CAnimationVariableChangeHandler` .|
|[CAnimationVariableChangeHandler:: OnValueChanged](#onvaluechanged)|애니메이션 변수 값이 변경 되 면 호출 됩니다. ( `CUIAnimationVariableChangeHandlerBase::OnValueChanged`을 재정의합니다.)|
|[CAnimationVariableChangeHandler:: Set애니메이션 컨트롤러](#setanimationcontroller)|애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.|

## <a name="remarks"></a>설명

이 이벤트 처리기는 `IUIAnimationVariable::SetVariableChangeHandler` `CAnimationVariable::EnableValueChangedEvent` 또는 `CAnimationBaseObject::EnableValueChangedEvent` (애니메이션 개체에 캡슐화 된 모든 애니메이션 변수에 대해이 이벤트를 사용 하도록 설정)를 호출할 때 생성 되어 메서드에 전달 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a> CAnimationVariableChangeHandler:: OnValueChanged

애니메이션 변수 값이 변경 되 면 호출 됩니다.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>매개 변수

*storyboard*<br/>
변수에 애니메이션 효과를 주는 storyboard입니다.

*variable*<br/>
업데이트 된 애니메이션 변수입니다.

*newValue*<br/>
새 값입니다.

*previousValue*<br/>
이전 값입니다.

### <a name="return-value"></a>반환 값

메서드가 성공하면 S_OK가 반환되고, 그렇지 않으면 HRESULT 오류 코드를 반환 합니다.

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> CAnimationVariableChangeHandler:: Set애니메이션 컨트롤러

애니메이션 컨트롤러에 대 한 포인터를 저장 하 여 이벤트를 라우팅합니다.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>매개 변수

*가는 Imationcontroller*<br/>
이벤트를 수신 하는 애니메이션 컨트롤러에 대 한 포인터입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
