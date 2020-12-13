---
description: '자세히 알아보기: 결합 가능한 클래스'
title: combinable 클래스
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: 117441be8ff7a54543adb419a1cb908d2eb9bec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331324"
---
# <a name="combinable-class"></a>combinable 클래스

`combinable<T>` 개체는 병렬 알고리즘 중에 잠금 없는 스레드 로컬 하위 계산을 수행하기 위해 데이터의 스레드 전용 복사본을 제공합니다. 병렬 작업이 끝나면 스레드 전용 하위 계산을 최종 결과에 병합할 수 있습니다. 이 클래스는 공유 변수 대신 사용될 수 있으며, 그렇지 않을 경우 해당 공유 변수에 대한 경합이 많으면 성능이 향상될 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
최종 병합 된 결과의 데이터 형식입니다. 형식에는 복사 생성자와 기본 생성자가 있어야 합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[조합을](#ctor)|오버로드됨. 새 `combinable` 개체를 생성합니다.|
|[~ 결합 가능한 소멸자](#dtor)|`combinable` 개체를 제거합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[clear](#clear)|이전 사용에서 중간 계산 결과를 모두 지웁니다.|
|[결합](#combine)|제공 된 combine 함수를 호출 하 여 스레드 로컬 하위 계산 집합에서 최종 값을 계산 합니다.|
|[combine_each](#combine_each)|스레드 로컬 하위 계산 마다 제공 된 조합 함수를 호출 하 여 스레드 로컬 하위 계산 집합에서 최종 값을 계산 합니다. 최종 결과는 함수 개체에 의해 누적 됩니다.|
|[로컬](#local)|오버로드됨. 스레드 전용 하위 계산에 대 한 참조를 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 =](#operator_eq)|`combinable`다른 개체에서 개체에 할당 `combinable` 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [병렬 컨테이너 및 개체](../../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`combinable`

## <a name="requirements"></a>요구 사항

**헤더:** ppl. h

**네임 스페이스:** 동시성

## <a name="clear"></a><a name="clear"></a> 해제

이전 사용에서 중간 계산 결과를 모두 지웁니다.

```cpp
void clear();
```

## <a name="combinable"></a><a name="ctor"></a> 조합을

새 `combinable` 개체를 생성합니다.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
초기화 함수 개체의 유형입니다.

*_FnInitialize*<br/>
형식의 새 스레드 전용 값을 초기화 하기 위해 호출 되는 함수입니다 `T` . 시그니처를 포함 하는 함수 호출 연산자를 지원 해야 합니다 `T ()` .

*_Copy*<br/>
`combinable`이 항목에 복사할 기존 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 형식에 대 한 기본 생성자를 사용 하 여 새 요소를 초기화 합니다 `T` .

두 번째 생성자는 매개 변수로 제공 된 초기화 함수를 사용 하 여 새 요소를 초기화 합니다 `_FnInitialize` .

세 번째 생성자는 복사 생성자입니다.

## <a name="combinable"></a><a name="dtor"></a> ~ 결합 가능한

`combinable` 개체를 제거합니다.

```cpp
~combinable();
```

## <a name="combine"></a><a name="combine"></a> 결합

제공 된 combine 함수를 호출 하 여 스레드 로컬 하위 계산 집합에서 최종 값을 계산 합니다.

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
두 스레드 로컬 하위 계산을 결합 하기 위해 호출 될 함수 개체의 형식입니다.

*_FnCombine*<br/>
하위 계산을 결합 하는 데 사용 되는 함수입니다. 해당 서명은 `T (T, T)` 또는 이며 `T (const T&, const T&)` 결합성과 교환 해야 합니다.

### <a name="return-value"></a>반환 값

모든 스레드 전용 하위 계산을 결합 한 최종 결과입니다.

## <a name="combine_each"></a><a name="combine_each"></a> combine_each

스레드 로컬 하위 계산 마다 제공 된 조합 함수를 호출 하 여 스레드 로컬 하위 계산 집합에서 최종 값을 계산 합니다. 최종 결과는 함수 개체에 의해 누적 됩니다.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>매개 변수

*_Function*<br/>
단일 스레드 로컬 하위 계산을 결합 하기 위해 호출 될 함수 개체의 형식입니다.

*_FnCombine*<br/>
하나의 하위 계산을 결합 하는 데 사용 되는 함수입니다. 해당 서명은 `void (T)` 또는 이며 `void (const T&)` 결합성과 교환 해야 합니다.

## <a name="local"></a><a name="local"></a> 로컬

스레드 전용 하위 계산에 대 한 참조를 반환 합니다.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>매개 변수

*_Exists*<br/>
부울에 대 한 참조입니다. 이 인수에서 참조 하는 부울 값은 **`true`** 이 스레드에 하위 계산이 이미 있는 경우로 설정 되 고,이 **`false`** 스레드의 첫 번째 하위 계산 인 경우로 설정 됩니다.

### <a name="return-value"></a>반환 값

스레드 전용 하위 계산에 대 한 참조입니다.

## <a name="operator"></a><a name="operator_eq"></a> 연산자 =

`combinable`다른 개체에서 개체에 할당 `combinable` 합니다.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>매개 변수

*_Copy*<br/>
`combinable`이 항목에 복사할 기존 개체입니다.

### <a name="return-value"></a>반환 값

이 개체에 대 한 참조 `combinable` 입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
