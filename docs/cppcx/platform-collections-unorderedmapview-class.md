---
title: Platform::Collections::UnorderedMapView 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: ebda6f179c365aaa009eb45425a36058105def10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161636"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView 클래스

읽기 전용 보기를 키/값 쌍의 컬렉션인 *맵*으로 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>매개 변수

*K*<br/>
키/값 쌍의 키 형식입니다.

*V*<br/>
키/값 쌍의 값 형식입니다.

*C*<br/>
같은지 확인하기 위해 두 키 값을 비교할 수 있는 함수 개체를 제공하는 형식입니다. 기본적으로 [std:: equal_to\<K >](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>설명

UnorderedMapView는 구체적인 C++ 구현의 합니다 [Windows::Foundation::Collections::IMapView\<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) 응용 프로그램 이진 인터페이스 ABI ()를 통해 전달 되는 인터페이스입니다. 자세한 내용은 [컬렉션(C++/CX)](../cppcx/collections-c-cx.md)을 참조하세요.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|UnorderedMapView 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[UnorderedMapView::First](#first)|맵 뷰의 첫 번째 요소로 초기화하는 반복기를 반환합니다.|
|[UnorderedMapView::HasKey](#haskey)|현재 UnorderedMapView에 지정한 키가 들어 있는지 여부를 확인합니다.|
|[UnorderedMapView::Lookup](#lookup)|현재 UnorderedMapView 개체의 지정된 키에 있는 요소를 검색합니다.|
|[UnorderedMapView::Size](#size)|현재 UnorderedMapView 개체의 요소 수를 반환합니다.|
|[UnorderedMapView::Split](#split)|원래 UnorderedMapView 개체를 두 개의 UnorderedMapView 개체로 분할합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`UnorderedMapView`

### <a name="requirements"></a>요구 사항

**헤더:** collection.h

**네임스페이스:** Platform::Collections

## <a name="first"></a>  UnorderedMapView::First 메서드

첫 번째를 지정 하는 반복기를 반환 [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) unordered map의 요소입니다.

### <a name="syntax"></a>구문

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>반환 값

맵 뷰의 첫 번째 요소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

First ()에서 반환 된 반복기를 보유 하는 편리한 방법을 사용 하 여 선언 된 변수에 반환 값을 할당 하는 것은 **자동** 형식 추론 키워드입니다. 예를 들어, `auto x = myMapView->First();`을 입력합니다.

## <a name="haskey"></a>  UnorderedMapView::HasKey 메서드

현재 UnorderedMap에 지정한 키가 들어 있는지 여부를 확인합니다.

### <a name="syntax"></a>구문

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
요소를 찾는 데 사용되는 키입니다. 유형의 `key` typename 됩니다 *K*합니다.

### <a name="return-value"></a>반환 값

**true 이면** 이 고, 그렇지 않으면 키가 없으면 **false**합니다.

## <a name="lookup"></a>  UnorderedMapView::Lookup 메서드

K 형식의 지정된 키와 연결된 V 형식의 값을 검색합니다.

### <a name="syntax"></a>구문

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
UnorderedMapView에서 요소를 찾는 데 사용되는 키입니다. 유형의 `key` typename 됩니다 *K*합니다.

### <a name="return-value"></a>반환 값

`key`와 쌍을 이루는 값입니다. 반환 값의 형식은 typename *V*합니다.

## <a name="size"></a>  UnorderedMapView::Size 메서드

개수를 반환 [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) UnorderedMapView에 있는 요소입니다.

### <a name="syntax"></a>구문

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>반환 값

UnorderedMapView의 요소 수입니다.

## <a name="split"></a>  UnorderedMapView::Split 메서드

현재 UnorderedMapView 개체를 두 개의 UnorderedMapView 개체로 나눕니다. 이 메서드는 작동하지 않습니다.

### <a name="syntax"></a>구문

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>매개 변수

*firstPartition*<br/>
원래 UnorderedMapView 개체의 첫 번째 부분입니다.

*secondPartition*<br/>
원래 UnorderedMapView 개체의 두 번째 부분입니다.

### <a name="remarks"></a>설명

이 메서드는 작동하지 않으며, 아무 작업도 수행하지 않습니다.

## <a name="ctor"></a>  UnorderedMapView::UnorderedMapView 생성자

UnorderedMapView 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>매개 변수

*n*<br/>
공간을 미리 할당할 요소의 수입니다.

*InIt*<br/>
UnorderedMapView의 형식 이름입니다.

*H*<br/>
키에 해시 값을 사용할 수 있는 함수 개체입니다. 기본값으로 [std:: hash\<K >](../standard-library/hash-class.md) 형식에는 `std::hash` 지원 합니다.

*P*<br/>
같은지 확인하기 위해 두 키를 비교할 수 있는 함수 개체를 제공하는 형식입니다. 기본값으로 [std:: equal_to\<K >](../standard-library/equal-to-struct.md)합니다.

*m*<br/>
참조 또는 [Lvalue 및 Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) 에 [std:: unordered_map](../standard-library/unordered-map-class.md) UnorderedMapView를 초기화 하는 데 사용 되는 합니다.

*first*<br/>
UnorderedMapView를 초기화하는 데 사용되는 요소 범위에서 첫 번째 요소의 입력 반복기입니다.

*last*<br/>
UnorderedMapView를 초기화하는 데 사용되는 요소 범위 다음의 첫 번째 요소의 입력 반복기입니다.

## <a name="see-also"></a>참고자료

[Platform::Collections 네임스페이스](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)
