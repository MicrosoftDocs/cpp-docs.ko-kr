---
title: HString 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fea4f576e347ca03dda1142b3118bf605bc9f385
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235349"
---
# <a name="hstring-class"></a>HString 클래스

RAII 패턴을 사용 하 여 HSTRING의 수명 관리에 대 한 도우미 클래스입니다.

## <a name="syntax"></a>구문

```cpp
class HString;
```

## <a name="remarks"></a>설명

Windows 런타임 HSTRING 핸들을 통해 문자열에 대 한 액세스를 제공합니다. `HString` 편의 함수 및 연산자 HSTRING 핸들을 사용 하 여 단순화 하기 위해 클래스를 제공 합니다. 이 클래스는 RAII 패턴을 통해 소유 HSTRING의 수명 동안을 처리할 수 있습니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                | 설명
----------------------------------- | -----------------------------------------------------
[Hstring:: Hstring](#hstring)        | `HString` 클래스의 새 인스턴스를 초기화합니다.
[HString:: ~ HString](#tilde-hstring) | 현재 인스턴스를 제거 합니다 `HString` 클래스입니다.

### <a name="public-methods"></a>Public 메서드

이름                                     | 설명
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Hstring:: Attach](#attach)               | 연결 된 `HString` 개체와 현재 `HString` 개체입니다.
[Hstring:: Copyto](#copyto)               | 현재 복사 `HString` 개체를 HSTRING 개체로 합니다.
[Hstring:: Detach](#detach)               | 지정 된 연결을 끊습니다 `HString` 해당 내부 값 개체입니다.
[Hstring:: Get](#get)                     | 기본 HSTRING 핸들의 값을 검색 합니다.
[Hstring:: Getaddressof](#getaddressof)   | 기본 HSTRING 핸들에 대 한 포인터를 검색합니다.
[Hstring:: Isvalid](#isvalid)             | 나타냅니다 여부 현재 `HString` 개체는 유효 합니다.
[Hstring:: Makereference](#makereference) | 만듭니다는 `HStringReference` 지정 된 문자열 매개 변수에서 개체입니다.
[Hstring:: Release](#release)             | 원본 문자열 값을 삭제 하 고 현재 초기화 `HString` 개체를 빈 값입니다.
[Hstring:: Set](#set)                     | 현재 값을 설정 `HString` 지정된 된 와이드 문자 문자열에는 개체 또는 `HString` 매개 변수입니다.

### <a name="public-operators"></a>Public 연산자

이름                                         | 설명
-------------------------------------------- | ----------------------------------------------------------------------------
[Hstring:: Operator =](#operator-assign)       | 다른 값으로 이동 `HString` 개체를 현재 `HString` 개체입니다.
[Hstring:: Operator = =](#operator-equality)    | 두 매개 변수가 같은지 여부를 나타냅니다.
[Hstring:: Operator! =](#operator-inequality)  | 두 매개 변수가 같지 않은지를 나타냅니다.
[Hstring:: Operator&lt;](#operator-less-than) | 첫 번째 매개 변수 인지 보다 작은 두 번째 매개 변수를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`HString`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

현재 인스턴스를 제거 합니다 `HString` 클래스입니다.

```cpp
~HString() throw()  
```

## <a name="attach"></a>Hstring:: Attach

연결 된 `HString` 개체와 현재 `HString` 개체입니다.

```cpp
void Attach(
       HSTRING hstr
       ) throw()  
```

### <a name="parameters"></a>매개 변수

*hstr*<br/>
기존 `HString` 개체입니다.

## <a name="copyto"></a>Hstring:: Copyto

현재 복사 `HString` 개체를 HSTRING 개체로 합니다.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>매개 변수

*str*<br/>
복사본을 받는 HSTRING입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 합니다 [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) 함수입니다.

## <a name="detach"></a>Hstring:: Detach

지정 된 연결을 끊습니다 `HString` 해당 내부 값 개체입니다.

```cpp
HSTRING Detach() throw()  
```

### <a name="return-value"></a>반환 값

기본 `HString` 분리 작업을 시작 하기 전에 값입니다.

## <a name="get"></a>Hstring:: Get

기본 HSTRING 핸들의 값을 검색 합니다.

```cpp
HSTRING Get() const throw()  
```

### <a name="return-value"></a>반환 값

기본 HSTRING 핸들의 값입니다.

## <a name="getaddressof"></a>Hstring:: Getaddressof

기본 HSTRING 핸들에 대 한 포인터를 검색합니다.

```cpp
HSTRING* GetAddressOf() throw()  
```

### <a name="return-value"></a>반환 값

기본 HSTRING 핸들에 대한 포인터입니다.

### <a name="remarks"></a>설명

이 작업 후에 기본 HSTRING 핸들의 문자열 값이 제거됩니다.

## <a name="hstring"></a>Hstring:: Hstring

`HString` 클래스의 새 인스턴스를 초기화합니다.

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>매개 변수

*hstr*<br/>
HSTRING 핸들입니다.

*other*<br/>
기존 `HString` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 초기화 새 `HString` 비어 있는 개체입니다.

두 번째 생성자는 새 `HString` 개체의 기존 값 *다른* 매개 변수를 되지 않으며 합니다 *다른* 매개 변수입니다.

## <a name="isvalid"></a>Hstring:: Isvalid

나타냅니다 여부를 현재 `HString` 개체가 비어 있습니다.

```cpp
bool IsValid() const throw()  
```

### <a name="parameters"></a>매개 변수

`true` 하는 경우 현재 `HString` 개체는 비어 있지 않으면 `false`합니다.

## <a name="makereference"></a>Hstring:: Makereference

만듭니다는 `HStringReference` 지정 된 문자열 매개 변수에서 개체입니다.

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
대상의 크기를 지정 하는 템플릿 매개 변수 `HStringReference` 버퍼입니다.

*str*<br/>
와이드 문자 문자열에 대한 참조입니다.

*Len 함수*<br/>
최대 길이 *str* 이 작업에 사용할 매개 변수 버퍼입니다. 경우는 *len* 매개 변수를 지정 하지 않으면 전체 *str* 매개 변수를 사용 합니다.

### <a name="return-value"></a>반환 값

`HStringReference` 개체는 지정 된 대로 동일한 값인 *str* 매개 변수입니다.

## <a name="operator-assign"></a>Hstring:: Operator = 연산자

다른 값으로 이동 `HString` 개체를 현재 `HString` 개체입니다.

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>매개 변수

*other*<br/>
기존 `HString` 개체입니다.

### <a name="remarks"></a>설명

기존 값 *다른* 현재 개체를 복사할 `HString` 개체를 차례로 합니다 *다른* 개체는 소멸 됩니다.

## <a name="operator-equality"></a>Hstring:: Operator = = 연산자

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
비교할 첫 번째 매개 변수입니다. *lhs* 수는 `HString` 또는 `HStringReference` 개체 또는 HSTRING 핸들입니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다. *rhs* 수는 `HString` 또는 `HStringReference` 개체 또는 HSTRING 핸들입니다.

### <a name="return-value"></a>반환 값

`true` 경우는 *lhs* 하 고 *rhs* 같고, 그렇지 않으면 매개 변수는 `false`합니다.

## <a name="operator-inequality"></a>Hstring:: Operator! = 연산자

두 매개 변수가 같지 않은지를 나타냅니다.

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
비교할 첫 번째 매개 변수입니다. *lhs* 수는 `HString` 또는 `HStringReference` 개체 또는 HSTRING 핸들입니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다. *rhs* 수는 `HString` 또는 `HStringReference` 개체 또는 HSTRING 핸들입니다.

### <a name="return-value"></a>반환 값

`true` 경우는 *lhs* 하 고 *rhs* 매개 변수는 같고, 그렇지 않으면 `false`합니다.

## <a name="operator-less-than"></a>Hstring:: Operator&lt; 연산자

첫 번째 매개 변수 인지 보다 작은 두 번째 매개 변수를 나타냅니다.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()  
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 에 대 한 참조 수를 `HString`입니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다. *rhs* 에 대 한 참조 수를 `HString`입니다.

### <a name="return-value"></a>반환 값

`true` 경우는 *lhs* 매개 변수는 보다 작은 *rhs* 매개 변수가 고, 그렇지 않으면 `false`합니다.

## <a name="release"></a>Hstring:: Release

원본 문자열 값을 삭제 하 고 현재 초기화 `HString` 개체를 빈 값입니다.

```cpp
void Release() throw()  
```

## <a name="set"></a>Hstring:: Set

현재 값을 설정 `HString` 지정된 된 와이드 문자 문자열에는 개체 또는 `HString` 매개 변수입니다.

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
와이드 문자 문자열입니다.

*Len 함수*<br/>
최대 길이 *str* 매개 변수는 현재 할당 된 `HString` 개체입니다.

*hstr*<br/>
기존 `HString` 개체입니다.
