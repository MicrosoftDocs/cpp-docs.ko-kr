---
description: '자세한 정보: Platform:: Guid 값 클래스'
title: Platform::Guid 값 클래스
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 4c2ffc5096e6b40266fef0934acc562edf721c24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195192"
---
# <a name="platformguid-value-class"></a>Platform::Guid 값 클래스

Windows 런타임 형식 시스템의 [GUID] (/windows/win32/api/guiddef/ns-guiddef-guid 형식)를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
public value struct Guid
```

### <a name="members"></a>멤버

`Platform::Guid` 에는 `Equals()` `GetHashCode()` `ToString()` [Platform:: Object 클래스](../cppcx/platform-object-class.md)에서 파생 된, 및 메서드와 `GetTypeCode()` [platform:: Type 클래스](../cppcx/platform-type-class.md)에서 파생 된 메서드가 있습니다. `Platform::Guid` 또한에는 다음과 같은 멤버도 있습니다.

|멤버|설명|
|------------|-----------------|
|[Eid](#ctor)|`Platform::Guid`의 새 인스턴스를 초기화합니다.|
|[연산자 = =](#operator-equality)|같음 연산자입니다.|
|[연산자! =](#operator-inequality)|같지 않음 연산자입니다.|
|[연산자&lt;](#operator-less)|보다 작음 연산자입니다.|
|[연산자 ()](#operator-call)|`Platform::Guid` 를 `GUID`로 변환합니다.|

### <a name="remarks"></a>설명

새을 생성 하려면 `Platform::Guid` [Windows:: Foundation:: GuidHelper:: CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid) 정적 메서드를 사용 합니다.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object

## <a name="guidguid-constructors"></a><a name="ctor"></a> Guid:: Guid 생성자

`Platform::Guid`의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>매개 변수

*은*<br/>
의 처음 4 바이트입니다 `GUID` .

*b*<br/>
의 다음 2 바이트입니다 `GUID` .

*c*<br/>
의 다음 2 바이트입니다 `GUID` .

*d*<br/>
`GUID`의 다음 바이트입니다.

*e*<br/>
`GUID`의 다음 바이트입니다.

*f*<br/>
`GUID`의 다음 바이트입니다.

*g*<br/>
`GUID`의 다음 바이트입니다.

*h*<br/>
`GUID`의 다음 바이트입니다.

*i*<br/>
`GUID`의 다음 바이트입니다.

*j*<br/>
`GUID`의 다음 바이트입니다.

*시계의*<br/>
`GUID`의 다음 바이트입니다.

*m*<br/>
`GUID` [GUID 구조체](/windows/win32/api/guiddef/ns-guiddef-guid)를 형성 하는의입니다.

*n*<br/>
의 나머지 8 바이트입니다 `GUID` .

## <a name="guidoperator-operator"></a><a name="operator-equality"></a> Guid:: operator = = 연산자

두 `Platform::Guid` 인스턴스가 같은지 비교합니다.

### <a name="syntax"></a>구문

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>매개 변수

*guid1*<br/>
비교할 첫 번째 `Platform::Guid`입니다.

*guid2*<br/>
비교할 두 번째 `Platform::Guid`입니다.

### <a name="return-value"></a>반환 값

두 `Platform::Guid` 인스턴스가 같으면 True입니다.

### <a name="remarks"></a>설명

`==` [Windows:: Foundation:: GuidHelper:: Equals](/uwp/api/windows.foundation.guidhelper.equals) 정적 메서드 대신 연산자를 사용 하는 것이 좋습니다.

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a> Guid:: operator! = 연산자

두 `Platform::Guid` 인스턴스가 다른지 비교합니다.

### <a name="syntax"></a>구문

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>매개 변수

*guid1*<br/>
비교할 첫 번째 `Platform::Guid`입니다.

*guid2*<br/>
비교할 두 번째 `Platform::Guid`입니다.

### <a name="return-value"></a>반환 값

두 `Platform::Guid` 인스턴스가 같지 않으면 True입니다.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a> Guid:: operator &lt; 연산자

두 `Platform::Guid` 인스턴스의 순서를 비교 합니다.

### <a name="syntax"></a>구문

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>매개 변수

*guid1*<br/>
비교할 첫 번째 `Platform::Guid`입니다.

*guid2*<br/>
비교할 두 번째 `Platform::Guid`입니다.

### <a name="return-value"></a>반환 값

*Guid1* 가 *guid2* 앞에 정렬 되 면 True입니다. 사전적는 `Platform::Guid` 4 32 비트 부호 없는 값의 배열인 것 처럼 각를 처리 한 후에 정렬 됩니다. 이는 SQL Server 또는 .NET Framework에서 사용 되는 순서가 아니라 문자열 표현에 따라 사전순으로 정렬 하는 것과 동일 하지 않습니다.

이 연산자는 `Guid` c + + 표준 라이브러리에서 개체를 더 쉽게 사용할 수 있도록 제공 됩니다.

## <a name="guidoperator-operator"></a><a name="operator-call"></a> Guid:: operator () 연산자

는를 `Platform::Guid` [GUID 구조체로](/windows/win32/api/guiddef/ns-guiddef-guid)암시적으로 변환 합니다.

### <a name="syntax"></a>구문

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Return Value

[GUID 구조체](/windows/win32/api/guiddef/ns-guiddef-guid)입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임스페이스](../cppcx/platform-namespace-c-cx.md)
