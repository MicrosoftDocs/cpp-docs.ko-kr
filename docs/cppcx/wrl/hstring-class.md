---
description: '자세한 정보: HString 클래스'
title: HString 클래스
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 3a7de2595fbc55cec21f74193cc53f29438530cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229160"
---
# <a name="hstring-class"></a>HString 클래스

RAII 패턴을 사용 하 여 [Hstring](/windows/win32/WinRT/hstring) 의 수명을 관리 하기 위한 도우미 클래스입니다.

## <a name="syntax"></a>구문

```cpp
class HString;
```

## <a name="remarks"></a>설명

Windows 런타임는 [Hstring](/windows/win32/WinRT/hstring) 핸들을 통해 문자열에 대 한 액세스를 제공 합니다. `HString`클래스는 HSTRING 핸들 사용을 간소화 하기 위해 편리한 함수와 연산자를 제공 합니다. 이 클래스는 RAII 패턴을 통해 소유한 HSTRING의 수명을 처리할 수 있습니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                | 설명
----------------------------------- | -----------------------------------------------------
[HString:: HString](#hstring)        | `HString` 클래스의 새 인스턴스를 초기화합니다.
[HString:: ~ HString](#tilde-hstring) | 클래스의 현재 인스턴스를 소멸 시킵니다 `HString` .

### <a name="public-methods"></a>Public 메서드

이름                                     | 설명
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString:: Attach](#attach)               | 지정 된 `HString` 개체를 현재 개체와 연결 `HString` 합니다.
[HString::CopyTo](#copyto)               | 현재 개체를 `HString` HSTRING 개체로 복사 합니다.
[HString::D etach](#detach)               | 지정 된 `HString` 개체를 내부 값에서 분리 합니다.
[HString:: Get](#get)                     | 기본 HSTRING 핸들의 값을 검색 합니다.
[HString:: GetAddressOf](#getaddressof)   | 기본 HSTRING 핸들에 대 한 포인터를 검색 합니다.
[HString:: GetRawBuffer](#getrawbuffer)   | 기본 문자열 데이터에 대 한 포인터를 검색 합니다.
[HString:: IsValid](#isvalid)             | 현재 개체가 유효한 지 여부를 나타냅니다 `HString` .
[HString:: MakeReference](#makereference) | 지정 된 `HStringReference` 문자열 매개 변수에서 개체를 만듭니다.
[HString:: Release](#release)             | 내부 문자열 값을 삭제 하 고 현재 `HString` 개체를 빈 값으로 초기화.
[HString:: Set](#set)                     | 현재 개체의 값을 `HString` 지정 된 와이드 문자 문자열 또는 매개 변수로 설정 합니다 `HString` .

### <a name="public-operators"></a>Public 연산자

Name                                         | 설명
-------------------------------------------- | ----------------------------------------------------------------------------
[HString:: operator =](#operator-assign)       | 다른 개체의 값을 `HString` 현재 `HString` 개체로 이동 합니다.
[HString:: operator = =](#operator-equality)    | 두 매개 변수가 같은지 여부를 나타냅니다.
[HString:: operator! =](#operator-inequality)  | 두 매개 변수가 같지 않은지 여부를 나타냅니다.
[HString:: operator&lt;](#operator-less-than) | 첫 번째 매개 변수가 두 번째 매개 변수 보다 작거나 같은지 여부를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HString`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="hstringhstring"></a><a name="tilde-hstring"></a> HString:: ~ HString

클래스의 현재 인스턴스를 소멸 시킵니다 `HString` .

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a> HString:: Attach

지정 된 `HString` 개체를 현재 개체와 연결 `HString` 합니다.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>매개 변수

*hstr*<br/>
기존 `HString` 개체입니다.

## <a name="hstringcopyto"></a><a name="copyto"></a> HString:: CopyTo

현재 개체를 `HString` HSTRING 개체로 복사 합니다.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>매개 변수

*str*<br/>
복사본을 받는 HSTRING입니다.

### <a name="remarks"></a>설명

이 메서드는 [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) 함수를 호출 합니다.

## <a name="hstringdetach"></a><a name="detach"></a> HString::D etach

지정 된 `HString` 개체를 내부 값에서 분리 합니다.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>반환 값

`HString`분리 작업이 시작 되기 전의 내부 값입니다.

## <a name="hstringget"></a><a name="get"></a> HString:: Get

기본 HSTRING 핸들의 값을 검색 합니다.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>반환 값

기본 HSTRING 핸들의 값입니다.

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a> HString:: GetAddressOf

기본 HSTRING 핸들에 대 한 포인터를 검색 합니다.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>반환 값

기본 HSTRING 핸들에 대한 포인터입니다.

### <a name="remarks"></a>설명

이 작업 후에 기본 HSTRING 핸들의 문자열 값이 삭제됩니다.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a> HString:: GetRawBuffer

기본 문자열 데이터에 대 한 포인터를 검색 합니다.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>매개 변수

*길이* **`int`** 데이터의 길이를 받는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`const`** 기본 문자열 데이터에 대 한 포인터입니다.

## <a name="hstringhstring"></a><a name="hstring"></a> HString:: HString

`HString` 클래스의 새 인스턴스를 초기화합니다.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>매개 변수

*hstr*<br/>
HSTRING 핸들입니다.

*다른*<br/>
기존 `HString` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 비어 있는 새 개체를 초기화 합니다 `HString` .

두 번째 생성자는 `HString` 기존 *다른* 매개 변수의 값으로 새 개체를 초기화 한 다음 *다른* 매개 변수를 소멸 시킵니다.

## <a name="hstringisvalid"></a><a name="isvalid"></a> HString:: IsValid

현재 개체가 비어 있는지 여부를 나타냅니다 `HString` .

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>매개 변수

**`true`** 현재 `HString` 개체가 비어 있지 않으면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="hstringmakereference"></a><a name="makereference"></a> HString:: MakeReference

지정 된 `HStringReference` 문자열 매개 변수에서 개체를 만듭니다.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>매개 변수

*sizeDest*<br/>
대상 버퍼의 크기를 지정 하는 템플릿 매개 변수입니다 `HStringReference` .

*str*<br/>
와이드 문자 문자열에 대한 참조입니다.

*len*<br/>
이 작업에 사용할 *str* 매개 변수 버퍼의 최대 길이입니다. *Len* 매개 변수를 지정 하지 않으면 전체 *str* 매개 변수가 사용 됩니다.

### <a name="return-value"></a>반환 값

`HStringReference`지정 된 *str* 매개 변수와 동일한 값을 갖는 개체입니다.

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a> HString:: operator = 연산자

다른 개체의 값을 `HString` 현재 `HString` 개체로 이동 합니다.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
기존 `HString` 개체입니다.

### <a name="remarks"></a>설명

기존의 *다른* 개체의 값이 현재 개체에 복사 된 `HString` 다음 *다른* 개체가 제거 됩니다.

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a> HString:: operator = = 연산자

두 매개 변수가 같은지 여부를 나타냅니다.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 는 `HString` 또는 `HStringReference` 개체 또는 hstring 핸들 일 수 있습니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다. *rhs* 는 `HString` 또는 `HStringReference` 개체 또는 hstring 핸들 일 수 있습니다.

### <a name="return-value"></a>반환 값

**`true`***lhs* 및 *rhs* 매개 변수가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a> HString:: operator! = 연산자

두 매개 변수가 같지 않은지 여부를 나타냅니다.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 는 `HString` 또는 `HStringReference` 개체 또는 hstring 핸들 일 수 있습니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다. *rhs* 는 `HString` 또는 `HStringReference` 개체 또는 hstring 핸들 일 수 있습니다.

### <a name="return-value"></a>반환 값

**`true`***lhs* 및 *rhs* 매개 변수가 같지 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a> HString:: operator &lt; 연산자

첫 번째 매개 변수가 두 번째 매개 변수 보다 작거나 같은지 여부를 나타냅니다.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 는에 대 한 참조일 수 있습니다 `HString` .

*rhs*<br/>
비교할 두 번째 매개 변수입니다. *rhs* 은에 대 한 참조일 수 있습니다 `HString` .

### <a name="return-value"></a>반환 값

**`true`***lhs* 매개 변수가 *rhs* 매개 변수 보다 작은 경우 그렇지 않으면 **`false`** 입니다.

## <a name="hstringrelease"></a><a name="release"></a> HString:: Release

내부 문자열 값을 삭제 하 고 현재 `HString` 개체를 빈 값으로 초기화.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a> HString:: Set

현재 개체의 값을 `HString` 지정 된 와이드 문자 문자열 또는 매개 변수로 설정 합니다 `HString` .

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>매개 변수

*str*<br/>
와이드 문자열입니다.

*len*<br/>
현재 개체에 할당 된 *str* 매개 변수의 최대 길이입니다 `HString` .

*hstr*<br/>
기존 `HString` 개체입니다.
