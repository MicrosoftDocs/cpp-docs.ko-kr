---
description: '자세한 정보: Platform:: Collections:: VectorView 클래스'
title: Platform::Collections::VectorView 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: f0d1244ed5331fa9732bdfef1f1b7e2133f99442
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250038"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView 클래스

인덱스로 각각 액세스할 수 있는 순차 개체 컬렉션의 읽기 전용 보기를 나타냅니다. 템플릿 매개 변수로 지정된 컬렉션의 각 개체 형식입니다.

## <a name="syntax"></a>구문

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
`VectorView` 개체에 포함된 요소의 형식입니다.

*E*<br/>
`T`형식의 값을 사용하여 같음을 테스트하기 위한 이진 조건자를 지정합니다. 기본값은 `std::equal_to<T>`입니다.

### <a name="remarks"></a>설명

`VectorView`클래스는 [Windows:: Foundation:: Collections:: IVectorView \<T> ](/uwp/api/windows.foundation.collections.ivectorview-1) 인터페이스와 표준 템플릿 라이브러리 반복기에 대 한 지원을 구현 합니다.

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[VectorView:: VectorView](#ctor)|VectorView 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[VectorView:: First](#first)|VectorView의 첫 번째 요소를 지정하는 반복기를 반환합니다.|
|[VectorView:: GetAt](#getat)|지정된 인덱스가 나타내는 현재 VectorView의 요소를 검색합니다.|
|[VectorView:: GetMany](#getmany)|현재 VectorView에서 지정된 인덱스부터 시작하여 일련의 항목을 검색합니다.|
|[VectorView:: IndexOf](#indexof)|현재 VectorView에서 지정한 항목을 검색하고 있는 경우 항목의 인덱스를 반환합니다.|
|[VectorView::Size](#size)|현재 VectorView 개체의 요소 수를 반환합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`VectorView`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a> VectorView:: First 메서드

VectorView의 첫 번째 요소를 지정하는 반복기를 반환합니다.

### <a name="syntax"></a>구문

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Return Value

VectorView의 첫 번째 요소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

First ()에서 반환 된 반복기를 편리 하 게 유지 하는 방법은 형식 추론 키워드를 사용 하 여 선언 된 변수에 반환 값을 할당 하는 것입니다 **`auto`** . 예: `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a> VectorView:: GetAt 메서드

지정된 인덱스가 나타내는 현재 VectorView의 요소를 검색합니다.

### <a name="syntax"></a>구문

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
VectorView 개체의 특정 요소를 지정하는 0부터 시작하는 부호 없는 정수입니다.

### <a name="return-value"></a>반환 값

`index` 매개 변수로 지정된 요소입니다. 요소 형식은 VectorView 템플릿 매개 변수 *T* 로 지정 됩니다.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a> VectorView:: GetMany 메서드

현재 VectorView에서 지정된 인덱스부터 시작하여 일련의 항목을 검색합니다.

### <a name="syntax"></a>구문

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>매개 변수

*startIndex*<br/>
검색할 항목 시작 부분의 0부터 시작하는 인덱스입니다.

*dest*<br/>
이 작업이 완료되면 `startIndex`로 지정된 요소에서 시작해 VectorView의 마지막 요소에서 끝나는 항목의 배열입니다.

### <a name="return-value"></a>반환 값

검색된 항목의 수입니다.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a> VectorView:: IndexOf 메서드

현재 VectorView에서 지정한 항목을 검색하고 있는 경우 항목의 인덱스를 반환합니다.

### <a name="syntax"></a>구문

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>매개 변수

*value*<br/>
찾을 항목입니다.

*index*<br/>
매개 변수 `value`가 있으면 0부터 시작하는 항목의 인덱스이고, 그렇지 않으면 0입니다.

항목이의 첫 번째 요소 이거나 항목을 찾을 수 없는 경우에는 *인덱스* 매개 변수가 0입니다 `VectorView` . 반환 값이 이면 **`true`** 항목이 검색 되 고 첫 번째 요소 이면이 고, 그렇지 않으면 항목을 찾을 수 없습니다.

### <a name="return-value"></a>반환 값

**`true`** 지정 된 항목이 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="vectorviewsize-method"></a><a name="size"></a> VectorView:: Size 메서드

현재 VectorView 개체의 요소 수를 반환합니다.

### <a name="syntax"></a>구문

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Return Value

현재 VectorView의 요소 수입니다.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a> VectorView:: VectorView 생성자

VectorView 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>매개 변수

*Cloud-init*<br/>
현재 VectorView를 초기화하는 데 사용되는 개체 컬렉션의 형식입니다.

*l*<br/>
VectorView를 초기화 하는 데 사용 되는 요소를 포함 하는 [std:: initializer_list](../standard-library/initializer-list-class.md) 입니다.

*N*<br/>
현재 VectorView를 초기화하는 데 사용되는 개체 컬렉션의 요소 수입니다.

*size*<br/>
VectorView의 요소 수입니다.

*value*<br/>
현재 VectorView의 각 요소를 초기화하는 데 사용되는 값입니다.

*v*<br/>
현재 VectorView를 초기화 하는 데 사용 되는 [std:: vector](../standard-library/vector-class.md) 에 대 [한 Lvalues 및 rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) 입니다.

*ptr*<br/>
현재 VectorView를 초기화하는 데 사용되는 `std::vector`에 대한 포인터입니다.

*arr*<br/>
현재 VectorView를 초기화 하는 데 사용 되는 [Platform:: Array](../cppcx/platform-array-class.md) 개체입니다.

*은*<br/>
현재 VectorView를 초기화 하는 데 사용 되는 [std:: array](../standard-library/array-class-stl.md) 개체입니다.

*first*<br/>
현재 VectorView를 초기화하는 데 사용되는 개체 시퀀스의 첫 번째 요소입니다. 의 형식은 `first` *완벽 한 전달* 수단으로 전달 됩니다. 자세한 내용은 [RValue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

*last*<br/>
현재 VectorView를 초기화하는 데 사용되는 개체 시퀀스의 마지막 요소입니다. 의 형식은 `last` *완벽 한 전달* 수단으로 전달 됩니다. 자세한 내용은 [RValue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)<br/>
[C++로 Windows Runtime 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
