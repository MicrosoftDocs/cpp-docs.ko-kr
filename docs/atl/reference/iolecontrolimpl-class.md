---
description: '자세히 알아보기: IOleControlImpl 클래스'
title: IOleControlImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: e224f6f8db79c05cb8a774cd57517ba06108e592
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139427"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 클래스

이 클래스는 인터페이스의 기본 구현을 제공 `IOleControl` 하 고을 구현 `IUnknown` 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IOleControlImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IOleControlImpl:: FreezeEvents](#freezeevents)|컨테이너가 컨트롤의 이벤트를 무시할지 또는 수락할지를 나타냅니다.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|컨트롤의 키보드 동작에 대 한 정보를 채웁니다. ATL 구현은 E_NOTIMPL 반환 합니다.|
|[IOleControlImpl:: OnAmbientPropertyChange](#onambientpropertychange)|하나 이상의 컨테이너 앰비언트 속성이 변경 되었음을 컨트롤에 알립니다. ATL 구현은 S_OK 반환 합니다.|
|[IOleControlImpl:: OnMnemonic](#onmnemonic)|사용자가 지정 된 키 입력을 눌렀음을 컨트롤에 알립니다. ATL 구현은 E_NOTIMPL 반환 합니다.|

## <a name="remarks"></a>설명

클래스는 `IOleControlImpl` [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 덤프 장치로 정보를 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a> IOleControlImpl:: FreezeEvents

ATL의 구현에서 `FreezeEvents` 가 TRUE 이면 컨트롤 클래스의 `m_nFreezeEvents` 데이터 멤버를 증가 `bFreeze` 시키고 `m_nFreezeEvents` 가 FALSE 이면를 감소 시킵니다 `bFreeze` .

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>설명

`FreezeEvents` 그런 다음 S_OK 반환 합니다.

Windows SDK에서 [IOleControl:: FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) 를 참조 하세요.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a> IOleControlImpl::GetControlInfo

컨트롤의 키보드 동작에 대 한 정보를 채웁니다.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>설명

Windows SDK [IOleControl: GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) 를 참조 하세요.

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a> IOleControlImpl:: OnAmbientPropertyChange

하나 이상의 컨테이너 앰비언트 속성이 변경 되었음을 컨트롤에 알립니다.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleControl:: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) 를 참조 하세요.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a> IOleControlImpl:: OnMnemonic

사용자가 지정 된 키 입력을 눌렀음을 컨트롤에 알립니다.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IOleControl:: OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[IOleObjectImpl 클래스](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 컨트롤 인터페이스](/windows/win32/com/activex-controls-interfaces)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
