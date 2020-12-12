---
description: Network_link_registry 클래스에 대해 자세히 알아보세요.
title: network_link_registry 클래스
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: d14ec5758b399d46d5a5f04200b9422b030305f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236596"
---
# <a name="network_link_registry-class"></a>network_link_registry 클래스

`network_link_registry` 추상 기본 클래스는 소스 및 대상 블록 간의 연결을 관리합니다.

## <a name="syntax"></a>구문

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>매개 변수

*_Block*<br/>
에 저장 되는 블록 데이터 형식 `network_link_registry` 입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`const_pointer`|개체의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** `network_link_registry` .|
|`const_reference`|**`const`** `network_link_registry` Const 작업을 읽고 수행 하기 위해 개체에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다.|
|`iterator`|개체의 모든 요소를 읽거나 수정할 수 있는 반복기를 제공 하는 형식입니다 `network_link_registry` .|
|`type`|개체에 저장 된 블록 형식을 나타내는 형식입니다 `network_link_registry` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[add](#add)|파생 클래스에서 재정의 되는 경우 개체에 대 한 링크를 추가 `network_link_registry` 합니다.|
|[시작](#begin)|파생 클래스에서 재정의 되는 경우 개체의 첫 번째 요소에 반복기를 반환 `network_link_registry` 합니다.|
|[contains](#contains)|파생 클래스에서 재정의 되는 경우 지정 된 `network_link_registry` 블록에 대 한 개체를 검색 합니다.|
|[count](#count)|파생 클래스에서 재정의 되는 경우 개체의 항목 수를 반환 합니다 `network_link_registry` .|
|[remove](#remove)|파생 클래스에서 재정의 되는 경우 개체에서 지정 된 블록을 제거 합니다 `network_link_registry` .|

## <a name="remarks"></a>설명

는 `network link registry` 동시 액세스에 안전 하지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`network_link_registry`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="add"></a><a name="add"></a> 추가

파생 클래스에서 재정의 되는 경우 개체에 대 한 링크를 추가 `network_link_registry` 합니다.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
추가할 블록에 대 한 포인터입니다.

## <a name="begin"></a><a name="begin"></a> begin

파생 클래스에서 재정의 되는 경우 개체의 첫 번째 요소에 반복기를 반환 `network_link_registry` 합니다.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>반환 값

개체의 첫 번째 요소를 주소 지정 하는 반복기 `network_link_registry` 입니다.

### <a name="remarks"></a>설명

반복기의 종료 상태는 링크로 표시 됩니다 `NULL` .

## <a name="contains"></a><a name="contains"></a> 에서는

파생 클래스에서 재정의 되는 경우 지정 된 `network_link_registry` 블록에 대 한 개체를 검색 합니다.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
개체에서 검색 되는 블록에 대 한 포인터입니다 `network_link_registry` .

### <a name="return-value"></a>반환 값

**`true`** 블록이 발견 되었으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="count"></a><a name="count"></a> 수

파생 클래스에서 재정의 되는 경우 개체의 항목 수를 반환 합니다 `network_link_registry` .

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>반환 값

`network_link_registry` 개체에 있는 항목 수입니다.

## <a name="remove"></a><a name="remove"></a> 삭제

파생 클래스에서 재정의 되는 경우 개체에서 지정 된 블록을 제거 합니다 `network_link_registry` .

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
제거 될 블록에 대 한 포인터입니다 (있는 경우).

### <a name="return-value"></a>반환 값

**`true`** 링크를 찾아 제거 했으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[single_link_registry 클래스](single-link-registry-class.md)<br/>
[multi_link_registry 클래스](multi-link-registry-class.md)
