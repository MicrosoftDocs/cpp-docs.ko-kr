---
description: '자세히 알아보기: Platform:: Collections:: MapView 클래스'
title: Platform::Collections::MapView 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: 6011948bb3708329f7dcce0841f2bc34879760a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258488"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView 클래스

읽기 전용 보기를 키/값 쌍의 컬렉션인 *맵* 으로 나타냅니다.

## <a name="syntax"></a>구문

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>매개 변수

*K*<br/>
키/값 쌍의 키 형식입니다.

*V*<br/>
키/값 쌍의 값 형식입니다.

*C*<br/>
두 요소 값을 정렬 키로 비교하여 MapView에서 해당 상대 순서를 확인할 수 있는 함수 개체를 제공하는 형식입니다. 기본적으로 [std:: less \<K> ](../standard-library/less-struct.md)입니다.

### <a name="remarks"></a>설명

MapView는 ABI (응용 프로그램 이진 인터페이스)를 통해 전달 되는 [Windows:: Foundation \<K,V> :: Collections:: IMapView](/uwp/api/windows.foundation.collections.imapview-2) 인터페이스의 구체적인 c + + 구현입니다. 자세한 내용은 [컬렉션(C++/CX)](../cppcx/collections-c-cx.md)을 참조하세요.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[MapView:: MapView](#ctor)|MapView 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[MapView:: First](#first)|맵 뷰의 첫 번째 요소로 초기화하는 반복기를 반환합니다.|
|[MapView:: HasKey](#haskey)|현재 MapView에 지정한 키가 들어 있는지 여부를 확인합니다.|
|[MapView:: Lookup](#lookup)|현재 MapView 개체의 지정된 키에 있는 요소를 검색합니다.|
|[MapView::Size](#size)|현재 MapView 개체의 요소 수를 반환합니다.|
|[MapView:: Split](#split)|원래 MapView 개체를 두 개의 MapView 개체로 분할합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`MapView`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform::Collections

## <a name="mapviewfirst-method"></a><a name="first"></a> MapView:: First 메서드

맵 뷰의 첫 번째 요소를 지정하는 반복기를 반환합니다.

### <a name="syntax"></a>구문

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Return Value

맵 뷰의 첫 번째 요소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

First ()에서 반환 된 반복기를 편리 하 게 유지 하는 방법은 형식 추론 키워드를 사용 하 여 선언 된 변수에 반환 값을 할당 하는 것입니다 **`auto`** . 예: `auto x = myMapView->First();`.

## <a name="mapviewhaskey-method"></a><a name="haskey"></a> MapView:: HasKey 메서드

현재 MapView에 지정한 키가 들어 있는지 여부를 확인합니다.

### <a name="syntax"></a>구문

```

bool HasKey(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
MapView 요소를 찾는 데 사용되는 키입니다. *키* 의 형식은 형식 이름 *K* 입니다.

### <a name="return-value"></a>반환 값

**`true`** 키가 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="mapviewlookup-method"></a><a name="lookup"></a> MapView:: Lookup 메서드

K 형식의 지정된 키와 연결된 V 형식의 값을 검색합니다.

### <a name="syntax"></a>구문

```
V Lookup(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
MapView에서 요소를 찾는 데 사용되는 키입니다. 의 형식은 형식 `key` 이름 *K* 입니다.

### <a name="return-value"></a>반환 값

`key`와 쌍을 이루는 값입니다. 반환 값의 형식은 형식 이름 *V* 입니다.

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a> MapView:: MapView 생성자

MapView 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>매개 변수

*Cloud-init*<br/>
현재 MapView의 형식 이름입니다.

*comp*<br/>
두 요소 값을 정렬 키로 비교하여 MapView에서 해당 상대 순서를 확인할 수 있는 함수 개체입니다.

*m*<br/>
현재 MapView를 초기화 하는 데 사용 되는에 대 한 참조 또는 [Lvalues 및 rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) 입니다 `map Class` .

*first*<br/>
현재 MapView를 초기화하는 데 사용되는 요소 범위에서 첫 번째 요소의 입력 반복기입니다.

*last*<br/>
현재 MapView를 초기화하는 데 사용되는 요소 범위 다음의 첫 번째 요소의 입력 반복기입니다.

*l*<br/>
요소가 mapview에 삽입 되는 [std:: initializer_list \<std::pair\<K,V> > ](../standard-library/initializer-list-class.md) 입니다.

## <a name="mapviewsize-method"></a><a name="size"></a> MapView:: Size 메서드

현재 MapView 개체의 요소 수를 반환합니다.

### <a name="syntax"></a>구문

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Return Value

현재 MapView의 요소 수입니다.

## <a name="mapviewsplit-method"></a><a name="split"></a> MapView:: Split 메서드

현재 MapView 개체를 두 개의 MapView 개체로 분할합니다. 이 메서드는 작동하지 않습니다.

### <a name="syntax"></a>구문

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>매개 변수

*firstPartition*<br/>
원래 MapView 개체의 첫 번째 부분입니다.

*secondPartition*<br/>
원래 MapView 개체의 두 번째 부분입니다.

### <a name="remarks"></a>설명

이 메서드는 작동하지 않으며, 아무 작업도 수행하지 않습니다.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)
