---
description: '자세히 알아보기: IObjectSafetyImpl 클래스'
title: IObjectSafetyImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: ac19fe24d12d7d09968b3e2d76f77741e83e1f81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139466"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl 클래스

이 클래스는 `IObjectSafety` 클라이언트에서 개체의 보안 수준을 검색 하 고 설정할 수 있도록 하는 인터페이스의 기본 구현을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IObjectSafetyImpl` 입니다.

*dwSupportedSafety*<br/>
컨트롤에 대해 지원 되는 보안 옵션을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) 매개 변수로 식별 되는 인터페이스는 `riid` 스크립팅에 안전 하 게 만들어야 합니다. INTERFACESAFE_FOR_UNTRUSTED_CALLER

- 매개 변수로 식별 되는 인터페이스를 초기화 하는 `SetInterfaceSafetyOptions` `riid` 동안 신뢰할 수 없는 데이터를 안전 하 게 보호 해야 하는 INTERFACESAFE_FOR_UNTRUSTED_DATA.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IObjectSafetyImpl:: GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|개체에서 지 원하는 안전 옵션과 현재 개체에 대해 설정 된 보안 옵션을 검색 합니다.|
|[IObjectSafetyImpl:: SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|개체를 초기화 또는 스크립팅에 안전 하 게 만듭니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[IObjectSafetyImpl:: m_dwCurrentSafety](#m_dwcurrentsafety)|개체의 현재 보안 수준을 저장 합니다.|

## <a name="remarks"></a>설명

클래스는 `IObjectSafetyImpl` 의 기본 구현을 제공 `IObjectSafety` 합니다. `IObjectSafety`인터페이스를 사용 하면 클라이언트에서 개체의 보안 수준을 검색 하 고 설정할 수 있습니다. 예를 들어 웹 브라우저는를 호출 `IObjectSafety::SetInterfaceSafetyOptions` 하 여 컨트롤을 초기화 하거나 스크립팅에 안전 하 게 만들 수 있습니다.

CATID_SafeForScripting 및 CATID_SafeForInitializing 구성 요소 범주에 [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) 매크로를 사용 하면 구성 요소를 안전 하 게 지정할 수 있는 대체 방법이 제공 됩니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a> IObjectSafetyImpl:: GetInterfaceSafetyOptions

개체에서 지 원하는 안전 옵션과 현재 개체에 대해 설정 된 보안 옵션을 검색 합니다.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>설명

구현은 개체의 구현에서 지원 되는 모든 인터페이스에 대 한 적절 한 값을 반환 합니다 `IUnknown::QueryInterface` .

> [!IMPORTANT]
> 에서 지 원하는 모든 개체는 `IObjectSafety` 자체 보안을 담당 하며이 개체는 위임 하는 모든 개체를 담당 합니다. 프로그래머는 사용자의 컨텍스트에서 코드를 실행할 때 발생 하는 문제를 고려해 야 하 고 사이트 간 스크립팅을 사용 하 여 적절 한 영역 검사를 수행 해야 합니다.

Windows SDK에서 [IObjectSafety:: GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) 를 참조 하세요.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a> IObjectSafetyImpl:: m_dwCurrentSafety

개체의 현재 보안 수준을 저장 합니다.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a> IObjectSafetyImpl:: SetInterfaceSafetyOptions

[M_dwCurrentSafety](#m_dwcurrentsafety) 멤버를 적절 한 값으로 설정 하 여 개체를 초기화 또는 스크립팅에 안전 하 게 만듭니다.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>설명

구현은 개체의 구현에서 지원 되지 않는 모든 인터페이스에 대 한 E_NOINTERFACE를 반환 합니다 `IUnknown::QueryInterface` .

> [!IMPORTANT]
> 에서 지 원하는 모든 개체는 `IObjectSafety` 자체 보안을 담당 하며이 개체는 위임 하는 모든 개체를 담당 합니다. 프로그래머는 사용자의 컨텍스트에서 코드를 실행할 때 발생 하는 문제를 고려해 야 하 고 사이트 간 스크립팅을 사용 하 여 적절 한 영역 검사를 수행 해야 합니다.

Windows SDK에서 [IObjectSafety:: SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[IObjectSafety 인터페이스](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[클래스 개요](../../atl/atl-class-overview.md)
