---
description: '자세히 알아보기: ScheduleGroup 클래스'
title: ScheduleGroup 클래스
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: ca6678cd8d8c13c5d62b3d98b0a0bb1ab14e29c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188913"
---
# <a name="schedulegroup-class"></a>ScheduleGroup 클래스

일정 그룹에 대한 추상화를 나타냅니다. 일정 그룹은 다른 그룹으로 이동하기 전에 동일한 그룹의 다른 작업을 실행하여 시간적으로 또는 동일한 NUMA 노드 또는 실제 소켓에서 동일한 그룹 내의 여러 항목을 실행하여 공간적으로 서로 가깝게 예약하면 도움이 되는 관련된 작업 집합을 구성합니다.

## <a name="syntax"></a>구문

```cpp
class ScheduleGroup;
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[~ ScheduleGroup 소멸자](#dtor)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ID](#id)|그룹이 속한 스케줄러 내에서 고유한 일정 그룹에 대 한 식별자를 반환 합니다.|
|[참조](#reference)|일정 그룹 참조 횟수를 증가시킵니다.|
|[릴리스](#release)|일정 그룹 참조 횟수를 감소시킵니다.|
|[ScheduleTask](#scheduletask)|일정 그룹 내에서 경량 작업을 예약 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ScheduleGroup`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="id"></a><a name="id"></a> A-id

그룹이 속한 스케줄러 내에서 고유한 일정 그룹에 대 한 식별자를 반환 합니다.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>반환 값

그룹이 속한 스케줄러 내에서 고유한 일정 그룹의 식별자입니다.

## <a name="operator-delete"></a><a name="operator_delete"></a> operator delete

`ScheduleGroup`개체는 모든 외부 참조가 해제 될 때 런타임에서 내부적으로 소멸 됩니다. 개체를 명시적으로 삭제할 수 없습니다.

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>매개 변수

*_PObject*<br/>
삭제할 개체에 대 한 포인터입니다.

## <a name="reference"></a><a name="reference"></a> 참조일

일정 그룹 참조 횟수를 증가시킵니다.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>반환 값

새로 증가 된 참조 수입니다.

### <a name="remarks"></a>설명

이는 일반적으로 컴퍼지션에 대 한 일정 그룹의 수명을 관리 하는 데 사용 됩니다. 일정 그룹의 참조 횟수가 0이 되 면 해당 일정 그룹은 런타임에 의해 삭제 됩니다. [Currentscheduler:: CreateScheduleGroup](currentscheduler-class.md#createschedulegroup) 메서드를 사용 하 여 만든 일정 그룹이 나 [Scheduler:: CreateScheduleGroup](scheduler-class.md#createschedulegroup) 메서드는 참조 횟수를 사용 하 여 시작 합니다.

## <a name="release"></a><a name="release"></a> 릴리스

일정 그룹 참조 횟수를 감소시킵니다.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>반환 값

새로 감소 한 참조 수입니다.

### <a name="remarks"></a>설명

이는 일반적으로 컴퍼지션에 대 한 일정 그룹의 수명을 관리 하는 데 사용 됩니다. 일정 그룹의 참조 횟수가 0이 되 면 해당 일정 그룹은 런타임에 의해 삭제 됩니다. `Release` 메서드를 사용하여 배치된 추가 참조와 생성 참조 횟수를 제거하기 위해 `Reference` 메서드를 특정 횟수 만큼 호출한 후에는 더 이상 일정 그룹을 이용할 수 없습니다. 이렇게 하면 정의 되지 않은 동작이 발생 합니다.

일정 그룹은 특정 스케줄러 인스턴스와 연결 됩니다. 스케줄러에 대한 모든 참조는 스케줄러에서 소멸될 수 있기 때문에 스케줄러에 대한 모든 참조가 해제되기 전에 일정 그룹에 대한 모든 참조가 해제되었는지 확인해야 합니다. 그러지 않으면 정의 되지 않은 동작이 발생 합니다.

## <a name="schedulegroup"></a><a name="dtor"></a> ~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask

일정 그룹 내에서 경량 작업을 예약 합니다.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>매개 변수

*_Proc*<br/>
경량 작업 본문을 수행 하기 위해 실행 하는 함수에 대 한 포인터입니다.

*_Data*<br/>
작업 본문에 매개 변수로 전달 될 데이터에 대 한 void 포인터입니다.

### <a name="remarks"></a>설명

메서드를 호출 하면 `ScheduleTask` 작업이 실행 된 후 적절 한 시간에 런타임에 의해 제거 되는 일정 그룹에 참조 수가 암시적으로 배치 됩니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[CurrentScheduler 클래스](currentscheduler-class.md)<br/>
[Scheduler 클래스](scheduler-class.md)<br/>
[작업 Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
