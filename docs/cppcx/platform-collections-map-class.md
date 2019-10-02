---
title: Platform::Collections::Map 클래스
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: 81721d719a424250beed89f4a5656b3f2fc27922
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816305"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 클래스

키/값 쌍의 컬렉션인 *맵*을 나타냅니다. XAML [데이터 바인딩을](/windows/uwp/data-binding/data-binding-in-depth)지원 하기 위해 [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap_k_v_) 을 구현 합니다.

## <a name="syntax"></a>구문

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>매개 변수

*K*<br/>
키/값 쌍의 키 형식입니다.

*V*<br/>
키/값 쌍의 값 형식입니다.

*C*<br/>
두 요소 값을 정렬 키로 비교하여 맵에서 해당 상대 순서를 확인할 수 있는 함수 개체를 제공하는 형식입니다. 기본적으로 [std:: less @ no__t-1k >](../standard-library/less-struct.md)합니다.

*__is_valid_winrt_type ()* *K* 및 *V* 형식의 유효성을 검사 하 고 해당 형식을 맵에 저장할 수 없는 경우 친숙 한 오류 메시지를 제공 하는 컴파일러 생성 함수입니다.

### <a name="remarks"></a>설명

허용되는 형식은 다음과 같습니다.

- 정수

- 인터페이스 클래스 ^

- public ref 클래스 ^

- value struct

- public enum 클래스

Map은 기본적으로 [std::map](../standard-library/map-class.md)에 대한 래퍼입니다. 이 클래스는 C++ [Windows:: Foundation:: Collections:: IMap < Windows:: Foundation:: Collections:: inputiterator<ikeyvaluepair<k @ no__t-2k, V > >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) 및 [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) 형식의 구체적 구현입니다. 런타임 인터페이스. 공용 반환 값 또는 매개 변수에서 `Platform::Collections::Map` 형식을 사용하려고 하면 컴파일러 오류 C3986이 발생합니다. 매개 변수 또는 반환 값의 형식을 [Windows:: Foundation:: Collections:: IMap @ no__t-1k, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)로 변경 하 여 오류를 해결할 수 있습니다.

자세한 내용은 [컬렉션](../cppcx/collections-c-cx.md)합니다.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Map::Map](#ctor)|Map 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Map::Clear](#clear)|현재 Map 개체에서 모든 키/값 쌍을 제거합니다.|
|[Map::First](#first)|맵의 첫 번째 요소를 지정하는 반복기를 반환합니다.|
|[Map::GetView](#getview)|현재 Map의 읽기 전용 보기, 즉 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)를 반환합니다.|
|[Map::HasKey](#haskey)|현재 Map에 지정한 키가 들어 있는지 여부를 확인합니다.|
|[Map::Insert](#insert)|지정한 키/값 쌍을 현재 Map 개체에 추가합니다.|
|[Map::Lookup](#lookup)|현재 Map 개체의 지정된 키에 있는 요소를 검색합니다.|
|[Map::Remove](#remove)|지정한 키/값 쌍을 현재 Map 개체에서 삭제합니다.|
|[Map::Size](#size)|현재 Map 개체의 요소 수를 반환합니다.|

### <a name="events"></a>이벤트

|||
|-|-|
|이름|설명|
|[Map:: MapChanged](#mapchanged) 이벤트|Map이 변경될 때 발생합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`Map`

### <a name="requirements"></a>요구 사항

**헤더:** collection.h

**네임스페이스:** Platform::Collections

## <a name="clear"></a>Map:: Clear 메서드

현재 Map 개체에서 모든 키/값 쌍을 제거합니다.

### <a name="syntax"></a>구문

```cpp
virtual void Clear();
```

## <a name="first"></a>Map:: First 메서드

맵의 첫 번째 요소를 지정하는 반복기 또는 `nullptr`(맵이 비어 있는 경우)을 반환합니다.

### <a name="syntax"></a>구문

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>반환 값

맵의 첫 번째 요소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

First ()에서 반환 된 반복기를 편리 하 게 유지 하는 방법은 **auto** 형식 추론 키워드로 선언 된 변수에 반환 값을 할당 하는 것입니다. 예를 들어, `auto x = myMap->First();`을 입력합니다.

## <a name="getview"></a>Map:: GetView 메서드

현재 지도의 읽기 전용 뷰를 반환 합니다. 즉, [Windows:: Foundation:: Collections:: IMapView @ no__t-1K, V >]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) 인터페이스를 구현 하는 [Platform:: Collections:: MapView 클래스](../cppcx/platform-collections-mapview-class.md)입니다.

### <a name="syntax"></a>구문

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>반환 값

`MapView` 개체입니다.

## <a name="haskey"></a>Map:: HasKey 메서드

현재 Map에 지정한 키가 들어 있는지 여부를 확인합니다.

### <a name="syntax"></a>구문

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
Map 요소를 찾는 데 사용되는 키입니다. *키* 의 형식은 형식 이름 *K*입니다.

### <a name="return-value"></a>반환 값

키가 있으면 **true** 이 고, 그렇지 않으면입니다. 그렇지 않으면 **false**입니다.

## <a name="insert"></a>Map:: Insert 메서드

지정한 키/값 쌍을 현재 Map 개체에 추가합니다.

### <a name="syntax"></a>구문

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키-값 쌍의 키 부분입니다. *키* 의 형식은 형식 이름 *K*입니다.

*value*<br/>
키-값 쌍의 값 부분입니다. *값* 의 형식은 형식 이름 *V*입니다.

### <a name="return-value"></a>반환 값

현재 Map의 기존 요소 키가 *키* 와 일치 하 고 해당 요소의 값 부분이 *value*로 설정 되어 있으면 **true** 입니다. 현재 Map의 기존 요소가 *키* 와 일치 하지 않고 *키 및* *값* 매개 변수가 키-값 쌍으로 만들어진 다음 현재 맵에 추가 되 면 **false** 입니다.

## <a name="lookup"></a>Map:: Lookup 메서드

K 형식의 지정된 키(해당 키가 있는 경우)와 연결된 V 형식의 값을 검색합니다.

### <a name="syntax"></a>구문

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
지도에서 요소를 찾는 데 사용되는 키입니다. *키* 의 형식은 형식 이름 *K*입니다.

### <a name="return-value"></a>반환 값

*키*와 쌍으로 연결 된 값입니다. 반환 값의 형식은 형식 이름 *V*입니다.

### <a name="remarks"></a>설명

키가 없으면 [Platform:: OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) 이 throw 됩니다.

## <a name="ctor"></a>Map:: Map 생성자

Map 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>매개 변수

*InIt*<br/>
현재 Map의 형식 이름입니다.

*comp*<br/>
두 요소 값을 정렬 키로 비교하여 맵에서 해당 상대 순서를 확인할 수 있는 함수 개체를 제공하는 형식입니다.

*m*<br/>
현재 Map을 초기화 하는 데 사용 되는 `map Class`에 대 한 참조 또는 [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) 입니다.

*first*<br/>
현재 Map를 초기화하는 데 사용되는 요소 범위에서 첫 번째 요소의 입력 반복기입니다.

*last*<br/>
현재 Map를 초기화하는 데 사용되는 요소 범위 다음의 첫 번째 요소의 입력 반복기입니다.

## <a name="mapchanged"></a>Map:: MapChanged 이벤트

맵에서 항목이 삽입되거나 제거될 때 발생합니다.

### <a name="syntax"></a>구문

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>속성 값/반환 값

[Mapchangedeventhandler @ no__t-1k, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) 이벤트를 발생 시킨 개체에 대 한 정보 및 발생 한 변경 내용의 종류를 포함 합니다. 또한 [imapchangedeventargs&lt @ no__t-1k >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) 및 [collectionchange 열거](/uwp/api/windows.foundation.collections.collectionchange)를 참조 하세요.

## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값

또는를 사용 하 C# 는 앱 Windows 런타임 Visual Basic IMap @ No__t-1K, v >을 IDictionary @ No__t-2K, v >로 사용 합니다.

## <a name="remove"></a>Map:: Remove 메서드

지정한 키/값 쌍을 현재 Map 개체에서 삭제합니다.

### <a name="syntax"></a>구문

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키-값 쌍의 키 부분입니다. *키* 의 형식은 형식 이름 *K*입니다.

## <a name="size"></a>Map:: Size 메서드

맵의 [Windows:: Foundation:: Collections:: inputiterator<ikeyvaluepair<k @ no__t-1k, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) 요소 수를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>반환 값

Map의 요소 수입니다.

## <a name="see-also"></a>참조

[컬렉션(C++/CX)](collections-c-cx.md)<br/>
[Platform 네임 스페이스](platform-namespace-c-cx.md)<br/>
[C++로 Windows Runtime 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
