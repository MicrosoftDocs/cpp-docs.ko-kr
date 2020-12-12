---
description: '다음에 대 한 자세한 정보: HStringReference 클래스'
title: HStringReference 클래스
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: d1a45eadd258ba6e17c26cc86aa362011d08ab8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249843"
---
# <a name="hstringreference-class"></a>HStringReference 클래스

기존 문자열에서 만들어진 HSTRING을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class HStringReference;
```

## <a name="remarks"></a>설명

새 HSTRING의 지원 버퍼 수명은 Windows 런타임에서 관리 되지 않습니다. 호출자는 힙 할당을 방지 하 고 메모리 누수 위험을 제거 하기 위해 스택 프레임에 원본 문자열을 할당 합니다. 또한 호출자는 첨부 된 HSTRING의 수명 동안 소스 문자열이 변경 되지 않은 상태로 유지 되도록 해야 합니다. 자세한 내용은 [WindowsCreateStringReference 함수](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference)를 참조 하세요.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                    | 설명
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference:: HStringReference](#hstringreference) | `HStringReference` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

멤버                              | 설명
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 현재 개체를 `HStringReference` HSTRING 개체로 복사 합니다.
[HStringReference:: Get](#get)       | 기본 HSTRING 핸들의 값을 검색 합니다.
[HStringReference:: GetRawBuffer](#getrawbuffer) | 기본 문자열 데이터에 대 한 포인터를 검색 합니다.

### <a name="public-operators"></a>Public 연산자

Name                                                  | 설명
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference:: operator =](#operator-assign)       | 다른 개체의 값을 `HStringReference` 현재 `HStringReference` 개체로 이동 합니다.
[HStringReference:: operator = =](#operator-equality)    | 두 매개 변수가 같은지 여부를 나타냅니다.
[HStringReference:: operator! =](#operator-inequality)  | 두 매개 변수가 같지 않은지 여부를 나타냅니다.
[HStringReference:: operator&lt;](#operator-less-than) | 첫 번째 매개 변수가 두 번째 매개 변수 보다 작거나 같은지 여부를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HStringReference`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="hstringreferencecopyto"></a><a name="copyto"></a> HStringReference:: CopyTo

현재 개체를 `HStringReference` HSTRING 개체로 복사 합니다.

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

## <a name="hstringreferenceget"></a><a name="get"></a> HStringReference:: Get

기본 HSTRING 핸들의 값을 검색 합니다.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>반환 값

기본 HSTRING 핸들의 값입니다.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a> HStringReference:: GetRawBuffer

기본 문자열 데이터에 대 한 포인터를 검색 합니다.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>매개 변수

*길이* **`int`** 데이터의 길이를 받는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`const`** 기본 문자열 데이터에 대 한 포인터입니다.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a> HStringReference:: HStringReference

`HStringReference` 클래스의 새 인스턴스를 초기화합니다.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>매개 변수

*sizeDest*<br/>
대상 버퍼의 크기를 지정 하는 템플릿 매개 변수입니다 `HStringReference` .

*str*<br/>
와이드 문자 문자열에 대한 참조입니다.

*len*<br/>
이 작업에 사용할 *str* 매개 변수 버퍼의 최대 길이입니다. *Len* 매개 변수를 지정 하지 않으면 전체 *str* 매개 변수가 사용 됩니다. *Len* 이 *sizedest* 보다 큰 경우 *len* 은 *sizedest*-1로 설정 됩니다.

*다른*<br/>
다른 `HStringReference` 개체입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `HStringReference` 매개 변수 *str* 과 동일한 크기의 새 개체를 초기화 합니다.

두 번째 생성자는 `HStringReference` 크기가 매개 변수 *len* 에에 새 개체를 초기화 합니다.

세 번째 생성자는 새 `HStringReference` 개체를 *다른* 매개 변수의 값으로 초기화 한 다음 *다른* 매개 변수를 소멸 시킵니다.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a> HStringReference:: operator =

다른 개체의 값을 `HStringReference` 현재 `HStringReference` 개체로 이동 합니다.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
기존 `HStringReference` 개체입니다.

### <a name="remarks"></a>설명

기존의 *다른* 개체의 값이 현재 개체에 복사 된 `HStringReference` 다음 *다른* 개체가 제거 됩니다.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a> HStringReference:: operator = =

두 매개 변수가 같은지 여부를 나타냅니다.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 는 `HStringReference` 개체 또는 hstring 핸들 일 수 있습니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다.  *rhs* 는 `HStringReference` 개체나 hstring 핸들 일 수 있습니다.

### <a name="return-value"></a>반환 값

**`true`***lhs* 및 *rhs* 매개 변수가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a> HStringReference:: operator! =

두 매개 변수가 같지 않은지 여부를 나타냅니다.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 는 `HStringReference` 개체 또는 hstring 핸들 일 수 있습니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다.  *rhs* 는 `HStringReference` 개체나 hstring 핸들 일 수 있습니다.

### <a name="return-value"></a>반환 값

**`true`***lhs* 및 *rhs* 매개 변수가 같지 않으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a> HStringReference:: operator&lt;

첫 번째 매개 변수가 두 번째 매개 변수 보다 작거나 같은지 여부를 나타냅니다.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 는에 대 한 참조일 수 있습니다 `HStringReference` .

*rhs*<br/>
비교할 두 번째 매개 변수입니다.  *rhs* 은에 대 한 참조일 수 있습니다 `HStringReference` .

### <a name="return-value"></a>반환 값

**`true`***lhs* 매개 변수가 *rhs* 매개 변수 보다 작은 경우 그렇지 않으면 **`false`** 입니다.
