---
description: Task_handle 클래스에 대해 자세히 알아보세요.
title: task_handle 클래스
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: 21fa2a1782fad200061deb1e85bf052613354a34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188224"
---
# <a name="task_handle-class"></a>task_handle 클래스

`task_handle` 클래스는 개별 병렬 작업 항목을 나타냅니다. 작업을 실행하는 데 필요한 지침 및 데이터를 캡슐화합니다.

## <a name="syntax"></a>구문

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
개체로 표시 되는 작업을 실행 하기 위해 호출 될 함수 개체의 형식입니다 `task_handle` .

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[task_handle](#task_handle)|새 `task_handle` 개체를 생성합니다. 작업은 생성자에 대 한 매개 변수로 지정 된 함수를 호출 하 여 수행 됩니다.|
|[~ task_handle 소멸자](#dtor)|개체를 소멸 시킵니다 `task_handle` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 ()](#task_handle__operator_call)|작업 핸들의 작업을 수행 하기 위해 런타임에서 호출 하는 함수 호출 연산자입니다.|

## <a name="remarks"></a>설명

`task_handle` 개체는 `structured_task_group` 또는 보다 일반적인 개체와 함께 사용 `task_group` 하 여 작업을 병렬 작업으로 분해할 수 있습니다. 자세한 내용은 [작업 병렬 처리](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

개체의 작성자는 동시성 런타임에 `task_handle` `task_handle` 더 이상 필요 하지 않을 때까지 생성 된 개체의 수명을 유지 관리 해야 합니다. 일반적으로이는 `task_handle` 개체가 큐에 대기 중인 또는 메서드 중 하나가 호출 될 때까지 개체를 소멸 하지 않아야 함을 의미 합니다 `wait` `run_and_wait` `task_group` `structured_task_group` .

`task_handle` 개체는 일반적으로 c + + 람다와 함께 사용 됩니다. 람다의 실제 형식을 알 수 없기 때문에 [make_task](concurrency-namespace-functions.md#make_task) 함수는 일반적으로 개체를 만드는 데 사용 됩니다 `task_handle` .

런타임에서는 개체에 전달 하는 작업 함수의 복사본을 만듭니다 `task_handle` . 따라서 개체에 전달 하는 함수 개체에서 발생 하는 상태 변경 내용은 `task_handle` 해당 함수 개체의 복사본에 표시 되지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`task_handle`

## <a name="requirements"></a>요구 사항

**헤더:** ppl. h

**네임 스페이스:** 동시성

## <a name="operator"></a><a name="task_handle__operator_call"></a> 연산자 ()

작업 핸들의 작업을 수행 하기 위해 런타임에서 호출 하는 함수 호출 연산자입니다.

```cpp
void operator()() const;
```

## <a name="task_handle"></a><a name="task_handle"></a> task_handle

새 `task_handle` 개체를 생성합니다. 작업은 생성자에 대 한 매개 변수로 지정 된 함수를 호출 하 여 수행 됩니다.

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>매개 변수

*_Func*<br/>
개체로 표시 되는 작업을 실행 하기 위해 호출 되는 함수입니다 `task_handle` . 이는 람다 함수, 함수에 대 한 포인터 또는 시그니처와 함께 함수 호출 연산자의 버전을 지 원하는 모든 개체 일 수 있습니다 `void operator()()` .

### <a name="remarks"></a>설명

런타임에서는 생성자에 전달 하는 작업 함수의 복사본을 만듭니다. 따라서 개체에 전달 하는 함수 개체에서 발생 하는 상태 변경 내용은 `task_handle` 해당 함수 개체의 복사본에 표시 되지 않습니다.

## <a name="task_handle"></a><a name="dtor"></a> ~ task_handle

개체를 소멸 시킵니다 `task_handle` .

```cpp
~task_handle();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[task_group 클래스](task-group-class.md)<br/>
[structured_task_group 클래스](structured-task-group-class.md)
