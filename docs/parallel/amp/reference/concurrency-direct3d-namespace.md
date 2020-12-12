---
description: '자세히 알아보기: Concurrency::d irect3d 네임 스페이스'
title: Concurrency::direct3d 네임스페이스
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: 9fb0e7d4f5abbccbd9cd931fe2c4520e9410cbc9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247737"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 네임스페이스

`direct3d`네임 스페이스는 D3D 상호 운용성을 지 원하는 함수를 제공 합니다. 이를 통해 AMP 코드에서 계산을 위해 D3D 리소스를 사용할 수 있습니다. 또한 중복 된 중간 복사본을 만들지 않고 D3D 코드의 AMP에서 만든 리소스를 사용할 수 있습니다. C++ AMP를 사용 하 여 DirectX 응용 프로그램의 계산 집약적 섹션을 점차적으로 가속화 하 고, AMP 계산에서 생성 된 데이터에 대해 D3D API를 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
namespace direct3d;
```

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[scoped_d3d_access_lock 클래스](scoped-d3d-access-lock-class.md)|개체에 대 한 D3D 액세스 잠금에 대 한 RAII 래퍼입니다 `accelerator_view` .|

### <a name="structures"></a>구조체

|Name|설명|
|----------|-----------------|
|[adopt_d3d_access_lock_t 구조체](adopt-d3d-access-lock-t-structure.md)|D3D 액세스 잠금을 획득 하지 않고 채택 해야 함을 나타내는 태그 유형입니다.|

### <a name="functions"></a>함수

|Name|설명|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|인수의 절대 값을 반환 합니다.|
|[클램프](concurrency-direct3d-namespace-functions-amp.md#clamp)|오버로드됨. 지정 된 _Min 및 _Max 범위에 _X 범위로 제한|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|_X에서 설정 비트 수를 계산 합니다.|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Direct3D 장치 인터페이스에 대 한 포인터에서 [Accelerator_view 클래스](accelerator-view-class.md) 를 만듭니다.|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Accelerator_view와 공유 되는 리소스에서 D3D 작업을 안전 하 게 수행 하기 위해 accelerator_view에 대 한 잠금을 획득 합니다.|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|차단을 사용 하지 않고 accelerator_view에 대 한 D3D 액세스 잠금을 가져오려고 시도 합니다.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|지정 된 accelerator_view에 대 한 D3D 액세스 잠금을 해제 합니다.|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|_X에서 첫 번째 설정 비트의 위치를 가져옵니다. 가장 높은 순서 비트부터 아래로 작동 합니다.|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|가장 낮은 순서 비트에서 시작 하 여 위쪽으로 작업 하는 _X에서 첫 번째 설정 비트의 위치를 가져옵니다.|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|배열을 기반으로 하는 D3D 버퍼 인터페이스를 가져옵니다.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|두 값을 비교 하 여 더 큰 값을 반환 합니다.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|두 값을 비교 하 여 더 작은 값을 반환 합니다.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|지정 된 accelerator_view에 대 한 제한 시간을 사용할 수 없는지 여부를 나타내는 부울 플래그를 반환 합니다.|
|[mad.exe](concurrency-direct3d-namespace-functions-amp.md#mad)|오버로드됨. 세 인수에 대해 산술 곱하기/추가 연산을 수행 합니다. _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|D3D 버퍼 인터페이스 포인터에서 배열을 만듭니다.|
|[노이즈](concurrency-direct3d-namespace-functions-amp.md#noise)|Perlin 노이즈 알고리즘을 사용 하 여 임의의 값을 생성 합니다.|
|[각도](concurrency-direct3d-namespace-functions-amp.md#radians)|도에서 라디안으로 _X 변환 합니다.|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|인수의 fast와 근사치를 계산 합니다.|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|_X 비트의 순서를 반대로 바꿉니다.|
|[용량](concurrency-direct3d-namespace-functions-amp.md#saturate)|범위로 제한 _X 범위는 0에서 1 사이입니다.|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|오버로드됨. 인수의 부호를 반환 합니다.|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|_X [_Min, _Max] 범위에 있는 경우 0과 1 사이의 부드러운 Hermite 보간을 반환 합니다.|
|[이동](concurrency-direct3d-namespace-functions-amp.md#step)|두 값을 비교 하 여 더 큰 값을 기준으로 0 또는 1을 반환 합니다.|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|부호 없는 두 값을 비교 하 여 더 큰 값을 반환 합니다.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|부호 없는 두 값을 비교 하 여 더 작은 값을 반환 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** amp.h

**네임스페이스:** 동시성

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)
