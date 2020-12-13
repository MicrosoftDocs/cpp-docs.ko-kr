---
description: '자세히 알아보기: 동시성 네임 스페이스 상수'
title: 동시성 네임 스페이스 상수
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::AgentEventGuid
- concrt/concurrency::COOPERATIVE_TIMEOUT_INFINITE
- concrt/concurrency::COOPERATIVE_WAIT_TIMEOUT
- concrt/concurrency::ConcRTEventGuid
- concrt/concurrency::ConcRT_ProviderGuid
- concrt/concurrency::INHERIT_THREAD_PRIORITY
- concrt/concurrency::LockEventGuid
- concrt/concurrency::PPLParallelForEventGuid
- concrt/concurrency::PPLParallelForeachEventGuid
- concrt/concurrency::ResourceManagerEventGuid
- concrt/concurrency::ScheduleGroupEventGuid
- concrt/concurrency::VirtualProcessorEventGuid
ms.assetid: 6f81fc4c-b10c-479e-8717-9c292360d5a0
ms.openlocfilehash: 281c8d41ec21d62eb15e58f792093b30f206dd00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331312"
---
# <a name="concurrency-namespace-constants"></a>동시성 네임 스페이스 상수

:::row:::
   :::column span="":::
      [`AgentEventGuid`](#agenteventguid)\
      [`CONCRT_RM_VERSION_1`](#concrt_rm_version_1)\
      [`COOPERATIVE_TIMEOUT_INFINITE`](#cooperative_timeout_infinite)\
      [`COOPERATIVE_WAIT_TIMEOUT`](#cooperative_wait_timeout)\
      [`ChoreEventGuid`](#choreeventguid)\
      [`ConcRTEventGuid`](#concrteventguid)
   :::column-end:::
   :::column span="":::
      [`ConcRT_ProviderGuid`](#concrt_providerguid)\
      [`ContextEventGuid`](#contexteventguid)\
      [`INHERIT_THREAD_PRIORITY`](#inherit_thread_priority)\
      [`LockEventGuid`](#lockeventguid)\
      [`MaxExecutionResources`](#maxexecutionresources)\
      [`PPLParallelForEventGuid`](#pplparallelforeventguid)
   :::column-end:::
   :::column span="":::
      [`PPLParallelForeachEventGuid`](#pplparallelforeacheventguid)\
      [`PPLParallelInvokeEventGuid`](#pplparallelinvokeeventguid)\
      [`ResourceManagerEventGuid`](#resourcemanagereventguid)\
      [`ScheduleGroupEventGuid`](#schedulegroupeventguid)\
      [`SchedulerEventGuid`](#schedulereventguid)\
      [`VirtualProcessorEventGuid`](#virtualprocessoreventguid)
   :::column-end:::
:::row-end:::

## <a name="agenteventguid"></a><a name="agenteventguid"></a> AgentEventGuid

동시성 런타임의 에이전트 라이브러리에서 발생하는 ETW 이벤트를 설명하는 범주 GUID({B9B5B78C-0713-4898-A21A-C67949DCED07})입니다.

```cpp
const __declspec(selectany) GUID AgentEventGuid = {0xb9b5b78c, 0x713, 0x4898, { 0xa2, 0x1a, 0xc6, 0x79, 0x49, 0xdc, 0xed, 0x7 } };
```

## <a name="choreeventguid"></a><a name="choreeventguid"></a> ChoreEventGuid

작업 또는 태스크와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID ChoreEventGuid =
    { 0x7E854EC7, 0xCDC4, 0x405a, { 0xB5, 0xB2, 0xAA, 0xF7, 0xC9, 0xE7, 0xD4, 0x0C } };
```

### <a name="remarks"></a>설명

이 이벤트 범주는 현재 동시성 런타임에서 발생 하지 않습니다.

## <a name="concrt_providerguid"></a><a name="concrt_providerguid"></a> ConcRT_ProviderGuid

동시성 런타임에 대한 ETW 공급자 GUID입니다.

```cpp
const __declspec(selectany) GUID ConcRT_ProviderGuid =
    { 0xF7B697A3, 0x4DB5, 0x4d3b, { 0xBE, 0x71, 0xC4, 0xD2, 0x84, 0xE6, 0x59, 0x2F } };
```

## <a name="concrt_rm_version_1"></a><a name="concrt_rm_version_1"></a> CONCRT_RM_VERSION_1

Visual Studio 2010에서 정의된 리소스 관리자 인터페이스의 지원을 나타냅니다.

```cpp
const unsigned int CONCRT_RM_VERSION_1 = 0x00010000;
```

## <a name="concrteventguid"></a><a name="concrteventguid"></a> ConcRTEventGuid

다른 범주에서 보다 구체적으로 설명되지 않은, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID ConcRTEventGuid =
    { 0x72B14A7D, 0x704C, 0x423e, { 0x92, 0xF8, 0x7E, 0x6D, 0x64, 0xBC, 0xB9, 0x2A } };
```

### <a name="remarks"></a>설명

이 이벤트 범주는 현재 동시성 런타임에서 발생 하지 않습니다.

## <a name="cooperative_timeout_infinite"></a><a name="cooperative_timeout_infinite"></a> COOPERATIVE_TIMEOUT_INFINITE

대기 시간이 초과되지 않아야 함을 나타내는 값입니다.

```cpp
const unsigned int COOPERATIVE_TIMEOUT_INFINITE = (unsigned int)-1;
```

## <a name="cooperative_wait_timeout"></a><a name="cooperative_wait_timeout"></a> COOPERATIVE_WAIT_TIMEOUT

대기 시간이 초과되었음을 나타내는 값입니다.

```cpp
const size_t COOPERATIVE_WAIT_TIMEOUT = SIZE_MAX;
```

## <a name="contexteventguid"></a><a name="contexteventguid"></a> ContextEventGuid

컨텍스트와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID ContextEventGuid =
    { 0x5727A00F, 0x50BE, 0x4519, { 0x82, 0x56, 0xF7, 0x69, 0x98, 0x71, 0xFE, 0xCB } };
```

## <a name="inherit_thread_priority"></a><a name="inherit_thread_priority"></a> INHERIT_THREAD_PRIORITY

스케줄러의 모든 컨텍스트에 대한 스레드 우선순위가 스케줄러를 만든 스레드의 우선순위와 같아야 함을 나타내는 정책 키 `ContextPriority`에 대한 특수 값입니다.

```cpp
const unsigned int INHERIT_THREAD_PRIORITY = 0x0000F000;
```

## <a name="lockeventguid"></a><a name="lockeventguid"></a> LockEventGuid

잠금과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID LockEventGuid =
    { 0x79A60DC6, 0x5FC8, 0x4952, { 0xA4, 0x1C, 0x11, 0x63, 0xAE, 0xEC, 0x5E, 0xB8 } };
```

### <a name="remarks"></a>설명

이 이벤트 범주는 현재 동시성 런타임에서 발생 하지 않습니다.

## <a name="maxexecutionresources"></a><a name="maxexecutionresources"></a> MaxExecutionResources

정책 키 `MinConcurrency` 및 `MaxConcurrency`에 대한 특수 값입니다. 기본값은 다른 제약 조건이 없는 경우 컴퓨터의 하드웨어 스레드 수입니다.

```cpp
const unsigned int MaxExecutionResources = 0xFFFFFFFF;
```

## <a name="pplparallelforeventguid"></a><a name="pplparallelforeventguid"></a> PPLParallelForEventGuid

`parallel_for` 함수 사용과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID PPLParallelForEventGuid =
    { 0x31c8da6b, 0x6165, 0x4042, { 0x8b, 0x92, 0x94, 0x9e, 0x31, 0x5f, 0x4d, 0x84 } };
```

## <a name="pplparallelforeacheventguid"></a><a name="pplparallelforeacheventguid"></a> PPLParallelForeachEventGuid

`parallel_for_each` 함수 사용과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID PPLParallelForeachEventGuid =
    { 0x5cb7d785, 0x9d66, 0x465d, { 0xba, 0xe1, 0x46, 0x11, 0x6, 0x1b, 0x54, 0x34 } };
```

## <a name="pplparallelinvokeeventguid"></a><a name="pplparallelinvokeeventguid"></a> PPLParallelInvokeEventGuid

`parallel_invoke` 함수 사용과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID PPLParallelInvokeEventGuid =
    { 0xd1b5b133, 0xec3d, 0x49f4, { 0x98, 0xa3, 0x46, 0x4d, 0x1a, 0x9e, 0x46, 0x82 } };
```

## <a name="resourcemanagereventguid"></a><a name="resourcemanagereventguid"></a> ResourceManagerEventGuid

리소스 관리자와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID ResourceManagerEventGuid =
    { 0x2718D25B, 0x5BF5, 0x4479, { 0x8E, 0x88, 0xBA, 0xBC, 0x64, 0xBD, 0xBF, 0xCA } };
```

### <a name="remarks"></a>설명

이 이벤트 범주는 현재 동시성 런타임에서 발생 하지 않습니다.

## <a name="schedulegroupeventguid"></a><a name="schedulegroupeventguid"></a> ScheduleGroupEventGuid

일정 그룹과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID ScheduleGroupEventGuid =
    { 0xE8A3BF1F, 0xA86B, 0x4390, { 0x9C, 0x60, 0x53, 0x90, 0xB9, 0x69, 0xD2, 0x2C } };
```

### <a name="remarks"></a>설명

이 이벤트 범주는 현재 동시성 런타임에서 발생 하지 않습니다.

## <a name="schedulereventguid"></a><a name="schedulereventguid"></a> SchedulerEventGuid

스케줄러 작업과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID SchedulerEventGuid =
    { 0xE2091F8A, 0x1E0A, 0x4731, { 0x84, 0xA2, 0x0D, 0xD5, 0x7C, 0x8A, 0x52, 0x61 } };
```

## <a name="virtualprocessoreventguid"></a><a name="virtualprocessoreventguid"></a> VirtualProcessorEventGuid

가상 프로세서와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.

```cpp
const __declspec(selectany) GUID VirtualProcessorEventGuid =
    { 0x2f27805f, 0x1676, 0x4ecc, { 0x96, 0xfa, 0x7e, 0xb0, 0x9d, 0x44, 0x30, 0x2f } };
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
