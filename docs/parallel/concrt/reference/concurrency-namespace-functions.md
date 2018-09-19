---
title: concurrency 네임 스페이스 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e71804a2b9b9420e4e7839bf33054fb1ed0a7797
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021202"
---
# <a name="concurrency-namespace-functions"></a>concurrency 네임 스페이스 함수
||||  
|-|-|-|  
|[할당](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|  
|[EnableTracing](#enabletracing)|[무료](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|  
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|  
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|  
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|  
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|  
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|  
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|  
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|  
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|  
|[run_with_cancellation_token](#run_with_cancellation_token)|[send](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|  
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|  
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[wait](#wait)|  
|[when_all](#when_all)|[when_any](#when_any)|  
  
##  <a name="alloc"></a>  Alloc  
 동시성 런타임 캐싱 하위 할당기에서 지정된 크기의 메모리 블록을 할당합니다.  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>매개 변수  
*_NumBytes*<br/>
할당할 메모리의 바이트 수입니다.  
  
### <a name="return-value"></a>반환 값  
 새로 할당 된 메모리에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 캐싱 하위 할당자를 사용 하 여 이점을 얻을 수 응용 프로그램에서 시나리오에 대 한 자세한 내용은 [작업 스케줄러](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)합니다.  
  
##  <a name="asend"></a>  asend  
 대상 블록에 데이터를 전파하는 작업을 예약하는 비동기 전송 작업입니다.  
  
```
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
전송할 데이터의 형식입니다.  
  
*_Trg*<br/>
포인터 또는 데이터 전송 하는 대상에 대 한 참조입니다.  
  
*(_D)*<br/>
데이터 전송에 대 한 참조입니다.  
  
### <a name="return-value"></a>반환 값  
 `true` 메서드가 반환 되기 전에 메시지가 허용 된 경우 `false` 그렇지 않은 경우.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [메시지 전달 함수](../../../parallel/concrt/message-passing-functions.md)합니다.  
  
##  <a name="cancel_current_task"></a>  cancel_current_task  
 현재 실행 중인 작업을 취소합니다. 이 함수는 작업 실행을 중단하도록 작업 본문 내에서 호출될 수 있으며 `canceled` 상태로 들어가도록 할 수 있습니다.  
  
 `task`의 본문에 없는 경우에 이 함수를 호출하는 것은 지원되는 시나리오가 아닙니다. 그럴 경우 응용 프로그램의 충돌 또는 시스템 중단 같이 정의되지 않은 동작이 발생합니다.  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear"></a>  clear  
 제거 된 동시 큐를 지웁니다 현재 큐에 넣은 요소입니다. 이 메서드는 동시성이 보장 되지 않습니다.  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>매개 변수  
*T*<br/>

*_Ax*<br/>
  
##  <a name="create_async"></a>  create_async  
 사용자가 제공한 람다 또는 함수 개체를 기준으로 Windows 런타임 비동기 구문을 만듭니다. `create_async`의 반환 형식은 메서드에 전달된 람다의 시그니처에 따라 `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` 또는 `IAsyncOperationWithProgress<TResult, TProgress>^` 중 하나입니다.  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>매개 변수  
*_Function*<br/>
형식입니다.

*_Func*<br/>
Windows 런타임 비동기 구문을 만들 람다 또는 함수 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 IAsyncAction로 표시 되는 비동기 구문 ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, 또는 an IAsyncOperationWithProgress\<TResult, TProgress > ^ 합니다. 반환된 인터페이스는 함수에 전달되는 람다의 시그니처에 종속됩니다.  
  
### <a name="remarks"></a>설명  
 람다의 반환 형식은 구문이 동작 또는 작업인지 여부를 결정합니다.  
  
 void를 반환하는 람다는 작업을 생성합니다. `TResult` 형식의 결과를 반환하는 람다는 TResult 작업을 생성합니다.  
  
 람다는 비동기 작업을 자체 내에 캡슐화하거나 비동기 작업을 나타내는 연속 작업 체인인 `task<TResult>`를 반환할 수도 있습니다. 이 경우 작업은 비동기적으로 실행되므로 람다 자체가 인라인으로 실행되며, 람다의 반환 형식은 래핑이 해제되어 `create_async`에서 반환된 비동기 구문을 생성합니다. 이 람다를 반환 하는 작업을 의미\<void > 작업 및 태스크를 반환 하는 람다 생성 하면\<TResult > 만든다는 TResult 작업을 합니다.  
  
 람다는 0개, 하나 또는 두 개의 인수를 사용할 수 있습니다. 해당 순서로 함께 사용되는 경우 올바른 인수는 `progress_reporter<TProgress>` 및 `cancellation_token`입니다. 인수가 없는 람다를 사용하면 진행률을 보고할 수 없는 비동기 구문이 생성됩니다. Progress_reporter를 사용 하는 람다\<TProgress > 하면 `create_async` 될 때마다 형식 TProgress의 진행률을 보고 하는 비동기 구문을 반환 하도록 합니다 `report` progress_reporter 개체의 메서드가 호출 됩니다. cancellation_token을 사용하는 람다는 해당 토큰을 사용하여 취소 여부를 확인하거나 이 토큰이 생성하는 작업에 전달되어 비동기 구문의 취소가 이러한 작업의 취소를 발생시키도록 할 수 있습니다.  
  
 람다 또는 함수 개체의 본문에는 결과 반환 하는 경우 (작업이 아닌\<TResult >)을 런타임 작업의 컨텍스트에서 MTA에 대 한 암시적으로 만드는 프로세스 내에서 람다를 비동기적으로 실행 됩니다. `IAsyncInfo::Cancel` 메서드는 암시적 작업의 취소를 발생시킵니다.  
  
 람다 본문이 작업을 반환하는 경우 람다는 인라인 실행됩니다. 그리고 람다가 `cancellation_token` 형식의 인수를 갖도록 선언함으로써 작업을 만들 때 해당 토큰을 전달하여 람다 내부에서 만든 모든 작업의 취소를 트리거할 수 있습니다. 생성된 비동기 작업 또는 동작에서 `register_callback`을 호출할 때 런타임에서 콜백을 호출하도록 토큰에 `IAsyncInfo::Cancel` 메서드를 사용할 수도 있습니다.  
  
 이 기능은 Windows 런타임 앱에 사용할 수만 있습니다.  
  
##  <a name="createresourcemanager"></a>  CreateResourceManager  
 동시성 런타임 리소스 관리자의 singleton 인스턴스를 나타내는 인터페이스를 반환합니다. 리소스 관리자는 서로 협력하려는 스케줄러에 리소스를 할당해야 합니다.  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>반환 값  
 `IResourceManager` 인터페이스입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 여러 후속 호출에는 리소스 관리자의 동일한 인스턴스를 반환 됩니다. 증분 메서드를 호출할 때마다 대 한 참조를 Resource Manager에 계산 및 호출 하 여 일치 해야 합니다는 [iresourcemanager:: Release](iresourcemanager-structure.md) 메서드 스케줄러 완료 되 면 리소스 관리자와 통신 합니다.  
  
 [unsupported_os](unsupported-os-class.md) 운영 체제가 동시성 런타임에 의해 지원 되지 않는 경우 throw 됩니다.  
  
##  <a name="create_task"></a>  create_task  
 PPL을 만듭니다 [태스크](task-class.md) 개체입니다. 작업 생성자를 사용하는 곳이면 어디에나 `create_task`를 사용할 수 있습니다. 작업을 만드는 동안 `auto` 키워드 사용을 허용하기 때문에 주로 편의상 제공됩니다.  
  
```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
작업이 생성되는 매개 변수 형식입니다.  
  
*_ReturnType*<br/>
형식입니다.

*되므로*<br/>
작업이 생성되는 매개 변수입니다. 이 람다 또는 함수 개체 수를 `task_completion_event` 개체, 다른 `task` 개체 또는 UWP 앱에서 작업을 사용 하는 경우 Windows::Foundation::IAsyncInfo 인터페이스.  
  
*_TaskOptions*<br/>
작업 옵션입니다.

*_Task*<br/>
만들 태스크입니다.

### <a name="return-value"></a>반환 값  
 형식의 새 작업 `T`, 즉에서 유추 `_Param`합니다.  
  
### <a name="remarks"></a>설명  
 첫 번째 오버 로드는 단일 매개 변수를 사용 하는 작업 생성자 처럼 동작 합니다.  
  
 두 번째 오버 로드는 새로 만들어진된 작업을 사용 하 여 제공 된 취소 토큰을 연결 합니다. 이 오버 로드를 사용 하는 경우 다른 전달할 수 있습니다 `task` 첫 번째 매개 변수로 개체입니다.  
  
 반환된 된 작업의 형식 함수를 첫 번째 매개 변수에서 유추 됩니다. 경우 `_Param` 되는 `task_completion_event<T>`, `task<T>`, 또는 유형 중 하나를 반환 하는 함수인 `T` 또는 `task<T>`, 만들어진된 작업의 유형입니다 `task<T>`합니다.  
  
 UWP 앱의 경우 `_Param` Windows::Foundation::IAsyncOperation 유형의\<T > ^ 또는 Windows::Foundation::IAsyncOperationWithProgress\<T, P > ^, 또는 이러한 형식 중 하나를 반환 하는 함수는 만들어진된 작업의 됩니다 형식 `task<T>`합니다. 하는 경우 `_Param` Windows::Foundation::IAsyncAction 형식의 ^ 또는 Windows::Foundation::IAsyncActionWithProgress\<P > ^, 또는 이러한 형식 중 하나를 반환 하는 함수는 만들어진된 작업 형식은 `task<void>`합니다.  
  
##  <a name="disabletracing"></a>  DisableTracing  
 동시성 런타임에서 추적을 사용하지 않도록 설정합니다. ETW 추적이 기본적으로 등록되지 않으므로 이 함수는 사용되지 않습니다.  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>반환 값  
 추적 된 올바르게 사용 하지 않도록 설정 하는 경우 `S_OK` 반환 됩니다. 추적이 이전에 시작되지 않은 경우 `E_NOT_STARTED`가 반환됩니다.  
  
##  <a name="enabletracing"></a>  EnableTracing  
 동시성 런타임에서 추적을 사용하도록 설정합니다. 이제 ETW 추적이 기본적으로 설정되므로 이 함수는 사용되지 않습니다.  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>반환 값  
 추적을 시작 잘못 되었으면 `S_OK` 반환 되 고, 그렇지 않으면 `E_NOT_STARTED` 반환 됩니다.  
  
##  <a name="free"></a>  Free  
 `Alloc` 메서드에 의해 동시성 런타임 캐싱 하위 할당자에 이전에 할당된 메모리 블록을 해제합니다.  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>매개 변수  
*_PAllocation*<br/>
이전에 의해 할당 된 메모리에 대 한 포인터를 `Alloc` 해제 하는 메서드. 경우 매개 변수 `_PAllocation` 값으로 설정 되어 `NULL`,이 메서드는 무시 하 고 즉시 반환 합니다.  
  
### <a name="remarks"></a>설명  
 캐싱 하위 할당자를 사용 하 여 이점을 얻을 수 응용 프로그램에서 시나리오에 대 한 자세한 내용은 [작업 스케줄러](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)합니다.  
  
##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler  
  
```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```  
  
### <a name="return-value"></a>반환 값  
  
##  <a name="getexecutioncontextid"></a>  GetExecutionContextId  
 `IExecutionContext` 인터페이스를 구현하는 실행 컨텍스트에 할당할 수 있는 고유 식별자를 반환합니다.  
  
```
unsigned int __cdecl GetExecutionContextId();
```  
  
### <a name="return-value"></a>반환 값  
 실행 컨텍스트에 대 한 고유 식별자입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 사용 하 여 전달 하기 전에 실행 컨텍스트에 대 한 식별자를 얻으려면는 `IExecutionContext` Resource Manager에서 제공 하는 방법 중 하나를 매개 변수로 인터페이스입니다.  
  
##  <a name="getosversion"></a>  GetOSVersion  
 운영 체제 버전을 반환합니다.  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>반환 값  
 운영 체제를 나타내는 열거형된 값입니다.  
  
### <a name="remarks"></a>설명  
 [unsupported_os](unsupported-os-class.md) 운영 체제가 동시성 런타임에 의해 지원 되지 않는 경우 throw 됩니다.  
  
##  <a name="getprocessorcount"></a>  GetProcessorCount  
 기본 시스템의 하드웨어 스레드 수를 반환합니다.  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>반환 값  
 하드웨어 스레드의 수입니다.  
  
### <a name="remarks"></a>설명  
 [unsupported_os](unsupported-os-class.md) 운영 체제가 동시성 런타임에 의해 지원 되지 않는 경우 throw 됩니다.  
  
##  <a name="getprocessornodecount"></a>  GetProcessorNodeCount  
 기본 시스템의 NUMA 노드 또는 프로세서 패키지 수를 반환합니다.  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>반환 값  
 NUMA 노드 또는 프로세서 패키지 수입니다.  
  
### <a name="remarks"></a>설명  
 시스템 프로세서 패키지 보다 많은 NUMA 노드가 들어 있으면 NUMA 노드 수가 반환 되 고, 그렇지 않으면 프로세서 패키지 수가 반환 됩니다.  
  
 [unsupported_os](unsupported-os-class.md) 운영 체제가 동시성 런타임에 의해 지원 되지 않는 경우 throw 됩니다.  
  
##  <a name="getschedulerid"></a>  GetSchedulerId  
 `IScheduler` 인터페이스를 구현하는 스케줄러에 할당할 수 있는 고유 식별자를 반환합니다.  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>반환 값  
 스케줄러에 대 한 고유 식별자입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 사용 하 여 전달 하기 전에 스케줄러에 대 한 식별자를 얻으려면는 `IScheduler` Resource Manager에서 제공 하는 방법 중 하나를 매개 변수로 인터페이스입니다.  
  
##  <a name="internal_assign_iterators"></a>  internal_assign_iterators  
  
```
template<typename T, class _Ax>
template<class _I> 
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```   
  
### <a name="parameters"></a>매개 변수  
*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*last*<br/>
  
##  <a name="interruption_point"></a>  interruption_point  
 취소를 위한 중단 지점을 만듭니다. 이 함수가 호출된 컨텍스트에서 취소가 진행 중이면 현재 실행 중인 병렬 작업의 실행을 중단하는 내부 예외가 발생합니다. 취소가 진행되고 있지 않으면 함수에서 아무 작업도 하지 않습니다.  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>설명  
 `interruption_point()` 함수에 의해 throw된 내부 취소 예외를 catch하면 안 됩니다. 예외는 런타임에서 catch되어 처리되며, 예외를 catch하면 프로그램이 비정상적으로 동작할 수 있습니다.  
  
##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling  
 현재 컨텍스트에서 현재 인라인으로 실행 중인 작업 그룹이 활성 취소 중이거나 곧 취소되는지 여부를 나타내는 표시를 반환합니다. 현재 컨텍스트에서 현재 인라인으로 실행 중인 작업 그룹이 없는 경우 `false`가 반환됩니다.  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>반환 값  
 `true` 현재 실행 중인 작업 그룹을 취소 하는 경우 `false` 그렇지 않은 경우.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [취소](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)합니다.  
  
##  <a name="make_choice"></a>  make_choice  
 선택적 `choice` 또는 `Scheduler`과 두 개 이상의 입력 소스로 `ScheduleGroup` 메시징 블록을 생성합니다.  
  
```
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```  
  
### <a name="parameters"></a>매개 변수  
*T1*<br/>
첫 번째 소스의 메시지 블록 형식입니다.  
  
*T2*<br/>
두 번째 소스 메시지 블록 형식입니다.  
  
*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `choice` 개체입니다.  
  
*_Item1*<br/>
첫 번째 소스입니다.  
  
*_Item2*<br/>
두 번째 소스입니다.  
  
*항목 (_i)*<br/>
추가적인 소스입니다.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `choice` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.  
  
### <a name="return-value"></a>반환 값  
 두 개 이상의 입력 소스가 있는 `choice` 메시지 블록입니다.  
  
##  <a name="make_greedy_join"></a>  make_greedy_join  
 선택적 `greedy multitype_join` 또는 `Scheduler`과 두 개 이상의 입력 소스로 `ScheduleGroup` 메시징 블록을 생성합니다.  
  
```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```  
  
### <a name="parameters"></a>매개 변수  
*T1*<br/>
첫 번째 소스의 메시지 블록 형식입니다.  
  
*T2*<br/>
두 번째 소스 메시지 블록 형식입니다.  
  
*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `multitype_join` 개체입니다.  
  
*_Item1*<br/>
첫 번째 소스입니다.  
  
*_Item2*<br/>
두 번째 소스입니다.  
  
*항목 (_i)*<br/>
추가적인 소스입니다.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `multitype_join` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.  
  
### <a name="return-value"></a>반환 값  
 두 개 이상의 입력 소스가 있는 `greedy multitype_join` 메시지 블록입니다.  
  
##  <a name="make_join"></a>  make_join  
 선택적 `non_greedy multitype_join` 또는 `Scheduler`과 두 개 이상의 입력 소스로 `ScheduleGroup` 메시징 블록을 생성합니다.  
  
```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> 
    make_join(
 Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
 ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```  
  
### <a name="parameters"></a>매개 변수  
*T1*<br/>
첫 번째 소스의 메시지 블록 형식입니다.  
  
*T2*<br/>
두 번째 소스 메시지 블록 형식입니다.  
  
*_PScheduler*<br/>
`Scheduler` 메시징 블록의 전파 작업이 예약되는 `multitype_join` 개체입니다.  
  
*_Item1*<br/>
첫 번째 소스입니다.  
  
*_Item2*<br/>
두 번째 소스입니다.  
  
*항목 (_i)*<br/>
추가적인 소스입니다.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` 메시징 블록의 전파 작업이 예약되는 `multitype_join` 개체입니다. 사용된 `Scheduler` 개체는 일정 그룹에서 암시됩니다.  
  
### <a name="return-value"></a>반환 값  
 두 개 이상의 입력 소스가 있는 `non_greedy multitype_join` 메시지 블록입니다.  
  
##  <a name="make_task"></a>  make_task  
 `task_handle` 개체를 만들기 위한 팩터리 메서드입니다.  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>매개 변수  
*_Function*<br/>
표현 되는 작업을 실행 하기 위해 호출 될 함수 개체의 형식은 `task_handle` 개체입니다.  
  
*_Func*<br/>
표현 되는 작업을 실행 하기 위해 호출 될 함수를 `task_handle` 개체입니다. 이 람다 함수, 함수에 대 한 포인터 이거나 서명 사용 하 여 함수 호출 연산자의 버전을 지 원하는 모든 개체 `void operator()()`합니다.  
  
### <a name="return-value"></a>반환 값  
 `task_handle` 개체입니다.  
  
### <a name="remarks"></a>설명  
 이 함수는 만들어야 하는 경우에 유용는 `task_handle` 람다 식으로 개체는 람다 함수의 실제 형식을 알지 못해도 개체를 만들 수 있습니다.  
  
##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort  
 지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 병렬로 정렬합니다. 이 함수는 `O(n)` 추가 공간이 필요하고 정렬되는 요소에 대한 기본 초기화를 요구한다는 점을 제외하고, 비교 기반의 불안정한 내부 정렬이라는 점에서 `std::sort`와 의미 체계가 비슷합니다.  
  
```
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```  
  
### <a name="parameters"></a>매개 변수  
*_Random_iterator*<br/>
입력 범위의 반복기 형식입니다.  
  
*_Allocator*<br/>
C + + 표준 라이브러리 호환 메모리 할당자의 형식입니다.  
  
*_Function*<br/>
이진 비교 연산자의 형식입니다.  
  
*시작 (_b)*<br/>
저장할 범위의 첫 번째 요소 위치를 주소 지정하는 임의 액세스 반복기입니다.  
  
*(_E)*<br/>
저장할 범위의 마지막 요소 하나 다음 위치를 주소 지정하는 임의 액세스 반복기입니다.  
  
*_Alloc*<br/>
C + + 표준 라이브러리 호환 메모리 할당자의 인스턴스.  
  
*_Func*<br/>
순서에 따라 연속적인 요소에 대해 충족될 비교 조건을 정의하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하여 조건이 충족되면 `true`를 반환하고, 충족되지 않으면 `false`를 반환합니다. 이 비교 함수는 시퀀스의 요소 쌍에 대해 엄밀히 약한 순서를 적용해야 합니다.  
  
*_Chunk_size*<br/>
병렬 실행을 위해 두 개로 분할될 청크의 최소 크기입니다.  
  
### <a name="remarks"></a>설명  
 모든 오버 로드 필요 `n * sizeof(T)` 추가 공간을 여기서 `n` 정렬 될 요소의 수 및 `T` 요소 형식입니다. 대부분의 경우 parallel_buffered_sort 알아보겠습니다 성능 향상을 통해 [parallel_sort](concurrency-namespace-functions.md), parallel_sort를 통해 사용 가능한 메모리가 사용 해야 합니다.  
  
 이진 비교 연산자를 제공 하지 않는 경우 `std::less` 연산자를 제공 하는 요소 형식이 필요로 하는 기본으로 사용 됩니다 `operator<()`합니다.  
  
 할당자 유형 또는 인스턴스, c + + 표준 라이브러리 메모리 할당자를 제공 하지 않는 경우 `std::allocator<T>` 버퍼를 할당 하는 데 사용 됩니다.  
  
 알고리즘은 입력 범위를 두 개의 청크로 나누고 이어서 각 청크를 병렬로 실행할 두 개의 하위 청크로 나눕니다. 선택적 인수 `_Chunk_size`를 사용하여 크기가 < `_Chunk_size`인 청크를 직렬로 처리하도록 알고리즘에 지정할 수 있습니다.  
  
##  <a name="parallel_for"></a>  parallel_for  
 `parallel_for`는 일정 범위의 인덱스를 반복하고 각 반복 시 사용자가 제공한 함수를 병렬로 실행합니다.  
  
```
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```  
  
### <a name="parameters"></a>매개 변수  
*_Index_type*<br/>
반복에 사용 되는 인덱스의 형식입니다.  
  
*_Function*<br/>
각 반복에서 실행 될 함수의 형식입니다.  
  
*_Partitioner*<br/>
제공 된 범위를 분할 하는 데 사용 되는 파티 셔 너의 형식입니다.  
  
*first*<br/>
반복에 포함할 첫 번째 인덱스입니다.  
  
*last*<br/>
인덱스 하나 이전 반복에 포함할 마지막 인덱스입니다.  
  
*_Step*<br/>
단계를 반복 하는 경우에 사용 되는 값 `first` 에 `last`입니다. 단계는 양수 여야 합니다. [invalid_argument](../../../standard-library/invalid-argument-class.md) 단계 1 보다 작은 경우 throw 됩니다.  
  
*_Func*<br/>
각 반복 시 실행할 함수입니다. 람다 식, 함수 포인터를 수 있습니다 또는 서명 사용 하 여 함수 호출 연산자의 버전을 지 원하는 모든 개체 `void operator()(_Index_type)`합니다.  
  
*_Part*<br/>
partitioner 개체에 대한 참조입니다. 인수 중 하나일 수 있습니다 `const` [auto_partitioner](auto-partitioner-class.md)`&`합니다 `const` [static_partitioner](static-partitioner-class.md)`&`하십시오 `const` [simple_ 파티 셔 너](simple-partitioner-class.md) `&` 하거나 [affinity_partitioner](affinity-partitioner-class.md) `&` 경우를 [affinity_partitioner](affinity-partitioner-class.md) 개체는, 참조는 비 const l-value 해야 합니다. 알고리즘을 재사용 하 여 향후의 루프에 대 한 상태를 저장할 수 있도록 참조 합니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [병렬 알고리즘](../../../parallel/concrt/parallel-algorithms.md)합니다.  
  
##  <a name="parallel_for_each"></a>  parallel_for_each  
 `parallel_for_each`는 범위 내의 각 요소에 지정된 함수를 병렬로 적용합니다. 요소에 대한 반복이 병렬로 수행되고 반복 순서가 지정되지 않는다는 점을 제외하고 `std` 네임스페이스의 `for_each` 함수와 의미 체계가 같습니다. `_Func` 인수는 `operator()(T)` 형식의 함수 호출 연산자를 지원해야 합니다. 여기서 `T` 매개 변수는 반복되는 컨테이너의 항목 형식입니다.  
  
```
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```  
  
### <a name="parameters"></a>매개 변수  
*_Iterator*<br/>
컨테이너를 통해 반복 하는 데 사용 되는 반복기의 형식입니다.  
  
*_Function*<br/>
형식 범위 내의 각 요소에 적용할 함수입니다.  
  
*_Partitioner*<br/>
*first*<br/>
병렬 반복에 포함할 첫 번째 요소 위치의 주소를 지정 반복기입니다.  
  
*last*<br/>
병렬 반복에 포함할 하나 마지막 요소 다음 위치의 주소 지정 반복기입니다.  
  
*_Func*<br/>
범위의 각 요소에 적용 되는 사용자 정의 함수 개체입니다.  
  
*_Part*<br/>
partitioner 개체에 대한 참조입니다. 인수 중 하나일 수 있습니다 `const` [auto_partitioner](auto-partitioner-class.md)`&`합니다 `const` [static_partitioner](static-partitioner-class.md)`&`하십시오 `const` [simple_ 파티 셔 너](simple-partitioner-class.md) `&` 하거나 [affinity_partitioner](affinity-partitioner-class.md) `&` 경우를 [affinity_partitioner](affinity-partitioner-class.md) 개체는, 참조는 비 const l-value 해야 합니다. 알고리즘을 재사용 하 여 향후의 루프에 대 한 상태를 저장할 수 있도록 참조 합니다.  
  
### <a name="remarks"></a>설명  
 [auto_partitioner](auto-partitioner-class.md) 는 명시적인 partitioner 없이 오버 로드에 사용 됩니다.  
  
 만 지원 하지 않는 임의 반복기 액세스할 [auto_partitioner](auto-partitioner-class.md) 지원 됩니다.  
  
 자세한 내용은 [병렬 알고리즘](../../../parallel/concrt/parallel-algorithms.md)합니다.  
  
##  <a name="parallel_invoke"></a>  parallel_invoke  
 매개 변수로 제공된 함수 개체를 병렬로 실행하고 실행이 완료될 때까지 차단됩니다. 각 함수 개체는 람다 식, 함수에 대한 포인터 또는 `void operator()()` 서명을 사용하여 함수 호출 연산자를 지원하는 모든 개체일 수 있습니다.  
  
```
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```  
  
### <a name="parameters"></a>매개 변수  
*_Function1*<br/>
병렬로 실행 될 첫 번째 함수 개체의 형식입니다.  
  
*_Function2*<br/>
병렬로 실행 될 두 번째 함수 개체의 형식입니다.  
  
*_Function3*<br/>
병렬 실행 수를 세 번째 함수 개체의 형식입니다.  
  
*_Function4*<br/>
네 번째 병렬로 실행 될 함수 개체의 형식입니다.  
  
*_Function5*<br/>
병렬로 실행 될 다섯 번째 함수 개체의 형식입니다.  
  
*_Function6*<br/>
병렬로 실행 될 여섯 번째 함수 개체의 형식입니다.  
  
*_Function7*<br/>
일곱 번째 병렬로 실행 될 함수 개체의 형식입니다.  
  
*_Function8*<br/>
병렬로 실행 될 여덟 번째 함수 개체의 형식입니다.  
  
*_Function9*<br/>
병렬로 실행 될 아홉 번째 함수 개체의 형식입니다.  
  
*_Function10*<br/>
병렬로 실행 될 열 번째 함수 개체의 형식입니다.  
  
*_Func1*<br/>
병렬로 실행 될 첫 번째 함수 개체입니다.  
  
*_Func2*<br/>
병렬로 실행할 두 번째 함수 개체입니다.  
  
*_Func3*<br/>
병렬 실행 수를 세 번째 함수 개체입니다.  
  
*_Func4*<br/>
병렬로 실행 될 네 번째 함수 개체입니다.  
  
*_Func5*<br/>
병렬로 실행 될 다섯 번째 함수 개체입니다.  
  
*_Func6*<br/>
병렬 실행에 여섯 번째 함수 개체입니다.  
  
*_Func7*<br/>
동시에 실행할 일곱 번째 함수 개체입니다.  
  
*_Func8*<br/>
병렬로 실행 될 여덟 번째 함수 개체입니다.  
  
*_Func9*<br/>
병렬로 실행 될 아홉 번째 함수 개체입니다.  
  
*_Func10*<br/>
병렬로 실행 될 열 번째 함수 개체입니다.  
  
### <a name="remarks"></a>설명  
 Note는 함수 개체 중 하나 이상을 제공 된 매개 변수 인라인 호출 컨텍스트에서 실행할 수 있습니다.  
  
 이 함수에 매개 변수로 전달 된 함수 개체의 하나 이상의 예외를 throw 하는 경우 런타임에서 해당 선택의 이러한 한 가지 예외를 선택 하 고에 대 한 호출에서 전파 `parallel_invoke`합니다.  
  
 자세한 내용은 [병렬 알고리즘](../../../parallel/concrt/parallel-algorithms.md)합니다.  
  
##  <a name="parallel_radixsort"></a>  parallel_radixsort  
 기수 정렬 알고리즘을 사용하여 지정된 범위의 요소를 비내림차순으로 정렬합니다. 부호 없는 정수와 유사한 키로 정렬할 요소를 프로젝션할 수 있는 프로젝션 함수를 요구하는 안정적인 정렬 함수입니다. 정렬되는 요소에 기본 초기화가 필요합니다.  
  
```
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```  
  
### <a name="parameters"></a>매개 변수  
*_Random_iterator*<br/>
입력 범위의 반복기 형식입니다.  
  
*_Allocator*<br/>
C + + 표준 라이브러리 호환 메모리 할당자의 형식입니다.  
  
*_Function*<br/>
형식 프로젝션 함수입니다.  
  
*시작 (_b)*<br/>
저장할 범위의 첫 번째 요소 위치를 주소 지정하는 임의 액세스 반복기입니다.  
  
*(_E)*<br/>
저장할 범위의 마지막 요소 하나 다음 위치를 주소 지정하는 임의 액세스 반복기입니다.  
  
*_Alloc*<br/>
C + + 표준 라이브러리 호환 메모리 할당자의 인스턴스.  
  
*_Proj_func*<br/>
정수 계열 값으로 요소를 변환 하는 프로젝션 사용자 정의 함수 개체입니다.  
  
*_Chunk_size*<br/>
병렬 실행을 위해 두 개로 분할될 청크의 최소 크기입니다.  
  
### <a name="remarks"></a>설명  
 모든 오버 로드 필요 `n * sizeof(T)` 추가 공간을 여기서 `n` 정렬 될 요소의 수 및 `T` 요소 형식입니다. 서명 사용 하 여 단항 프로젝션 함수를 `I _Proj_func(T)` 요소에 지정 된 경우 키를 반환 하는 데 필요한 위치 `T` 의 요소 형식 및 `I` 부호 없는 정수와 유사한 형식입니다.  
  
 프로젝션 함수를 제공 하지 않으면 기본 프로젝션 함수 단순히 요소를 반환 하는 정수 계열 형식에 대 한 사용 됩니다. 함수는 요소가 없는 경우 정수 계열 형식의 프로젝션 함수 없으면 컴파일되지 것입니다.  
  
 할당자 유형 또는 인스턴스, c + + 표준 라이브러리 메모리 할당자를 제공 하지 않는 경우 `std::allocator<T>` 버퍼를 할당 하는 데 사용 됩니다.  
  
 알고리즘은 입력 범위를 두 개의 청크로 나누고 이어서 각 청크를 병렬로 실행할 두 개의 하위 청크로 나눕니다. 선택적 인수 `_Chunk_size`를 사용하여 크기가 < `_Chunk_size`인 청크를 직렬로 처리하도록 알고리즘에 지정할 수 있습니다.  
  
##  <a name="parallel_reduce"></a>  parallel_reduce  
 연속적 부분 합계를 계산하여 지정된 범위 내 모든 요소의 합계를 계산하거나, 합계 대신 지정된 이항 연산을 사용하여 유사하게 구한 연속적 부분 결과의 결과를 병렬로 계산합니다. `parallel_reduce`는 이항 연산이 결합형이어야 하고 초기 값 대신 ID 값을 요구한다는 점을 제외하고 `std::accumulate`와 의미 체계가 비슷합니다.  
  
```
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```  
  
### <a name="parameters"></a>매개 변수  
*_Forward_iterator*<br/>
입력 범위의 반복기 형식입니다.  
  
*_Sym_reduce_fun*<br/>
대칭 감소 함수의 형식입니다. 이 서명 사용 하 여 함수 형식 이어야 `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`_Reduce_type 인 동일한 id 형식 및 감소의 결과 형식으로, 합니다. 세 번째 오버 로드에 대 한이 일치 해야 출력 유형의 `_Range_reduce_fun`합니다.  
  
*_Reduce_type*<br/>
형식으로 입력을 줄이는 입력된 요소 형식과 다를 수 있습니다. 반환 값 및 id 값은이 형식이 발생 합니다.  
  
*_Range_reduce_fun*<br/>
범위 감소 함수의 형식입니다. 이 서명 사용 하 여 함수 형식 이어야 `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type id 형식 및 감소의 결과 형식으로는 동일 합니다.  
  
*시작 (_b)*<br/>
입력된 반복기 범위에서 첫 번째 요소를 주소 지정을 줄일 수 있습니다.  
  
*(_E)*<br/>
요소를 줄일 수 범위에서 마지막 요소 하나 다음 위치의 주소를 지정 하는 입력된 반복기입니다.  
  
*_Identity*<br/>
Id 값을 `_Identity` 감소의 결과 형식과 동일한 형식입니다. 그리고를 `value_type` 첫 번째와 두 번째 오버 로드에 대 한 반복기의 합니다. 세 번째 오버 로드에 대 한 id 값을 감소의 결과 형식과 같은 형식이 있어야 하지만 다를 수 있습니다는 `value_type` 반복기입니다. 적절 한 값이 없어야 되도록 범위 감소 연산자 `_Range_fun`다양 한 종류의 단일 요소에 적용 된 경우 `value_type` id 값을 형식에서 값의 형식 캐스팅을 처럼 및 `value_type` id 형식에 있습니다.  
  
*_Sym_fun*<br/>
감소의 두 번째에서 사용할 대칭 함수입니다. 자세한 내용은 주의를 참조 하십시오.  
  
*_Range_fun*<br/>
감소의 첫 번째 단계에서 사용할 함수입니다. 자세한 내용은 주의를 참조 하십시오.  
  
### <a name="return-value"></a>반환 값  
 결과 감소입니다.  
  
### <a name="remarks"></a>설명  
 위한 병렬 영역 감소를 수행 하려면 함수는 범위를 기본 스케줄러를 사용할 수 있는 작업자의 수에 따라 청크로 나눕니다. 감소 하면서 두 단계로 이루어집니다, 그리고 첫 번째 단계는 각 청크 안에 감소를 수행 하 고 두 번째 단계 각 청크에서 부분 결과 간의 감소를 수행 합니다.  
  
 첫 번째 오버 로드 해야 하는 반복기 `value_type`, `T`동일 하 게 감소 결과 형식 뿐만 아니라 id 값 형식, 합니다. 요소 유형 T에서 연산자를 제공 해야 `T T::operator + (T)` 각 청크에서 요소를 줄일 수 있습니다. 동일한 연산자는 두 번째 단계 에서도 사용 됩니다.  
  
 두 번째 오버 로드 해야 하는 반복기의 `value_type` 동일 하 게 감소 결과 형식 뿐만 아니라 id 값 형식입니다. 제공 된 이항 연산자 `_Sym_fun` 첫 번째 단계에 대 한 초기 값으로 id 값을 사용 하 여 두 감소 단계에서 사용 됩니다.  
  
 세 번째 오버 로드에 대 한 id 값 형식 해야와 동일 하 게 감소 결과 형식이 아니라 반복기의 `value_type` 다 둘 다를 수 있습니다. 범위 감소 함수의 `_Range_fun` 초기 값 및 이항 함수의 id 값을 사용 하 여 첫 번째 단계에서는 `_Sym_reduce_fun` 결과 두 번째 단계에서는 하위에 적용 됩니다.  
  
##  <a name="parallel_sort"></a>  parallel_sort  
 지정된 범위에 있는 요소를 비내림차순 또는 이진 조건자로 지정한 정렬 기준에 따라 병렬로 정렬합니다. 이 함수는 비교 기반의 불안정한 내부 정렬이라는 점에서 `std::sort`와 의미 체계가 비슷합니다.  
  
```
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```  
  
### <a name="parameters"></a>매개 변수  
*_Random_iterator*<br/>
입력 범위의 반복기 형식입니다.  
  
*_Function*<br/>
이진 비교 구조 함수의 형식입니다.  
  
*시작 (_b)*<br/>
저장할 범위의 첫 번째 요소 위치를 주소 지정하는 임의 액세스 반복기입니다.  
  
*(_E)*<br/>
저장할 범위의 마지막 요소 하나 다음 위치를 주소 지정하는 임의 액세스 반복기입니다.  
  
*_Func*<br/>
순서에 따라 연속적인 요소에 대해 충족될 비교 조건을 정의하는 사용자 정의 조건자 함수 개체입니다. 이진 조건자는 두 개의 인수를 사용하여 조건이 충족되면 `true`를 반환하고, 충족되지 않으면 `false`를 반환합니다. 이 비교 함수는 시퀀스의 요소 쌍에 대해 엄밀히 약한 순서를 적용해야 합니다.  
  
*_Chunk_size*<br/>
병렬 실행을 위해 두 개로 분할될 청크의 최소 크기입니다.  
  
### <a name="remarks"></a>설명  
 첫 번째 오버 로드는 이진 비교 연산자를 사용 하 여 `std::less`입니다.  
  
 두 번째 오버로드는 `bool _Func(T, T)` 시그니처를 포함하는 제공된 이진 비교 연산자를 사용합니다. 여기서 `T`는 입력 범위 요소의 형식입니다.  
  
 알고리즘은 입력 범위를 두 개의 청크로 나누고 이어서 각 청크를 병렬로 실행할 두 개의 하위 청크로 나눕니다. 선택적 인수 `_Chunk_size`를 사용하여 크기가 < `_Chunk_size`인 청크를 직렬로 처리하도록 알고리즘에 지정할 수 있습니다.  
  
##  <a name="parallel_transform"></a>  parallel_transform  
 두 소스 범위에서 요소 쌍에 또는 소스 범위에 있는 각 요소에 지정된 함수 개체를 적용하고 대상 범위에 함수 개체의 반환 값을 병렬로 복사합니다. 이 함수는 `std::transform`과 의미 체계가 같습니다.  
  
```
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
 first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
 first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```  
  
### <a name="parameters"></a>매개 변수  
*_Input_iterator1*<br/>
첫 번째 입력 반복기 또는 유일한 입력 반복기의 형식입니다.  
  
*_Output_iterator*<br/>
출력 반복기의 형식입니다.  
  
*_Unary_operator*<br/>
입력 범위의 각 요소에서 실행될 단항 구조 함수의 형식입니다.  
  
*_Input_iterator2*<br/>
두 번째 입력 반복기의 형식입니다.  
  
*_Binary_operator*<br/>
두 소스 범위의 요소에서 쌍 단위로 실행될 이진 구조 함수의 형식입니다.  
  
*_Partitioner*<br/>
*first1*<br/>
작업을 수행할 첫 번째 소스 범위 또는 유일한 소스 범위의 첫 번째 요소의 위치를 주소 지정하는 입력 반복기입니다.  
  
*last1*<br/>
작업을 수행할 첫 번째 소스 범위 또는 유일한 소스 범위에서 최종 요소의 하나 다음 위치를 주소 지정하는 입력 반복기입니다.  
  
*_Result*<br/>
대상 범위의 첫 번째 요소의 위치를 주소 지정하는 출력 반복기입니다.  
  
*_Unary_op*<br/>
소스 범위의 각 요소에 적용되는 사용자 정의 단항 함수 개체입니다.  
  
*_Part*<br/>
partitioner 개체에 대한 참조입니다. 인수 중 하나일 수 있습니다 `const` [auto_partitioner](auto-partitioner-class.md)`&`합니다 `const` [static_partitioner](static-partitioner-class.md)`&`하십시오 `const` [simple_ 파티 셔 너](simple-partitioner-class.md) `&` 하거나 [affinity_partitioner](affinity-partitioner-class.md) `&` 경우를 [affinity_partitioner](affinity-partitioner-class.md) 개체는, 참조는 비 const l-value 해야 합니다. 알고리즘을 재사용 하 여 향후의 루프에 대 한 상태를 저장할 수 있도록 참조 합니다.  
  
*first2*<br/>
작업을 수행할 두 번째 소스 범위에서 첫 번째 요소의 위치를 주소 지정하는 입력 반복기입니다.  
  
*_Binary_op*<br/>
두 소스 범위에 쌍 단위 정방향으로 적용되는 사용자 정의 이진 함수 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 함수 개체에 의해 변형된 출력 요소를 받는 대상 범위에서 최종 요소의 하나 다음 위치를 주소 지정하는 출력 반복기입니다.  
  
### <a name="remarks"></a>설명  
 [auto_partitioner](auto-partitioner-class.md) 명시적인 partitioner 인수 없이 오버 로드에 사용 됩니다.  
  
 만 지원 하지 않는 임의 반복기 액세스할 [auto_partitioner](auto-partitioner-class.md) 지원 됩니다.  
  
 `_Unary_op` 인수를 사용하는 오버로드는 입력 범위의 각 요소에 단항 구조 함수를 적용하여 입력 범위를 출력 범위로 변환합니다. `_Unary_op`는 `operator()(T)` 시그니처를 포함하는 함수 호출 연산자를 지원해야 합니다. 여기서 `T`는 반복되는 범위의 값 형식입니다.  
  
 `_Binary_op` 인수를 사용하는 오버로드는 첫 번째 입력 범위의 한 요소와 두 번째 입력 범위의 한 요소에 이진 구조 함수를 적용하여 두 개의 입력 범위를 출력 범위로 변환합니다. `_Binary_op`는 `operator()(T, U)` 시그니처를 포함하는 함수 호출 연산자를 지원해야 합니다. 여기서 `T`, `U`는 두 입력 반복기의 값 형식입니다.  
  
 자세한 내용은 [병렬 알고리즘](../../../parallel/concrt/parallel-algorithms.md)합니다.  
  
##  <a name="receive"></a>  receive  
 컨텍스트에서 정확히 한 소스의 데이터를 대기하고 허용되는 값을 필터링할 수 있게 하는 일반 receive 구현입니다.  
  
```
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
페이로드 유형입니다.  
  
*_Src*<br/>
포인터 또는 데이터가 예상 되는 원본에 대 한 참조입니다.  
  
*시간 제한 _t*<br/>
메서드에 없어야 하는 시간 (밀리초)의 데이터에 대해 최대 된 시간입니다.  
  
*_Filter_proc*<br/>
메시지를 허용 해야 하는지 여부를 결정 하는 필터 함수입니다.  
  
### <a name="return-value"></a>반환 값  
 페이로드 형식의 원본에서 사용 되는 값입니다.  
  
### <a name="remarks"></a>설명  
 경우 매개 변수 `_Timeout` 상수가 아닌 값이 `COOPERATIVE_TIMEOUT_INFINITE`, 예외 [operation_timed_out](operation-timed-out-class.md) 지정된 기간 동안 만료 된 메시지가 수신 되기 전에 throw 됩니다. 길이가 0 인 제한 시간을 원하는 경우 사용 해야 합니다 [try_receive](concurrency-namespace-functions.md) 함수를 호출 하는 대신 `receive` 시간 제한은 `0` (제로)으로 효율적 이며 시간 제한 시 예외를 throw 하지 않습니다.  
  
 자세한 내용은 [메시지 전달 함수](../../../parallel/concrt/message-passing-functions.md)합니다.  
  
##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token  
 지정된 취소 토큰의 컨텍스트에서 동기적으로 즉시 함수 개체를 실행합니다.  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>매개 변수  
*_Function*<br/>
호출될 함수 개체의 형식입니다.  
  
*_Func*<br/>
실행될 함수 개체입니다. 이 개체는 void(void)의 시그니처가 있는 함수 호출 연산자를 지원해야 합니다.  
  
*_Ct*<br/>
함수 객체의 암시 취소를 제어하는 취소 토큰입니다. 취소 중인 부모 작업 그룹에서 암시적 취소의 가능성 없이 함수 실행을 원할 경우 `cancellation_token::none()`을 사용합니다.  
  
### <a name="remarks"></a>설명  
 `cancellation_token`가 취소될 때 함수 개체의 중단점이 트리거됩니다. 명시적 토큰 `_Ct`는 부모에 다른 토큰이 있거나 토큰이 없는 경우 부모 취소로부터 `_Func`를 격리합니다.  
  
##  <a name="send"></a>  send  
 대상이 메시지를 수락 또는 거절할 때까지 기다리는 동기 전송 작업입니다.  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
페이로드 유형입니다.  
  
*_Trg*<br/>
포인터 또는 데이터 전송 하는 대상에 대 한 참조입니다.  
  
*(_D)*<br/>
데이터 전송에 대 한 참조입니다.  
  
### <a name="return-value"></a>반환 값  
 `true` 메시지가 허용 된 경우 `false` 그렇지 않은 경우.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [메시지 전달 함수](../../../parallel/concrt/message-passing-functions.md)합니다.  
  
##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>매개 변수  
*_Scheduler*<br/>
앰비언트 스케줄러 설정입니다.
  
##  <a name="set_task_execution_resources"></a>  set_task_execution_resources  
 동시성 런타임 내부 작업자 스레드가 사용하는 실행 리소스를 지정된 선호도 집합으로 제한합니다.  
  
 리소스 관리자가 생성되기 전이나 두 리소스 관리자 수명 사이에만 이 메서드를 호출할 수 있습니다. 리소스 관리자가 호출 시 존재하지 않는 한 여러 번 호출할 수 있습니다. 선호도 제한이 설정된 후에는 다음 유효한 `set_task_execution_resources` 메서드 호출까지 적용된 상태로 유지됩니다.  
  
 제공된 선호도 마스크는 프로세스 선호도 마스크의 하위 집합이 아니어야 합니다. 필요한 경우 프로세스 선호도가 업데이트됩니다.  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>매개 변수  
*_ProcessAffinityMask*<br/>
동시성 런타임의 작업자 스레드를 제한할 선호도 마스크입니다. 동시성 런타임을 현재 프로세서 그룹의 하위 집합으로 제한하려는 경우 하드웨어 스레드 수가 64개보다 많은 시스템에서만 이 메서드를 사용하십시오. 하드웨어 스레드 수가 64개보다 많은 컴퓨터에서는 일반적으로 그룹 선호도 배열을 매개 변수로 사용하는 메서드 버전을 사용해야 합니다.  
  
*count*<br/>
`GROUP_AFFINITY` 매개 변수로 지정된 배열에서 `_PGroupAffinity` 항목의 수입니다.  
  
*_PGroupAffinity*<br/>
`GROUP_AFFINITY` 항목의 배열입니다.  
  
### <a name="remarks"></a>설명  
 메서드에 throw 합니다는 [invalid_operation](invalid-operation-class.md) Resource Manager는 호출 시점에 있는 경우 예외와 [invalid_argument](../../../standard-library/invalid-argument-class.md) 예외에 대 한 선호도의 빈 집합에서 결과 지정 하는 경우 리소스입니다.  
  
 매개 변수로 그룹 선호도 배열을 사용하는 이 메서드 버전은 Windows 7 이상과 운영 체제에서만 사용해야 합니다. 그렇지 않은 경우는 [invalid_operation](invalid-operation-class.md) 예외가 throw 됩니다.  
  
 이 메서드가 호출된 후 프로세스 선호도를 프로그래밍 방식으로 수정하면 리소스 관리자에서 제한된 선호도를 다시 평가하지 않습니다. 따라서 프로세스 선호도에 대한 모든 변경은 이 메서드를 호출하기 전에 해야 합니다.  
  
##  <a name="swap"></a>  swap  
 두 `concurrent_vector` 개체의 요소를 교환합니다.  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
동시 벡터에 저장 된 요소의 데이터 형식입니다.  
  
*_Ax*<br/>
할당자 유형 동시 벡터입니다.  
  
*_A*<br/>
동시 벡터와 교환할 요소가 들어 있는 동시 벡터가 `_B`합니다.  
  
*_B*<br/>
교환할 요소를 제공 하는 동시 벡터 또는 교환할 동시 벡터의 요소가 벡터 `_A`입니다.  
  
### <a name="remarks"></a>설명  
 템플릿 함수는 컨테이너 클래스의 특수화 된 알고리즘 `concurrent_vector` 멤버 함수를 실행 하려면 `_A`합니다. [concurrent_vector:: swap](concurrent-vector-class.md#swap)( `_B`). 이러한 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 템플릿 함수의 일반 버전인 `template <class T> void swap(T&, T&)`, 알고리즘에서 클래스 할당으로 작동 하며 속도가 느린 작업입니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.  
  
 이 메서드는 동시성이 보장 되지 않습니다. 이 메서드를 호출할 때 다른 스레드가 없는 동시 벡터 중 하나에서 작업을 수행 중인 있는지 확인 해야 합니다.  
  
##  <a name="task_from_exception"></a>  task_from_exception  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>매개 변수  
*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>
  
### <a name="return-value"></a>반환 값  
  
##  <a name="task_from_result"></a>  task_from_result  
  
```
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>

*되므로*<br/>

*_TaskOptions*<br/>
  
### <a name="return-value"></a>반환 값  
  
##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name  
 ETW 추적에서 메시지 블록 또는 에이전트에 지정된 이름을 연결합니다.  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
개체의 형식입니다. 일반적으로 메시지 블록 또는 에이전트입니다.  
  
*_PObject*<br/>
추적에 명명된 에이전트 또는 메시지 블록에 대한 포인터입니다.  
  
*이름 (_n)*<br/>
지정된 개체의 이름입니다.  
  
##  <a name="try_receive"></a>  try_receive  
 컨텍스트에서 정확히 한 소스의 데이터를 찾고 허용되는 값을 필터링할 수 있게 하는 일반 try-receive 구현입니다. 데이터가 준비되지 않은 경우 메서드가 false를 반환합니다.  
  
``` 
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```  
  
### <a name="parameters"></a>매개 변수  
*T*<br/>
페이로드 형식  
  
*_Src*<br/>
포인터 또는 데이터가 예상 되는 원본에 대 한 참조입니다.  
  
*이름이 _value*<br/>
결과 배치할 위치에 대 한 참조입니다.  
  
*_Filter_proc*<br/>
메시지를 허용 해야 하는지 여부를 결정 하는 필터 함수입니다.  
  
### <a name="return-value"></a>반환 값  
 A `bool` 페이로드가에 있는지 여부를 나타내는 값 `_value`합니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [메시지 전달 함수](../../../parallel/concrt/message-passing-functions.md)합니다.  
  
##  <a name="wait"></a>  wait  
 지정된 시간 동안 현재 컨텍스트를 일시 중지합니다.  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>매개 변수  
*_Milliseconds*<br/>
현재 컨텍스트가 일시 중지되어야 하는 시간(밀리초)입니다. `_Milliseconds` 매개 변수의 값이 `0`으로 설정된 경우 현재 컨텍스트는 계속하기 전에 다른 실행 가능한 컨텍스트에 실행을 양보해야 합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 동시성 런타임 스케줄러 컨텍스트에서 스케줄러 내부 리소스에서 실행 하는 다른 컨텍스트를 찾을 수 있습니다. 스케줄러는 본질적으로 협조적이기 때문에 이 컨텍스트는 지정된 시간(밀리초) 후에 정확하게 다시 시작할 수 없습니다. 스케줄러가 스케줄러에 협조적으로 양보하지 않는 다른 작업을 실행 중인 경우 대기 기간이 무한할 수 있습니다.  
  
##  <a name="when_all"></a>  when_all  
 인수로 제공된 모든 작업이 성공적으로 완료될 경우 완료되는 작업을 만듭니다.  
  
```
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) -> 
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```   
  
### <a name="parameters"></a>매개 변수  
*_Iterator*<br/>
입력 반복기의 형식입니다.  
  
*시작 (_b)*<br/>
결과 작업으로 결합되는 요소 범위 내 첫 번째 요소의 위치입니다.  
  
*(_E)*<br/>
결과 작업으로 결합되는 요소 범위를 벗어나는 첫 번째 요소의 위치입니다.  
  
*_TaskOptions*<br/>
`task_options` 개체
  
### <a name="return-value"></a>반환 값  
 모든 입력 작업이 성공적으로 완료되는 경우 완료되는 작업입니다. 입력 작업이 `T` 형식이면 이 함수의 출력은 `task<std::vector<T>>`가 됩니다. 입력 작업이 `void` 형식이면 이 함수의 출력 작업도 `task<void>`가 됩니다.  
  
### <a name="remarks"></a>설명  
 `when_all`은 `task`를 해당 결과로 생성하는 비블로킹 함수입니다. 와 달리 [task:: wait](task-class.md#wait), ASTA (응용 프로그램 STA) 스레드에서 UWP 앱에서이 함수를 호출 해도 됩니다.  
  
 반환된 된 작업은 취소 된 상태로 일찍 완료 및 예외를 한 경우 throw 됩니다 호출 하는 경우 작업 중 하나가 취소 되거나 예외를 throw 하는 경우 [task:: get](task-class.md#get) 또는 `task::wait` 해당 작업에서.  
  
 자세한 내용은 [작업 병렬 처리](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)합니다.  
  
##  <a name="when_any"></a>  when_any  
 인수로 제공된 모든 작업이 성공적으로 완료될 경우 완료되는 작업을 만듭니다.  
  
```
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) 
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken) 
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```   
  
### <a name="parameters"></a>매개 변수  
*_Iterator*<br/>
입력 반복기의 형식입니다.  
  
*시작 (_b)*<br/>
결과 작업으로 결합되는 요소 범위 내 첫 번째 요소의 위치입니다.  
  
*(_E)*<br/>
결과 작업으로 결합되는 요소 범위를 벗어나는 첫 번째 요소의 위치입니다.  
  
*_TaskOptions*<br/>
*_CancellationToken*<br/>
반환된 작업의 취소를 제어하는 취소 토큰입니다. 취소 토큰을 제공하지 않으면 결과 작업은 작업의 취소 토큰을 받으므로 완료됩니다.  
  
### <a name="return-value"></a>반환 값  
 두 입력 작업 중 하나라도 성공적으로 완료되는 경우 완료되는 작업입니다. 입력 작업이 `T` 형식이면 이 함수의 출력은 `task<std::pair<T, size_t>>>`이 되며, 여기서 쌍의 첫 번째 요소는 완료되는 작업의 결과이고 두 번째 요소는 완료된 작업의 인덱스입니다. 입력 작업이 `void` 형식이면 출력은 `task<size_t>`이 됩니다. 여기서 결과는 완료되는 작업의 인덱스입니다.  
  
### <a name="remarks"></a>설명  
 `when_any`은 `task`를 해당 결과로 생성하는 비블로킹 함수입니다. 와 달리 [task:: wait](task-class.md#wait), ASTA (응용 프로그램 STA) 스레드에서 UWP 앱에서이 함수를 호출 해도 됩니다.  
  
 자세한 내용은 [작업 병렬 처리](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [concurrency 네임스페이스](concurrency-namespace.md)
