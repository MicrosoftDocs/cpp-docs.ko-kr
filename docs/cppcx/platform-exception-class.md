---
description: '자세한 정보: Platform:: Exception 클래스'
title: Platform::Exception 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: 1b6ad35e04ae239d90dbfceecaaf72223ae6a7ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195218"
---
# <a name="platformexception-class"></a>Platform::Exception 클래스

애플리케이션 실행 중에 발생하는 오류를 나타냅니다. 사용자 지정 예외 클래스는 `Platform::Exception`에서 파생될 수 없습니다. 사용자 지정 예외가 필요한 경우 `Platform::COMException` 을 사용하고 앱 관련 HRESULT를 지정할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>멤버

`Exception` 클래스는 `Object` 클래스 및 `IException`, `IPrintable`, `IEquatable` 인터페이스에서 상속됩니다.

`Exception` 클래스에는 다음과 같은 종류의 멤버도 있습니다.

### <a name="constructors"></a>생성자

|멤버|설명|
|------------|-----------------|
|[예외:: Exception](#ctor)|`Exception` 클래스의 새 인스턴스를 초기화합니다.|

### <a name="methods"></a>메서드

`Exception`클래스는 `Equals()` `Finalize()` `GetHashCode()` `GetType()` `MemberwiseClose()` `ToString()` [Platform:: Object 클래스](../cppcx/platform-object-class.md)에서,,,, 및 메서드를 상속 합니다. `Exception` 클래스에는 다음 메서드도 있습니다.

|멤버|설명|
|------------|-----------------|
|[예외:: CreateException](#createexception)|지정된 HRESULT 값을 나타내는 예외를 만듭니다.|

### <a name="properties"></a>속성

Exception 클래스에는 다음과 같은 속성도 있습니다.

|멤버|설명|
|------------|-----------------|
|[예외:: HResult](#hresult)|예외에 해당하는 HRESULT입니다.|
|[예외:: Message](#message)|예외를 설명하는 메시지입니다. 이 값은 읽기 전용이며 `Exception` 이 생성된 후 수정될 수 없습니다.|

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a> Exception:: CreateException 메서드

지정된 HRESULT 값에서 Platform::Exception^을 만듭니다.

### <a name="syntax"></a>구문

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>매개 변수

*시간*<br/>
일반적으로 COM 메서드 호출에서 가져오는 HRESULT 값입니다. 값이 0이 고 S_OK와 같으면이 메서드는 성공 하는 COM 메서드가 예외를 throw 하지 않아야 하므로 [Platform:: InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) 을 throw 합니다.

*message*<br/>
오류를 설명하는 문자열입니다.

### <a name="return-value"></a>반환 값

오류 HRESULT를 나타내는 예외입니다.

### <a name="remarks"></a>설명

예를 들어 COM 인터페이스 메서드에 대한 호출에서 반환되는 HRESULT에서 예외를 만들려면 이 메서드를 사용합니다. String^ 매개 변수를 사용하는 오버로드를 사용하여 사용자 지정 메시지를 제공할 수 있습니다.

단순히 HRESULT를 포함 하는 [Platform:: COMException](../cppcx/platform-comexception-class.md) 를 만드는 대신 createexception을 사용 하 여 강력한 형식의 예외를 만드는 것이 좋습니다.

## <a name="exceptionexception-constructor"></a><a name="ctor"></a> Exception:: Exception 생성자

Exception 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>매개 변수

*hresult*<br/>
예외로 표시되는 오류 HRESULT입니다.

*message*<br/>
예외와 관련된 지침 텍스트와 같은 사용자 지정 메시지입니다. 일반적으로 오류 발생 이유와 그 방법에 대해 최대한 구체적인 설명 메시지를 제공하기 위해서는 두 번째 오버로드를 사용하는 것이 좋습니다.

## <a name="exceptionhresult-property"></a><a name="hresult"></a> Exception:: HResult 속성

예외에 해당하는 HRESULT입니다.

### <a name="syntax"></a>Syntax

```cpp
public:
    property int HResult { int get(); }
```

### <a name="property-value"></a>속성 값

HRESULT 값입니다.

### <a name="remarks"></a>설명

대부분의 예외는 HRESULT 값으로 반환되는 COM 오류로 시작합니다. C++/CX가 이러한 값을 Platform::Exception^ 개체로 변환하고, 이 속성이 원래 오류 코드의 값을 저장합니다.

## <a name="exceptionmessage-property"></a><a name="message"></a> Exception:: Message 속성

오류를 설명하는 메시지입니다.

### <a name="syntax"></a>Syntax

```cpp
public:property String^ Message;
```

### <a name="property-value"></a>속성 값

Windows 런타임에서 발생하는 예외의 경우, 이것은 오류에 대한 시스템 제공 설명입니다.

### <a name="remarks"></a>설명

Windows 8에서이 속성은 해당 버전의 Windows 런타임에 대 한 예외가 ABI에서 HRESULT로만 전송 되기 때문에 읽기 전용입니다. Windows 8.1에서는 다양한 예외 정보가 ABI 전체에 전송되며 다른 구성 요소에서 프로그래밍 방식으로 액세스할 수 있는 사용자 지정 메시지를 제공할 수 있습니다. 자세한 내용은 [예외 (c + +/cx)](../cppcx/exceptions-c-cx.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)
