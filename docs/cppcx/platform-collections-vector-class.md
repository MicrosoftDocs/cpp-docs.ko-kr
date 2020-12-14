---
description: '자세한 정보: Platform:: Collections:: Vector 클래스'
title: Platform::Collections::Vector 클래스
ms.date: 12/04/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: b13221c6280e0e94572cb4b6710bb59fbd7db4c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221191"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 클래스

개별적으로 인덱스에 의해 액세스될 수 있는 개체의 순차적인 컬렉션을 나타냅니다. XAML [데이터 바인딩을](/windows/uwp/data-binding/data-binding-in-depth)지원 하기 위해 [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) 을 구현 합니다.

## <a name="syntax"></a>구문

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
Vector 개체에 포함된 요소의 형식입니다.

*E*<br/>
*T* 형식의 값과 같은지 테스트 하기 위한 이진 조건자를 지정 합니다. 기본값은 `std::equal_to<T>` 입니다.

### <a name="remarks"></a>설명

허용 유형은 다음과 같습니다.

1. integers

1. 인터페이스 클래스 ^

1. public ref 클래스 ^

1. value struct

1. public enum 클래스

**Vector** 클래스는 [Windows:: Foundation:: Collections:: IVector](/uwp/api/windows.foundation.collections.ivector-1) 인터페이스의 구체적인 c + + 구현입니다.

공용 반환 값 또는 매개 변수에서 **Vector** 형식을 사용 하려고 하면 컴파일러 오류 c 3986이 발생 합니다. 매개 변수나 반환 값 형식을 [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1)로 변경하여 오류를 수정할 수 있습니다. 자세한 내용은 [컬렉션(C++/CX)](../cppcx/collections-c-cx.md)을 참조하세요.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Vector:: Vector](#ctor)|Vector 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Vector::Append](#append)|현재 Vector의 마지막 항목 다음에 지정된 항목을 삽입합니다.|
|[Vector:: Clear](#clear)|현재 Vector의 모든 요소를 삭제합니다.|
|[Vector:: First](#first)|Vector의 첫 번째 요소를 지정하는 반복기를 반환합니다.|
|[Vector:: GetAt](#getat)|지정된 인덱스로 식별되는 현재 Vector의 요소를 검색합니다.|
|[Vector:: GetMany](#getmany)|현재 Vector에서 지정된 인덱스부터 시작하여 일련의 항목을 검색합니다.|
|[Vector:: GetView](#getview)|Vector의 읽기 전용 보기, 즉 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)를 반환합니다.|
|[Vector:: IndexOf](#indexof)|현재 Vector에서 지정한 항목을 검색하고 있는 경우 항목의 인덱스를 반환합니다.|
|[Vector::InsertAt](#insertat)|지정 된 항목을 지정 된 인덱스로 식별 되는 요소의 현재 Vector에 삽입 합니다.|
|[Vector::ReplaceAll](#replaceall)|현재 Vector에서 요소를 삭제한 다음 지정된 배열의 요소를 삽입합니다.|
|[Vector::RemoveAt](#removeat)|현재 Vector에서 지정된 인덱스로 식별되는 요소를 삭제합니다.|
|[Vector::RemoveAtEnd](#removeatend)|현재 Vector의 끝에 있는 요소를 삭제합니다.|
|[Vector::SetAt](#setat)|현재 Vector에서 지정된 인덱스로 식별되는 요소에 지정된 값을 할당합니다.|
|[Vector:: Size](#size)|현재 Vector 개체의 요소 수를 반환합니다.|

### <a name="events"></a>이벤트

| Name | 설명 |
|--|--|
| 이벤트 [Windows:: Foundation:: Collection:: VectorChangedEventHandler \<T> ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) | Vector가 변경될 때 발생합니다. |

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Vector`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a> Vector:: Append 메서드

현재 Vector의 마지막 항목 다음에 지정된 항목을 삽입합니다.

### <a name="syntax"></a>구문

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
Vector에 삽입할 항목입니다. *항목* 의 형식은 *T* 형식 이름으로 정의 됩니다.

## <a name="vectorclear-method"></a><a name="clear"></a> Vector:: Clear 메서드

현재 Vector의 모든 요소를 삭제합니다.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a> Vector:: First 메서드

Vector의 첫 번째 요소를 가리키는 반복기를 반환합니다.

### <a name="syntax"></a>구문

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Return Value

Vector의 첫 번째 요소를 가리키는 반복기입니다.

### <a name="remarks"></a>설명

First ()에서 반환 된 반복기를 편리 하 게 유지 하는 방법은 형식 추론 키워드를 사용 하 여 선언 된 변수에 반환 값을 할당 하는 것입니다 **`auto`** . 예: `auto x = myVector->First();`. 이 반복기는 컬렉션의 길이를 알고 있습니다.

STL 함수에 전달할 반복기 쌍이 필요한 경우 free 함수 [Windows:: foundation:: collections:: begin](../cppcx/begin-function.md) 및 [Windows:: Foundation:: collections:: end](../cppcx/end-function.md) 를 사용 합니다.

## <a name="vectorgetat-method"></a><a name="getat"></a> Vector:: GetAt 메서드

지정된 인덱스로 식별되는 현재 Vector의 요소를 검색합니다.

### <a name="syntax"></a>구문

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
Vector 개체의 특정 요소를 지정하는 0부터 시작하는 부호 없는 정수입니다.

### <a name="return-value"></a>반환 값

*Index* 매개 변수로 지정 된 요소입니다. 요소 형식은 *T* 형식 이름으로 정의 됩니다.

## <a name="vectorgetmany-method"></a><a name="getmany"></a> Vector:: GetMany 메서드

현재 Vector에서 지정된 인덱스부터 시작해 일련의 항목을 검색해서 호출자가 할당한 배열에 복사합니다.

### <a name="syntax"></a>구문

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>매개 변수

*startIndex*<br/>
검색할 항목 시작 부분의 0부터 시작하는 인덱스입니다.

*dest*<br/>
*StartIndex* 로 지정 된 요소에서 시작 하 여 벡터의 마지막 요소에서 끝나는 항목의, 호출자가 할당 한 배열입니다.

### <a name="return-value"></a>반환 값

검색된 항목의 수입니다.

### <a name="remarks"></a>설명

이 함수는 클라이언트 코드에서 직접 사용하지 않습니다. [To_vector 함수](../cppcx/to-vector-function.md) 에서 내부적으로 사용 되어 Platform:: vector 인스턴스로만를 std:: vector 인스턴스로 효율적으로 변환할 수 있습니다.

## <a name="vectorgetview-method"></a><a name="getview"></a> Vector:: GetView 메서드

Vector의 읽기 전용 보기, 즉 IVectorView를 반환합니다.

### <a name="syntax"></a>구문

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Return Value

IVectorView 개체입니다.

## <a name="vectorindexof-method"></a><a name="indexof"></a> Vector:: IndexOf 메서드

현재 Vector에서 지정한 항목을 검색하고 있는 경우 항목의 인덱스를 반환합니다.

### <a name="syntax"></a>구문

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>매개 변수

*value*<br/>
찾을 항목입니다.

*index*<br/>
매개 변수 *값* 이 있는 경우 항목의 인덱스 (0부터 시작)입니다. 그렇지 않으면 0입니다.

항목이 벡터의 첫 번째 요소 이거나 항목을 찾을 수 없는 경우에는 *인덱스* 매개 변수가 0입니다. 반환 값이 이면 **`true`** 항목이 검색 되 고 첫 번째 요소 이면이 고, 그렇지 않으면 항목을 찾을 수 없습니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 항목이 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

IndexOf는 std::find_if를 사용하여 항목을 찾습니다. 그러므로 find_if에 필요한 같음 비교를 사용하려면 사용자 지정 요소 형식이 == 및 != 연산자를 오버로드해야 합니다.

## <a name="vectorinsertat-method"></a><a name="insertat"></a> Vector:: InsertAt 메서드

지정 된 항목을 지정 된 인덱스로 식별 되는 요소의 현재 Vector에 삽입 합니다.

### <a name="syntax"></a>구문

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>매개 변수

*index*<br/>
Vector 개체의 특정 요소를 지정하는 0부터 시작하는 부호 없는 정수입니다.

*item*<br/>
*인덱스로* 지정 된 요소에서 벡터에 삽입할 항목입니다. *항목* 의 형식은 *T* 형식 이름으로 정의 됩니다.

## <a name="vectorremoveat-method"></a><a name="removeat"></a> Vector:: RemoveAt 메서드

현재 Vector에서 지정된 인덱스로 식별되는 요소를 삭제합니다.

### <a name="syntax"></a>구문

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
Vector 개체의 특정 요소를 지정하는 0부터 시작하는 부호 없는 정수입니다.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a> Vector:: RemoveAtEnd 메서드

현재 Vector의 끝에 있는 요소를 삭제합니다.

### <a name="syntax"></a>Syntax

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a> Vector:: ReplaceAll 메서드

현재 Vector에서 요소를 삭제한 다음 지정된 배열의 요소를 삽입합니다.

### <a name="syntax"></a>구문

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>매개 변수

*arr*<br/>
*T* 형식 이름으로 정의 되는 형식의 개체 배열입니다.

## <a name="vectorsetat-method"></a><a name="setat"></a> Vector:: SetAt 메서드

현재 Vector에서 지정된 인덱스로 식별되는 요소에 지정된 값을 할당합니다.

### <a name="syntax"></a>구문

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
Vector 개체의 특정 요소를 지정하는 0부터 시작하는 부호 없는 정수입니다.

*item*<br/>
지정된 요소에 할당할 값입니다. *항목* 의 형식은 *T* 형식 이름으로 정의 됩니다.

## <a name="vectorsize-method"></a><a name="size"></a> Vector:: Size 메서드

현재 Vector 개체의 요소 수를 반환합니다.

### <a name="syntax"></a>구문

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Return Value

현재 Vector의 요소 수입니다.

## <a name="vectorvector-constructor"></a><a name="ctor"></a> Vector:: Vector 생성자

Vector 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>매개 변수

*은*<br/>
벡터를 초기화 하는 데 사용 되는 [std:: array](../standard-library/array-class-stl.md) 입니다.

*arr*<br/>
Vector를 초기화 하는 데 사용 되는 [Platform:: Array](../cppcx/platform-array-class.md) 입니다.

*Cloud-init*<br/>
현재 Vector를 초기화하는 데 사용되는 개체 컬렉션의 형식입니다.

*l*<br/>
Vector를 초기화 하는 데 사용 되는 *T* 형식의 개체의 [std:: initializer_list](../standard-library/initializer-list-class.md) 입니다.

*N*<br/>
현재 Vector를 초기화하는 데 사용되는 개체 컬렉션의 요소 수입니다.

*size*<br/>
Vector의 요소 수입니다.

*value*<br/>
현재 Vector의 각 요소를 초기화하는 데 사용되는 값입니다.

*v*<br/>
현재 Vector를 초기화 하는 데 사용 되는 [std:: vector](../standard-library/vector-class.md) 에 대 [한 Lvalues 및 rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) 입니다.

*ptr*<br/>
현재 Vector를 초기화하는 데 사용되는 `std::vector`에 대한 포인터입니다.

*first*<br/>
현재 Vector를 초기화하는 데 사용되는 개체 시퀀스의 첫 번째 요소입니다. *첫 번째* 형식은 *완벽 한 전달* 을 통해 전달 됩니다. 자세한 내용은 [RValue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

*last*<br/>
현재 Vector를 초기화하는 데 사용되는 개체 시퀀스의 마지막 요소입니다. *마지막* 의 형식은 *완벽 한 전달* 방법으로 전달 됩니다. 자세한 내용은 [RValue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컬렉션 (c + +/CX)](collections-c-cx.md)<br/>
[Platform 네임 스페이스](platform-namespace-c-cx.md)<br/>
[C++로 Windows Runtime 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
