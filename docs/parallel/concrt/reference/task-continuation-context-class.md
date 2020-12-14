---
description: Task_continuation_context 클래스에 대해 자세히 알아보세요.
title: task_continuation_context 클래스
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ff843a84dd3e0bdaeee9df99e91b1708116191d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188302"
---
# <a name="task_continuation_context-class"></a>task_continuation_context 클래스

`task_continuation_context` 클래스를 사용하면 연속 실행 위치를 지정할 수 있습니다. Windows 런타임 앱에서이 클래스를 사용 하는 경우에만 유용 합니다. Windows 런타임 않는 앱의 경우 작업 연속의 실행 컨텍스트는 런타임에 의해 결정 되며 구성할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|현재 winrt 스레드 컨텍스트를 나타내는 작업 연속 컨텍스트 개체를 반환 합니다.|
|[use_arbitrary](#use_arbitrary)|런타임이 연속에 대한 실행 컨텍스트를 선택할 수 있는 작업 연속 컨텍스트를 만듭니다.|
|[use_current](#use_current)|현재 실행 컨텍스트를 나타내는 작업 연속 컨텍스트 개체를 반환합니다.|
|[use_default](#use_default)|기본 작업 연속 컨텍스트를 만듭니다.|
|[use_synchronous_execution](#use_synchronous_execution)|동기 실행 컨텍스트를 나타내는 작업 연속 컨텍스트 개체를 반환 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>요구 사항

**헤더:** ppltasks.h

**네임 스페이스:** 동시성

## <a name="get_current_winrt_context"></a><a name="get_current_winrt_context"></a> get_current_winrt_context

현재 WinRT 스레드 컨텍스트를 나타내는 작업 연속 컨텍스트 개체를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>Return Value

현재 Windows 런타임 스레드 컨텍스트입니다. Windows 런타임 되지 않은 컨텍스트에서 호출 되는 경우 빈 task_continuation_context을 반환 합니다.

### <a name="remarks"></a>설명

`get_current_winrt_context`메서드는 호출자의 Windows 런타임 스레드 컨텍스트를 캡처합니다. Windows 런타임 아닌 호출자에 게 빈 컨텍스트를 반환 합니다.

에서 반환 되는 값은 `get_current_winrt_context` 선행 작업이 아파트를 인식 하는지 여부에 관계 없이 캡처된 컨텍스트 (STA VS MTA)의 아파트 모델에서 연속 작업이 실행 되어야 함을 런타임에 나타내는 데 사용할 수 있습니다. 아파트 인식 작업은 Windows 런타임 `IAsyncInfo` 인터페이스 또는 이러한 작업의 하위 작업을의 래핑을 해제 하는 작업입니다.

이 메서드는  `use_current` 메서드와 유사 하지만 c + +/cx 확장을 지원 하지 않는 네이티브 c + + 코드에도 사용할 수 있습니다. 네이티브 및 Windows 런타임 호출자를 위한 c + +/CX-agnostic 라이브러리 코드를 작성 하는 고급 사용자를 위한 것입니다. 이 기능이 필요 하지 않은 경우 `use_current` 에는 c + +/cx 클라이언트만 사용할 수 있는 메서드를 사용 하는 것이 좋습니다.

## <a name="use_arbitrary"></a><a name="use_arbitrary"></a> use_arbitrary

런타임이 연속에 대한 실행 컨텍스트를 선택할 수 있는 작업 연속 컨텍스트를 만듭니다.

### <a name="syntax"></a>구문

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Return Value

임의의 위치를 나타내는 작업 연속 컨텍스트입니다.

### <a name="remarks"></a>설명

이 연속 컨텍스트를 사용 하는 경우 선행 작업이 아파트를 인식 하는 경우에도 연속 작업이 실행 되는 컨텍스트에서 실행 됩니다.

`use_arbitrary` 는 STA에서 만든 아파트 인식 작업에 대 한 연속 작업의 기본 동작을 해제 하는 데 사용할 수 있습니다.

이 메서드는 Windows 런타임 앱 에서만 사용할 수 있습니다.

## <a name="use_current"></a><a name="use_current"></a> use_current

현재 실행 컨텍스트를 나타내는 작업 연속 컨텍스트 개체를 반환합니다.

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>반환 값

현재 실행 컨텍스트입니다.

### <a name="remarks"></a>설명

이 메서드는 올바른 아파트에서 연속 작업을 실행할 수 있도록 호출자의 Windows 런타임 컨텍스트를 캡처합니다.

에서 반환 되는 값을 사용 하 여 `use_current` 선행 작업이 아파트를 인식 하는지 여부에 관계 없이 캡처된 컨텍스트 (STA VS MTA)에서 연속 작업이 실행 되도록 런타임에를 나타낼 수 있습니다. 아파트 인식 작업은 Windows 런타임 `IAsyncInfo` 인터페이스 또는 이러한 작업의 하위 작업을의 래핑을 해제 하는 작업입니다.

이 메서드는 Windows 런타임 앱 에서만 사용할 수 있습니다.

## <a name="use_default"></a><a name="use_default"></a> use_default

기본 작업 연속 컨텍스트를 만듭니다.

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>반환 값

기본 연속 컨텍스트입니다.

### <a name="remarks"></a>설명

메서드를 호출할 때 연속 컨텍스트를 지정 하지 않는 경우 기본 컨텍스트가 사용 됩니다 `then` . Windows 7 이하의 windows 응용 프로그램 및 Windows 8 이상에서 데스크톱 응용 프로그램의 경우 런타임은 작업 연속이 실행 되는 위치를 결정 합니다. 그러나 Windows 런타임 된 앱에서 아파트 인식 작업에 대 한 연속 작업의 기본 연속 컨텍스트는가 호출 되는 아파트입니다 `then` .

아파트 인식 작업은 Windows 런타임 `IAsyncInfo` 인터페이스 또는 이러한 작업의 하위 작업을의 래핑을 해제 하는 작업입니다. 따라서 Windows 런타임 STA에서 아파트 인식 작업에 대 한 연속 작업을 예약 하는 경우 연속 작업이 해당 STA에서 실행 됩니다.

아파트를 인식 하지 않는 작업에 대 한 연속은 런타임에서 선택 하는 컨텍스트에서 실행 됩니다.

## <a name="task_continuation_contextuse_synchronous_execution"></a><a name="use_synchronous_execution"></a> task_continuation_context:: use_synchronous_execution

동기 실행 컨텍스트를 나타내는 작업 연속 컨텍스트 개체를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>Return Value

동기 실행 컨텍스트입니다.

### <a name="remarks"></a>설명

`use_synchronous_execution`메서드는 연속 작업이 컨텍스트에서 동기적으로 실행 되도록 하 여 선행 작업의 완료를 발생 시킵니다.

연속 작업이 연결 될 때 선행 작업이 이미 완료 된 경우 연속 작업은 연속 작업을 연결 하는 컨텍스트에서 동기적으로 실행 됩니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
