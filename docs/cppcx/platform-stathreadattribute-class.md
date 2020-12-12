---
description: '자세한 정보: Platform:: STAThreadAttribute 클래스'
title: Platform::STAThreadAttribute 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: a1c235ef9a171e650c960df184b081c4b6511cf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308005"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute 클래스

애플리케이션에 대한 스레딩 모델이 STA(단일 스레드 아파트)임을 나타냅니다.

## <a name="syntax"></a>구문

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[STAThreadAttribute 생성자 1](#ctor)|클래스의 새 인스턴스를 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

STAThreadAttribute 특성은 [Platform:: Object 클래스](../cppcx/platform-object-class.md)에서 상속 됩니다. STAThreadAttribute도 다음 멤버를 오버로드하거나 포함합니다.

|Name|설명|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|지정된 개체가 현재 개체와 같은지 확인합니다.|
|[STAThreadAttribute::GetHashCode](#gethashcode)|이 인스턴스의 해시 코드를 반환합니다.|
|[STAThreadAttribute::ToString](#tostring)|현재 개체를 나타내는 문자열을 반환합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Platform`

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Platform

## <a name="stathreadattribute-constructor"></a><a name="ctor"></a> STAThreadAttribute constructor

STAThreadAttribute 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>Syntax

```cpp
public:STAThreadAttribute();
```

## <a name="stathreadattributeequals"></a><a name="equals"></a> STAThreadAttribute:: Equals

지정된 개체가 현재 개체와 같은지 확인합니다.

### <a name="syntax"></a>구문

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>매개 변수

*obj*<br/>
비교할 개체입니다.

### <a name="return-value"></a>반환 값

**`true`** 개체가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="stathreadattributegethashcode"></a><a name="gethashcode"></a> STAThreadAttribute:: GetHashCode

이 인스턴스의 해시 코드를 반환합니다.

### <a name="syntax"></a>구문

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Return Value

이 인스턴스의 해시 코드입니다.

## <a name="stathreadattributetostring"></a><a name="tostring"></a> STAThreadAttribute:: ToString

현재 개체를 나타내는 문자열을 반환합니다.

### <a name="syntax"></a>구문

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Return Value

현재 개체를 나타내는 문자열입니다.

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)
