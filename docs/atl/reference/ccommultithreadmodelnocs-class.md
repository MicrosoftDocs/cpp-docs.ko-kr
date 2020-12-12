---
description: '자세히 알아보기: CComMultiThreadModelNoCS 클래스'
title: CComMultiThreadModelNoCS 클래스
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 8b26c59564f9a7869bb3429ee31284925815e6ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152011"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 클래스

`CComMultiThreadModelNoCS` 임계 영역 잠금 또는 잠금 해제 기능 없이 변수 값을 증가 및 감소 시키는 스레드로부터 안전한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)클래스를 참조 합니다.|
|[CComMultiThreadModelNoCS:: CriticalSection](#criticalsection)|References 클래스 `CComFakeCriticalSection` 입니다.|
|[CComMultiThreadModelNoCS:: ThreadModelNoCS](#threadmodelnocs)|References 클래스 `CComMultiThreadModelNoCS` 입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComMultiThreadModelNoCS::D ecrement](#decrement)|정적인 스레드로부터 안전한 방식으로 지정 된 변수의 값을 감소 시킵니다.|
|[CComMultiThreadModelNoCS:: 증가값](#increment)|정적인 스레드로부터 안전한 방식으로 지정 된 변수의 값을 증가 시킵니다.|

## <a name="remarks"></a>설명

`CComMultiThreadModelNoCS` 는 변수를 증가 및 감소 시킬 수 있는 스레드로부터 안전한 메서드를 제공 한다는 점에서 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 와 비슷합니다. 그러나를 통해 임계 영역 클래스를 참조 하는 경우 `CComMultiThreadModelNoCS` 및와 같은 `Lock` 메서드 `Unlock` 는 아무 작업도 수행 하지 않습니다.

일반적으로 `CComMultiThreadModelNoCS` 는 이름을 통해를 사용 `ThreadModelNoCS` **`typedef`** 합니다. 이 **`typedef`** 는 `CComMultiThreadModelNoCS` , `CComMultiThreadModel` 및 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)에 정의 되어 있습니다.

> [!NOTE]
> **`typedef`** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) 및 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) 전역 이름은 참조 하지 않습니다 `CComMultiThreadModelNoCS` .

외에 `ThreadModelNoCS` 도 `CComMultiThreadModelNoCS` 및을 `AutoCriticalSection` 정의 `CriticalSection` 합니다. 이러한 후자의 두 **`typedef`** 이름에는 임계 영역을 가져오고 해제 하는 것과 관련 된 빈 메서드를 제공 하는 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)가 참조 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a> CComMultiThreadModelNoCS::AutoCriticalSection

를 사용 하 `CComMultiThreadModelNoCS` 는 경우 **`typedef`** 이름이 `AutoCriticalSection` [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)클래스를 참조 합니다.

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>설명

는 `CComFakeCriticalSection` 임계 영역을 제공 하지 않으므로 해당 메서드는 아무 작업도 수행 하지 않습니다.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 에는에 대 한 정의도 포함 되어 `AutoCriticalSection` 있습니다. 다음 표에서는에서 참조 하는 스레딩 모델 클래스와 임계 영역 클래스 간의 관계를 보여 줍니다 `AutoCriticalSection` .

|클래스 정의|참조 된 클래스|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

뿐만 아니라 `AutoCriticalSection` **`typedef`** [CriticalSection](#criticalsection)이름도 사용할 수 있습니다. `AutoCriticalSection`CRT 시작 코드를 제거 하려는 경우에는 전역 개체 또는 정적 클래스 멤버에를 지정 하면 안 됩니다.

### <a name="example"></a>예제

[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)를 참조 하세요.

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a> CComMultiThreadModelNoCS:: CriticalSection

를 사용 하 `CComMultiThreadModelNoCS` 는 경우 **`typedef`** 이름이 `CriticalSection` [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)클래스를 참조 합니다.

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>설명

는 `CComFakeCriticalSection` 임계 영역을 제공 하지 않으므로 해당 메서드는 아무 작업도 수행 하지 않습니다.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 에는에 대 한 정의도 포함 되어 `CriticalSection` 있습니다. 다음 표에서는에서 참조 하는 스레딩 모델 클래스와 임계 영역 클래스 간의 관계를 보여 줍니다 `CriticalSection` .

|클래스 정의|참조 된 클래스|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

외에도 `CriticalSection` 이름을 사용할 수 있습니다 **`typedef`** `AutoCriticalSection` . `AutoCriticalSection`CRT 시작 코드를 제거 하려는 경우에는 전역 개체 또는 정적 클래스 멤버에를 지정 하면 안 됩니다.

### <a name="example"></a>예제

[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)를 참조 하세요.

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a> CComMultiThreadModelNoCS::D ecrement

이 정적 함수는 *p* 로 가리키는 변수의 값을 감소 시키는 Win32 함수 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)를 호출 합니다.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 감소 시킬 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

감소 결과가 0 이면는 `Decrement` 0을 반환 합니다. 감소 결과 값이 0이 아니면 반환 값도 0이 아니라 감소의 결과와 다를 수 있습니다.

### <a name="remarks"></a>설명

**InterlockedDecrement** 은이 변수를 사용 하 여 두 개 이상의 스레드가 동시에 수행 되지 않도록 방지 합니다.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a> CComMultiThreadModelNoCS:: 증가값

이 정적 함수는 *p* 로 가리키는 변수의 값을 증가 시키는 Win32 함수 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)를 호출 합니다.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 증가 시킬 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

증가값의 결과가 0 이면 **increment** 는 0을 반환 합니다. 증가값의 결과가 0이 아닌 경우 반환 값도 0이 아니라 증가값의 결과와 다를 수 있습니다.

### <a name="remarks"></a>설명

**InterlockedIncrement** 은이 변수를 사용 하 여 두 개 이상의 스레드가 동시에 수행 되지 않도록 방지 합니다.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a> CComMultiThreadModelNoCS:: ThreadModelNoCS

를 사용 하 `CComMultiThreadModelNoCS` 는 경우 **`typedef`** 이름은를 `ThreadModelNoCS` 참조 하기만 `CComMultiThreadModelNoCS` 합니다.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>설명

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 에는에 대 한 정의도 포함 되어 `ThreadModelNoCS` 있습니다. 다음 표에서는에서 참조 하는 클래스와 스레딩 모델 클래스 간의 관계를 보여 줍니다 `ThreadModelNoCS` .

|클래스 정의|참조 된 클래스|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

에서의 정의는 및에 대 `ThreadModelNoCS` `CComMultiThreadModelNoCS` 한 대칭을 제공 합니다 `CComMultiThreadModel` `CComSingleThreadModel` . 예를 들어의 샘플 코드는 다음을 선언 했다고 가정 합니다 `CComMultiThreadModel::AutoCriticalSection` **`typedef`** .

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

에 대해 지정 된 클래스 `ThreadModel` (예:)에 관계 없이 `CComMultiThreadModelNoCS` 는 `_ThreadModel` 그에 따라 확인 됩니다.

### <a name="example"></a>예제

[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
