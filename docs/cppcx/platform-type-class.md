---
description: '자세한 정보: Platform:: Type 클래스'
title: Platform::Type 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: c11e85180dfb3eeeeb6eea88c3bd47b40fa7289b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307901"
---
# <a name="platformtype-class"></a>Platform::Type 클래스

특정 형식에 대한 런타임 정보(문자열 이름 및 형식 코드)를 포함합니다. 모든 개체에서 [object:: GetType](../cppcx/platform-object-class.md#gettype) 을 호출 하거나 클래스 또는 구조체 이름에 [typeid](../extensions/typeid-cpp-component-extensions.md) 연산자를 사용 하 여 가져옵니다.

## <a name="syntax"></a>구문

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>설명

`Type`클래스는 **`if`** **`switch`** 개체의 런타임 형식을 기반으로 분기 하는 또는 문을 사용 하 여 처리를 지시 해야 하는 응용 프로그램에서 유용 합니다. 형식 범주를 설명 하는 형식 코드는 [type:: GetTypeCode](#gettypecode) 멤버 함수를 사용 하 여 검색 합니다.

## <a name="public-methods"></a>public 메서드

| Name | 설명 |
|--|--|
| [Type::GetTypeCode 메서드](#gettypecode) | 개체의 [Platform::TypeCode 열거형](../cppcx/platform-typecode-enumeration.md) 값을 반환합니다. |
| [Type:: ToString 메서드](#tostring) | 메타 데이터에 지정 된 형식의 이름을 반환 합니다. |

## <a name="public-properties"></a>public 속성

| Name | 설명 |
|--|--|
| [형식:: FullName](#fullname) | 형식의 정규화된 이름을 나타내며 ::(콜론 두 개) 대신 .(점)을 구분 기호로 사용(예: "MyNamespace.MyClass")하는 [Platform::String 클래스](../cppcx/platform-string-class.md)^을 (점)을 구분 기호로 사용할 수 없습니다 (예: `MyNamespace.MyClass` ). |

## <a name="conversion-operators"></a>변환 연산자

| Name | 설명 |
|--|--|
| [연산자 유형 ^](../cppcx/operator-type-hat.md) | `Windows::UI::Xaml::Interop::TypeName` 을 `Platform::Type`으로 변환할 수 있습니다. |
| [연산자 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md) | `Platform::Type` 을 `Windows::UI::Xaml::Interop::TypeName`으로 변환할 수 있습니다. |

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object

## <a name="typefullname-property"></a><a name="fullname"></a> Type:: FullName 속성

폼에서 현재 형식의 정규화 된 이름을 검색 합니다 `Namespace.Type` .

### <a name="syntax"></a>구문

```cpp
String^ FullName();
```

### <a name="return-value"></a>Return Value

형식의 이름입니다.

### <a name="example"></a>예제

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a> Type:: GetTypeCode 메서드

기본 제공 형식의 숫자 형식 범주를 검색합니다.

### <a name="syntax"></a>구문

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Return Value

Platform::TypeCode 열거형 값의 하나입니다.

### <a name="remarks"></a>설명

GetTypeCode () 멤버 메서드에 해당 하는는 **`typeid`** 속성입니다.

## <a name="typetostring-method"></a><a name="tostring"></a> Type:: ToString 메서드

형식의 이름을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Return Value

메타 데이터에 지정 된 형식의 이름입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)
