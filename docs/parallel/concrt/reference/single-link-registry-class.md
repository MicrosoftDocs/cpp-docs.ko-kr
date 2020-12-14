---
description: Single_link_registry 클래스에 대해 자세히 알아보세요.
title: single_link_registry 클래스
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: 415dcaf8062eaf47a3e92cf4a949790eb364d0c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188640"
---
# <a name="single_link_registry-class"></a>single_link_registry 클래스

`single_link_registry` 개체는 단일 소스 또는 대상 블록만 관리하는 `network_link_registry`입니다.

## <a name="syntax"></a>구문

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>매개 변수

*_Block*<br/>
개체에 저장 되는 블록 데이터 형식 `single_link_registry` 입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[single_link_registry](#ctor)|`single_link_registry` 개체를 생성합니다.|
|[~ single_link_registry 소멸자](#dtor)|개체를 소멸 시킵니다 `single_link_registry` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[add](#add)|개체에 대 한 링크를 추가 `single_link_registry` 합니다. [Network_link_registry:: add](network-link-registry-class.md#add)를 재정의 합니다.|
|[시작](#begin)|개체의 첫 번째 요소에 대 한 반복기를 반환 `single_link_registry` 합니다. [Network_link_registry:: begin](network-link-registry-class.md#begin)을 재정의 합니다.|
|[contains](#contains)|지정 된 `single_link_registry` 블록에 대 한 개체를 검색 합니다. [Network_link_registry:: contains](network-link-registry-class.md#contains)를 재정의 합니다.|
|[count](#count)|개체의 항목 수를 셉니다 `single_link_registry` . [Network_link_registry:: count](network-link-registry-class.md#count)를 재정의 합니다.|
|[remove](#remove)|개체에서 링크를 제거 합니다 `single_link_registry` . [Network_link_registry:: remove](network-link-registry-class.md#remove)를 재정의 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="add"></a><a name="add"></a> 추가

개체에 대 한 링크를 추가 `single_link_registry` 합니다.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
추가할 블록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 레지스트리에 이미 링크가 있는 경우 메서드는 [invalid_link_target](invalid-link-target-class.md) 예외를 throw 합니다.

## <a name="begin"></a><a name="begin"></a> begin

개체의 첫 번째 요소에 대 한 반복기를 반환 `single_link_registry` 합니다.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>반환 값

개체의 첫 번째 요소를 주소 지정 하는 반복기 `single_link_registry` 입니다.

### <a name="remarks"></a>설명

End 상태는 링크로 표시 됩니다 `NULL` .

## <a name="contains"></a><a name="contains"></a> 에서는

지정 된 `single_link_registry` 블록에 대 한 개체를 검색 합니다.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
개체에서 검색할 블록에 대 한 포인터입니다 `single_link_registry` .

### <a name="return-value"></a>반환 값

**`true`** 링크를 찾았으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="count"></a><a name="count"></a> 수

개체의 항목 수를 셉니다 `single_link_registry` .

```cpp
virtual size_t count();
```

### <a name="return-value"></a>반환 값

`single_link_registry` 개체에 있는 항목 수입니다.

## <a name="remove"></a><a name="remove"></a> 삭제

개체에서 링크를 제거 합니다 `single_link_registry` .

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
제거 될 블록에 대 한 포인터입니다 (있는 경우).

### <a name="return-value"></a>반환 값

**`true`** 링크를 찾아 제거 했으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="single_link_registry"></a><a name="ctor"></a> single_link_registry

`single_link_registry` 개체를 생성합니다.

```cpp
single_link_registry();
```

## <a name="single_link_registry"></a><a name="dtor"></a> ~ single_link_registry

개체를 소멸 시킵니다 `single_link_registry` .

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>설명

메서드는 링크가 제거 되기 전에 호출 되는 경우 [invalid_operation](invalid-operation-class.md) 예외를 throw 합니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[multi_link_registry 클래스](multi-link-registry-class.md)
