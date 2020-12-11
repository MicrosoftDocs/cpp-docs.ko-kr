---
description: '자세히 알아보기: IQuickActivateImpl 클래스'
title: IQuickActivateImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 1e9dc2891351512ec3ebe54ebe6711ee9d4a3fa0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158129"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 클래스

이 클래스는 컨테이너의 컨트롤 초기화를 단일 호출로 결합 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IQuickActivateImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IQuickActivateImpl:: GetContentExtent](#getcontentextent)|실행 중인 컨트롤의 현재 표시 크기를 검색 합니다.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|로드 되는 컨트롤의 빠른 초기화를 수행 합니다.|
|[IQuickActivateImpl:: SetContentExtent](#setcontentextent)|컨테이너가 할당 한 표시 공간의 크기를 컨트롤에 알립니다.|

## <a name="remarks"></a>설명

[Iquickactivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) 인터페이스를 통해 컨테이너는 단일 호출에서 초기화를 결합 하 여 컨트롤을 로드할 때 지연을 방지할 수 있습니다. `QuickActivate` 메서드를 통해 컨테이너는 컨트롤에 필요한 모든 인터페이스에 대한 포인터를 포함하는 [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) 구조체에 대한 포인터를 전달할 수 있습니다. 반환 시 컨트롤은 컨테이너에서 사용 되는 자체 인터페이스에 대 한 포인터를 보유 하는 [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) 구조체에 포인터를 다시 전달 합니다. 클래스는 `IQuickActivateImpl` 의 기본 구현을 제공 `IQuickActivate` 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a> IQuickActivateImpl:: GetContentExtent

실행 중인 컨트롤의 현재 표시 크기를 검색 합니다.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>설명

크기는 컨트롤의 전체 렌더링을 위한 것 이며 HIMETRIC unit에 지정 됩니다.

Windows SDK에서 [Iquickactivate:: GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) 를 참조 하세요.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a> IQuickActivateImpl:: QuickActivate

로드 되는 컨트롤의 빠른 초기화를 수행 합니다.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>설명

구조체에는 컨트롤에 필요한 인터페이스에 대 한 포인터와 일부 앰비언트 속성의 값이 포함 되어 있습니다. 반환 될 때 컨트롤은 컨테이너에 필요한 자체 인터페이스에 대 한 포인터와 추가 상태 정보를 포함 하는 [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) 구조체에 대 한 포인터를 전달 합니다.

Windows SDK에서 [Iquickactivate:: QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) 를 참조 하세요.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a> IQuickActivateImpl:: SetContentExtent

컨테이너가 할당 한 표시 공간의 크기를 컨트롤에 알립니다.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>설명

크기는 HIMETRIC units로 지정 됩니다.

Windows SDK에서 [Iquickactivate:: SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
