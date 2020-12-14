---
description: Source_link_manager 클래스에 대해 자세히 알아보세요.
title: source_link_manager 클래스
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 132dc2db07a1c9abeeb04672f97e262761764feb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188510"
---
# <a name="source_link_manager-class"></a>source_link_manager 클래스

`source_link_manager` 개체는 `ISource` 블록에 대한 메시징 블록 네트워크 연결을 관리합니다.

## <a name="syntax"></a>구문

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>매개 변수

*_LinkRegistry*<br/>
네트워크 링크 레지스트리

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`const_pointer`|개체의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** `source_link_manager` .|
|`const_reference`|**`const`** `source_link_manager` Const 작업을 읽고 수행 하기 위해 개체에 저장 된 요소에 대 한 참조를 제공 하는 형식입니다.|
|`iterator`|개체의 모든 요소를 읽거나 수정할 수 있는 반복기를 제공 하는 형식입니다 `source_link_manager` .|
|`type`|개체에서 관리 하는 링크 레지스트리의 형식입니다 `source_link_manager` .|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[source_link_manager](#ctor)|`source_link_manager` 개체를 생성합니다.|
|[~ source_link_manager 소멸자](#dtor)|개체를 소멸 시킵니다 `source_link_manager` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[add](#add)|개체에 소스 링크를 추가 `source_link_manager` 합니다.|
|[시작](#begin)|개체의 첫 번째 요소에 대 한 반복기를 반환 `source_link_manager` 합니다.|
|[contains](#contains)|`network_link_registry`이 개체 내에서 지정 된 블록을 검색 합니다 `source_link_manager` .|
|[count](#count)|개체의 연결 된 블록 수를 셉니다 `source_link_manager` .|
|[reference](#reference)|개체에 대 한 참조를 가져옵니다 `source_link_manager` .|
|[register_target_block](#register_target_block)|이 개체를 보유 하는 대상 블록을 등록 `source_link_manager` 합니다.|
|[릴리스](#release)|개체에 대 한 참조를 해제 `source_link_manager` 합니다.|
|[remove](#remove)|개체에서 링크를 제거 합니다 `source_link_manager` .|
|[set_bound](#set_bound)|이 개체에 추가할 수 있는 최대 소스 링크 수를 설정 합니다 `source_link_manager` .|

## <a name="remarks"></a>설명

현재 소스 블록은 참조 횟수가 계산 됩니다. 이는 링크에 대 한 `network_link_registry` 동시 액세스를 허용 하 고 콜백을 통해 링크를 참조 하는 기능을 제공 하는 개체의 래퍼입니다. 메시지 블록은 `target_block` `propagator_block` 소스 링크에 대해이 클래스를 사용 해야 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`source_link_manager`

## <a name="requirements"></a>요구 사항

**헤더:** agents.h

**네임 스페이스:** 동시성

## <a name="add"></a><a name="add"></a> 추가

개체에 소스 링크를 추가 `source_link_manager` 합니다.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
추가할 블록에 대 한 포인터입니다.

## <a name="begin"></a><a name="begin"></a> begin

개체의 첫 번째 요소에 대 한 반복기를 반환 `source_link_manager` 합니다.

```cpp
iterator begin();
```

### <a name="return-value"></a>반환 값

개체의 첫 번째 요소를 주소 지정 하는 반복기 `source_link_manager` 입니다.

### <a name="remarks"></a>설명

반복기의 종료 상태는 링크로 표시 됩니다 `NULL` .

## <a name="contains"></a><a name="contains"></a> 에서는

`network_link_registry`이 개체 내에서 지정 된 블록을 검색 합니다 `source_link_manager` .

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
개체에서 검색할 블록에 대 한 포인터입니다 `source_link_manager` .

### <a name="return-value"></a>반환 값

**`true`** 지정 된 블록이 발견 되었으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="count"></a><a name="count"></a> 수

개체의 연결 된 블록 수를 셉니다 `source_link_manager` .

```cpp
size_t count();
```

### <a name="return-value"></a>반환 값

개체의 연결 된 블록 수 `source_link_manager` 입니다.

## <a name="reference"></a><a name="reference"></a> 참조일

개체에 대 한 참조를 가져옵니다 `source_link_manager` .

```cpp
void reference();
```

## <a name="register_target_block"></a><a name="register_target_block"></a> register_target_block

이 개체를 보유 하는 대상 블록을 등록 `source_link_manager` 합니다.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>매개 변수

*_PTarget*<br/>
이 개체를 보유 하는 대상 블록 `source_link_manager` 입니다.

## <a name="release"></a><a name="release"></a> 릴리스

개체에 대 한 참조를 해제 `source_link_manager` 합니다.

```cpp
void release();
```

## <a name="remove"></a><a name="remove"></a> 삭제

개체에서 링크를 제거 합니다 `source_link_manager` .

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>매개 변수

*_Link*<br/>
제거 될 블록에 대 한 포인터입니다 (있는 경우).

### <a name="return-value"></a>반환 값

**`true`** 링크를 찾아 제거 했으면이 고, **`false`** 그렇지 않으면입니다.

## <a name="set_bound"></a><a name="set_bound"></a> set_bound

이 개체에 추가할 수 있는 최대 소스 링크 수를 설정 합니다 `source_link_manager` .

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>매개 변수

*_MaxLinks*<br/>
최대 링크 수입니다.

## <a name="source_link_manager"></a><a name="ctor"></a> source_link_manager

`source_link_manager` 개체를 생성합니다.

```cpp
source_link_manager();
```

## <a name="source_link_manager"></a><a name="dtor"></a> ~ source_link_manager

개체를 소멸 시킵니다 `source_link_manager` .

```cpp
~source_link_manager();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[single_link_registry 클래스](single-link-registry-class.md)<br/>
[multi_link_registry 클래스](multi-link-registry-class.md)
