---
description: '자세히 알아보기: SchedulerPolicy 클래스'
title: SchedulerPolicy 클래스
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: 2bb4c8961f46f077c203d1a49fb352171ad3f318
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188705"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy 클래스

`SchedulerPolicy` 클래스에는 정책 요소마다 하나씩, 스케줄러 인스턴스의 동작을 제어하는 키/값 쌍 집합을 포함합니다.

## <a name="syntax"></a>구문

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|오버로드됨. 새 스케줄러 정책을 생성 하 고 동시성 런타임 스케줄러 및 리소스 관리자에서 지 원하는 [정책 키](concurrency-namespace-enums.md) 에 대 한 값으로 채웁니다.|
|[~ SchedulerPolicy 소멸자](#dtor)|스케줄러 정책을 소멸 시킵니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|매개 변수로 제공 된 정책 키의 값을 검색 합니다 `key` .|
|[SetConcurrencyLimits](#setconcurrencylimits)|`MinConcurrency`개체에 대 한 및 정책을 동시에 설정 합니다 `MaxConcurrency` `SchedulerPolicy` .|
|[SetPolicyValue](#setpolicyvalue)|매개 변수로 제공 된 정책 키의 값을 설정 `key` 하 고 이전 값을 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 =](#operator_eq)|다른 스케줄러 정책의 스케줄러 정책을 할당 합니다.|

## <a name="remarks"></a>설명

클래스를 사용 하 여 제어할 수 있는 정책에 대 한 자세한 내용은 `SchedulerPolicy` [Policyelementkey](concurrency-namespace-enums.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SchedulerPolicy`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h, concrtrm. h

**네임 스페이스:** 동시성

## <a name="getpolicyvalue"></a><a name="getpolicyvalue"></a> GetPolicyValue

매개 변수로 제공 된 정책 키의 값을 검색 합니다 `key` .

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>매개 변수

*key*<br/>
값을 검색할 정책 키입니다.

### <a name="return-value"></a>반환 값

매개 변수로 지정 된 키 `key` 가 지원 되 면 키에 대 한 정책 값이로 캐스팅 **`unsigned int`** 됩니다.

### <a name="remarks"></a>설명

이 메서드는 잘못 된 정책 키에 대 한 [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) 를 throw 합니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

다른 스케줄러 정책의 스케줄러 정책을 할당 합니다.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>매개 변수

*_RhsPolicy*<br/>
이 정책에 할당할 정책입니다.

### <a name="return-value"></a>반환 값

스케줄러 정책에 대 한 참조입니다.

### <a name="remarks"></a>설명

대부분의 경우 새로운 스케줄러 정책을 정의하는 가장 편리한 방법은 기존 정책을 복사한 후 `SetPolicyValue` 또는 `SetConcurrencyLimits` 메서드를 사용하여 수정하는 것입니다.

## <a name="schedulerpolicy"></a><a name="ctor"></a> SchedulerPolicy

새 스케줄러 정책을 생성 하 고 동시성 런타임 스케줄러 및 리소스 관리자에서 지 원하는 [정책 키](concurrency-namespace-enums.md) 에 대 한 값으로 채웁니다.

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>매개 변수

*_PolicyKeyCount*<br/>
매개 변수 다음에 오는 키/값 쌍의 수입니다 `_PolicyKeyCount` .

*_SrcPolicy*<br/>
복사할 원본 정책입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 모든 정책이 기본값으로 초기화 되는 새 스케줄러 정책을 만듭니다.

두 번째 생성자는 초기화의 명명 된 매개 변수 스타일을 사용 하는 새 스케줄러 정책을 만듭니다. 매개 변수 다음에 오는 값 `_PolicyKeyCount` 은 키/값 쌍으로 제공 됩니다. 이 생성자에 지정 되지 않은 모든 정책 키의 기본값은입니다. 이 생성자는 [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) 또는 [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)예외를 throw 할 수 있습니다.

세 번째 생성자는 복사 생성자입니다. 대부분의 경우 새로운 스케줄러 정책을 정의하는 가장 편리한 방법은 기존 정책을 복사한 후 `SetPolicyValue` 또는 `SetConcurrencyLimits` 메서드를 사용하여 수정하는 것입니다.

## <a name="schedulerpolicy"></a><a name="dtor"></a> ~ SchedulerPolicy

스케줄러 정책을 소멸 시킵니다.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a><a name="setconcurrencylimits"></a> SetConcurrencyLimits

`MinConcurrency`개체에 대 한 및 정책을 동시에 설정 합니다 `MaxConcurrency` `SchedulerPolicy` .

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>매개 변수

*_MinConcurrency*<br/>
정책 키에 대 한 값 `MinConcurrency` 입니다.

*_MaxConcurrency*<br/>
정책 키에 대 한 값 `MaxConcurrency` 입니다.

### <a name="remarks"></a>설명

정책에 지정 된 값이 정책에 지정 된 값 보다 크면 메서드는 [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) 을 throw 합니다 `MinConcurrency` `MaxConcurrency` .

메서드는 다른 잘못 된 값에 대해 [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) 을 throw 할 수도 있습니다.

## <a name="setpolicyvalue"></a><a name="setpolicyvalue"></a> SetPolicyValue

매개 변수로 제공 된 정책 키의 값을 설정 `key` 하 고 이전 값을 반환 합니다.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
값을 설정할 정책 키입니다.

*value*<br/>
정책 키를 설정할 값입니다.

### <a name="return-value"></a>반환 값

매개 변수로 지정 된 키 `key` 가 지원 되는 경우 키에 대 한 이전 정책 값은로 캐스팅 **`unsigned int`** 됩니다.

### <a name="remarks"></a>설명

메서드는 값이 메서드에 의해 설정 될 수 없는 잘못 된 정책 키 또는 정책 키에 대 한 [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) 를 throw 합니다 `SetPolicyValue` .

메서드는 매개 변수로 지정 된 키에 지원 되지 않는 값에 대 한 [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) 를 throw `key` 합니다.

이 메서드는 또는 정책을 설정할 수 없습니다 `MinConcurrency` `MaxConcurrency` . 이러한 값을 설정 하려면 [SetConcurrencyLimits](#setconcurrencylimits) 메서드를 사용 합니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler 클래스](currentscheduler-class.md)<br/>
[Scheduler 클래스](scheduler-class.md)<br/>
[작업 Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
