---
title: Concurrency::direct3d 네임스페이스 함수(AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375928"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 네임스페이스 함수(AMP)

||||
|-|-|-|
|[아 bs](#abs)|[클램프](#clamp)|[카운트비트](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[퍼스트 비트하이](#firstbithigh)|
|[퍼스트 비트로우](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[아이 맥스](#imax)|[이미인](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[미친](#mad)|[make_array](#make_array)|[소음](#noise)|
|[라디안](#radians)|[rcp](#rcp)|[리버스 비트](#reversebits)|
|[포화](#saturate)|[서명](#sign)|[스무스스텝](#smoothstep)|
|[단계](#step)|[유맥스 (주)](#umax)|[우민 (주)](#umin)|

## <a name="requirements"></a>요구 사항

**헤더:** amp.h **네임스페이스:** 동시성

## <a name="abs"></a><a name="abs"></a>아 bs

인수의 절대 값을 반환합니다.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

### <a name="return-value"></a>Return Value

인수의 절대 값을 반환합니다.

## <a name="clamp"></a><a name="clamp"></a>클램프

두 번째 및 세 번째 지정된 인수에 의해 정의된 범위에 고정된 첫 번째 지정된 인수의 값을 계산합니다.

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
클램프할 값

*_Min*<br/>
클램핑 범위의 하한입니다.

*_Max*<br/>
클램핑 범위의 상한입니다.

### <a name="return-value"></a>Return Value

의 고정 된 `_X`값입니다.

## <a name="countbits"></a><a name="countbits"></a>카운트비트

_X 세트 비트 수를 계산합니다.

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
부호 없는 정수 값

### <a name="return-value"></a>Return Value

_X 세트 비트 수를 반환합니다.

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

포인터에서 Direct3D 장치 인터페이스에 대한 [accelerator_view](accelerator-view-class.md) 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>매개 변수

*_Accelerator*<br/>
새 accelerator_view 생성할 가속기입니다.

*_D3D_device*<br/>
Direct3D 장치 인터페이스에 대한 포인터입니다.

*_Disable_timeout*<br/>
새로 만든 accelerator_view 대해 시간 지정을 사용하지 않도록 설정해야 하는지 여부를 지정하는 부울 매개 변수입니다. 이는 Direct3D 장치 생성을 위한 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 플래그에 해당하며 운영 체제에서 Windows 시간 초과 검색 및 복구 메커니즘에 따라 장치를 재설정하지 않고 2초 이상 걸리는 워크로드를 실행하도록 허용해야 하는지 를 나타내는 데 사용됩니다. accelerator_view 시간이 많이 걸리는 작업을 수행해야 하는 경우 이 플래그를 사용하는 것이 좋습니다.

*_Qmode*<br/>
새로 생성된 accelerator_view 사용할 [queuing_mode.](concurrency-namespace-enums-amp.md#queuing_mode) 이 매개 변수의 `queuing_mode_automatic`기본값은 입니다.

## <a name="return-value"></a>Return Value

전달된 Direct3D 장치 인터페이스에서 만든 `accelerator_view` 개체입니다.

## <a name="remarks"></a>설명

이 함수는 `accelerator_view` 기존 포인터에서 Direct3D 장치 인터페이스로 새 개체를 만듭니다. 함수 호출이 성공하면 매개 변수의 참조 수는 인터페이스 호출을 `AddRef` 통해 증가합니다. DirectX 코드에 더 이상 필요하지 않은 경우 개체를 안전하게 해제할 수 있습니다. 메서드 호출이 실패하면 [runtime_exception](runtime-exception-class.md) throw됩니다.

이 `accelerator_view` 함수를 사용하여 만든 개체는 스레드에서 사용할 수 있습니다. `accelerator_view` 개체의 동시 사용을 동기화해야 합니다. `accelerator_view` 개체의 동기화되지 않은 동시 사용 및 원시 ID3D11Device 인터페이스는 정의되지 않은 동작을 일으킵니다.

C++ AMP 런타임은 `D3D11_CREATE_DEVICE_DEBUG` 플래그를 사용하는 경우 D3D 디버그 계층을 사용하여 디버그 모드에서 자세한 오류 정보를 제공합니다.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

accelerator_view 공유하는 리소스에 대해 D3D 작업을 안전하게 수행할 수 accelerator_view 잠금을 획득합니다. 이 accelerator_view 관련된 모든 C++ AMP 리소스와 accelerator_view 작업을 수행할 때 내부적으로 이 잠금을 수행하고 다른 스레드에서 D3D 액세스 잠금을 보유하는 동안 차단됩니다. 이 잠금은 재귀적이지 않습니다: 이미 잠금을 보유한 스레드에서 이 함수를 호출하는 것은 정의되지 않은 동작입니다. D3D 액세스 잠금을 보유한 스레드에서 accelerator_view 연결된 accelerator_view 또는 데이터 컨테이너에서 작업을 수행하는 것은 정의되지 않은 동작입니다. 스코프 기반 D3D 액세스 잠금에 대한 RAII 스타일 클래스인 scoped_d3d_access_lock 참조하세요.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>매개 변수

*_Av*<br/>
잠글 accelerator_view.

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

차단하지 않고 accelerator_view D3D 액세스 잠금을 획득하려고 시도합니다.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>매개 변수

*_Av*<br/>
잠글 accelerator_view.

### <a name="return-value"></a>Return Value

false가 획득된 경우 true이거나 현재 다른 스레드에 의해 보유된 경우 false입니다.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

지정된 accelerator_view D3D 액세스 잠금을 해제합니다. 호출 스레드가 accelerator_view 잠금을 보유하지 않으면 결과가 정의되지 않습니다.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>매개 변수

*_Av*<br/>
잠금을 해제할 accelerator_view.

## <a name="firstbithigh"></a><a name="firstbithigh"></a>퍼스트 비트하이

_X 첫 번째 세트 비트의 위치를 가져옵니다., 가장 높은 순서 비트로 시작 하 고 가장 낮은 순서 비트쪽으로 이동.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

### <a name="return-value"></a>Return Value

첫 번째 세트 비트의 위치

## <a name="firstbitlow"></a><a name="firstbitlow"></a>퍼스트 비트로우

_X 첫 번째 세트 비트의 위치를 가져옵니다., 가장 낮은 순서 비트로 시작 하 고 가장 높은 순서 비트를 향해 작업.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

### <a name="return-value"></a>Return Value

첫 번째 세트 비트의 위치를 반환합니다.

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

지정된 배열의 기본으로 Direct3D 버퍼 인터페이스를 가져옵니다.

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>매개 변수

*Value_type*<br/>
배열 요소의 형식입니다.

*_Rank*<br/>
배열의 차수입니다.

*_Array*<br/>
기본 Direct3D 버퍼 인터페이스가 반환되는 Direct3D accelerator_view 배열입니다.

### <a name="return-value"></a>Return Value

배열의 기본을 기본으로 하는 Direct3D 버퍼에 해당하는 IUnknown 인터페이스 포인터입니다.

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

accelerator_view 기본으로 D3D 장치 인터페이스를 가져옵니다.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>매개 변수

*Av*<br/>
기본 D3D 장치 인터페이스가 반환되는 D3D accelerator_view.

### <a name="return-value"></a>반환 값

accelerator_view `IUnknown` 기본D3D 장치의 인터페이스 포인터입니다.

## <a name="imax"></a><a name="imax"></a>아이 맥스

인수의 최대 숫자 값 결정

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

*_y*<br/>
정수 값

### <a name="return-value"></a>Return Value

인수의 최대 숫자 값을 반환합니다.

## <a name="imin"></a><a name="imin"></a>이미인

인수의 최소 숫자 값 결정

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

*_y*<br/>
정수 값

### <a name="return-value"></a>Return Value

인수의 최소 숫자 값을 반환합니다.

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

지정된 accelerator_view 대해 시간 지정이 비활성화되어 있는지 를 나타내는 부울 플래그를 반환합니다. 이는 Direct3D 장치 생성을 위한 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 플래그에 해당합니다.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>매개 변수

*_Accelerator_view*<br/>
시간 비활성화된 설정을 쿼리하는 accelerator_view.

### <a name="return-value"></a>Return Value

지정된 accelerator_view 대해 시간 지정이 비활성화되어 있는지 를 나타내는 부울 플래그입니다.

## <a name="mad"></a><a name="mad"></a>미친

첫 번째 및 두 번째 지정된 인수의 곱을 계산한 다음 세 번째 지정된 인수를 추가합니다.

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
첫 번째 지정된 인수입니다.

*_y*<br/>
두 번째로 지정된 인수입니다.

*_Z*<br/>
세 번째 지정된 인수입니다.

### <a name="return-value"></a>Return Value

`_X` \* 의 `_Y`  + 결과입니다. `_Z`

## <a name="make_array"></a><a name="make_array"></a>make_array

Direct3D 버퍼 인터페이스 포인터에서 배열을 만듭니다.

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>매개 변수

*Value_type*<br/>
만들 어레이의 요소 형식입니다.

*_Rank*<br/>
만들 배열의 순위입니다.

*_Extent*<br/>
배열 집계의 모양을 설명하는 익스텐트입니다.

*_Rv*<br/>
배열을 작성할 D3D 가속기 보기입니다.

*_D3D_buffer*<br/>
D3D 버퍼의 IUnknown 인터페이스 포인터를 사용하여 배열을 만듭니다.

### <a name="return-value"></a>Return Value

제공된 Direct3D 버퍼를 사용하여 만든 배열입니다.

## <a name="noise"></a><a name="noise"></a>소음

Perlin 노이즈 알고리즘을 사용하여 임의의 값을 생성합니다.

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
Perlin 노이즈를 생성하는 부동 소수점 값

### <a name="return-value"></a>Return Value

-1과 1 사이의 범위 내에서 Perlin 노이즈 값을 반환합니다.

## <a name="radians"></a><a name="radians"></a>라디안

_X 도에서 라디안으로 변환

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
부동 소수점 값

### <a name="return-value"></a>Return Value

각도에서 라디안으로 변환한 _X를 반환합니다.

## <a name="rcp"></a><a name="rcp"></a>Rcp

빠른 근사치를 사용하여 지정된 인수의 상호를 계산합니다.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
상호를 계산할 값입니다.

### <a name="return-value"></a>Return Value

지정된 인수의 상호입니다.

## <a name="reversebits"></a><a name="reversebits"></a>리버스 비트

_X 비트의 순서를 반전합니다.

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
부호 없는 정수 값

### <a name="return-value"></a>Return Value

_X의 반대로 바뀐 비트 순서 값을 반환합니다.

## <a name="saturate"></a><a name="saturate"></a>포화

클램프는 0에서 1 범위 내에서 _X.

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
부동 소수점 값

### <a name="return-value"></a>Return Value

0 - 1의 범위 내로 제한된 _X를 반환합니다.

## <a name="sign"></a><a name="sign"></a>서명

지정된 인수의 부호를 결정합니다.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

### <a name="return-value"></a>Return Value

인수의 부호입니다.

## <a name="smoothstep"></a><a name="smoothstep"></a>스무스스텝

_X [_Min, _Max] 범위에 있는 경우 0에서 1 사이의 부드러운 Hermite 보간을 반환합니다.

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_Min*<br/>
부동 소수점 값

*_Max*<br/>
부동 소수점 값

*_x*<br/>
부동 소수점 값

### <a name="return-value"></a>Return Value

_X가 _Min보다 작은 경우 0을, _X가 _Max보다 큰 경우 1을 반환합니다. 그렇지 않으면, _X가 [_Min, _Max] 범위에 있는 경우 0과 1 사이의 값입니다.

## <a name="step"></a><a name="step"></a>단계

두 값을 비교하여 값이 큰 값을 기준으로 0 또는 1을 반환합니다.

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_y*<br/>
부동 소수점 값

*_x*<br/>
부동 소수점 값

### <a name="return-value"></a>Return Value

_X가 _Y보다 큰 경우 1을 반환합니다. 그렇지 않으면, 0을 반환합니다.

## <a name="umax"></a><a name="umax"></a>유맥스 (주)

인수의 최대 숫자 값 결정

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

*_y*<br/>
정수 값

### <a name="return-value"></a>Return Value

인수의 최대 숫자 값을 반환합니다.

## <a name="umin"></a><a name="umin"></a>우민 (주)

인수의 최소 숫자 값 결정

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>매개 변수

*_x*<br/>
정수 값

*_y*<br/>
정수 값

### <a name="return-value"></a>Return Value

인수의 최소 숫자 값을 반환합니다.

## <a name="see-also"></a>참고 항목

[Concurrency::direct3d 네임스페이스](concurrency-direct3d-namespace.md)
