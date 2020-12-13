---
description: '자세한 정보: IPointerInactiveImpl 클래스'
title: IPointerInactiveImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 0ee5c103582ff68c80edd36316179b47a1b7931d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139310"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 클래스

이 클래스 `IUnknown` 는 및 [Ipointerinactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) 인터페이스 메서드를 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IPointerInactiveImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IPointerInactiveImpl:: GetActivationPolicy](#getactivationpolicy)|개체에 대 한 현재 활성화 정책을 검색 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IPointerInactiveImpl:: OnInactiveMouseMove](#oninactivemousemove)|개체가 마우스 이벤트를 발생 시킬 수 있음을 나타내는 마우스 포인터를 개체 위로 이동 했음을 알립니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IPointerInactiveImpl:: OnInactiveSetCursor](#oninactivesetcursor)|비활성 개체에 대 한 마우스 포인터를 설정 합니다. ATL 구현은 E_NOTIMPL 반환 합니다.|

## <a name="remarks"></a>설명

비활성 개체는 단순히 로드 되거나 실행 되는 개체입니다. 활성 개체와 달리 비활성 개체는 Windows 마우스 및 키보드 메시지를 수신할 수 없습니다. 따라서 비활성 개체는 더 많은 리소스를 사용 하며 일반적으로 더 효율적입니다.

[Ipointerinactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) 인터페이스를 사용 하면 개체가 비활성화 된 상태에서 최소 수준의 마우스 상호 작용을 지원할 수 있습니다. 이 기능은 컨트롤에 특히 유용 합니다.

클래스 `IPointerInactiveImpl` 는 `IPointerInactive` 단순히 E_NOTIMPL 반환 하 여 메서드를 구현 합니다. 그러나 `IUnknown` 디버그 빌드에서 덤프 장치로 정보를 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a> IPointerInactiveImpl:: GetActivationPolicy

개체에 대 한 현재 활성화 정책을 검색 합니다.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK의 [Ipointerinactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) 을 참조 하세요.

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a> IPointerInactiveImpl:: OnInactiveMouseMove

개체가 마우스 이벤트를 발생 시킬 수 있음을 나타내는 마우스 포인터를 개체 위로 이동 했음을 알립니다.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK의 [Ipointerinactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) 를 참조 하세요.

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a> IPointerInactiveImpl:: OnInactiveSetCursor

비활성 개체에 대 한 마우스 포인터를 설정 합니다.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK의 [Ipointerinactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
