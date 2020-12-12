---
description: '자세한 정보: Platform:: WriteOnlyArray 클래스'
title: Platform::WriteOnlyArray 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: cddbe0d3823ba7b9751bd60844d9ce699546b804
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307771"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray 클래스

호출자가 채울 메서드에 대해 배열을 전달할 때 입력 매개 변수로 사용되는 1차원 배열을 나타냅니다.

이 ref 클래스는 vccorlib.h에서 private으로 선언되므로 메타데이터로 내보내지지 않고 C++에서만 사용할 수 있습니다. 이 클래스는 호출자가 할당한 배열을 받는 입력 매개 변수로만 사용해야 합니다. 이 클래스는 사용자 코드에서 생성할 수 없으며 C++ 메서드가 해당 배열에 직접 작성할 수 있게 합니다( *FillArray* 패턴). 자세한 내용은 [Array 및 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)를 참조 하세요.

## <a name="syntax"></a>구문

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

이러한 메서드의 액세스 가능성은 internal이므로 C++ 앱 또는 구성 요소 내에서만 액세스할 수 있습니다.

|Name|설명|
|----------|-----------------|
|[WriteOnlyArray:: begin](#begin)|배열의 첫 번째 요소를 가리키는 반복기입니다.|
|[WriteOnlyArray: ata:D](#data)|데이터 버퍼에 대한 포인터입니다.|
|[WriteOnlyArray:: end](#end)|배열의 마지막 요소를 지난 요소를 가리키는 반복기입니다.|
|[WriteOnlyArray:: FastPass](#fastpass)|시스템에서 투명하게 수행되는 최적화인 FastPass 메커니즘을 배열이 사용할 수 있는지 여부를 나타냅니다. 이 메서드는 코드에 사용하지 마세요.|
|[WriteOnlyArray:: Length](#length)|배열의 요소 수를 반환합니다.|
|[WriteOnlyArray:: set](#set)|지정한 요소를 지정한 값으로 설정합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`WriteOnlyArray`

### <a name="requirements"></a>요구 사항

컴파일러 옵션: **/Zw**

**메타데이터:** Platform.winmd

**네임스페이스:** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a> WriteOnlyArray:: begin 메서드

배열의 첫 번째 요소에 대한 포인터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
T* begin() const;
```

### <a name="return-value"></a>Return Value

배열의 첫 번째 요소에 대한 포인터입니다.

### <a name="remarks"></a>설명

이 반복기를 `std::sort`와 같은 STL 알고리즘과 함께 사용하여 배열 요소에 대해 작업을 수행할 수 있습니다.

## <a name="writeonlyarraydata-property"></a><a name="data"></a> WriteOnlyArray::D ata 속성

데이터 버퍼에 대한 포인터입니다.

### <a name="syntax"></a>구문

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Return Value

원시 배열 바이트에 대한 포인터입니다.

## <a name="writeonlyarrayend-method"></a><a name="end"></a> WriteOnlyArray:: end 메서드

배열의 마지막 요소를 지난 요소에 대한 포인터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
T* end() const;
```

### <a name="return-value"></a>Return Value

배열의 마지막 요소를 지난 요소에 대한 포인터 반복기입니다.

### <a name="remarks"></a>설명

이 반복기를 STL 알고리즘과 함께 사용하여 배열 요소에 대해 `std::sort`와 같은 작업을 수행할 수 있습니다.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a> WriteOnlyArray:: FastPass 속성

내부 FastPass 최적화를 수행할 수 있는지 여부를 나타냅니다. 사용자 코드에서는 사용되지 않습니다.

### <a name="syntax"></a>구문

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Return Value

배열이 FastPass인지 여부를 나타내는 부울 값입니다.

## <a name="writeonlyarrayget-method"></a><a name="get"></a> WriteOnlyArray:: get 메서드

지정한 인덱스의 요소를 반환합니다.

### <a name="syntax"></a>구문

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>매개 변수

*indexArg*<br/>
사용할 인덱스입니다.

### <a name="return-value"></a>반환 값

## <a name="writeonlyarraylength-property"></a><a name="length"></a> WriteOnlyArray:: Length 속성

호출자가 할당한 배열의 요소 수를 반환합니다.

### <a name="syntax"></a>구문

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Return Value

배열의 요소 수입니다.

## <a name="writeonlyarrayset-function"></a><a name="set"></a> WriteOnlyArray:: set 함수

지정한 인덱스의 지정된 값을 배열에 설정합니다.

### <a name="syntax"></a>구문

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>매개 변수

*indexArg*<br/>
설정할 요소의 인덱스입니다.

*이상*<br/>
`indexArg`에서 설정할 값입니다.

### <a name="return-value"></a>반환 값

방금 설정한 요소에 대한 참조입니다.

### <a name="remarks"></a>설명

HRESULT 값을 해석 하는 방법에 대 한 자세한 내용은 [COM 오류 코드 구조](/windows/win32/com/structure-of-com-error-codes)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)<br/>
[C++로 Windows Runtime 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
