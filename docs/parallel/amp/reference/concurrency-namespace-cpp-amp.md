---
description: '자세한 정보: Concurrency 네임 스페이스 (C++ AMP)'
title: Concurrency 네임스페이스(C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 9334634dc3d332b24f067c04f00e82feea5a6001
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342584"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 네임스페이스(C++ AMP)

데이터 병렬 하드웨어에서 c + + 코드의 실행 속도를 가속화 하는 클래스와 함수를 제공 합니다. 자세한 내용은 [C++ AMP 개요](../cpp-amp-overview.md) 를 참조 하세요.

## <a name="syntax"></a>구문

```cpp
namespace Concurrency;
```

## <a name="members"></a>멤버

### <a name="namespaces"></a>네임스페이스

|Name|설명|
|----------|-----------------|
|[Concurrency::direct3d 네임스페이스](concurrency-direct3d-namespace.md)|는 D3D 상호 운용성을 지 원하는 함수를 제공 합니다. 중복 된 중간 복사본을 만들지 않고 AMP 코드에서 계산을 위해 D3D 리소스를 원활 하 게 사용 하 고 D3D 코드의 AMP에서 만든 리소스를 사용할 수 있습니다. C++ AMP를 사용 하 여 DirectX 응용 프로그램의 계산 집약적인 섹션을 점차적으로 가속화 하 고 AMP 계산에서 생성 된 데이터에 대해 D3D API를 사용할 수 있습니다.|
|[Concurrency::fast_math 네임스페이스](concurrency-fast-math-namespace.md)|`fast_math`네임 스페이스의 함수는 C99 규격이 아닙니다. 각 함수의 단 정밀도 버전만 제공 됩니다. 이러한 함수는 DirectX 내장 함수를 사용 합니다 .이 함수는 네임 스페이스의 해당 함수 보다 빠르지만 `precise_math` 액셀러레이터에 대 한 확장 된 배정밀도 지원이 필요 하지 않지만 정확도가 떨어집니다. C99 코드와의 소스 수준 호환성을 위한 각 함수에는 두 가지 버전이 있습니다. 두 버전 모두 단일 전체 자릿수 값을 사용 하 고 반환 합니다.|
|[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)|그래픽 프로그래밍을 위해 디자인 된 형식 및 함수를 제공 합니다.|
|[동시성::p recise_math 네임 스페이스](concurrency-precise-math-namespace.md)|`precise_math`네임 스페이스의 함수는 C99 규격입니다. 각 함수의 단 정밀도와 배정밀도 버전이 모두 포함 됩니다. 단 정밀도 함수를 포함 하는 이러한 함수에는 액셀러레이터에 대 한 확장 된 배정밀도 지원이 필요 합니다.|

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[accelerator 클래스](accelerator-class.md)|실제 DP 최적화 계산 노드의 추상화를 나타냅니다.|
|[accelerator_view 클래스](accelerator-view-class.md)|데이터 병렬 가속기 C++ AMP의 가상 장치 추상화를 나타냅니다.|
|[accelerator_view_removed 클래스](accelerator-view-removed-class.md)|Windows 시간 초과 검색 및 복구 메커니즘으로 인해 내부 DirectX 호출이 실패할 때 throw 되는 예외입니다.|
|[array 클래스](array-class.md)|그리드 도메인의에 대 한 데이터 집계 `accelerator_view` 입니다. 이는 그리드 도메인의 각 요소에 대 한 변수의 컬렉션입니다. 각 변수는 c + + 형식에 해당 하는 값을 포함 합니다.|
|[array_view 클래스](array-view-class.md)|배열의 데이터에 대 한 뷰를 나타냅니다 \<T,N> .|
|[completion_future 클래스](completion-future-class.md)|비동기 작업 C++ AMP에 해당 하는 미래를 나타냅니다.|
|[익스텐트 클래스](extent-class.md)|원점이 0 인 N 차원 공간의 경계를 지정 하는 N 정수 값의 벡터를 나타냅니다. 좌표 벡터의 값은 가장 중요 한 값부터 최하위 순서로 정렬 됩니다. 예를 들어, 데카르트 3 차원 공간에서 범위 벡터 (7, 5, 3)는 z 좌표 범위가 0에서 7 사이이 고, y 좌표 범위는 0에서 5 사이이 고, x 좌표 범위는 0에서 3 사이에 있는 공간을 나타냅니다.|
|[index 클래스](index-class.md)|N 차원 인덱스 포인트를 정의 합니다.|
|[invalid_compute_domain 클래스](invalid-compute-domain-class.md)|런타임이 호출 사이트에서 지정 된 계산 도메인을 사용 하 여 커널을 시작할 수 없는 경우 throw 되는 예외입니다 `parallel_for_each` .|
|[out_of_memory 클래스](out-of-memory-class.md)|시스템이 나 장치 메모리 부족으로 인해 메서드가 실패 하는 경우 throw 되는 예외입니다.|
|[runtime_exception 클래스](runtime-exception-class.md)|C++ AMP 라이브러리의 예외에 대 한 기본 형식입니다.|
|[tile_barrier 클래스](tile-barrier-class.md)|시스템 에서만 만들 수 있는 기능 클래스 이며, `parallel_for_each` 매개 변수의 일부로 바둑판식 람다로 전달 됩니다 `tiled_index` . 이 메서드는 `wait()` 스레드 그룹 (타일)에서 실행 되는 스레드 실행을 동기화 하는 데 사용할 수 있는 메서드 하나를 제공 합니다.|
|[tiled_extent 클래스](tiled-extent-class.md)|`tiled_extent`개체는 `extent` 익스텐트 공간을 1 차원, 2 차원 또는 3 차원 타일로 세분 하는 1 ~ 3 차원에 대 한 개체입니다.|
|[tiled_index 클래스](tiled-index-class.md)|개체에 대 한 인덱스를 제공 `tiled_grid` 합니다. 이 클래스에는 로컬 타일 원본 및 전역 원본에 상대적인 요소에 액세스 하기 위한 속성이 있습니다.|
|[uninitialized_object 클래스](uninitialized-object-class.md)|초기화 되지 않은 개체를 사용할 때 throw 되는 예외입니다.|
|[unsupported_feature 클래스](unsupported-feature-class.md)|지원 되지 않는 기능을 사용할 때 throw 되는 예외입니다.|

### <a name="enumerations"></a>열거형

|Name|설명|
|----------|-----------------|
|[access_type 열거형](concurrency-namespace-enums-amp.md#access_type)|데이터 액세스 유형을 지정 합니다.|
|[queuing_mode 열거형](concurrency-namespace-enums-amp.md#queuing_mode)|가속기에서 지원 되는 큐 모드를 지정 합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|--------------|-----------------|
|[operator = = 연산자 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|지정 된 데이터 구조체가 같은지 여부를 확인 합니다.|
|[operator! = 연산자 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|지정 된 데이터 구조가 같지 않은지 여부를 확인 합니다.|
|[operator + 연산자 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|지정 된 인수의 구성 요소 단위 합계를 계산 합니다.|
|[operator- 연산자(C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|지정 된 인수 사이의 구성 요소 단위 차이를 계산 합니다.|
|[operator * 연산자 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|지정 된 인수의 구성 요소 단위 곱을 계산 합니다.|
|[operator/연산자 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|지정 된 인수의 구성 요소별 몫을 계산 합니다.|
|[operator% 연산자 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|지정 된 두 번째 인수를 기준으로 지정 된 첫 번째 인수의 모듈러스를 계산 합니다.|

### <a name="functions"></a>함수

|Name|설명|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|모든 메모리 액세스가 완료 될 때까지 타일에 있는 모든 스레드의 실행을 차단 합니다.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|C++ AMP 런타임을 초기화 하지 않습니다 합니다.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|오버로드됨. 지정 된 위치에 저장 된 값이 지정 된 첫 번째 값과 같으면 지정 된 두 번째 값은 원자성 작업과 동일한 위치에 저장 됩니다.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|오버로드됨. 원자 단위 연산으로 지정 된 위치에 저장 된 값을 지정 된 값으로 설정 합니다.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|오버로드됨. 지정 된 위치에 저장 된 값을 해당 값의 합으로 설정 하 고 원자 단위 연산으로 지정 된 값으로 설정 합니다.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|오버로드됨. 지정 된 위치에 저장 된 값을 해당 값의 비트 값으로 설정 하 `and` 고 원자 단위 연산으로 지정 된 값으로 설정 합니다.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|오버로드됨. 지정 된 위치에 저장 된 값을 감소 시키고 결과를 원자성 작업과 동일한 위치에 저장 합니다.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|오버로드됨. 지정 된 위치에 저장 된 값을 늘리고 원자 작업과 동일한 위치에 결과를 저장 합니다.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|오버로드됨. 지정 된 위치에 저장 된 값을 해당 값 중 더 큰 값으로 설정 하 고 원자 단위 연산으로 지정 된 값을 설정 합니다.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|오버로드됨. 지정 된 위치에 저장 된 값을 해당 값의 더 작은 값으로 설정 하 고 원자 단위 연산으로 지정 된 값을 설정 합니다.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|오버로드됨. 지정 된 위치에 저장 된 값을 해당 값의 비트 값으로 설정 하 `or` 고 원자 단위 연산으로 지정 된 값으로 설정 합니다.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|오버로드됨. 지정 된 위치에 저장 된 값을이 값과 지정 된 값의 차이 (원자 단위 연산)로 설정 합니다.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|오버로드됨. 지정 된 위치에 저장 된 값을 해당 값의 비트 값으로 설정 하 `xor` 고 원자 단위 연산으로 지정 된 값으로 설정 합니다.|
|[copy](concurrency-namespace-functions-amp.md#copy)|C++ AMP 개체를 복사 합니다. 모든 동기 데이터 전송 요구 사항이 충족 됩니다. 코드가 액셀러레이터 키에서 코드를 실행 하는 경우 데이터를 복사할 수 없습니다. 이 함수의 일반적인 형태는 `copy(src, dest)` 입니다.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|C++ AMP 개체를 복사 하 고 대기 될 수 있는 [completion_future](completion-future-class.md) 반환 합니다. 코드가 액셀러레이터 키에서 실행 중일 때는 데이터를 복사할 수 없습니다. 이 함수의 일반적인 형태는 `copy(src, dest)` 입니다.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Restriction 절이 있는 함수의 실행을 중단 `restrict(amp)` 합니다.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|서식이 지정 된 문자열을 Visual Studio **출력** 창에 출력 하 고 동일한 서식 지정 문자열이 있는 [runtime_exception](runtime-exception-class.md) 예외를 발생 시킵니다.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|서식이 지정 된 문자열을 Visual Studio **출력** 창에 인쇄 합니다. Restriction 절이 있는 함수에서 호출 됩니다 `restrict(amp)` .|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|모든 전역 메모리 액세스가 완료 될 때까지 타일에 있는 모든 스레드의 실행을 차단 합니다.|
|[parallel_for_each 함수(C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|계산 도메인에서 함수를 실행 합니다.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|메모리 액세스가 완료 될 때까지 타일에 있는 모든 스레드의 실행을 차단 `tile_static` 합니다.|

## <a name="constants"></a>상수

|Name|설명|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS 상수](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|DirectX에서 허용 하는 최대 버퍼 수입니다.|
|[MODULENAME_MAX_LENGTH 상수](concurrency-namespace-constants-amp.md#modulename_max_length)|모듈 이름의 최대 길이를 저장 합니다. 이 값은 컴파일러와 런타임에서 동일 해야 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

## <a name="see-also"></a>참고 항목

[참조(C++ AMP)](reference-cpp-amp.md)
