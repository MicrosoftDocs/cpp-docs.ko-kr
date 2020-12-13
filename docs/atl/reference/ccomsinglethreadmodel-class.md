---
description: '자세히 알아보기: CComSingleThreadModel 클래스'
title: CComSingleThreadModel 클래스
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 42f1111590dd8e03a541ecc7a71b461e34a08f0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142209"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 클래스

이 클래스는 변수의 값을 증가 및 감소 시키는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComSingleThreadModel
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)클래스를 참조 합니다.|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|References 클래스 `CComFakeCriticalSection` 입니다.|
|[CComSingleThreadModel:: ThreadModelNoCS](#threadmodelnocs)|참조 `CComSingleThreadModel` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|지정 된 변수의 값을 감소 시킵니다. 이 구현은 스레드로부터 안전 하지 않습니다.|
|[CComSingleThreadModel:: 증가값](#increment)|지정 된 변수의 값을 증가 시킵니다. 이 구현은 스레드로부터 안전 하지 않습니다.|

## <a name="remarks"></a>설명

`CComSingleThreadModel` 변수의 값을 증가 및 감소 시키는 메서드를 제공 합니다. [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)와 달리 이러한 메서드는 스레드로부터 안전 하지 않습니다.

일반적으로 `CComSingleThreadModel` **`typedef`** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) 또는 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)의 두 이름 중 하나를 사용 합니다. 각에서 참조 하는 클래스는 **`typedef`** 다음 표에 나와 있는 것 처럼 사용 된 스레딩 모델에 따라 달라 집니다.

|형식 정의|단일 스레딩 모델|아파트 스레딩 모델|자유 스레딩 모델|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ; M = `CComMultiThreadModel`

`CComSingleThreadModel` 자체는 세 개의 **`typedef`** 이름을 정의 합니다. `ThreadModelNoCS` 참조 `CComSingleThreadModel` . `AutoCriticalSection` 및 `CriticalSection` 참조 클래스 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)는 임계 영역에 대 한 소유권을 가져오고 해제 하는 것과 관련 된 빈 메서드를 제공 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a> CComSingleThreadModel::AutoCriticalSection

를 사용 하 `CComSingleThreadModel` 는 경우 **`typedef`** 이름이 `AutoCriticalSection` [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)클래스를 참조 합니다.

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>설명

는 `CComFakeCriticalSection` 임계 영역을 제공 하지 않으므로 해당 메서드는 아무 작업도 수행 하지 않습니다.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) 에는에 대 한 정의가 포함 되어 `AutoCriticalSection` 있습니다. 다음 표에서는에서 참조 하는 스레딩 모델 클래스와 임계 영역 클래스 간의 관계를 보여 줍니다 `AutoCriticalSection` .

|클래스 정의|참조 된 클래스|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

뿐만 아니라 `AutoCriticalSection` **`typedef`** [CriticalSection](#criticalsection)이름도 사용할 수 있습니다. `AutoCriticalSection`CRT 시작 코드를 제거 하려는 경우에는 전역 개체 또는 정적 클래스 멤버에를 지정 하면 안 됩니다.

### <a name="example"></a>예제

[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)를 참조 하세요.

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a> CComSingleThreadModel:: CriticalSection

를 사용 하 `CComSingleThreadModel` 는 경우 **`typedef`** 이름이 `CriticalSection` [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)클래스를 참조 합니다.

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>설명

는 `CComFakeCriticalSection` 임계 영역을 제공 하지 않으므로 해당 메서드는 아무 작업도 수행 하지 않습니다.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) 에는에 대 한 정의가 포함 되어 `CriticalSection` 있습니다. 다음 표에서는에서 참조 하는 스레딩 모델 클래스와 임계 영역 클래스 간의 관계를 보여 줍니다 `CriticalSection` .

|클래스 정의|참조 된 클래스|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

뿐만 아니라 `CriticalSection` **`typedef`** [AutoCriticalSection](#autocriticalsection)이름도 사용할 수 있습니다. `AutoCriticalSection`CRT 시작 코드를 제거 하려는 경우에는 전역 개체 또는 정적 클래스 멤버에를 지정 하면 안 됩니다.

### <a name="example"></a>예제

[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)를 참조 하세요.

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a> CComSingleThreadModel::D ecrement

이 정적 함수는 *p* 가 가리키는 변수의 값을 감소 시킵니다.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 감소 시킬 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

감소의 결과입니다.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a> CComSingleThreadModel:: 증가값

이 정적 함수는 *p* 가 가리키는 변수의 값을 증가 시킵니다.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 증가 시킬 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

증가값의 결과입니다.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a> CComSingleThreadModel:: ThreadModelNoCS

를 사용 하 `CComSingleThreadModel` 는 경우 **`typedef`** 이름은를 `ThreadModelNoCS` 참조 하기만 `CComSingleThreadModel` 합니다.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>설명

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 및 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) 에는에 대 한 정의가 포함 되어 `ThreadModelNoCS` 있습니다. 다음 표에서는에서 참조 하는 클래스와 스레딩 모델 클래스 간의 관계를 보여 줍니다 `ThreadModelNoCS` .

|클래스 정의|참조 된 클래스|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>예제

[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
