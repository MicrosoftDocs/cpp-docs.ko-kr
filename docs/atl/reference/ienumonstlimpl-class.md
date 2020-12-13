---
description: '자세히 알아보기: IEnumOnSTLImpl 클래스'
title: IEnumOnSTLImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 33bc34288ebd03f987532ebb078fed62ce2204c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139492"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 클래스

이 클래스는 c + + 표준 라이브러리 컬렉션을 기반으로 하는 열거자 인터페이스를 정의 합니다.

## <a name="syntax"></a>구문

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
COM 열거자입니다. 예는 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 을 참조 하세요.

*piid*<br/>
열거자 인터페이스의 인터페이스 ID에 대 한 포인터입니다.

*T*<br/>
열거자 인터페이스에 의해 노출 되는 항목의 형식입니다.

*복사*<br/>
[복사 정책 클래스](../../atl/atl-copy-policy-classes.md)입니다.

*CollType*<br/>
C + + 표준 라이브러리 컨테이너 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|**복제본** 의 구현입니다.|
|[IEnumOnSTLImpl::Init](#init)|열거자를 초기화합니다.|
|[IEnumOnSTLImpl:: Next](#next)|**다음** 의 구현입니다.|
|[IEnumOnSTLImpl:: Reset](#reset)|**Reset** 의 구현입니다.|
|[IEnumOnSTLImpl:: Skip](#skip)|**Skip** 의 구현입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|컬렉션 내에서 열거자의 현재 위치를 나타내는 반복기입니다.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|열거할 항목을 보유 하는 c + + 표준 라이브러리 컨테이너에 대 한 포인터입니다.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown`컬렉션을 제공 하는 개체의 포인터입니다.|

## <a name="remarks"></a>설명

`IEnumOnSTLImpl` 열거 되는 항목이 c + + 표준 라이브러리 호환 컨테이너에 저장 되는 COM 열거자 인터페이스에 대 한 구현을 제공 합니다. 이 클래스는 배열을 기반으로 하는 열거자 인터페이스에 대 한 구현을 제공 하는 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) 클래스와 유사 합니다.

> [!NOTE]
> `CComEnumImpl` 및 `IEnumOnSTLImpl` 간의 추가 차이점에 대한 자세한 내용은 [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)를 참조하십시오.

일반적으로이 인터페이스 구현에서 파생 하 여 사용자 고유의 열거자 클래스를 만들 필요는 *없습니다* . C++ 표준 라이브러리 컨테이너를 기반으로 ATL 제공 열거자를 사용 하려는 경우 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)의 인스턴스를 만들거나 [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)에서 파생 하 여 열거자를 반환 하는 컬렉션 클래스를 만드는 것이 더 일반적입니다.

그러나 사용자 지정 열거자를 제공 해야 하는 경우 (예: 열거자 인터페이스 외에 인터페이스를 노출 하는 경우)이 클래스에서 파생 될 수 있습니다. 이 경우 사용자 고유의 구현을 제공 하기 위해 [Clone](#clone) 메서드를 재정의 해야 할 가능성이 높습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ienumonstlimplinit"></a><a name="init"></a> IEnumOnSTLImpl:: Init

열거자를 초기화합니다.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>매개 변수

*pUnkForRelease*<br/>
진행 `IUnknown` 열거자의 수명 동안 유지 해야 하는 개체의 포인터입니다. 이러한 개체가 없는 경우 NULL을 전달 합니다.

*컬렉션*<br/>
열거할 항목을 보유 하는 c + + 표준 라이브러리 컨테이너에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

다른 개체에 보관 된 컬렉션에 대 한 참조를 전달 하는 경우 `Init` *pUnkForRelease* 매개 변수를 사용 하 여 개체 및 개체를 포함 하는 컬렉션을 열거자가 필요로 하는 한에 사용할 수 있는지 확인할 수 있습니다.

열거자 인터페이스에 대 한 포인터를 클라이언트에 다시 전달 하기 전에이 메서드를 호출 해야 합니다.

## <a name="ienumonstlimplclone"></a><a name="clone"></a> IEnumOnSTLImpl:: Clone

이 메서드는 형식의 개체를 만들고  `CComEnumOnSTL` 현재 개체에서 사용 하는 것과 동일한 컬렉션과 반복기를 사용 하 여 초기화 한 다음 새로 만든 개체에서 인터페이스를 반환 하 여 Clone 메서드의 구현을 제공 합니다.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>매개 변수

*ppEnum*<br/>
제한이 현재 열거자에서 복제 된 새로 만든 개체의 열거자 인터페이스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a> IEnumOnSTLImpl:: m_spUnk

`IUnknown`컬렉션을 제공 하는 개체의 포인터입니다.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>설명

이 스마트 포인터는 [IEnumOnSTLImpl:: Init](#init)에 전달 된 개체에 대 한 참조를 유지 관리 하 여 열거자의 수명 동안 활성 상태로 유지 되도록 합니다.

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a> IEnumOnSTLImpl:: m_pcollection

이 멤버는 열거자 인터페이스의 구현을 구동 하는 데이터를 제공 하는 컬렉션을 가리킵니다.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>설명

이 멤버는 [IEnumOnSTLImpl:: Init](#init)를 호출 하 여 초기화 됩니다.

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a> IEnumOnSTLImpl:: m_iter

이 멤버는 컬렉션 내의 현재 위치를 표시 하 고 후속 요소로 이동 하는 데 사용 되는 반복기를 보유 합니다.

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a> IEnumOnSTLImpl:: Next

이 메서드는 **다음** 메서드의 구현을 제공 합니다.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>매개 변수

*celt*<br/>
진행 요청 된 요소의 수입니다.

*rgelt*<br/>
제한이 요소로 채워질 배열입니다.

*pceltFetched*<br/>
제한이 *Rgelt* 에서 실제로 반환 된 요소의 수입니다. *Celt* 요소가 목록에 남아 있는 경우이 *celt* 보다 적을 수 있습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ienumonstlimplreset"></a><a name="reset"></a> IEnumOnSTLImpl:: Reset

이 메서드는 **Reset** 메서드의 구현을 제공 합니다.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ienumonstlimplskip"></a><a name="skip"></a> IEnumOnSTLImpl:: Skip

이 메서드는 **Skip** 메서드의 구현을 제공 합니다.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>매개 변수

*celt*<br/>
진행 건너뛸 요소의 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
