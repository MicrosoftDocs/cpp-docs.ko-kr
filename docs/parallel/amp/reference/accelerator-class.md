---
description: '자세한 정보: accelerator 클래스'
title: accelerator 클래스
ms.date: 11/04/2016
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 3f5c8ba2d68049097acb89e90caf83d92be6f7e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254536"
---
# <a name="accelerator-class"></a>accelerator 클래스

액셀러레이터는 데이터 병렬 컴퓨팅에 최적화 된 하드웨어 기능입니다. 액셀러레이터는 PCIe 버스에 연결 된 장치 (예: GPU) 일 수도 있고, 주 CPU에서 확장 된 명령 집합이 될 수도 있습니다.

## <a name="syntax"></a>구문

```cpp
class accelerator;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[액셀러레이터 키 생성자](#ctor)|`accelerator` 클래스의 새 인스턴스를 초기화합니다.|
|[~ accelerator 소멸자](#ctor)|개체를 소멸 시킵니다 `accelerator` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[create_view](#create_view)|`accelerator_view`이 액셀러레이터 키에 대 한 개체를 만들어 반환 합니다.|
|[get_all](#get_all)|`accelerator`사용 가능한 모든 액셀러레이터 키를 나타내는 개체의 벡터를 반환 합니다.|
|[get_auto_selection_view](#get_auto_selection_view)|자동 선택을 반환 합니다 `accelerator_view` .|
|[get_dedicated_memory](#get_dedicated_memory)|의 전용 메모리 (kb)를 반환 합니다 `accelerator` .|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|이 액셀러레이터에 생성 된 버퍼에 대 한 기본 [access_type](concurrency-namespace-enums-amp.md#access_type) 을 반환 합니다.|
|[get_default_view](#get_default_view)|와 연결 된 기본 개체를 반환 합니다 `accelerator_view` `accelerator` .|
|[get_description](#get_description)|장치에 대 한 간단한 설명을 반환 합니다 `accelerator` .|
|[get_device_path](#get_device_path)|장치의 경로를 반환 합니다.|
|[get_has_display](#get_has_display)|`accelerator`가 디스플레이에 연결 되어 있는지 여부를 확인 합니다.|
|[get_is_debug](#get_is_debug)|에 `accelerator` 확장 오류 보고를 위해 디버그 계층이 사용 하도록 설정 되어 있는지 여부를 확인 합니다.|
|[get_is_emulated](#get_is_emulated)|이 에뮬레이션 되었는지 여부를 확인 `accelerator` 합니다.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|에서 `accelerator` 공유 메모리를 지원 하는지 여부를 확인 합니다.|
|[get_supports_double_precision](#get_supports_double_precision)|`accelerator`가 디스플레이에 연결 되어 있는지 여부를 확인 합니다.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|에서 `accelerator` 이중 정밀도 수치를 제한적으로 지원 하는지 여부를 확인 합니다.|
|[get_version](#get_version)|의 버전을 반환 합니다 `accelerator` .|
|[set_default](#set_default)|기본 액셀러레이터 키의 경로를 반환 합니다.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|이에서 만든 배열 및 암시적 메모리 할당에 대 한 기본 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)를 설정 합니다 `accelerator` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자! =](#operator_neq)|이 `accelerator` 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`false`** , 그렇지 않으면를 반환 **`true`** 합니다.|
|[연산자 =](#operator_eq)|지정 된 개체의 내용을 `accelerator` 이 개체에 복사 합니다.|
|[연산자 = =](#operator_eq_eq)|이 `accelerator` 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`true`** , 그렇지 않으면를 반환 **`false`** 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|CPU에 대 한 문자열 상수를 가져옵니다 `accelerator` .|
|[dedicated_memory](#dedicated_memory)|의 전용 메모리를 `accelerator` 킬로바이트 단위로 가져옵니다.|
|[default_accelerator](#default_accelerator)|기본값에 대 한 문자열 상수를 가져옵니다 `accelerator` .|
|[default_cpu_access_type](#default_cpu_access_type)|이에서 만든 배열 및 암시적 메모리 할당에 대 한 기본 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)을 가져오거나 설정 합니다 `accelerator` .|
|[default_view](#default_view)|와 연결 된 기본 개체를 가져옵니다 `accelerator_view` `accelerator` .|
|[description](#description)|장치에 대 한 간단한 설명을 가져옵니다 `accelerator` .|
|[device_path](#device_path)|장치의 경로를 가져옵니다.|
|[direct3d_ref](#direct3d_ref)|Direct3D 참조에 대 한 문자열 상수를 가져옵니다 `accelerator` .|
|[direct3d_warp](#direct3d_warp)|`accelerator`SSE (스트리밍 SIMD 확장)를 사용 하는 다중 코어 cpu에서 C++ AMP 코드를 실행 하는 데 사용할 수 있는 개체에 대 한 문자열 상수를 가져옵니다.|
|[has_display](#has_display)|가 디스플레이에 연결 되어 있는지 여부를 나타내는 부울 값을 가져옵니다 `accelerator` .|
|[is_debug](#is_debug)|에 `accelerator` 확장 오류 보고를 위해 디버그 계층이 사용 하도록 설정 되어 있는지 여부를 나타냅니다.|
|[is_emulated](#is_emulated)|이 에뮬레이션 되었는지 여부를 나타냅니다 `accelerator` .|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|에서 공유 메모리를 지원 하는지 여부를 나타냅니다 `accelerator` .|
|[supports_double_precision](#supports_double_precision)|액셀러레이터 키가 이중 정밀도 수치를 지원 하는지 여부를 나타냅니다.|
|[supports_limited_double_precision](#supports_limited_double_precision)|액셀러레이터 키가 이중 정밀도 수치를 제한적으로 지원 하는지 여부를 나타냅니다.|
|[version](#version)|`accelerator`의 버전을 가져옵니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`accelerator`

## <a name="remarks"></a>설명

액셀러레이터는 데이터 병렬 컴퓨팅에 최적화 된 하드웨어 기능입니다. 액셀러레이터는 종종 불연속 GPU 이지만 DirectX 참조 장치, 구부리기 (SSE 명령을 통해 가속화 된 CPU 측 장치) 또는 CPU 자체와 같은 가상 호스트 측 엔터티가 될 수도 있습니다.

`accelerator`사용 가능한 장치를 열거 하거나 기본 장치, 참조 장치 또는 구부리기 장치를 가져와서 개체를 생성할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** amprt. h

**네임스페이스:** 동시성

## <a name="a-accelerator"></a><a name="dtor"></a></a> ~ accelerator

개체를 소멸 시킵니다 `accelerator` .

```cpp
~accelerator();
```

### <a name="return-value"></a>반환 값

## <a name="accelerator"></a><a name="ctor"></a> accelerator

[Accelerator 클래스](accelerator-class.md)의 새 인스턴스를 초기화 합니다.

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>매개 변수

*_Device_path*<br/>
물리적 장치의 경로입니다.

*_Other*<br/>
복사할 액셀러레이터입니다.

## <a name="cpu_accelerator"></a><a name="cpu_accelerator"></a> cpu_accelerator

CPU 엑셀러레이터에 대한 문자열 상수를 가져옵니다.

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a><a name="create_view"></a> create_view

지정된 큐 모드를 사용하여 이 액셀러레이터에서 `accelerator_view` 개체를 만들고 반환합니다. 큐 모드를 지정 하지 않으면 새는 `accelerator_view` [queuing_mode:: 즉각적인](concurrency-namespace-enums-amp.md#queuing_mode) 큐 모드를 사용 합니다.

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>매개 변수

*qmode*<br/>
큐 모드입니다.

### <a name="return-value"></a>반환 값

지정된 큐 모드를 사용하는 이 액셀러레이터의 새로운 `accelerator_view` 개체입니다.

## <a name="dedicated_memory"></a><a name="dedicated_memory"></a> dedicated_memory

의 전용 메모리를 `accelerator` 킬로바이트 단위로 가져옵니다.

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a><a name="default_accelerator"></a> default_accelerator

기본값에 대 한 문자열 상수를 가져옵니다 `accelerator` .

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a><a name="default_cpu_access_type"></a> default_cpu_access_type

이에서 만든 배열 및 암시적 메모리 할당에 대 한 기본 cpu [access_type](concurrency-namespace-enums-amp.md#access_type) `accelerator` 입니다.

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a><a name="default_view"></a> default_view

와 연결 된 기본 액셀러레이터 뷰를 가져옵니다 `accelerator` .

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a><a name="description"></a> 한

장치에 대 한 간단한 설명을 가져옵니다 `accelerator` .

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a><a name="device_path"></a> device_path

액셀러레이터의 경로를 가져옵니다. 이 경로는 시스템에서 고유합니다.

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a><a name="direct3d_ref"></a> direct3d_ref

Direct3D 참조 엑셀러레이터에 대한 문자열 상수를 가져옵니다.

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a><a name="direct3d_warp"></a> direct3d_warp

`accelerator`SSE (스트리밍 SIMD 확장)를 사용 하 여 다중 코어 cpu에서 C++ AMP 코드를 실행 하는 데 사용할 수 있는 개체에 대 한 문자열 상수를 가져옵니다.

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a><a name="get_all"></a> get_all

`accelerator`사용 가능한 모든 액셀러레이터 키를 나타내는 개체의 벡터를 반환 합니다.

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>반환 값

사용할 수 있는 액셀러레이터의 벡터

## <a name="get_auto_selection_view"></a><a name="get_auto_selection_view"></a> get_auto_selection_view

런타임에 의해 자동으로 선택 될 parallel_for_each 커널을 실행 하기 위한 대상 accelerator_view parallel_for_each 대상으로 지정 되는 경우 자동 선택 accelerator_view을 반환 합니다. 다른 모든 용도에 대해이 메서드에서 반환 하는 accelerator_view는 기본 액셀러레이터 키의 기본 accelerator_view와 동일 합니다.

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>반환 값

자동 선택 accelerator_view입니다.

## <a name="get_dedicated_memory"></a><a name="get_dedicated_memory"></a> get_dedicated_memory

의 전용 메모리 (kb)를 반환 합니다 `accelerator` .

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>반환 값

`accelerator`를 위해 전용된 메모리(킬로바이트)입니다.

## <a name="get_default_cpu_access_type"></a><a name="get_default_cpu_access_type"></a> get_default_cpu_access_type

이 액셀러레이터에 생성 된 버퍼에 대 한 기본 cpu access_type 가져옵니다.

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>반환 값

이 가속기에서 만든 버퍼에 대 한 기본 cpu access_type입니다.

## <a name="get_default_view"></a><a name="get_default_view"></a> get_default_view

와 연결 된 기본 개체를 반환 합니다 `accelerator_view` `accelerator` .

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>반환 값

`accelerator_view`와 연결된 기본 `accelerator` 개체입니다.

## <a name="get_description"></a><a name="get_description"></a> get_description

장치에 대 한 간단한 설명을 반환 합니다 `accelerator` .

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>반환 값

`accelerator` 디바이스에 대한 간단한 설명입니다.

## <a name="get_device_path"></a><a name="get_device_path"></a> get_device_path

액셀러레이터 키의 경로를 반환 합니다. 이 경로는 시스템에서 고유합니다.

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>반환 값

시스템 차원의 고유한 장치 인스턴스 경로입니다.

## <a name="get_has_display"></a><a name="get_has_display"></a> get_has_display

가 디스플레이에 출력할 수 있는지 여부를 나타내는 부울 값을 반환 합니다 `accelerator` .

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>반환 값

**`true`** 가 `accelerator` 표시에 출력 될 수 있으면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="get_is_debug"></a><a name="get_is_debug"></a> get_is_debug

에 `accelerator` 확장 오류 보고를 위해 디버그 계층이 사용 하도록 설정 되어 있는지 여부를 확인 합니다.

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>반환 값

**`true`** 에 `accelerator` 확장 오류 보고를 위해 디버그 계층이 사용 하도록 설정 되어 있으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="get_is_emulated"></a><a name="get_is_emulated"></a> get_is_emulated

이 에뮬레이션 되었는지 여부를 확인 `accelerator` 합니다.

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>반환 값

**`true`**`accelerator`가 에뮬레이트된 경우입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="get_supports_cpu_shared_memory"></a><a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory

액셀러레이터는 액셀러레이터와 CPU 모두에서 액세스할 수 있는 메모리를 지원 하는지 여부를 나타내는 부울 값을 반환 합니다.

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>반환 값

**`true`** 가속기가 CPU 공유 메모리를 지 원하는 경우 그렇지 않으면 **`false`** 입니다.

## <a name="get_supports_double_precision"></a><a name="get_supports_double_precision"></a> get_supports_double_precision

액셀러레이터는 FMA (퓨즈 곱하기 추가), 나누기, 상호 간의 캐스트 및와 간의 캐스트를 비롯 한 배정밀도 수치를 지원 하는지 여부를 나타내는 부울 값을 반환 합니다. **`int`****`double`**

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>반환 값

**`true`** 액셀러레이터 키가 이중 정밀도 수치를 지원 하면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="get_supports_limited_double_precision"></a><a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision

액셀러레이터가 이중 정밀도 수치를 제한적으로 지원하는지 여부를 나타내는 부울 값을 반환합니다. 액셀러레이터 키가 제한적 으로만 지원 되는 경우 및 간에 FMA (퓨즈 곱하기 추가), 나누기, 상호 캐스트 및 **`int`** 캐스팅이 **`double`** 지원 되지 않습니다.

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>반환 값

**`true`** 액셀러레이터 키가 이중 정밀도 수치를 제한적으로 지 원하는 경우 그렇지 않으면 **`false`** 입니다.

## <a name="get_version"></a><a name="get_version"></a> get_version

의 버전을 반환 합니다 `accelerator` .

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>반환 값

`accelerator`의 버전입니다.

## <a name="has_display"></a><a name="has_display"></a> has_display

가 디스플레이에 출력할 수 있는지 여부를 나타내는 부울 값을 가져옵니다 `accelerator` .

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a><a name="is_debug"></a> is_debug

에 `accelerator` 확장 오류 보고를 위해 디버그 계층이 사용 하도록 설정 되어 있는지 여부를 나타내는 부울 값을 가져옵니다.

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a><a name="is_emulated"></a> is_emulated

가 에뮬레이트된 인지 여부를 나타내는 부울 값을 가져옵니다 `accelerator` .

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator"></a><a name="operator_neq"></a> 연산자! =

이 `accelerator` 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`false`** , 그렇지 않으면를 반환 **`true`** 합니다.

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
이것과 비교할 `accelerator` 개체입니다.

### <a name="return-value"></a>반환 값

**`false`** 두 `accelerator` 개체가 같으면이 고, 그렇지 않으면 **`true`** 입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

지정 된 개체의 내용을 `accelerator` 이 개체에 복사 합니다.

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
`accelerator`복사할 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `accelerator` 입니다.

## <a name="operator"></a><a name="operator_eq_eq"></a> 연산자 = =

이 `accelerator` 개체를 다른 개체와 비교 하 고 같으면를 반환 하 고 **`true`** , 그렇지 않으면를 반환 **`false`** 합니다.

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
이것과 비교할 `accelerator` 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 다른 `accelerator` 개체가이 개체와 같으면이 고 `accelerator` , 그렇지 않으면 **`false`** 입니다.

## <a name="set_default"></a><a name="set_default"></a> set_default

기본 액셀러레이터를 암시적으로 사용 하는 모든 작업에 사용할 기본 액셀러레이터를 설정 합니다. 이 메서드는 기본적으로 기본 액셀러레이터를 사용 하는 작업에서 런타임에 선택한 기본 액셀러레이터 키가 아직 사용 되지 않은 경우에만 성공 합니다.

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>매개 변수

*_Path*<br/>
액셀러레이터 키의 경로입니다.

### <a name="return-value"></a>반환 값

**`true`** 기본 액셀러레이터 키 설정에 대 한 호출이 성공 하면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="set_default_cpu_access_type"></a><a name="set_default_cpu_access_type"></a> set_default_cpu_access_type

이 액셀러레이터 키에 생성 된 array_views의 일부로 암시적 메모리 할당에 대해이 액셀러레이터에 생성 된 배열에 대 한 기본 cpu access_type 설정 합니다. 이 메서드는 액셀러레이터에 대 한 default_cpu_access_type이이 메서드에 대 한 이전 호출에 의해 재정의 되지 않은 경우에만 성공 하 고,이 액셀러레이터에 대해 선택한 default_cpu_access_type 런타임이 아직 배열을 할당 하는 데 사용 되지 않았거나이 액셀러레이터에서 액세스 한 array_view를 지 원하는 암시적 메모리 할당에 대해 아직 사용 되지 않은 경우에만 성공 합니다.

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>매개 변수

*_Default_cpu_access_type*<br/>
이 액셀러레이터 키에 대 한 배열/array_view 메모리 할당에 사용 되는 기본 cpu access_type입니다.

### <a name="return-value"></a>반환 값

액셀러레이터 키에 대 한 기본 cpu access_type 성공적으로 설정 되었는지 여부를 나타내는 부울 값입니다.

## <a name="supports_cpu_shared_memory"></a><a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory

에서 공유 메모리를 지원 하는지 여부를 나타내는 부울 값을 가져옵니다 `accelerator` .

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a><a name="supports_double_precision"></a> supports_double_precision

액셀러레이터가 배정밀도 수치를 지원하는지 여부를 나타내는 부울 값을 가져옵니다.

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a><a name="supports_limited_double_precision"></a> supports_limited_double_precision

액셀러레이터 키가 이중 정밀도 수치를 제한적으로 지원 하는지 여부를 나타내는 부울 값을 가져옵니다. 액셀러레이터 키가 제한적 으로만 지원 되는 경우 및 간에 FMA (퓨즈 곱하기 추가), 나누기, 상호 캐스트 및 **`int`** 캐스팅이 **`double`** 지원 되지 않습니다.

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a><a name="version"></a> 버전

`accelerator`의 버전을 가져옵니다.

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
