---
description: Task_group 클래스에 대해 자세히 알아보세요.
title: task_group 클래스
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 8ac3fac0e1feadc2e6c609ee6a0c2946f5061bd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188243"
---
# <a name="task_group-class"></a>task_group 클래스

`task_group` 클래스는 대기하거나 취소할 수 있는 병렬 작업 컬렉션을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class task_group;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[task_group](#ctor)|오버로드됨. 새 `task_group` 개체를 생성합니다.|
|[~ task_group 소멸자](#dtor)|`task_group` 개체를 제거합니다. `wait` `run_and_wait` 소멸자가 예외로 인해 스택 해제의 결과로 실행 되는 경우가 아니면 소멸자를 실행 하기 전에 개체에 대해 또는 메서드를 호출 해야 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[cancel](#cancel)|이 작업 그룹을 기반으로 하는 작업의 하위 트리를 취소 하려고 하는 것이 가장 좋습니다. 작업 그룹에 대해 예약 된 모든 작업은 가능 하면 전이적으로 취소 됩니다.|
|[is_canceling](#is_canceling)|작업 그룹이 현재 취소를 진행 중인지 여부를 호출자에 게 알립니다. 이는 메서드가 개체에 대해 호출 되었음을 나타내는 것은 아닙니다. 이러한 경우에는 `cancel` `task_group` 이 메서드가 반환 **`true`** 됩니다. `task_group`개체가 인라인으로 실행 중이 고 작업 트리에서 작업 그룹이 더 이상 취소 된 경우에 발생할 수 있습니다. 런타임에서 취소가이 개체를 통과 하는 시간을 미리 확인할 수 있는 경우에 `task_group` **`true`** 도이 반환 됩니다.|
|[실행할지](#run)|오버로드됨. 개체에 대 한 작업을 예약 `task_group` 합니다. `task_handle`개체가에 대 한 매개 변수로 전달 되는 경우 `run` 호출자는 개체의 수명을 관리 하는 일을 담당 합니다 `task_handle` . 함수 개체에 대 한 참조를 매개 변수로 사용 하는 메서드 버전에는 개체에 대 한 참조를 사용 하는 버전을 사용 하는 것 보다 성능이 떨어질 수 있는 런타임 내의 힙 할당이 포함 됩니다 `task_handle` . `_Placement` 매개 변수를 사용하는 버전은 이 매개 변수로 지정된 위치에서 작업이 실행되도록 합니다.|
|[run_and_wait](#run_and_wait)|오버로드됨. `task_group`전체 취소 지원에 대 한 개체의 지원을 사용 하 여 호출 컨텍스트에서 인라인으로 실행할 작업을 예약 합니다. 그러면 함수는 개체에 대 한 모든 작업이 `task_group` 완료 되거나 취소 될 때까지 대기 합니다. `task_handle`개체가에 대 한 매개 변수로 전달 되는 경우 `run_and_wait` 호출자는 개체의 수명을 관리 하는 일을 담당 합니다 `task_handle` .|
|[대기한](#wait)|개체에 대 한 모든 작업이 `task_group` 완료 되거나 취소 될 때까지 대기 합니다.|

## <a name="remarks"></a>설명

과도 하 게 제한 된 클래스와 달리 `structured_task_group` `task_group` 클래스는 훨씬 더 일반적인 구문입니다. [Structured_task_group](structured-task-group-class.md)에서 설명 하는 제한 사항이 없습니다. `task_group` 개체는 스레드 간에 안전 하 게 사용 되 고 자유 형식으로 활용 될 수 있습니다. 구문의 단점은 작업을 `task_group` 수행 하지 않을 수 있다는 것입니다. 작업을 수행 하는 작업의 경우에는이 작업을 수행할 수 없습니다 `structured_task_group` .

자세한 내용은 [작업 병렬 처리](../task-parallelism-concurrency-runtime.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`task_group`

## <a name="requirements"></a>요구 사항

**헤더:** ppl. h

**네임 스페이스:** 동시성

## <a name="cancel"></a><a name="cancel"></a> 취소

이 작업 그룹을 기반으로 하는 작업의 하위 트리를 취소 하려고 하는 것이 가장 좋습니다. 작업 그룹에 대해 예약 된 모든 작업은 가능 하면 전이적으로 취소 됩니다.

```cpp
void cancel();
```

### <a name="remarks"></a>설명

자세한 내용은 [취소](../cancellation-in-the-ppl.md)를 참조 하세요.

## <a name="is_canceling"></a><a name="is_canceling"></a> is_canceling

작업 그룹이 현재 취소를 진행 중인지 여부를 호출자에 게 알립니다. 이는 메서드가 개체에 대해 호출 되었음을 나타내는 것은 아닙니다. 이러한 경우에는 `cancel` `task_group` 이 메서드가 반환 **`true`** 됩니다. `task_group`개체가 인라인으로 실행 중이 고 작업 트리에서 작업 그룹이 더 이상 취소 된 경우에 발생할 수 있습니다. 런타임에서 취소가이 개체를 통과 하는 시간을 미리 확인할 수 있는 경우에 `task_group` **`true`** 도이 반환 됩니다.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>반환 값

`task_group`개체가 취소를 진행 하 고 있는지 여부를 나타내는 값입니다.

### <a name="remarks"></a>설명

자세한 내용은 [취소](../cancellation-in-the-ppl.md)를 참조 하세요.

## <a name="run"></a><a name="run"></a> 실행할지

개체에 대 한 작업을 예약 `task_group` 합니다. `task_handle`개체가에 대 한 매개 변수로 전달 되는 경우 `run` 호출자는 개체의 수명을 관리 하는 일을 담당 합니다 `task_handle` . 함수 개체에 대 한 참조를 매개 변수로 사용 하는 메서드 버전에는 개체에 대 한 참조를 사용 하는 버전을 사용 하는 것 보다 성능이 떨어질 수 있는 런타임 내의 힙 할당이 포함 됩니다 `task_handle` . `_Placement` 매개 변수를 사용하는 버전은 이 매개 변수로 지정된 위치에서 작업이 실행되도록 합니다.

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
작업 핸들의 본문을 실행 하기 위해 호출 될 함수 개체의 형식입니다.

*_Func*<br/>
작업의 본문을 호출 하기 위해 호출 되는 함수입니다. 이는 시그니처를 사용 하 여 함수 호출 연산자의 버전을 지 원하는 람다 식 이거나 다른 개체 일 수 있습니다 `void operator()()` .

*_Placement*<br/>
`_Func` 매개 변수가 나타내는 작업을 실행해야 할 위치에 대한 참조입니다.

*_Task_handle*<br/>
예약 중인 작업에 대 한 핸들입니다. 호출자는이 개체의 수명에 대 한 책임이 있습니다. 런타임은 `wait` 또는 `run_and_wait` 메서드가이 개체에 대해 호출 될 때까지 계속 존재할 것으로 간주 됩니다 `task_group` .

### <a name="remarks"></a>설명

런타임은 제공 된 작업 함수를 나중에 실행 하도록 예약 합니다 .이 작업은 호출 함수가 반환 될 때 일 수 있습니다. 이 메서드는 [task_handle](task-handle-class.md) 개체를 사용 하 여 제공 된 작업 함수의 복사본을 저장 합니다. 따라서이 메서드에 전달 하는 함수 개체에서 발생 하는 상태 변경 내용은 해당 함수 개체의 복사본에 표시 되지 않습니다. 또한 작업 함수가 반환 될 때까지 포인터나 작업 함수에 대 한 참조로 전달 되는 개체의 수명이 유효한 상태 인지 확인 합니다.

`task_group`예외에서 스택 해제의 결과로 destructs 또는 메서드를 호출 하는 것을 보장할 필요가 없습니다 `wait` `run_and_wait` . 이 경우 소멸자는 적절 하 게 취소 하 고 매개 변수로 표시 된 작업이 완료 될 때까지 기다립니다 `_Task_handle` .

매개 변수에 지정 된 [](invalid-multiple-scheduling-class.md) 작업 핸들이 `_Task_handle` 이미 메서드를 통해 작업 그룹 개체에 예약 되어 `run` 있고 `wait` `run_and_wait` 해당 작업 그룹의 또는 메서드에 대 한 중간 호출이 없는 경우 메서드는 invalid_multiple_scheduling 예외를 throw 합니다.

## <a name="run_and_wait"></a><a name="run_and_wait"></a> run_and_wait

`task_group`전체 취소 지원에 대 한 개체의 지원을 사용 하 여 호출 컨텍스트에서 인라인으로 실행할 작업을 예약 합니다. 그러면 함수는 개체에 대 한 모든 작업이 `task_group` 완료 되거나 취소 될 때까지 대기 합니다. `task_handle`개체가에 대 한 매개 변수로 전달 되는 경우 `run_and_wait` 호출자는 개체의 수명을 관리 하는 일을 담당 합니다 `task_handle` .

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
작업의 본문을 실행하기 위해 호출될 함수 개체의 형식입니다.

*_Task_handle*<br/>
호출 컨텍스트에서 인라인으로 실행 될 작업에 대 한 핸들입니다. 호출자는이 개체의 수명에 대 한 책임이 있습니다. 런타임은 메서드가 실행을 완료할 때까지 계속 라이브 상태로 유지 됩니다 `run_and_wait` .

*_Func*<br/>
작업 본문을 호출 하기 위해 호출 되는 함수입니다. 이는 시그니처를 사용 하 여 함수 호출 연산자의 버전을 지 원하는 람다 식 이거나 다른 개체 일 수 있습니다 `void operator()()` .

### <a name="return-value"></a>반환 값

명시적 취소 작업이 나 작업 중 하나에서 throw 되는 예외로 인해 대기가 충족 되었거나 작업 그룹이 취소 되었는지 여부를 나타냅니다. 자세한 내용은 [task_group_status](concurrency-namespace-enums.md#task_group_status)를 참조 하세요.

### <a name="remarks"></a>설명

이 개체에 예약 된 작업 중 하나 이상이 `task_group` 호출 컨텍스트에서 인라인으로 실행 될 수 있습니다.

이 개체에 예약 된 작업 중 하나 이상이 `task_group` 예외를 throw 하는 경우 런타임은 이러한 예외 중 하나를 선택 하 여 메서드에 대 한 호출에서 전파 합니다 `run_and_wait` .

`run_and_wait`개체의 메서드에서 반환 될 때 `task_group` 런타임은 개체를 다시 사용할 수 있는 깨끗 한 상태로 다시 설정 합니다. 여기에는 개체가 취소 된 사례가 포함 됩니다 `task_group` .

실행의 비 예외 경로에 `wait` 는의 소멸자가 실행 되기 전에이 메서드나 메서드를 호출 해야 합니다 `task_group` .

## <a name="task_group"></a><a name="ctor"></a> task_group

새 `task_group` 개체를 생성합니다.

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>매개 변수

*_CancellationToken*<br/>
이 작업 그룹에 연결할 취소 토큰입니다. 작업 그룹은 토큰이 취소될 때 취소됩니다.

### <a name="remarks"></a>설명

취소 토큰을 사용하는 생성자는 토큰에 연결된 소스가 취소될 때 취소될 `task_group`을 만듭니다. 명시적 취소 토큰을 제공하면 다른 토큰을 사용하거나 토큰을 사용하지 않는 부모 그룹에서의 암시적 취소에 이 작업 그룹이 참여하지 않도록 격리됩니다.

## <a name="task_group"></a><a name="dtor"></a> ~ task_group

`task_group` 개체를 제거합니다. `wait` `run_and_wait` 소멸자가 예외로 인해 스택 해제의 결과로 실행 되는 경우가 아니면 소멸자를 실행 하기 전에 개체에 대해 또는 메서드를 호출 해야 합니다.

```cpp
~task_group();
```

### <a name="remarks"></a>설명

소멸자가 일반 실행의 결과로 실행 되는 경우 (예: 예외로 인해 스택 해제 되지 않음) 및 메서드가 호출 되지 않은 `wait` 경우 `run_and_wait` 소멸자는 [missing_wait](missing-wait-class.md) 예외를 throw 할 수 있습니다.

## <a name="wait"></a><a name="wait"></a> 대기한

개체에 대 한 모든 작업이 `task_group` 완료 되거나 취소 될 때까지 대기 합니다.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>반환 값

명시적 취소 작업이 나 작업 중 하나에서 throw 되는 예외로 인해 대기가 충족 되었거나 작업 그룹이 취소 되었는지 여부를 나타냅니다. 자세한 내용은 [task_group_status](concurrency-namespace-enums.md#task_group_status)를 참조 하세요.

### <a name="remarks"></a>설명

이 개체에 예약 된 작업 중 하나 이상이 `task_group` 호출 컨텍스트에서 인라인으로 실행 될 수 있습니다.

이 개체에 예약 된 작업 중 하나 이상이 `task_group` 예외를 throw 하는 경우 런타임은 이러한 예외 중 하나를 선택 하 여 메서드에 대 한 호출에서 전파 합니다 `wait` .

`wait`개체에 대해를 호출 하면 `task_group` 이를 다시 사용할 수 있는 깨끗 한 상태로 다시 설정 합니다. 여기에는 개체가 취소 된 사례가 포함 됩니다 `task_group` .

실행의 비 예외 경로에 `run_and_wait` 는의 소멸자가 실행 되기 전에이 메서드나 메서드를 호출 해야 합니다 `task_group` .

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[structured_task_group 클래스](structured-task-group-class.md)<br/>
[task_handle 클래스](task-handle-class.md)
