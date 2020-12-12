---
description: '자세한 정보: Platform:: Object 클래스'
title: Platform::Object 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: a190d5a56bb27fb95ac2c2c8bd2ba0e0d0572427
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308252"
---
# <a name="platformobject-class"></a>Platform::Object 클래스

Windows 런타임 apps의 ref 클래스 및 ref 구조체에 대해 일반적인 동작을 제공 합니다. 모든 ref 클래스 및 ref 구조체 인스턴스는 Platform::Object^로 암시적으로 변환될 수 있고 해당하는 가상 ToString 메서드를 재정의할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
public ref class Object : Object
```

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Object::Object](#ctor)|Object 클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Object::Equals](#equals)|지정된 개체가 현재 개체와 같은지 확인합니다.|
|[Object::GetHashCode](#gethashcode)|이 인스턴스의 해시 코드를 반환합니다.|
|[Object::ReferenceEquals](#referenceequals)|지정한 Object 인스턴스가 동일한지 여부를 확인합니다.|
|[ToString](#tostring)|현재 개체를 나타내는 문자열을 반환합니다. 재정의될 수 있습니다.|
|[GetType](#gettype)|현재 인스턴스를 설명하는 [Platform::Type](../cppcx/platform-type-class.md) 을 가져옵니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Object`

`Object`

### <a name="requirements"></a>요구 사항

**헤더:** vccorlib.h

**네임스페이스:** Platform

## <a name="objectequals-method"></a><a name="equals"></a> Object:: Equals 메서드

지정된 개체가 현재 개체와 같은지 확인합니다.

### <a name="syntax"></a>구문

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>매개 변수

*obj*<br/>
비교할 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 개체가 같으면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a> Object:: GetHashCode 메서드

COM 개체인 경우 이 인스턴스에 대한 `IUnknown`* ID 값을 반환하고, COM 개체가 아닌 경우 계산된 해시 값을 반환합니다.

### <a name="syntax"></a>구문

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Return Value

이 개체를 고유하게 식별하는 숫자 값입니다.

### <a name="remarks"></a>설명

GetHashCode를 사용하여 맵에 개체의 키를 만들 수 있습니다. [Object:: Equals](#equals)를 사용 하 여 해시 코드를 비교할 수 있습니다. 코드 경로가 매우 중요하며 `GetHashCode` 및 `Equals`가 충분히 빠르지 않은 경우 기본 COM 레이어로 드롭다운하고 네이티브 `IUnknown` 포인터 비교를 수행할 수 있습니다.

## <a name="objectgettype-method"></a><a name="gettype"></a> Object:: GetType 메서드

개체의 런타임 형식을 설명 하는 [Platform:: Type](../cppcx/platform-type-class.md) 개체를 반환 합니다.

### <a name="syntax"></a>Syntax

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>속성 값/반환 값

개체의 런타임 형식을 설명 하는 [Platform:: Type](../cppcx/platform-type-class.md) 개체입니다.

### <a name="remarks"></a>설명

Static [type:: GetTypeCode](../cppcx/platform-type-class.md#gettypecode) 를 사용 하 여 현재 형식을 나타내는 [Platform:: TypeCode 열거형](../cppcx/platform-typecode-enumeration.md) 값을 가져올 수 있습니다. 대부분의 경우 이는 기본 제공 형식에 유용합니다. [Platform:: String](../cppcx/platform-string-class.md) 이외의 ref 클래스에 대 한 형식 코드는 Object (1)입니다.

Windows [:: UI:: Xaml:: Interop:: TypeName](/uwp/api/windows.ui.xaml.interop.typename) 클래스는 windows api에서 언어와 관계 없이 windows 구성 요소와 앱 간에 형식 정보를 전달 하는 방법으로 사용 됩니다. T[Platform:: Type 클래스](../cppcx/platform-type-class.md) 에는와 간에 변환 하는 연산자가 있습니다. `Type` `TypeName`

다음과 같이 [typeid](../extensions/typeid-cpp-component-extensions.md) 연산자를 사용 하 여 `Platform::Type` 클래스 이름에 대 한 개체를 반환 합니다. 예를 들어 XAML 페이지 간을 탐색할 수 있습니다.

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a> Object:: Object 생성자

Object 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>Syntax

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a> Object:: ReferenceEquals 메서드

지정한 Object 인스턴스가 동일한지 여부를 확인합니다.

### <a name="syntax"></a>구문

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>매개 변수

*obj1*<br/>
비교할 첫 번째 개체입니다.

*obj2*<br/>
비교할 두 번째 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 두 개체가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a> Object:: ToString 메서드 (c + +/CX)

현재 개체를 나타내는 문자열을 반환합니다.

### <a name="syntax"></a>구문

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Return Value

현재 개체를 나타내는 문자열입니다. 이 메서드를 재정의하여 ref 클래스 또는 구조체에서 사용자 지정 문자열 메시지를 제공할 수 있습니다.

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)<br/>
[Platform:: Type 클래스](platform-type-class.md)<br/>
[유형 시스템](type-system-c-cx.md)
