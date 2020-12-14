---
description: '자세한 정보: Platform:: Collections:: UnorderedMap 클래스'
title: Platform::Collections::UnorderedMap 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 51acfa7e411f96addd8a33024224779c32ebcda0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242537"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap 클래스

키-값 쌍의 컬렉션인 순서가 지정되지 않은 *맵* 을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>매개 변수

*K*<br/>
키/값 쌍의 키 형식입니다.

*V*<br/>
키/값 쌍의 값 형식입니다.

*C*<br/>
두 요소 값을 정렬 키로 비교하여 맵에서 해당 상대 순서를 확인할 수 있는 함수 개체를 제공하는 형식입니다. 기본적으로 [std:: equal_to \<K> ](../standard-library/equal-to-struct.md)입니다.

### <a name="remarks"></a>설명

허용 유형은 다음과 같습니다.

- integers

- 인터페이스 클래스 ^

- public ref 클래스 ^

- value struct

- public enum 클래스

**UnorderedMap** 은 기본적으로 Windows 런타임 형식의 저장을 지 원하는 [std:: unordered_map](../standard-library/unordered-map-class.md) 에 대 한 래퍼입니다. 공용 Windows 런타임 인터페이스를 통해 전달 되는 [Windows:: Foundation:: Collections:: IMap](/uwp/api/windows.foundation.collections.imap-2) 및 [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) 형식의 구체적 구현입니다. 공용 반환 값 또는 매개 변수에서 `Platform::Collections::UnorderedMap` 형식을 사용하려고 하면 컴파일러 오류 C3986이 발생합니다. 매개 변수나 반환 값 형식을 [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2)으로 변경하여 오류를 수정할 수 있습니다.

자세한 내용은 [컬렉션](../cppcx/collections-c-cx.md)을 참조 하세요.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[UnorderedMap:: UnorderedMap](#ctor)|Map 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[UnorderedMap:: Clear](#clear)|현재 Map 개체에서 모든 키/값 쌍을 제거합니다.|
|[UnorderedMap:: First](#first)|맵의 첫 번째 요소를 지정하는 반복기를 반환합니다.|
|[UnorderedMap:: GetView](#getview)|현재 Map의 읽기 전용 뷰, 즉 Platform::Collections::UnorderedMapView 클래스를 반환합니다.|
|[UnorderedMap:: HasKey](#haskey)|현재 Map에 지정한 키가 들어 있는지 여부를 확인합니다.|
|[UnorderedMap:: Insert](#insert)|지정한 키/값 쌍을 현재 Map 개체에 추가합니다.|
|[UnorderedMap:: Lookup](#lookup)|현재 Map 개체의 지정된 키에 있는 요소를 검색합니다.|
|[UnorderedMap:: Remove](#remove)|지정한 키/값 쌍을 현재 Map 개체에서 삭제합니다.|
|[UnorderedMap:: Size](#size)|현재 Map 개체의 요소 수를 반환합니다.|

### <a name="events"></a>이벤트

| Name | 설명 |
|--|--|
| [Map:: MapChanged](#mapchanged) 이벤트 | Map이 변경될 때 발생합니다. |

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`UnorderedMap`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a> UnorderedMap:: Clear 메서드

현재 UnorderedMap 개체에서 모든 키-값 쌍을 제거합니다.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a> UnorderedMap:: First 메서드

순서가 지정 되지 않은 맵에서 첫 번째 [Windows:: Foundation:: Collections:: inputiterator<ikeyvaluepair<k \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) 요소를 지정 하는 반복기를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Return Value

맵의 첫 번째 요소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

First ()에서 반환 된 반복기를 편리 하 게 유지 하는 방법은 형식 추론 키워드를 사용 하 여 선언 된 변수에 반환 값을 할당 하는 것입니다 **`auto`** . 예: `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a> UnorderedMap:: GetView 메서드

현재 UnorderedMap의 읽기 전용 뷰를 반환 합니다. 즉, [Windows:: Foundation:: collections:: IMapView:: IMapView](/uwp/api/windows.foundation.collections.imapview-2) 인터페이스를 구현 하는 [Platform:: Collections:: UnorderedMapView 클래스](../cppcx/platform-collections-unorderedmapview-class.md) 입니다.

### <a name="syntax"></a>구문

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Return Value

`UnorderedMapView` 개체입니다.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a> UnorderedMap:: HasKey 메서드

현재 UnorderedMap에 지정한 키가 들어 있는지 여부를 확인합니다.

### <a name="syntax"></a>구문

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
UnorderedMap 요소를 찾는 데 사용되는 키입니다. *키* 의 형식은 형식 이름 *K* 입니다.

### <a name="return-value"></a>반환 값

**`true`** 키가 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="unorderedmapinsert-method"></a><a name="insert"></a> UnorderedMap:: Insert 메서드

지정한 키-값 쌍을 현재 UnorderedMap 개체에 추가합니다.

### <a name="syntax"></a>구문

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키-값 쌍의 키 부분입니다. *키* 의 형식은 형식 이름 *K* 입니다.

*value*<br/>
키-값 쌍의 값 부분입니다. *값* 의 형식은 형식 이름 *V* 입니다.

### <a name="return-value"></a>반환 값

**`true`** 현재 Map의 기존 요소 키가 *키* 와 일치 하 고 해당 요소의 값 부분이 *value* 로 설정 되어 있으면입니다. **`false`** 현재 Map의 기존 요소가 *키* 와 일치 하지 않고 키 및 *값* 매개 *변수를 키* -값 쌍으로 만든 다음 현재 UnorderedMap에 추가 하면입니다.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a> UnorderedMap:: Lookup 메서드

K 형식의 지정된 키와 연결된 V 형식의 값을 검색합니다.

### <a name="syntax"></a>구문

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
UnorderedMap에서 요소를 찾는 데 사용되는 키입니다. *키* 의 형식은 형식 이름 *K* 입니다.

### <a name="return-value"></a>반환 값

*키* 와 쌍으로 연결 된 값입니다. 반환 값의 형식은 형식 이름 *V* 입니다.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a> UnorderedMap:: MapChanged

맵에서 항목이 삽입되거나 제거될 때 발생합니다.

### <a name="syntax"></a>Syntax

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>속성 값/반환 값

이벤트를 발생 시킨 개체에 대 한 정보 및 발생 한 변경 내용의 종류를 포함 하는 [Mapchangedeventhandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) 입니다. [Imapchangedeventargs&lt \<K> ](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) 및 [collectionchange 열거](/uwp/api/windows.foundation.collections.collectionchange)도 참조 하세요.

## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값

C # 또는 Visual Basic project IMap를 IDictionary로 Windows 런타임 앱을 \<K,V> \<K,V> 합니다.

## <a name="unorderedmapremove-method"></a><a name="remove"></a> UnorderedMap:: Remove 메서드

지정한 키-값 쌍을 UnorderedMap 개체에서 삭제합니다.

### <a name="syntax"></a>구문

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키-값 쌍의 키 부분입니다. *키* 의 형식은 형식 이름 *K* 입니다.

## <a name="unorderedmapsize-method"></a><a name="size"></a> UnorderedMap:: Size 메서드

UnorderedMap의 [Windows:: Foundation:: Collections:: inputiterator<ikeyvaluepair<k \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) 요소 수를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Return Value

UnorderedMap의 요소 수입니다.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a> UnorderedMap:: UnorderedMap 생성자

UnorderedMap 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>매개 변수

*Cloud-init*<br/>
현재 UnorderedMap의 형식 이름입니다.

*P*<br/>
같은지 여부를 확인하기 위해 두 키를 비교할 수 있는 함수 개체입니다. 이 매개 변수의 기본값은 [std:: \<K> equal_to](../standard-library/equal-to-struct.md)입니다.

*H*<br/>
키에 대한 해시 값을 생성하는 함수 개체입니다. 이 매개 변수는 클래스가 지 원하는 키 형식에 대 한 [해시 클래스 1](../standard-library/hash-class.md) 로 기본 설정 됩니다.

*m*<br/>
현재 UnorderedMap를 초기화 하는 데 사용 되는 [std:: unordered_map](../standard-library/unordered-map-class.md) 에 대 한 참조 또는 [Lvalues 및 rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) 입니다.

*l*<br/>
지도를 초기화 하는 데 사용 되는 [std::p air](../standard-library/pair-structure.md) 개체의 [std:: initializer_list](../standard-library/initializer-list-class.md) 입니다.

*first*<br/>
현재 UnorderedMap을 초기화하는 데 사용되는 요소 범위에서 첫 번째 요소의 입력 반복기입니다.

*last*<br/>
현재 UnorderedMap을 초기화하는 데 사용되는 요소 범위 다음의 첫 번째 요소의 입력 반복기입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)<br/>
[Platform:: Collections 네임 스페이스](../cppcx/platform-collections-namespace.md)<br/>
[Platform:: Collections:: Map 클래스](../cppcx/platform-collections-map-class.md)<br/>
[Platform:: Collections:: UnorderedMapView 클래스](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[컬렉션](../cppcx/collections-c-cx.md)<br/>
[C++로 Windows Runtime 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
