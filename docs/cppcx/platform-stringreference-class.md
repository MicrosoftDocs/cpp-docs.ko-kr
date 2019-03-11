---
title: Platform::StringReference 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 7b6ab42dc630ce7e0014534064e8f1ce6da00857
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750925"
---
# <a name="platformstringreference-class"></a>Platform::StringReference 클래스

최저의 복사 작업으로 `Platform::String^` 입력 매개 변수의 문자열 데이터를 다른 메서드로 전달하는 데 사용할 수 있는 최적화 형식입니다.

## <a name="syntax"></a>구문

```cpp
class StringReference
```

### <a name="remarks"></a>설명

### <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|`StringReference`인스턴스를 만드는 두 개의 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[StringReference::Data](#data)|문자열 데이터를 char16 값의 배열로 반환합니다.|
|[StringReference::Length](#length)|문자열의 문자 수를 반환합니다.|
|[StringReference::GetHSTRING](#gethstring)|문자열 데이터를 HSTRING으로 반환합니다.|
|[StringReference::GetString](#getstring)|문자열 데이터를 `Platform::String^`로 반환합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|설명|
|----------|-----------------|
|[StringReference::operator=](#operator-assign)|새 `StringReference` 인스턴스에 `StringReference` 를 할당합니다.|
|[StringReference::operator()](#operator-call)|`StringReference` 를 `Platform::String^`로 변환합니다.|

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** 플랫폼

**헤더:** vccorlib.h

## <a name="data"></a>  Stringreference:: Data 메서드

이 `StringReference`의 콘텐츠를 char16 값의 배열로 반환합니다.

### <a name="syntax"></a>구문

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>반환 값

char16 유니코드 텍스트 문자의 배열입니다.

## <a name="gethstring"></a>  Stringreference:: Gethstring 메서드

문자열의 내용을 `__abi_HSTRING`으로 반환합니다.

### <a name="syntax"></a>구문

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>반환 값

문자열 데이터가 포함된 `__abi_HSTRING`입니다.

### <a name="remarks"></a>설명

## <a name="getstring"></a>  Stringreference:: Getstring 메서드

문자열의 내용을 `Platform::String^`로 반환합니다.

### <a name="syntax"></a>구문

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>반환 값

문자열 데이터가 포함된 `Platform::String^`입니다.

## <a name="length"></a>  Stringreference:: Length 메서드

문자열의 문자 수를 반환합니다.

### <a name="syntax"></a>구문

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>반환 값

문자열에 있는 문자의 수를 지정하는 부호 없는 정수입니다.

### <a name="remarks"></a>설명

## <a name="operator-assign"></a>  Stringreference:: Operator = 연산자

지정한 개체를 현재 `StringReference` 개체에 할당합니다.

### <a name="syntax"></a>구문

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>매개 변수

*__fstrArg*<br/>
현재 `StringReference` 개체를 초기화하는 데 사용되는 `StringReference` 개체의 주소입니다.

*__strArg*<br/>
현재 `StringReference` 개체를 초기화하는 데 사용되는 char16 값의 배열에 대한 포인터입니다.

### <a name="return-value"></a>반환 값


  `StringReference` 형식의 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

때문에 `StringReference` 표준 c + + 클래스 및 ref 클래스가 아닌 이면에 나타나지 않으면 합니다 **개체 브라우저**합니다.

## <a name="operator-call"></a>  StringReference::operator()  Operator

`StringReference` 개체를 `Platform::String^` 개체로 변환합니다.

### <a name="syntax"></a>구문

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>반환 값


  `Platform::String` 형식의 개체에 대한 핸들입니다.

## <a name="ctor"></a>  StringReference::StringReference 생성자

`StringReference` 클래스의 새 인스턴스를 초기화합니다.

### <a name="syntax"></a>구문

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>매개 변수

*__fstrArg*<br/>
새 인스턴스를 초기화하는 데 해당 데이터가 사용되는 `StringReference`입니다.

*__strArg*<br/>
새 인스턴스를 초기화하는 데 사용되는 char16 값의 배열에 대한 포인터입니다.

*__lenArg*<br/>
`__strArg`의 요소 수입니다.

### <a name="remarks"></a>설명

이 생성자의 첫 번째 버전은 기본 생성자입니다. 두 번째 버전은 `StringReference` 매개 변수로 지정된 개체에서 새 `__fstrArg` 인스턴스 클래스를 초기화합니다. 세 번째 및 네 번째 오버로드는 char16 값의 배열에서 새 `StringReference` 인스턴스를 초기화합니다. char16은 16비트 유니코드 텍스트 문자를 나타냅니다.

## <a name="see-also"></a>참고자료

[Platform::StringReference 클래스](../cppcx/platform-stringreference-class.md)
