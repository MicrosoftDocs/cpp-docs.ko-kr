---
description: Multi_link_registry 클래스에 대해 자세히 알아보세요.
title: multi_link_registry 클래스
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: a5d5e6c7e837f76a422c3f2879f74d1af36d64d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202134"
---
# <a name="multi_link_registry-class"></a>multi_link_registry 클래스

`multi_link_registry` 개체는 여러 소스 블록 또는 여러 대상 블록을 관리하는 `network_link_registry`입니다.

## <a name="syntax"></a>구문

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>매개 변수

*_Block*<br/>
개체에 저장 되는 블록 데이터 형식 `multi_link_registry` 입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[multi_link_registry](#ctor)|`multi_link_registry` 개체를 생성합니다.|
|[~ multi_link_registry 소멸자](#dtor)|개체를 소멸 시킵니다 `multi_link_registry` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[add](#add)|개체에 대 한 링크를 추가 `multi_link_registry` 합니다. [Network_link_registry:: add](network-link-registry-class.md#add)를 재정의 합니다.|
|[시작](#begin)|개체의 첫 번째 요소에 대 한 반복기를 반환 `multi_link_registry` 합니다. [Network_link_registry:: begin](network-link-registry-class.md#begin)을 재정의 합니다.|
|[contains](#contains)|지정 된 `multi_link_registry` 블록에 대 한 개체를 검색 합니다. [Network_link_registry:: contains](network-link-registry-class.md#contains)를 재정의 합니다.|
|[count](#count)|개체의 항목 수를 셉니다 `multi_link_registry` . [Network_link_registry:: count](network-link-registry-class.md#count)를 재정의 합니다.|
|[remove](#remove)|개체에서 링크를 제거 합니다 `multi_link_registry` . [Network_link_registry:: remove](network-link-registry-class.md#remove)를 재정의 합니다.|
|[set_bound](#set_bound)|개체가 보유할 수 있는 링크 수의 상한을 설정 `multi_link_registry` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="add"></a><a name="add"></a> 추가

개체에 대 한 링크를 추가 `multi_link_registry` 합니다.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
추가할 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 레지스트리에 링크가 이미 있는 경우 또는 바인딩된가 이미 함수를 사용 하 여 설정 되어 있고 링크가 제거 된 후에는 [invalid_link_target](invalid-link-target-class.md) 예외를 throw 합니다 `set_bound` .

## <a name="begin"></a><a name="begin"></a> begin

개체의 첫 번째 요소에 대 한 반복기를 반환 `multi_link_registry` 합니다.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>반환 값

개체의 첫 번째 요소를 주소 지정 하는 반복기 `multi_link_registry` 입니다.

### <a name="remarks"></a>설명

End 상태는 링크로 표시 됩니다 `NULL` .

## <a name="contains"></a><a name="contains"></a> 에서는

지정 된 `multi_link_registry` 블록에 대 한 개체를 검색 합니다.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
개체에서 검색할 블록에 대 한 포인터입니다 `multi_link_registry` .

### <a name="return-value"></a>반환 값

**`true`** 지정 된 블록이 발견 되었으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="count"></a><a name="count"></a> 수

개체의 항목 수를 셉니다 `multi_link_registry` .

```cpp
virtual size_t count();
```

### <a name="return-value"></a>반환 값

`multi_link_registry` 개체에 있는 항목 수입니다.

## <a name="multi_link_registry"></a><a name="ctor"></a> multi_link_registry

`multi_link_registry` 개체를 생성합니다.

```cpp
multi_link_registry();
```

## <a name="multi_link_registry"></a><a name="dtor"></a> ~ multi_link_registry

개체를 소멸 시킵니다 `multi_link_registry` .

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>설명

메서드는 모든 링크가 제거 되기 전에 호출 되는 경우 [invalid_operation](invalid-operation-class.md) 예외를 throw 합니다.

## <a name="remove"></a><a name="remove"></a> 삭제

개체에서 링크를 제거 합니다 `multi_link_registry` .

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
제거 될 블록에 대 한 포인터입니다 (있는 경우).

### <a name="return-value"></a>반환 값

**`true`** 링크를 찾아 제거 했으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="set_bound"></a><a name="set_bound"></a> set_bound

개체가 보유할 수 있는 링크 수의 상한을 설정 `multi_link_registry` 합니다.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>매개 변수

*_MaxLinks*<br/>
개체가 보유할 수 있는 최대 링크 수입니다 `multi_link_registry` .

### <a name="remarks"></a>설명

한도가 설정된 후 항목의 연결을 해제하면 `multi_link_registry` 개체가 변경 불가능한 상태로 전환됩니다. 이 상태에서 `add`를 추가로 호출하면 `invalid_link_target` 예외가 throw됩니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[single_link_registry 클래스](single-link-registry-class.md)
