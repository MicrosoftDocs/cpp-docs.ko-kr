---
description: '자세히 알아보기: CComEnumImpl 클래스'
title: CComEnumImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 25cdaaeeb424d0770df1dab16ef5f72e7bc5cdb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152076"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl 클래스

이 클래스는 열거 되는 항목이 배열에 저장 되는 COM 열거자 인터페이스에 대 한 구현을 제공 합니다.

## <a name="syntax"></a>구문

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
COM 열거자 인터페이스입니다. 예는 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 을 참조 하세요.

*piid*<br/>
열거자 인터페이스의 인터페이스 ID에 대 한 포인터입니다.

*T*<br/>
열거자 인터페이스에 의해 노출 되는 항목의 형식입니다.

*복사*<br/>
유형이 같은 [복사 정책 클래스](../../atl/atl-copy-policy-classes.md)입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|생성자입니다.|
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComEnumImpl:: Clone](#clone)|**Clone** 열거 인터페이스 메서드의 구현입니다.|
|[CComEnumImpl:: Init](#init)|열거자를 초기화합니다.|
|[CComEnumImpl:: Next](#next)|**다음** 의 구현입니다.|
|[CComEnumImpl:: Reset](#reset)|**Reset** 의 구현입니다.|
|[CComEnumImpl:: Skip](#skip)|**Skip** 의 구현입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComEnumImpl:: m_begin](#m_begin)|배열의 첫 번째 항목에 대 한 포인터입니다.|
|[CComEnumImpl:: m_dwFlags](#m_dwflags)|를 통해 전달 된 복사 플래그 `Init` 입니다.|
|[CComEnumImpl:: m_end](#m_end)|배열의 마지막 항목 바로 다음 위치에 대 한 포인터입니다.|
|[CComEnumImpl:: m_iter](#m_iter)|배열의 현재 항목에 대 한 포인터입니다.|
|[CComEnumImpl:: m_spUnk](#m_spunk)|`IUnknown`열거 되는 컬렉션을 제공 하는 개체의 포인터입니다.|

## <a name="remarks"></a>설명

메서드 구현에 대 한 예제는 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 를 참조 하세요. `CComEnumImpl` 열거 되는 항목이 배열에 저장 되는 COM 열거자 인터페이스에 대 한 구현을 제공 합니다. 이 클래스는 `IEnumOnSTLImpl` c + + 표준 라이브러리 컨테이너를 기반으로 하는 열거자 인터페이스의 구현을 제공 하는 클래스와 유사 합니다.

> [!NOTE]
> 및 간의 추가 차이점에 대 한 자세한 `CComEnumImpl` `IEnumOnSTLImpl` 내용은 [CComEnumImpl:: Init](#init)를 참조 하세요.

일반적으로이 인터페이스 구현에서 파생 하 여 사용자 고유의 열거자 클래스를 만들 필요는 *없습니다* . 배열에 따라 ATL 제공 열거자를 사용 하려는 경우 [CComEnum](../../atl/reference/ccomenum-class.md)의 인스턴스를 만드는 것이 더 일반적입니다.

그러나 사용자 지정 열거자를 제공 해야 하는 경우 (예: 열거자 인터페이스 외에 인터페이스를 노출 하는 경우)이 클래스에서 파생 될 수 있습니다. 이 경우 사용자 고유의 구현을 제공 하기 위해 [CComEnumImpl:: Clone](#clone) 메서드를 재정의 해야 할 수 있습니다.

자세한 내용은 [ATL 컬렉션 및 열거자](../../atl/atl-collections-and-enumerators.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`CComEnumImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a> CComEnumImpl::CComEnumImpl

생성자입니다.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a> CComEnumImpl:: ~ CComEnumImpl

소멸자입니다.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a> CComEnumImpl:: Init

열거자 인터페이스에 대 한 포인터를 클라이언트에 다시 전달 하기 전에이 메서드를 호출 해야 합니다.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>매개 변수

*시작*<br/>
열거할 항목을 포함 하는 배열의 첫 번째 요소에 대 한 포인터입니다.

*end*<br/>
열거할 항목이 들어 있는 배열의 마지막 요소 바로 다음 위치에 대 한 포인터입니다.

*pUnk*<br/>
진행 `IUnknown` 열거자의 수명 동안 유지 해야 하는 개체의 포인터입니다. 이러한 개체가 없는 경우 NULL을 전달 합니다.

*flags*<br/>
열거자가 배열의 소유권을 가져와야 하는지 아니면 복사를 만들지를 지정 하는 플래그입니다. 가능한 값은 아래에 설명 되어 있습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 메서드를 한 번만 호출 합니다. 즉, 열거자를 초기화 하 고 사용한 다음이를 throw 합니다.

다른 개체에 보관 된 배열의 항목에 대 한 포인터를 전달 하 고 데이터를 복사 하도록 열거자에 요청 하지 않는 경우 *pUnk* 매개 변수를 사용 하 여 열거자에 필요한 경우에만 개체와 해당 개체를 사용할 수 있도록 합니다. 열거자는 개체에 대 한 COM 참조를 보유 하 여 활성 상태로 유지 합니다. COM 참조는 열거자가 제거 될 때 자동으로 해제 됩니다.

*Flags* 매개 변수를 사용 하면 열거자가 전달 된 배열 요소를 처리 하는 방법을 지정할 수 있습니다. *플래그* 는 아래에 표시 된 열거형의 값 중 하나를 사용할 수 있습니다 `CComEnumFlags` .

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy` 는 배열의 수명이 열거자에 의해 제어 되지 않음을 의미 합니다. 이 경우 배열이 정적 이거나 *pUnk* 으로 식별 되는 개체가 더 이상 필요 하지 않을 때 배열을 해제 해야 합니다.

`AtlFlagTakeOwnership` 는 열거자가 배열의 소멸을 제어 함을 의미 합니다. 이 경우에는를 사용 하 여 배열을 동적으로 할당 해야 합니다 **`new`** . 열거자가 해당 소멸자에서 배열을 삭제 합니다. 일반적으로 *pUnk* 에 대해 NULL을 전달 합니다. 그러나 어떤 이유로 든 열거자 소멸에 대 한 알림이 필요한 경우에도 유효한 포인터를 전달할 수 있습니다.

`AtlFlagCopy` 로 전달 된 배열을 복사 하 여 새 배열을 만들 수 있음을 의미 `Init` 합니다. 새 배열의 수명은 열거자에 의해 제어 됩니다. 열거자가 해당 소멸자에서 배열을 삭제 합니다. 일반적으로 *pUnk* 에 대해 NULL을 전달 합니다. 그러나 어떤 이유로 든 열거자 소멸에 대 한 알림이 필요한 경우에도 유효한 포인터를 전달할 수 있습니다.

> [!NOTE]
> 이 메서드의 프로토타입은 배열 요소를 형식으로 지정 합니다 `T` . 여기서는 `T` 클래스에 대 한 템플릿 매개 변수로 정의 됩니다. 이는 COM 인터페이스 메서드 [CComEnumImpl:: Next](#next)를 통해 노출 되는 형식과 동일 합니다. 이는 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)와 달리이 클래스는 다른 저장소 및 노출 된 데이터 형식을 지원 하지 않는다는 의미입니다. 배열에 있는 요소의 데이터 형식은 COM 인터페이스를 통해 노출 되는 데이터 형식과 동일 해야 합니다.

## <a name="ccomenumimplclone"></a><a name="clone"></a> CComEnumImpl:: Clone

이 메서드는 형식의 개체를 만들고  `CComEnum` 현재 개체에서 사용 하는 동일한 배열 및 반복기를 사용 하 여 초기화 한 다음 새로 만든 개체에 대 한 인터페이스를 반환 하 여 Clone 메서드의 구현을 제공 합니다.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>매개 변수

*ppEnum*<br/>
제한이 현재 열거자에서 복제 된 새로 만든 개체의 열거자 인터페이스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

복제 된 열거자는 원래 열거자에서 사용 하는 데이터의 자체 복사본을 만들거나 소유권을 받지 않습니다. 필요한 경우 복제 된 열거자는 원본 열거자를 활성 상태로 유지 하 여 (COM 참조 사용) 데이터를 필요할 때까지 사용할 수 있도록 합니다.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a> CComEnumImpl:: m_spUnk

이 스마트 포인터는 [CComEnumImpl:: Init](#init)에 전달 된 개체에 대 한 참조를 유지 관리 하 여 열거자의 수명 동안 활성 상태로 유지 되도록 합니다.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a> CComEnumImpl:: m_begin

열거할 항목이 들어 있는 배열의 마지막 요소 바로 다음 위치에 대 한 포인터입니다.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a> CComEnumImpl:: m_end

열거할 항목을 포함 하는 배열의 첫 번째 요소에 대 한 포인터입니다.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a> CComEnumImpl:: m_iter

열거할 항목을 포함 하는 배열의 현재 요소에 대 한 포인터입니다.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a> CComEnumImpl:: m_dwFlags

[CComEnumImpl:: Init](#init)에 전달 된 플래그입니다.

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a> CComEnumImpl:: Next

이 메서드는 **다음** 메서드의 구현을 제공 합니다.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>매개 변수

*celt*<br/>
진행 요청 된 요소의 수입니다.

*rgelt*<br/>
제한이 요소로 채워질 배열입니다.

*pceltFetched*<br/>
제한이 *Rgelt* 에서 실제로 반환 된 요소의 수입니다. *Celt* 요소가 목록에 남아 있는 경우 *celt* 보다 적을 수 있습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ccomenumimplreset"></a><a name="reset"></a> CComEnumImpl:: Reset

이 메서드는 **Reset** 메서드의 구현을 제공 합니다.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ccomenumimplskip"></a><a name="skip"></a> CComEnumImpl:: Skip

이 메서드는 **Skip** 메서드의 구현을 제공 합니다.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>매개 변수

*celt*<br/>
진행 건너뛸 요소의 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

*Celt* 가 0 이면 E_INVALIDARG을 반환 하 고, *celt* 요소 보다 작은 값을 반환 하면 S_FALSE S_OK을 반환 하 고, 그렇지 않으면를 반환 합니다.

## <a name="see-also"></a>참고 항목

[IEnumOnSTLImpl 클래스](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum 클래스](../../atl/reference/ccomenum-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
