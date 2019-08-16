---
title: COM 인터페이스 항목 매크로
ms.date: 03/28/2017
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: 1e1674bad1164e640939d430a860beac7a6e4208
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496719"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY 매크로

이러한 매크로는에서 `QueryInterface`액세스할 수 있도록 COM 맵에 개체의 인터페이스를 입력 합니다. COM 맵의 항목 순서는 중 `QueryInterface`에 일치 하는 IID에 대해 인터페이스를 검사 하는 순서입니다.

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|인터페이스를 COM 인터페이스 맵에 입력 합니다.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|이 매크로를 사용 하 여 두 상속 분기를 구분할 수 있습니다.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|이 매크로를 사용 하 여 COM 맵에 인터페이스를 입력 하 고 해당 IID를 지정 합니다.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|다른 IID를 지정할 수 있다는 점을 제외 하 고 [COM_INTERFACE_ENTRY2](#com_interface_entry2)와 동일 합니다.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|*Iid* 로 식별 된 인터페이스가에 대해 `COM_INTERFACE_ENTRY_AGGREGATE` 쿼리 되 면에 전달 `punk`됩니다.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|IID를 쿼리하면 쿼리를 *punk*로 전달 하는 것을 제외 하 고 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)와 동일 합니다.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|*Punk* 가 NULL 인 경우를 제외 하 고 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)와 동일 합니다.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)와 동일 합니다. 단, IID를 쿼리하여 쿼리를 *punk*에 전달 하 고 *punk* 가 NULL 인 경우 *clsid*가 설명 하는 집계를 자동으로 만듭니다.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|지정 된 인터페이스를 쿼리할 때 프로그램에서 [Debugbreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 를 호출 하도록 합니다.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|모든 인스턴스에 대 한 인터페이스 관련 데이터를 저장 합니다.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|는 분리 인터페이스를 노출 합니다.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|처리가 COM 맵의이 항목에 도달할 때 기본 클래스의 COM 맵을 처리 합니다.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|ATL의 `QueryInterface` 논리에 후크 하기 위한 일반적인 메커니즘입니다.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|IID를 쿼리하면 *FUNC*호출이 발생 한다는 점을 제외 하 고 [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)와 동일 합니다.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|E_NOINTERFACE를 반환 하 고 지정 된 인터페이스를 쿼리할 때 COM 맵 처리를 종료 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY

인터페이스를 COM 인터페이스 맵에 입력 합니다.

### <a name="syntax"></a>구문

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 클래스 개체가 직접 파생 되는 인터페이스의 이름입니다.

### <a name="remarks"></a>설명

일반적으로 가장 자주 사용 하는 항목 유형입니다.

### <a name="example"></a>예제

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더:**

##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2

이 매크로를 사용 하 여 두 상속 분기를 구분할 수 있습니다.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 개체에서 노출 하려는 인터페이스의 이름입니다.

*x2*<br/>
진행 *X* 가 노출 되는 상속 분기의 이름입니다.

### <a name="remarks"></a>설명

예를 들어 두 개의 이중 인터페이스에서 클래스 개체를 파생 하는 경우 두 `IDispatch` 인터페이스 중 하나 `IDispatch` 에서 가져올 수 있으므로 COM_INTERFACE_ENTRY2를 사용 하 여 노출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID

이 매크로를 사용 하 여 COM 맵에 인터페이스를 입력 하 고 해당 IID를 지정 합니다.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 노출 된 인터페이스의 GUID입니다.

*x*<br/>
진행 Vtable이 *iid*에 의해 식별 되는 인터페이스로 노출 되는 클래스의 이름입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID

다른 IID를 지정할 수 있다는 점을 제외 하 고 [COM_INTERFACE_ENTRY2](#com_interface_entry2)와 동일 합니다.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 인터페이스에 대해 지정 하는 GUID입니다.

*x*<br/>
진행 클래스 개체에서 직접 파생 되는 인터페이스의 이름입니다.

*x2*<br/>
진행 클래스 개체에서 직접 파생 되는 두 번째 인터페이스의 이름입니다.

##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE

*Iid* 에 의해 식별 된 인터페이스가에 대해 쿼리 되 면 COM_INTERFACE_ENTRY_AGGREGATE가 *punk*에 전달 됩니다.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 에 대해 쿼리 된 인터페이스의 GUID입니다.

*punk*<br/>
진행 `IUnknown` 포인터의 이름입니다.

### <a name="remarks"></a>설명

*Punk* 매개 변수는 집계의 내부 unknown을 가리키거나 NULL 인 것으로 가정 합니다 .이 경우 항목은 무시 됩니다. 일반적으로의 `FinalConstruct`집계 `CoCreate` 를 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND

IID를 쿼리하면 쿼리를 *punk*로 전달 하는 것을 제외 하 고 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)와 동일 합니다.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>매개 변수

*punk*<br/>
진행 `IUnknown` 포인터의 이름입니다.

### <a name="remarks"></a>설명

인터페이스 쿼리가 실패 하면 COM 맵 처리가 계속 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE

*Punk* 가 NULL 인 경우를 제외 하 고 [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)와 동일 합니다.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 에 대해 쿼리 된 인터페이스의 GUID입니다.

*punk*<br/>
진행 `IUnknown` 포인터의 이름입니다. 은 COM 맵을 포함 하는 클래스의 멤버 여야 합니다.

*clsid*<br/>
진행 *Punk* 가 NULL 인 경우 생성 되는 집계의 식별자입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)와 동일 합니다. 단, IID를 쿼리하여 쿼리를 *punk*에 전달 하 고 *punk* 가 NULL 인 경우 *clsid*가 설명 하는 집계를 자동으로 만듭니다.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>매개 변수

*punk*<br/>
진행 `IUnknown` 포인터의 이름입니다. 은 COM 맵을 포함 하는 클래스의 멤버 여야 합니다.

*clsid*<br/>
진행 *Punk* 가 NULL 인 경우 생성 되는 집계의 식별자입니다.

### <a name="remarks"></a>설명

인터페이스 쿼리가 실패 하면 COM 맵 처리가 계속 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK

지정 된 인터페이스를 쿼리할 때 프로그램에서 [Debugbreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 를 호출 하도록 합니다.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 인터페이스 식별자를 생성 하는 데 사용 되는 텍스트입니다.

### <a name="remarks"></a>설명

인터페이스 IID는에 *x* 를 `IID_`추가 하 여 생성 됩니다. 예를 들어 *x* 가 `IPersistStorage`이면 IID `IID_IPersistStorage`는이 됩니다.

##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

모든 인스턴스에 대 한 인터페이스 관련 데이터를 저장 합니다.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 분리 된 인터페이스의 GUID입니다.

*x*<br/>
진행 인터페이스를 구현 하는 클래스의 이름입니다.

*punk*<br/>
진행 `IUnknown` 포인터의 이름입니다. 은 COM 맵을 포함 하는 클래스의 멤버 여야 합니다. 클래스 개체의 생성자에서 NULL로 초기화 되어야 합니다.

### <a name="remarks"></a>설명

인터페이스를 사용 하지 않으면 개체의 전체 인스턴스 크기가 줄어듭니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF

는 분리 인터페이스를 노출 합니다.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 분리 된 인터페이스의 GUID입니다.

*x*<br/>
진행 인터페이스를 구현 하는 클래스의 이름입니다.

### <a name="remarks"></a>설명

떼어내기 인터페이스는 해당 인터페이스가 나타내는 인터페이스가 쿼리 될 때마다 인스턴스화되는 별도의 개체로 구현 됩니다. 일반적으로 인터페이스가 거의 사용 되지 않는 경우 기본 개체의 모든 인스턴스에 vtable 포인터를 저장 하므로 인터페이스를 분리 하 여 빌드합니다. 참조 횟수가 0이 되 면 분리가 삭제 됩니다. 분리를 구현 하는 클래스는에서 `CComTearOffObjectBase` 파생 되 고 고유한 COM 맵을 포함 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN

처리가 COM 맵의이 항목에 도달할 때 기본 클래스의 COM 맵을 처리 합니다.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>매개 변수

*classname*<br/>
진행 현재 개체의 기본 클래스입니다.

### <a name="remarks"></a>설명

예를 들어, 다음 코드에서입니다.

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

COM 맵의 첫 번째 항목은 COM 맵을 포함 하는 개체의 인터페이스 여야 합니다. 따라서 COM_INTERFACE_ENTRY_CHAIN를 사용 하 여 com 맵 항목을 시작할 수 없습니다. 그러면 **COM_INTERFACE_ENTRY_CHAIN (** `COtherObject` **)** 이 개체의 com 맵에 표시 되는 지점에서 다른 개체의 com 맵을 검색 합니다. 다른 개체의 com 맵을 먼저 검색 하려는 경우에 대 한 `IUnknown` 인터페이스 항목을 com 맵에 추가 하 고 다른 개체의 com 맵을 연결 합니다. 예:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC

ATL의 `QueryInterface` 논리에 후크 하기 위한 일반적인 메커니즘입니다.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 노출 된 인터페이스의 GUID입니다.

*dw*<br/>
진행 *Func*로 전달 되는 매개 변수입니다.

*func*<br/>
진행 *Iid*를 반환 하는 함수 포인터입니다.

### <a name="remarks"></a>설명

*Iid* 가에 대해 쿼리 된 인터페이스의 iid와 일치 하는 경우 *func* 로 지정 된 함수가 호출 됩니다. 함수 선언은 다음과 같아야 합니다.

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

함수가 호출 `pv` 되 면는 클래스 개체를 가리킵니다. *Riid* 매개 변수는 쿼리 되는 인터페이스를 참조 하 `ppv` 고,는 함수에서 인터페이스에 포인터를 저장 해야 하는 위치에 대 한 포인터이 고, *dw* 는 항목에 지정 된 매개 변수입니다. 인터페이스를 반환 하지 \* 않도록 선택 하는 경우 함수는 NULL로 설정 `ppv` 되 고 E_NOINTERFACE 또는 S_FALSE를 반환 해야 합니다. E_NOINTERFACE를 사용 하면 COM 맵 처리가 종료 됩니다. S_FALSE를 사용 하면 인터페이스 포인터가 반환 되지 않은 경우에도 COM 맵 처리가 계속 됩니다. 함수가 인터페이스 포인터를 반환 하는 경우 S_OK를 반환 해야 합니다.

##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND

IID를 쿼리하면 *FUNC*호출이 발생 한다는 점을 제외 하 고 [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)와 동일 합니다.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>매개 변수

*dw*<br/>
진행 *Func*로 전달 되는 매개 변수입니다.

*func*<br/>
진행 COM 맵의이 항목이 처리 될 때 호출 되는 함수입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 COM 맵에서 처리가 계속 됩니다. 함수가 인터페이스 포인터를 반환 하는 경우 S_OK를 반환 해야 합니다.

##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE

E_NOINTERFACE를 반환 하 고 지정 된 인터페이스를 쿼리할 때 COM 맵 처리를 종료 합니다.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 인터페이스 식별자를 생성 하는 데 사용 되는 텍스트입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 인터페이스가 특정 사례에서 사용 되지 않도록 할 수 있습니다. 예를 들어, COM_INTERFACE_ENTRY_AGGREGATE_BLIND 바로 앞에이 매크로를 추가 하 여 인터페이스에 대 한 쿼리가 집계의 내부 unknown에 전달 되지 않도록 할 수 있습니다.

인터페이스 IID는에 *x* 를 `IID_`추가 하 여 생성 됩니다. 예를 들어 *x* 가 `IPersistStorage`이면 IID `IID_IPersistStorage`는이 됩니다.
