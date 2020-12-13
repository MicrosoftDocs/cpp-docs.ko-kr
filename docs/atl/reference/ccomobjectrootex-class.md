---
description: '자세히 알아보기: CComObjectRootEx 클래스'
title: CComObjectRootEx 클래스
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 9fe0140944e3da5ddf70e0da38d054a35bb648ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142482"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 클래스

이 클래스는 집계할 수 없는 개체와 집계 된 개체 모두에 대 한 개체 참조 수 관리를 처리 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>매개 변수

*ThreadModel*<br/>
해당 메서드가 원하는 스레딩 모델을 구현 하는 클래스입니다. *Threadmodel* 을 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)또는 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)로 설정 하 여 스레딩 모델을 명시적으로 선택할 수 있습니다. *Threadmodel* 을 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) 또는 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)로 설정 하 여 서버의 기본 스레드 모델을 허용할 수 있습니다.

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|함수|설명|
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|생성자입니다.|
|[InternalAddRef](#internaladdref)|집계할 수 없는 개체에 대 한 참조 횟수를 늘립니다.|
|[InternalRelease](#internalrelease)|집계할 수 없는 개체의 참조 횟수를 감소 시킵니다.|
|[잠금](#lock)|스레드 모델이 다중 스레드 인 경우 임계 영역 개체의 소유권을 가져옵니다.|
|[잠금 해제](#unlock)|스레드 모델이 다중 스레드 인 경우는 임계 영역 개체의 소유권을 해제 합니다.|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 메서드

|함수|설명|
|-|-|
|[모든 구문](#finalconstruct)|클래스에서를 재정의 하 여 개체에 필요한 초기화를 수행 합니다.|
|[버전 릴리스](#finalrelease)|클래스에서를 재정의 하 여 개체에 필요한 정리를 수행 합니다.|
|[OuterAddRef](#outeraddref)|집계 된 개체의 참조 횟수를 증가 시킵니다.|
|[OuterQueryInterface](#outerqueryinterface)|집계 된 개체의 외부에 대리자를 위임 `IUnknown` 합니다.|
|[OuterRelease](#outerrelease)|집계 된 개체의 참조 횟수를 감소 시킵니다.|

### <a name="static-functions"></a>정적 함수

|함수|설명|
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|집계할 수 없는 개체의에 대 한 대리자입니다 `IUnknown` .|
|[ObjectMain](#objectmain)|개체 맵에 나열 된 파생 클래스에 대해 모듈을 초기화 하 고 종료 하는 동안 호출 됩니다.|

### <a name="data-members"></a>데이터 멤버

|데이터 멤버|설명|
|-|-|
|[m_dwRef](#m_dwref)|`m_pOuterUnknown`를 사용 하 여 합집합의 일부입니다. 및의 참조 횟수를 유지 하기 위해 개체를 집계 하지 않을 때 사용 됩니다 `AddRef` `Release` .|
|[m_pOuterUnknown](#m_pouterunknown)|`m_dwRef`를 사용 하 여 합집합의 일부입니다. 외부 알려지지 않은에 대 한 포인터를 포함 하기 위해 개체를 집계할 때 사용 됩니다.|

## <a name="remarks"></a>설명

`CComObjectRootEx` 집계할 수 없는 개체와 집계 된 개체 모두에 대 한 개체 참조 수 관리를 처리 합니다. 개체를 집계할 수 없는 경우 개체 참조 횟수를 유지 하 고, 개체를 집계할 때 외부 unknown에 대 한 포인터를 보유 합니다. 집계 된 개체의 경우 메서드를 사용 하 여 `CComObjectRootEx` 생성할 내부 개체의 오류를 처리 하 고 내부 인터페이스가 해제 되거나 내부 개체가 삭제 될 때 외부 개체가 삭제 되지 않도록 보호할 수 있습니다.

COM 서버를 구현 하는 클래스는 또는 CComObjectRoot에서 상속 되어야 합니다 `CComObjectRootEx` . [](../../atl/reference/ccomobjectroot-class.md)

클래스 정의에서 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) 매크로를 지정 하는 경우 ATL `CComPolyObject<CYourClass>` 은가 호출 될 때의 인스턴스를 만듭니다 `IClassFactory::CreateInstance` . 생성 하는 동안 알 수 없는 외부 값이 확인 됩니다. NULL 인 경우 `IUnknown` 는 집계할 수 없는 개체에 대해 구현 됩니다. 외부 unknown이 NULL이 아닌 경우는 `IUnknown` 집계 된 개체에 대해 구현 됩니다.

클래스가 DECLARE_POLY_AGGREGATABLE 매크로를 지정 하지 않는 경우에는 ATL에서 집계 된 개체 `CAggComObject<CYourClass>` 에 대 한 인스턴스 또는 집계할 수 없는 개체에 대 한 인스턴스를 만듭니다 `CComObject<CYourClass>` .

를 사용 하는 경우의 장점은 `CComPolyObject` 집계 된 사례와 집계할 수 없는 사례를 `CComAggObject` `CComObject` 처리 하기 위해 모듈에서 및를 모두 사용 하지 않도록 하는 것입니다. 단일 `CComPolyObject` 개체는 두 경우를 모두 처리 합니다. 따라서 모듈에는 vtable의 한 복사본과 함수의 복사본 하나만 있습니다. Vtable이 큰 경우 모듈 크기를 크게 줄일 수 있습니다. 그러나 vtable이 작은 경우를 사용 하면 `CComPolyObject` 집계 된 개체 또는 집계할 수 없는 개체에 대해 최적화 되지 않으므로를 사용 하 여 모듈 크기가 약간 커질 수 있습니다 `CComAggObject` `CComObject` .

개체가 집계 된 경우 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 은 또는에 의해 구현 `CComAggObject` 됩니다 `CComPolyObject` . 이러한 클래스는,, 및에 대 한 호출을, 및에 대 한 `QueryInterface` `AddRef` 호출을 `Release` `CComObjectRootEx` `OuterQueryInterface` `OuterAddRef` `OuterRelease` 외부 unknown으로 전달 합니다. 일반적으로 `CComObjectRootEx::FinalConstruct` 클래스에서를 재정의 하 여 집계 된 개체를 만들고를 재정의 하 여 `CComObjectRootEx::FinalRelease` 집계 된 개체를 해제 합니다.

개체가 집계 되지 않은 경우 `IUnknown` 은 또는에 의해 구현 `CComObject` 됩니다 `CComPolyObject` . 이 경우, 및에 대 한 호출은 `QueryInterface` `AddRef` `Release` `CComObjectRootEx` `InternalQueryInterface` `InternalAddRef` `InternalRelease` 실제 작업을 수행 하기 위해, 및로 위임 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a> CComObjectRootEx:: CComObjectRootEx

생성자는 참조 횟수를 0으로 초기화 합니다.

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a> CComObjectRootEx:: 구문

파생 클래스에서이 메서드를 재정의 하 여 개체에 필요한 초기화를 수행할 수 있습니다.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>반환 값

성공 시 또는 표준 오류 HRESULT 값 중 하나를 반환 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

기본적으로는 `CComObjectRootEx::FinalConstruct` S_OK 반환 합니다.

클래스의 생성자가 아니라에서 초기화를 수행 하는 경우 다음과 같은 이점이 있습니다 `FinalConstruct` .

- 생성자에서 상태 코드를 반환할 수 없지만의 반환 값을 통해 HRESULT를 반환할 수 있습니다 `FinalConstruct` . ATL에서 제공 하는 표준 클래스 팩터리를 사용 하 여 클래스의 개체를 만드는 경우이 반환 값은 자세한 오류 정보를 제공 하는 COM 클라이언트에 다시 전파 됩니다.

- 클래스의 생성자에서 가상 함수 메커니즘을 통해 가상 함수를 호출할 수 없습니다. 클래스의 생성자에서 가상 함수를 호출 하면 상속 계층 구조에서 해당 지점에 정의 된 함수에 대 한 정적 확인 호출이 발생 합니다. 순수 가상 함수를 호출 하면 링커 오류가 발생 합니다.

   클래스는 상속 계층 구조에서 가장 많이 파생 되는 클래스가 아닙니다 .이 클래스는 ATL에서 제공 하는 파생 클래스를 사용 하 여 일부 기능을 제공 합니다. 초기화가 해당 클래스에서 제공 하는 기능을 사용 해야 하는 것이 좋습니다 .이는 클래스의 개체가 다른 개체를 집계 해야 하는 경우에는 분명히 발생 하지만 클래스의 생성자에는 해당 기능에 액세스할 수 있는 방법이 없습니다. 클래스에 대 한 생성 코드는 가장 많이 파생 된 클래스가 완전히 구성 되기 전에 실행 됩니다.

   그러나를 `FinalConstruct` 사용 하면 대부분의 파생 클래스가 완전히 생성 된 직후에 호출 되어 가상 함수를 호출 하 고 ATL에서 제공 하는 참조 계산 구현을 사용할 수 있습니다.

### <a name="example"></a>예제

일반적으로에서 파생 된 클래스의이 메서드 `CComObjectRootEx` 를 재정의 하 여 집계 된 개체를 만듭니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

생성에 실패 하는 경우 오류를 반환할 수 있습니다. 또한 매크로 [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) 를 사용 하 여 외부 개체가 삭제 되지 않도록 보호할 수 있습니다. 생성 하는 동안 내부 집계 개체가 참조 횟수를 증가 시킨 다음 해당 개수를 0으로 감소 시킵니다.

집계를 만드는 일반적인 방법은 다음과 같습니다.

- `IUnknown`클래스 개체에 포인터를 추가 하 고 생성자에서 NULL로 초기화 합니다.

- `FinalConstruct`집계를 만들려면를 재정의 합니다.

- `IUnknown` [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) 매크로에 대 한 매개 변수로 정의한 포인터를 사용 합니다.

- `FinalRelease`포인터를 해제 하려면를 재정의 `IUnknown` 합니다.

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a> CComObjectRootEx:: 버전 릴리스

파생 클래스에서이 메서드를 재정의 하 여 개체에 필요한 정리를 수행할 수 있습니다.

```cpp
void FinalRelease();
```

### <a name="remarks"></a>설명

기본적으로는 `CComObjectRootEx::FinalRelease` 아무 작업도 수행 하지 않습니다.

에서 정리 작업을 수행 `FinalRelease` 하는 것은 개체가를 호출 하는 지점에서 여전히 완전히 구성 되기 때문에 클래스의 소멸자에 코드를 추가 하는 것 보다 좋습니다 `FinalRelease` . 이렇게 하면 가장 많이 파생 된 클래스에서 제공 하는 메서드에 안전 하 게 액세스할 수 있습니다. 이는 삭제 하기 전에 집계 된 개체를 해제 하는 데 특히 중요 합니다.

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a> CComObjectRootEx:: InternalAddRef

집계할 수 없는 개체의 참조 횟수를 1 씩 증가 시킵니다.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>반환 값

진단 및 테스트에 유용할 수 있는 값입니다.

### <a name="remarks"></a>설명

스레드 모델이 다중 스레드 모델인 경우를 `InterlockedIncrement` 사용 하 여 두 개 이상의 스레드가 동시에 참조 횟수를 변경 하지 않도록 합니다.

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a> CComObjectRootEx:: InternalQueryInterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*pThis*<br/>
진행 에 노출 된 인터페이스의 COM 맵을 포함 하는 개체에 대 한 포인터입니다 `QueryInterface` .

*pEntries*<br/>
진행 `_ATL_INTMAP_ENTRY` 사용 가능한 인터페이스의 맵에 액세스 하는 구조체에 대 한 포인터입니다.

*iid*<br/>
진행 요청 되는 인터페이스의 GUID입니다.

*ppvObject*<br/>
제한이 *Iid* 에 지정 된 인터페이스 포인터에 대 한 포인터 이거나, 인터페이스를 찾을 수 없는 경우 NULL입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

`InternalQueryInterface`에서는 COM 맵 테이블의 인터페이스만 처리됩니다. 개체가 집계 된 경우는 `InternalQueryInterface` 알 수 없는 외부에 위임 하지 않습니다. 매크로 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 또는 해당 변형 중 하나를 사용 하 여 COM 맵 테이블에 인터페이스를 입력할 수 있습니다.

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a> CComObjectRootEx:: InternalRelease

집계할 수 없는 개체의 참조 횟수를 1 씩 감소 시킵니다.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>반환 값

디버그가 아닌 빌드와 디버그 빌드에서이 함수는 진단 또는 테스트에 유용할 수 있는 값을 반환 합니다. 반환 되는 정확한 값은 사용 되는 운영 체제와 같은 여러 요소에 따라 달라 지 며, 참조 횟수가 될 수도 있고 그렇지 않을 수도 있습니다.

### <a name="remarks"></a>설명

스레드 모델이 다중 스레드 모델인 경우를 `InterlockedDecrement` 사용 하 여 두 개 이상의 스레드가 동시에 참조 횟수를 변경 하지 않도록 합니다.

## <a name="ccomobjectrootexlock"></a><a name="lock"></a> CComObjectRootEx:: Lock

스레드 모델이 다중 스레드 모델 인 경우이 메서드는 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)함수를 호출 Win32 API 합니다 .이 함수는 스레드가 전용 데이터 멤버를 통해 가져온 임계 영역 개체의 소유권을 가져올 수 있을 때까지 대기 합니다.

```cpp
void Lock();
```

### <a name="remarks"></a>설명

보호 된 코드의 실행이 완료 되 면 스레드가를 호출 `Unlock` 하 여 임계 영역에 대 한 소유권을 해제 해야 합니다.

스레드 모델이 단일 스레드 인 경우이 메서드는 아무 작업도 수행 하지 않습니다.

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a> CComObjectRootEx:: m_dwRef

4 바이트의 메모리에 액세스 하는 공용 구조체의 일부입니다.

```
long m_dwRef;
```

### <a name="remarks"></a>설명

를 사용 `m_pOuterUnknown` 하는 경우 공용 구조체의 일부는 다음과 같습니다.

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

개체가 집계 되지 않으면 및에서 액세스 하는 참조 횟수가 `AddRef` `Release` 에 저장 됩니다 `m_dwRef` . 개체가 집계 된 경우 알 수 없는 외부에 대 한 포인터는 [m_pOuterUnknown](#m_pouterunknown)에 저장 됩니다.

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a> CComObjectRootEx:: m_pOuterUnknown

4 바이트의 메모리에 액세스 하는 공용 구조체의 일부입니다.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>설명

를 사용 `m_dwRef` 하는 경우 공용 구조체의 일부는 다음과 같습니다.

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

개체가 집계 된 경우 알 수 없는 외부에 대 한 포인터는에 저장 됩니다 `m_pOuterUnknown` . 개체가 집계 되지 않으면 및에서 액세스 하는 참조 수가 `AddRef` `Release` [m_dwRef](#m_dwref)에 저장 됩니다.

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a> CComObjectRootEx:: ObjectMain

개체 맵에 나열 된 각 클래스에 대해이 함수는 모듈이 초기화 될 때 한 번, 종료 될 때 호출 됩니다.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>매개 변수

*bStarting*<br/>
제한이 클래스를 초기화 하는 경우 값은 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*Bstarting* 매개 변수의 값은 모듈이 초기화 되거나 종료 되는지 여부를 나타냅니다. 의 기본 구현은 `ObjectMain` 아무 작업도 수행 하지 않지만 클래스에서이 함수를 재정의 하 여 클래스에 할당 하려는 리소스를 초기화 하거나 정리할 수 있습니다. 는 `ObjectMain` 클래스의 인스턴스를 요청 하기 전에 호출 됩니다.

`ObjectMain` 는 DLL의 진입점에서 호출 되므로 진입점 함수에서 수행할 수 있는 작업의 유형은 제한 됩니다. 이러한 제한 사항에 대 한 자세한 내용은 [dll 및 Visual C++ 런타임 라이브러리 동작](../../build/run-time-library-behavior.md) 및 [DllMain](/windows/win32/Dlls/dllmain)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a> CComObjectRootEx:: OuterAddRef

집계에서 알 수 없는 외부의 참조 횟수를 늘립니다.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>반환 값

진단 및 테스트에 유용할 수 있는 값입니다.

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a> CComObjectRootEx:: OuterQueryInterface

요청 된 인터페이스에 대 한 간접 포인터를 검색 합니다.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 요청 되는 인터페이스의 GUID입니다.

*ppvObject*<br/>
제한이 *Iid* 에 지정 된 인터페이스 포인터에 대 한 포인터 이거나, 집계가 인터페이스를 지원 하지 않는 경우 NULL입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a> CComObjectRootEx:: OuterRelease

집계에서 알 수 없는 외부의 참조 횟수를 감소 시킵니다.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>반환 값

디버그가 아닌 빌드에서는 항상 0을 반환 합니다. 디버그 빌드에서는 진단 또는 테스트에 유용할 수 있는 값을 반환 합니다.

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a> CComObjectRootEx:: Unlock

스레드 모델이 다중 스레드 모델 인 경우이 메서드는 전용 데이터 멤버를 통해 가져온 임계 영역 개체의 소유권을 해제 하는 Win32 API 함수 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)를 호출 합니다.

```cpp
void Unlock();
```

### <a name="remarks"></a>설명

소유권을 얻으려면 스레드가를 호출 해야 합니다 `Lock` . 에 대 한 각 호출에는 임계 영역에 대 한 `Lock` `Unlock` 소유권을 해제 하기 위해에 대 한 해당 호출이 필요 합니다.

스레드 모델이 단일 스레드 인 경우이 메서드는 아무 작업도 수행 하지 않습니다.

## <a name="see-also"></a>참고 항목

[CComAggObject 클래스](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 클래스](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 클래스](../../atl/reference/ccompolyobject-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
