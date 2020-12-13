---
description: '자세히 알아보기: CFirePropNotifyEvent 클래스'
title: CFirePropNotifyEvent 클래스
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 09102e67408195751e083807f444c1b028fd2762
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141728"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 클래스

이 클래스는 컨테이너의 싱크에 컨트롤 속성 변경 내용에 대 한 알림을 제공 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CFirePropNotifyEvent
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|정적인 컨트롤 속성이 변경 되었음을 컨테이너 싱크에 알립니다.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|정적인 컨트롤 속성이 변경 될 것으로 컨테이너 싱크에 알립니다.|

## <a name="remarks"></a>설명

`CFirePropNotifyEvent` 에는 컨트롤 속성이 변경 되었거나 변경 될 것 이라는 것을 컨테이너 싱크에 알리는 두 가지 메서드가 있습니다.

컨트롤을 구현 하는 클래스가에서 파생 되는 경우 `IPropertyNotifySink` `CFirePropNotifyEvent` 또는를 호출할 때 메서드가 호출 `FireOnRequestEdit` 됩니다 `FireOnChanged` . 컨트롤 클래스가에서 파생 되지 않은 경우 `IPropertyNotifySink` 이러한 함수를 호출 하면 S_OK 반환 됩니다.

컨트롤을 만드는 방법에 대 한 자세한 내용은 [ATL 자습서](../../atl/active-template-library-atl-tutorial.md)를 참조 하십시오.

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a> CFirePropNotifyEvent::FireOnChanged

지정 된 개체 속성이 변경 된 모든 연결 된 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스 (개체의 모든 연결 지점에서)에 게 알립니다.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 알림을 보내는 개체의에 대 한 포인터입니다.

*dispID*<br/>
진행 변경 된 속성의 식별자입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

컨트롤에서 연결 지점이 지원 되지 않는 경우에도이 함수는를 호출 하는 것이 안전 합니다.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a> CFirePropNotifyEvent::FireOnRequestEdit

지정 된 개체 속성이 변경 될 모든 연결 된 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스 (개체의 모든 연결 지점에서)에 게 알립니다.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 알림을 보내는 개체의에 대 한 포인터입니다.

*dispID*<br/>
진행 변경할 속성의 식별자입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

컨트롤에서 연결 지점이 지원 되지 않는 경우에도이 함수는를 호출 하는 것이 안전 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
