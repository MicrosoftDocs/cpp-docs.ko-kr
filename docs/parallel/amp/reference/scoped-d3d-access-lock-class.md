---
description: Scoped_d3d_access_lock 클래스에 대해 자세히 알아보세요.
title: scoped_d3d_access_lock 클래스
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: 1106673ba9ca095b33660f6a713a40ae8498d384
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329915"
---
# <a name="scoped_d3d_access_lock-class"></a>scoped_d3d_access_lock 클래스

Accelerator_view 개체에 대 한 D3D 액세스 잠금에 대 한 RAII 래퍼입니다.

## <a name="syntax"></a>구문

```cpp
class scoped_d3d_access_lock;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[scoped_d3d_access_lock 생성자](#ctor)|오버로드됨. `scoped_d3d_access_lock` 개체를 생성합니다. 이 개체가 범위를 벗어나면 잠금이 해제 됩니다.|
|[~ scoped_d3d_access_lock 소멸자](#dtor)|연결 된 개체에 대 한 D3D 액세스 잠금을 해제 합니다 `accelerator_view` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 =](#operator_eq)|다른의 잠금 소유권을 가져옵니다 `scoped_d3d_access_lock` .|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`scoped_d3d_access_lock`

## <a name="requirements"></a>요구 사항

**헤더:** amprt. h

**네임 스페이스:** 동시성::d irect3d

## <a name="scoped_d3d_access_lock"></a><a name="ctor"></a> scoped_d3d_access_lock

`scoped_d3d_access_lock` 개체를 생성합니다. 이 개체가 범위를 벗어나면 잠금이 해제 됩니다.

```cpp
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>매개 변수

*_Av*<br/>
`accelerator_view`적용할 잠금에 대 한입니다.

*_T*<br/>
`adopt_d3d_access_lock_t` 개체

*_Other*<br/>
`scoped_d3d_access_lock`기존 잠금을 이동할 개체입니다.

## <a name="construction"></a>건설

[1] 생성자가 지정 된 [accelerator_view](accelerator-view-class.md) 개체에 대 한 D3D 액세스 잠금을 획득 합니다. 잠금이 획득 될 때까지 생성이 차단 됩니다.

[2] 생성자는 지정 된 [accelerator_view](accelerator-view-class.md) 개체에서 D3D 액세스 잠금을 채택 합니다.

[3] 이동 생성자는 다른 개체에서 기존 D3D 액세스 잠금을 사용 `scoped_d3d_access_lock` 합니다. 생성이 차단 되지 않습니다.

## <a name="scoped_d3d_access_lock"></a><a name="dtor"></a> ~ scoped_d3d_access_lock

연결 된 개체에 대 한 D3D 액세스 잠금을 해제 합니다 `accelerator_view` .

```cpp
~scoped_d3d_access_lock();
```

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

이전 잠금을 해제 하 여 다른 개체에서 D3D 액세스 잠금 소유권 `scoped_d3d_access_lock` 을 가져옵니다.

```cpp
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>매개 변수

*_Other*<br/>
D3D 액세스 잠금을 이동할 accelerator_view입니다.

### <a name="return-value"></a>반환 값

이에 대 한 참조 `scoped_accelerator_view_lock` 입니다.

## <a name="see-also"></a>참고 항목

[Concurrency::direct3d 네임스페이스](concurrency-direct3d-namespace.md)
