---
title: Platform::Collections::BackInsertIterator 클래스
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: 56393fd522ecd0e2f161dfa5b9fe8230563c0f65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223488"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator 클래스

요소를 덮어쓰지 않고 순차 컬렉션의 백 엔드에 삽입하는 반복기를 나타냅니다.

## <a name="syntax"></a>구문

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
현재 컬렉션에 있는 항목의 형식입니다.

### <a name="remarks"></a>설명

BackInsertIterator 클래스는 [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md)에 필요한 규칙을 구현합니다.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[BackInsertIterator:: BackInsertIterator](#ctor)|BackInsertIterator 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[BackInsertIterator:: operator * 연산자](#operator-dereference)|현재 BackInsertIterator에 대한 참조를 검색합니다.|
|[BackInsertIterator:: operator + + 연산자](#operator-increment)|현재 BackInsertIterator에 대한 참조를 반환합니다. 반복기는 수정되지 않습니다.|
|[BackInsertIterator::operator= 연산자](#operator-assign)|지정된 개체를 현재 순차 컬렉션의 끝에 추가합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`BackInsertIterator`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform::Collections

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a>BackInsertIterator:: BackInsertIterator 생성자

`BackInsertIterator` 클래스의 새 인스턴스를 초기화합니다.

## <a name="syntax"></a>구문

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>매개 변수

*hyper-v*<br/>
IVector \<T> 개체입니다.

### <a name="remarks"></a>설명

`BackInsertIterator`는 `v` 매개 변수로 지정된 개체의 마지막 요소 뒤에 요소를 삽입합니다.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a>BackInsertIterator:: operator = 연산자

지정된 개체를 현재 순차 컬렉션의 끝에 추가합니다.

## <a name="syntax"></a>구문

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>매개 변수

*트*<br/>
현재 컬렉션에 추가할 개체입니다.

### <a name="return-value"></a>Return Value

현재 BackInsertIterator에 대한 참조입니다.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a>BackInsertIterator:: operator * 연산자

현재 BackInsertIterator에 대한 참조를 검색합니다.

## <a name="syntax"></a>구문

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Return Value

현재 BackInsertIterator에 대한 참조입니다.

### <a name="remarks"></a>설명

이 연산자는 현재 컬렉션의 요소가 아닌 현재 BackInsertIterator에 대한 참조를 반환합니다.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a>BackInsertIterator:: operator + + 연산자

현재 BackInsertIterator에 대한 참조를 반환합니다. 반복기는 수정되지 않습니다.

## <a name="syntax"></a>구문

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Return Value

현재 BackInsertIterator에 대한 참조입니다.

### <a name="remarks"></a>설명

의도적으로, 첫 번째 구문 예는 현재 BackInsertIterator를 사전에 증가시키고 두 번째 구문은 현재 BackInsertIterator를 사후에 증가시킵니다. **`int`** 두 번째 구문의 형식은 실제 정수 피연산자가 아니라 후 위 증가 연산을 나타냅니다.

그러나 이 연산자는 BackInsertIterator를 실제로 수정하지 않습니다. 대신에 수정되지 않은 현재 반복기에 대한 참조를 반환합니다. 이는 [operator *](#operator-dereference)와 동일한 동작입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)
