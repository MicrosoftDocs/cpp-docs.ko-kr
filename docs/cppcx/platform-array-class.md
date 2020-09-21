---
title: Platform::Array 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 4903c18f981c87c418a6ab08595816ce22a7413c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742946"
---
# <a name="platformarray-class"></a>Platform::Array 클래스

ABI(애플리케이션 이진 인터페이스)를 통해 받고 전달할 수 있는 수정 가능한 1차원 배열을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>멤버

Platform:: Array는 platform:: [WriteOnlyArray 클래스](../cppcx/platform-writeonlyarray-class.md) 의 모든 메서드를 상속 하 고 `Value` [Platform:: iboxarray 인터페이스](../cppcx/platform-iboxarray-interface.md)의 속성을 구현 합니다.

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[Array 생성자](#ctor)|클래스 템플릿 매개 변수 *T*로 지정 된, 수정 가능한 1 차원 형식 배열을 초기화 합니다.|

### <a name="methods"></a>메서드

[Platform:: WriteOnlyArray 클래스](../cppcx/platform-writeonlyarray-class.md)를 참조 하세요.

### <a name="properties"></a>속성

| 속성 | Description |
|--|--|
| [Array:: Value](#value) | 현재 배열에 대한 핸들을 검색합니다. |

### <a name="remarks"></a>설명

Array 클래스는 봉인되므로 상속할 수 없습니다.

Windows 런타임 형식 시스템은 가변 배열의 개념을 지원 하지 않으므로를 `IVector<Platform::Array<T>>` 반환 값 또는 메서드 매개 변수로 전달할 수 없습니다. ABI 전반에서 가변 배열 또는 시퀀스의 시퀀스를 전달하려면 `IVector<IVector<T>^>`를 사용합니다.

Platform:: Array를 사용 하는 시기 및 방법에 대 한 자세한 내용은 [array 및 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)를 참조 하세요.

이 클래스는 컴파일러가 자동으로 포함하는 vccorlib.h 헤더에 정의됩니다. IntelliSense에는 표시 되지만 개체 브라우저에는 표시 되지 않습니다 .이는 플랫폼별에 정의 된 공용 형식이 아니기 때문입니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: **/Zw**

## <a name="array-constructors"></a><a name="ctor"></a> 배열 생성자

클래스 템플릿 매개 변수 *T*로 지정 된, 수정 가능한 1 차원 형식 배열을 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
클래스 템플릿 매개 변수입니다.

*size*<br/>
배열의 요소 수입니다.

*data*<br/>
이 Array 개체를 초기화하는 데 사용되는 `T` 형식 데이터의 배열에 대한 포인터입니다.

### <a name="remarks"></a>설명

Platform:: Array 인스턴스를 만드는 방법에 대 한 자세한 내용은 [array 및 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)를 참조 하세요.

## <a name="arrayget-method"></a><a name="get"></a> Array:: get 메서드

지정된 인덱스 위치에서 배열 요소에 대한 참조를 검색합니다.

### <a name="syntax"></a>구문

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>매개 변수

*index*<br/>
배열에서 요소를 식별하는 0부터 시작하는 인덱스를 확인합니다. 최소 인덱스는 0이 고 최대 인덱스는 `size` [배열 생성자](#ctor)의 매개 변수에 지정 된 값입니다.

### <a name="return-value"></a>반환 값

`index` 매개 변수로 지정된 배열 요소입니다.

## <a name="arrayvalue-property"></a><a name="value"></a> Array:: Value 속성

현재 배열에 대한 핸들을 검색합니다.

### <a name="syntax"></a>구문

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Return Value

현재 배열에 대한 핸들입니다.

## <a name="see-also"></a>추가 정보

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)<br/>
[Array 및 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
