---
description: '자세한 정보: Platform:: COMException 클래스'
title: Platform::COMException 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::COMException::HResult
- VCCORLIB/Platform::COMException::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 71f6c3fa6d29a884627f2bf5aae07fbc0349ec9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176121"
---
# <a name="platformcomexception-class"></a>Platform::COMException 클래스

애플리케이션을 실행할 때 나타나는 COM 오류를 나타냅니다. COMException은 미리 정의된 표준 예외 집합의 기본 클래스입니다.

## <a name="syntax"></a>구문

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>멤버

COMException 클래스는 Object 클래스 및 IException, IPrintable 및 IEquatable 인터페이스에서 상속합니다.

COMException에는 다음 형식의 멤버도 있습니다.

**생성자**

|멤버|설명|
|------------|-----------------|
|[COMException](#ctor)|COMException 클래스의 새 인스턴스를 초기화합니다.|

**메서드**

COMException 클래스는 [Platform::Object Class](../cppcx/platform-object-class.md)의 Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() 및 ToString() 메서드를 상속합니다.

**속성**

COMException 클래스에는 다음과 같은 속성이 있습니다.

|멤버|설명|
|------------|-----------------|
|[예외:: HResult](#hresult)|예외에 해당하는 HRESULT입니다.|
|[예외:: Message](#message)|예외를 설명하는 메시지입니다.|

## <a name="derived-exceptions"></a>파생된 예외

다음과 같은 미리 정의된 예외는 COMException에서 파생됩니다. COMException과 이름, 생성자 이름 및 내부 HRESULT 값만 다릅니다.

|Name|내부 HRESULT|설명|
|----------|------------------------|-----------------|
|COMException|*사용자 정의 hresult*|COM 메서드 호출에서 인식할 수 없는 HRESULT가 반환되는 경우에 throw됩니다.|
|AccessDeniedException|E_ACCESSDENIED|리소스 또는 기능에 대한 액세스가 거부된 경우 throw됩니다.|
|ChangedStateException|E_CHANGED_STATE|부모 컬렉션이 변경된 후 컬렉션 반복기 또는 컬렉션 뷰의 메서드가 호출되어 메서드 결과가 무효화되면 throw됩니다.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|COM 클래스가 등록되지 않은 경우 throw됩니다.|
|DisconnectedException|RPC_E_DISCONNECTED|개체와 클라이언트의 연결이 끊기면 throw됩니다.|
|FailureException|E_FAIL|작업이 실패하면 throw됩니다.|
|InvalidArgumentException|E_INVALIDARG|메서드에 제공된 인수 중 하나가 유효하지 않을 때 throw됩니다.|
|InvalidCastException|E_NOINTERFACE|형식이 다른 형식에 대한 캐스트가 될 수 없는 경우 throw됩니다.|
|NotImplementedException|E_NOTIMPL|클래스에 인터페이스 메서드가 구현되어 있지 않은 경우 throw됩니다.|
|NullReferenceException|E_POINTER|null 개체 참조를 역참조하려고 할 때 throw됩니다.|
|OperationCanceledException|E_ABORT|작업이 중단되면 throw됩니다.|
|OutOfBoundsException|E_BOUNDS|작업이 유효한 범위를 벗어난 데이터에 액세스하려고 하면 throw됩니다.|
|OutOfMemoryException|E_OUTOFMEMORY|메모리가 부족하여 작업을 완료할 수 없는 경우 throw됩니다.|

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object

## <a name="comexceptioncomexception-constructor"></a><a name="ctor"></a> COMException:: COMException 생성자

COMException 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>매개 변수

*hresult*<br/>
예외로 표시되는 오류 HRESULT입니다.

## <a name="comexceptionhresult-property"></a><a name="hresult"></a> COMException:: HResult 속성

예외에 해당하는 HRESULT입니다.

### <a name="syntax"></a>Syntax

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>속성 값

오류를 지정하는 HRESULT 값입니다.

### <a name="remarks"></a>설명

HRESULT 값을 해석 하는 방법에 대 한 자세한 내용은 [COM 오류 코드 구조](/windows/win32/com/structure-of-com-error-codes)를 참조 하세요.

## <a name="comexceptionmessage-property"></a><a name="message"></a> COMException:: Message 속성

예외를 설명하는 메시지입니다.

### <a name="syntax"></a>Syntax

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>속성 값

예외에 대한 설명입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)
