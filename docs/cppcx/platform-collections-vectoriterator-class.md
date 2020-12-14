---
description: '자세한 정보: Platform:: Collections:: VectorIterator 클래스'
title: Platform::Collections::VectorIterator 클래스
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: ad572a8b426092fb0ddb39db44f387598674c988
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253912"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator 클래스

Windows 런타임 IVector 인터페이스에서 파생 된 개체에 대 한 표준 템플릿 라이브러리 반복기를 제공 합니다.

VectorIterator는 VectorProxy 형식의 요소를 저장 하는 프록시 반복기입니다 \<T> . 그러나 프록시 개체는 사용자 코드에 거의 표시되지 않습니다. 자세한 내용은 [컬렉션(C++/CX)](../cppcx/collections-c-cx.md)을 참조하세요.

## <a name="syntax"></a>구문

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
VectorIterator 템플릿 클래스의 형식 이름입니다.

### <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|`difference_type`|포인터 차이(ptrdiff_t)입니다.|
|`iterator_category`|임의 액세스 반복기의 범주입니다(::std::random_access_iterator_tag).|
|`pointer`|\<T>VectorIterator의 구현에 필요한 내부 형식 Platform:: Collections::D etails:: VectorProxy에 대 한 포인터입니다.|
|`reference`|VectorIterator의 구현에 필요한 내부 형식 Platform:: Collections::D etails:: VectorProxy에 대 한 참조입니다 \<T> .|
|`value_type`|`T` 형식 이름입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[VectorIterator:: VectorIterator](#ctor)|VectorIterator 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[VectorIterator:: operator-연산자](#operator-minus)|현재 반복기에서 지정된 요소 수를 빼서 새 반복기를 계산하거나 현재 반복기에서 지정된 반복기를 빼서 반복기 간 요소 수 차이를 계산합니다.|
|[VectorIterator:: operator--연산자](#operator-decrement)|현재 VectorIterator를 감소시킵니다.|
|[VectorIterator:: operator! = 연산자](#operator-inequality)|현재 VectorIterator가 지정된 VectorIterator와 같지 않은지 여부를 나타냅니다.|
|[VectorIterator:: operator * 연산자](#operator-dereference)|현재 VectorIterator가 지정하는 요소에 대한 참조를 검색합니다.|
|[VectorIterator:: operator\[\]](#operator-at)|현재 VectorIterator에서 지정된 치환에 해당하는 요소에 대한 참조를 검색합니다.|
|[VectorIterator:: operator + 연산자](#operator-plus)|지정된 VectorIterator에서 지정된 치환에 해당하는 요소를 참조하는 VectorIterator를 반환합니다.|
|[VectorIterator:: operator + + 연산자](#operator-increment)|현재 VectorIterator를 증가시킵니다.|
|[VectorIterator:: operator + = 연산자](#operator-plus-assign)|지정된 치환으로 현재 VectorIterator를 늘립니다.|
|[VectorIterator:: operator< 연산자](#operator-less-than)|현재 VectorIterator가 지정된 VectorIterator보다 작은지 여부를 나타냅니다.|
|[VectorIterator:: operator \< = 연산자](#operator-less-than-or-equals)|현재 VectorIterator가 지정된 VectorIterator보다 작거나 같은지 여부를 나타냅니다.|
|[VectorIterator:: operator-= 연산자](#operator-minus-equals)|지정된 치환으로 현재 VectorIterator를 줄입니다.|
|[VectorIterator:: operator = = 연산자](#operator-equality)|현재 VectorIterator가 지정된 VectorIterator와 같은지 여부를 나타냅니다.|
|[VectorIterator::operator> 연산자](#operator-greater-than)|현재 VectorIterator가 지정된 VectorIterator보다 큰지 여부를 나타냅니다.|
|[VectorIterator:: operator-> 연산자](#operator-arrow)|현재 VectorIterator가 참조하는 요소의 주소를 검색합니다.|
|[VectorIterator:: operator>= 연산자](#operator-greater-than-or-equals)|현재 VectorIterator가 지정된 VectorIterator보다 크거나 같은지 여부를 나타냅니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`VectorIterator`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a> VectorIterator:: operator- &gt; 연산자

현재 VectorIterator가 참조하는 요소의 주소를 검색합니다.

### <a name="syntax"></a>구문

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Return Value

현재 VectorIterator가 참조하는 요소의 값입니다.

반환 값의 형식은 이 연산자의 구현에 필요한 지정되지 않은 내부 형식입니다.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a> VectorIterator:: operator--연산자

현재 VectorIterator를 감소시킵니다.

### <a name="syntax"></a>구문

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Return Value

첫 번째 구문은 현재 VectorIterator를 감소시킨 다음 반환합니다. 두 번째 구문은 현재 VectorIterator의 복사본을 반환한 다음 현재 VectorIterator를 감소시킵니다.

### <a name="remarks"></a>설명

첫 번째 VectorIterator 구문은 현재 VectorIterator를 사전에 감소시킵니다.

두 번째 구문은 현재 VectorIterator를 사후에 감소시킵니다. **`int`** 두 번째 구문의 형식은 실제 정수 피연산자가 아니라 감소 후 연산을 나타냅니다.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a> VectorIterator:: operator \* 연산자

현재 VectorIterator가 지정하는 요소의 주소를 검색합니다.

### <a name="syntax"></a>구문

```
reference operator*() const;
```

### <a name="return-value"></a>Return Value

현재 VectorIterator가 지정하는 요소입니다.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a> VectorIterator:: operator = = 연산자

현재 VectorIterator가 지정된 VectorIterator와 같은지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 VectorIterator와 같으면이 *고, 그렇지 않으면입니다*. 그렇지 않으면 **`false`** 입니다.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a> VectorIterator:: operator &gt; 연산자

현재 VectorIterator가 지정된 VectorIterator보다 큰지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 VectorIterator이 *다른* 값 보다 크면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a> VectorIterator:: operator &gt; = 연산자

현재 VectorIterator가 지정된 VectorIterator보다 크거나 같은지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 VectorIterator이 *다른* 값 보다 크거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a> VectorIterator:: operator + + 연산자

현재 VectorIterator를 증가시킵니다.

### <a name="syntax"></a>구문

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Return Value

첫 번째 구문은 현재 VectorIterator를 증가시킨 다음 반환합니다. 두 번째 구문은 현재 VectorIterator의 복사본을 반환한 다음 현재 VectorIterator를 증가시킵니다.

### <a name="remarks"></a>설명

첫 번째 VectorIterator 구문은 현재 VectorIterator를 사전에 증가시킵니다.

두 번째 구문은 현재 VectorIterator를 사후에 증가시킵니다. **`int`** 두 번째 구문의 형식은 실제 정수 피연산자가 아니라 후 위 증가 연산을 나타냅니다.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a> VectorIterator:: operator! = 연산자

현재 VectorIterator가 지정된 VectorIterator와 같지 않은지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 VectorIterator가 *다른* 와 같지 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a> VectorIterator:: operator &lt; 연산자

현재 VectorIterator가 지정된 VectorIterator보다 작은지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 VectorIterator이 *다른* 값 보다 작은 경우 그렇지 않으면 **`false`** 입니다.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a> VectorIterator:: operator &lt; = 연산자

현재 VectorIterator가 지정된 VectorIterator보다 작거나 같은지 여부를 나타냅니다.

### <a name="syntax"></a>구문

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 VectorIterator이 *다른* 값 보다 작거나 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a> VectorIterator:: operator-연산자

현재 반복기에서 지정된 요소 수를 빼서 새 반복기를 계산하거나 현재 반복기에서 지정된 반복기를 빼서 반복기 간 요소 수 차이를 계산합니다.

### <a name="syntax"></a>구문

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>매개 변수

*n*<br/>
요소 수입니다.

*다른*<br/>
다른 VectorIterator입니다.

### <a name="return-value"></a>반환 값

첫 번째 연산자 구문은 현재 VectorIterator에서 `n`개 요소를 뺀 VectorIterator 개체를 반환합니다. 두 번째 구문은 현재 VectorIterator와 `other` VectorIterator의 요소 수 차이를 반환합니다.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a> VectorIterator:: operator + = 연산자

지정된 치환으로 현재 VectorIterator를 늘립니다.

### <a name="syntax"></a>구문

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>매개 변수

*n*<br/>
정수 치환입니다.

### <a name="return-value"></a>반환 값

업데이트된 VectorIterator입니다.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a> VectorIterator:: operator + 연산자

지정된 VectorIterator에서 지정된 치환에 해당하는 요소를 참조하는 VectorIterator를 반환합니다.

### <a name="syntax"></a>구문

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
두 번째 구문에서 VectorIterator의 형식 이름입니다.

*n*<br/>
정수 치환입니다.

*i*<br/>
두 번째 구문의 VectorIterator입니다.

### <a name="return-value"></a>반환 값

첫 번째 구문에서 현재 VectorIterator에서 지정된 치환에 해당하는 요소를 참조하는 VectorIterator입니다.

두 번째 구문에서 매개 변수 `i` 시작 부분의 지정된 치환에 해당하는 요소를 참조하는 VectorIterator입니다.

### <a name="remarks"></a>설명

첫 번째 구문 예제

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a> VectorIterator:: operator-= 연산자

지정된 치환으로 현재 VectorIterator를 줄입니다.

### <a name="syntax"></a>구문

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>매개 변수

*n*<br/>
정수 치환입니다.

### <a name="return-value"></a>반환 값

업데이트된 VectorIterator입니다.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a> VectorIterator:: operator\[\]

현재 VectorIterator에서 지정된 치환에 해당하는 요소에 대한 참조를 검색합니다.

### <a name="syntax"></a>구문

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>매개 변수

*n*<br/>
정수 치환입니다.

### <a name="return-value"></a>반환 값

현재 VectorIterator에서 `n` 요소에 의해 치환되는 요소입니다.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a> VectorIterator:: VectorIterator 생성자

VectorIterator 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>매개 변수

*v*<br/>
IVector \<T> 개체입니다.

### <a name="remarks"></a>설명

첫 번째 구문 예제에서는 기본 생성자를 호출합니다. 두 번째 구문 예제는 IVector 개체에서 VectorIterator를 생성 하는 데 사용 되는 명시적 생성자입니다 \<T> .

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)
