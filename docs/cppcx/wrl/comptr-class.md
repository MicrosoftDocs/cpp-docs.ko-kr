---
description: '자세히 알아보기: ComPtr 클래스'
title: ComPtr 클래스
ms.date: 06/02/2020
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: a78264a0728382bf78b14193d130b19b0095240b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273178"
---
# <a name="comptr-class"></a>ComPtr 클래스

템플릿 매개 변수로 지정된 인터페이스를 나타내는 *스마트 포인터* 형식을 만듭니다. `ComPtr`은 기본 인터페이스 포인터의 참조 개수를 자동으로 관리하여 참조 횟수가 0이 되면 인터페이스를 릴리스합니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
이 나타내는 인터페이스입니다 `ComPtr` .

*U*<br/>
현재이 friend 인 클래스입니다 `ComPtr` . 이 매개 변수를 사용하는 템플릿은 보호됩니다.

## <a name="remarks"></a>설명

`ComPtr<>` 기본 인터페이스 포인터를 나타내는 형식을 선언 합니다. 를 사용 하 여 `ComPtr<>` 변수를 선언한 다음 화살표 멤버 액세스 연산자 ()를 사용 `->` 하 여 인터페이스 멤버 함수에 액세스 합니다.

스마트 포인터에 대 한 자세한 내용은 [Com 코딩 방법](/windows/win32/LearnWin32/com-coding-practices) 문서의 "Com 스마트 포인터" 하위 섹션을 참조 하세요.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name            | 설명
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T* 템플릿 매개 변수로 지정 된 형식의 동의어입니다.

### <a name="public-constructors"></a>Public 생성자

이름                             | 설명
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:: ComPtr](#comptr)        | `ComPtr` 클래스의 새 인스턴스를 초기화합니다. 오버로드는 기본, 복사, 이동 및 변환 생성자를 제공합니다.
[ComPtr:: ~ ComPtr](#tilde-comptr) | 의 인스턴스를 초기화 하지 `ComPtr` 않습니다.

### <a name="public-methods"></a>Public 메서드

이름                                                      | 설명
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: As](#as)                                         | 지정 된 `ComPtr` 템플릿 매개 변수로 식별 되는 인터페이스를 나타내는 개체를 반환 합니다.
[ComPtr:: AsIID](#asiid)                                   | 지정 된 `ComPtr` 인터페이스 ID로 식별 되는 인터페이스를 나타내는 개체를 반환 합니다.
[ComPtr:: AsWeak](#asweak)                                 | 현재 개체에 대한 약한 참조를 검색합니다.
[ComPtr:: Attach](#attach)                                 | `ComPtr`현재 템플릿 형식 매개 변수에 지정 된 인터페이스 형식과이를 연결 합니다.
[ComPtr:: CopyTo](#copyto)                                 | 이와 연결 된 현재 또는 지정 된 인터페이스를 `ComPtr` 지정 된 출력 포인터에 복사 합니다.
[ComPtr::D etach](#detach)                                 | 이 `ComPtr` 가 나타내는 인터페이스에서이를 분리 합니다.
[ComPtr:: Get](#get)                                       | 이와 연결 된 인터페이스에 대 한 포인터를 검색 `ComPtr` 합니다.
[ComPtr:: GetAddressOf](#getaddressof)                     | 이가 나타내는 인터페이스에 대 한 포인터를 포함 하는 [ptr_](#ptr) 데이터 멤버의 주소를 검색 합니다 `ComPtr` .
[ComPtr:: ReleaseAndGetAddressOf](#releaseandgetaddressof) | 이와 연결 된 인터페이스를 해제 한 `ComPtr` 다음 해제 된 인터페이스에 대 한 포인터를 포함 하는 [ptr_](#ptr) 데이터 멤버의 주소를 검색 합니다.
[ComPtr::Reset](#reset)                                   | 이와 연결 된 인터페이스를 해제 `ComPtr` 하 고 새 참조 횟수를 반환 합니다.
[ComPtr:: Swap](#swap)                                     | 현재에 의해 관리 되는 인터페이스를 지정 된에서 관리 하는 `ComPtr` 인터페이스와 교환 합니다 `ComPtr` .

### <a name="protected-methods"></a>Protected 메서드

Name                                        | 설명
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr:: InternalAddRef](#internaladdref)   | 이와 연결 된 인터페이스의 참조 횟수를 늘립니다 `ComPtr` .
[ComPtr:: InternalRelease](#internalrelease) | 이와 연결 된 인터페이스에서 COM 해제 작업을 수행 `ComPtr` 합니다.

### <a name="public-operators"></a>Public 연산자

Name                                                                                           | 설명
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator&](#operator-ampersand)                                                       | 현재의 주소를 검색 합니다 `ComPtr` .
[ComPtr:: operator->](#operator-arrow)                                                          | 현재 템플릿 매개 변수에 지정된 형식에 대한 포인터를 검색합니다.
[ComPtr:: operator =](#operator-assign)                                                          | 현재에 값을 할당 `ComPtr` 합니다.
[ComPtr:: operator = =](#operator-equality)                                                       | 두 `ComPtr` 개체가 같은지를 나타냅니다.
[ComPtr:: operator! =](#operator-inequality)                                                     | 두 개체가 같지 않은지 여부를 나타냅니다 `ComPtr` .
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType](#operator-microsoft-wrl-details-booltype) | 가 `ComPtr` 인터페이스의 개체 수명을 관리 하 고 있는지 여부를 나타냅니다.

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                 | 설명
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::p tr_](#ptr) | 이에 연결 되어 있고이에서 관리 하는 인터페이스에 대 한 포인터를 포함 `ComPtr` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ComPtr`

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임스페이스:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a> ComPtr:: ~ ComPtr

의 인스턴스를 초기화 하지 `ComPtr` 않습니다.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a> ComPtr:: As

지정 된 `ComPtr` 템플릿 매개 변수로 식별 되는 인터페이스를 나타내는 개체를 반환 합니다.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>매개 변수

*U*<br/>
매개 변수 *p* 로 나타낼 인터페이스입니다.

*®*<br/>
`ComPtr`매개 변수 *U* 로 지정 된 인터페이스를 나타내는 개체입니다. *P* 매개 변수는 현재 개체를 참조 하지 않아야 합니다 `ComPtr` .

### <a name="remarks"></a>설명

첫 번째 템플릿은 코드에서 사용해야 하는 폼입니다. 두 번째 템플릿은 내부 도우미 특수화입니다. [Auto](../../cpp/auto-cpp.md) 형식 추론 키워드와 같은 c + + 언어 기능을 지원 합니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="comptrasiid"></a><a name="asiid"></a> ComPtr:: AsIID

지정 된 `ComPtr` 인터페이스 ID로 식별 되는 인터페이스를 나타내는 개체를 반환 합니다.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID입니다.

*®*<br/>
개체에 ID가 *riid* 인 인터페이스가 있는 경우 *riid* 매개 변수로 지정 된 인터페이스에 대 한 이중 간접 포인터입니다. 그렇지 않으면에 대 한 포인터 `IUnknown` 입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="comptrasweak"></a><a name="asweak"></a> ComPtr:: AsWeak

현재 개체에 대한 약한 참조를 검색합니다.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>매개 변수

*pWeakRef*<br/>
이 작업이 완료 되 면 약한 참조 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="comptrattach"></a><a name="attach"></a> ComPtr:: Attach

`ComPtr`현재 템플릿 형식 매개 변수에 지정 된 인터페이스 형식과이를 연결 합니다.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
인터페이스 형식입니다.

## <a name="comptrcomptr"></a><a name="comptr"></a> ComPtr:: ComPtr

`ComPtr` 클래스의 새 인스턴스를 초기화합니다. 오버로드는 기본, 복사, 이동 및 변환 생성자를 제공합니다.

```cpp
WRL_NOTHROW ComPtr();

WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);

template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);

WRL_NOTHROW ComPtr(
   const ComPtr& other
);

template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>매개 변수

*U*<br/>
*다른* 매개 변수의 형식입니다.

*다른*<br/>
*U* 형식의 개체입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

첫 번째 생성자는 빈 개체를 암시적으로 만드는 기본 생성자입니다. 두 번째 생성자는 빈 개체를 명시적으로 만드는 [__nullptr](../../extensions/nullptr-cpp-component-extensions.md)를 지정 합니다.

세 번째 생성자는 포인터로 지정 된 개체에서 개체를 만듭니다. 이제 ComPtr가 가리키는 메모리를 소유 하 고이에 대 한 참조 횟수를 유지 관리 합니다.

네 번째 및 다섯 번째 생성자는 복사 생성자입니다. 다섯 번째 생성자는 현재 형식으로 변환할 수 있는 경우 개체를 복사 합니다.

여섯 번째 및 일곱 번째 생성자는 이동 생성자입니다. 일곱 번째 생성자는 현재 형식으로 변환할 수 있는 경우 개체를 이동 합니다.

## <a name="comptrcopyto"></a><a name="copyto"></a> ComPtr:: CopyTo

이와 연결 된 현재 또는 지정 된 인터페이스를 `ComPtr` 지정 된 포인터에 복사 합니다.

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>매개 변수

*U*<br/>
형식 이름.

*ptr*<br/>
이 작업이 완료 되 면 요청 된 인터페이스에 대 한 포인터입니다.

*riid*<br/>
인터페이스 ID입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 암시적 작업이 실패 한 이유를 나타내는 HRESULT입니다 `QueryInterface` .

### <a name="remarks"></a>설명

첫 번째 함수는이와 연결 된 인터페이스에 대 한 포인터의 복사본을 반환 합니다 `ComPtr` . 이 함수는 항상 S_OK 반환 합니다.

두 번째 함수는 `QueryInterface` `ComPtr` *riid* 매개 변수로 지정 된 인터페이스에 대해이와 연결 된 인터페이스에서 작업을 수행 합니다.

세 번째 함수는 `QueryInterface` `ComPtr`  *U* 매개 변수의 기본 인터페이스에 대해 this와 연결 된 인터페이스에서 작업을 수행 합니다.

## <a name="comptrdetach"></a><a name="detach"></a> ComPtr::D etach

이 `ComPtr` 개체를 나타내는 인터페이스에서이 개체의 분리를 끊습니다.

```cpp
T* Detach();
```

### <a name="return-value"></a>반환 값

이 개체가 나타내는 인터페이스에 대 한 포인터입니다 `ComPtr` .

## <a name="comptrget"></a><a name="get"></a> ComPtr:: Get

이와 연결 된 인터페이스에 대 한 포인터를 검색 `ComPtr` 합니다.

```cpp
T* Get() const;
```

### <a name="return-value"></a>반환 값

이와 연결 된 인터페이스에 대 한 포인터 `ComPtr` 입니다.

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a> ComPtr:: GetAddressOf

이가 나타내는 인터페이스에 대 한 포인터를 포함 하는 [ptr_](#ptr) 데이터 멤버의 주소를 검색 합니다 `ComPtr` .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>반환 값

변수의 주소입니다.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a> ComPtr:: InternalAddRef

이와 연결 된 인터페이스의 참조 횟수를 늘립니다 `ComPtr` .

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>설명

이 메서드는 protected입니다.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a> ComPtr:: InternalRelease

이와 연결 된 인터페이스에서 COM 해제 작업을 수행 `ComPtr` 합니다.

```cpp
unsigned long InternalRelease();
```

### <a name="remarks"></a>설명

이 메서드는 protected입니다.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a> ComPtr:: operator&amp;

이 개체와 연결 된 인터페이스를 해제 한 `ComPtr` 다음 개체의 주소를 검색 합니다 `ComPtr` .

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>반환 값

현재에 대 한 약한 참조 `ComPtr` 입니다.

### <a name="remarks"></a>설명

이 메서드는 인터페이스 포인터에 대 한 참조를 해제 하는 [ComPtr:: GetAddressOf](#getaddressof) 와는 다릅니다. `ComPtr::GetAddressOf`인터페이스 포인터의 주소가 필요 하지만 해당 인터페이스를 해제 하지 않으려는 경우에 사용 합니다.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a> ComPtr:: operator-&gt;

현재 템플릿 매개 변수에 지정된 형식에 대한 포인터를 검색합니다.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>반환 값

현재 템플릿 형식 이름으로 지정 된 형식에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 도우미 함수는 STDMETHOD 매크로를 사용 하 여 발생 하는 불필요 한 오버 헤드를 제거 합니다. 이 함수 `IUnknown` **`private`** 는 대신 형식을 사용 **`virtual`** 합니다.

## <a name="comptroperator"></a><a name="operator-assign"></a> ComPtr:: operator =

현재에 값을 할당 `ComPtr` 합니다.

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>매개 변수

*U*<br/>
클래스입니다.

*다른*<br/>
형식 또는 다른 형식에 대 한 포인터, 참조 또는 rvalue 참조 `ComPtr` 입니다.

### <a name="return-value"></a>반환 값

현재에 대 한 참조 `ComPtr` 입니다.

### <a name="remarks"></a>설명

이 연산자의 첫 번째 버전은 빈 값을 현재에 할당 합니다 `ComPtr` .

두 번째 버전에서는 할당 인터페이스 포인터가 현재 인터페이스 포인터와 같지 않은 경우 `ComPtr` 두 번째 인터페이스 포인터가 현재에 할당 됩니다 `ComPtr` .

세 번째 버전에서는 할당 인터페이스 포인터가 현재에 할당 됩니다 `ComPtr` .

네 번째 버전에서 할당 값의 인터페이스 포인터가 현재 인터페이스 포인터와 같지 않은 경우 `ComPtr` 두 번째 인터페이스 포인터가 현재에 할당 됩니다 `ComPtr` .

다섯 번째 버전은 복사 연산자입니다. 에 대 한 참조가 `ComPtr` 현재에 할당 `ComPtr` 된 경우

여섯 번째 버전은 이동 의미 체계를 사용 하는 복사 연산자입니다. `ComPtr` 정적 캐스트 형식이 고 현재에 할당 된 경우에 대 한 rvalue 참조입니다 `ComPtr` .

일곱 번째 버전은 이동 의미 체계를 사용 하는 복사 연산자입니다. U 형식의에 대 한 rvalue 참조 `ComPtr` 는 정적 캐스팅 된 후 현재에 할당 됩니다  `ComPtr` .

## <a name="comptroperator"></a><a name="operator-equality"></a> ComPtr:: operator = =

두 `ComPtr` 개체가 같은지를 나타냅니다.

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>매개 변수

*은*<br/>
`ComPtr` 개체에 대한 참조입니다.

*b*<br/>
다른 개체에 대 한 참조 `ComPtr` 입니다.

### <a name="return-value"></a>반환 값

첫 번째 연산자는 **`true`** 개체 *a* 가 개체 *b* 와 같으면를, 그렇지 않으면를 생성 **`false`** 합니다.

두 번째 및 세 번째 연산자는 **`true`** 개체 *a* 가와 같으면 **`nullptr`** 이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="comptroperator"></a><a name="operator-inequality"></a> ComPtr:: operator! =

두 개체가 같지 않은지 여부를 나타냅니다 `ComPtr` .

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>매개 변수

*은*<br/>
`ComPtr` 개체에 대한 참조입니다.

*b*<br/>
다른 개체에 대 한 참조 `ComPtr` 입니다.

### <a name="return-value"></a>반환 값

첫 번째 연산자는 **`true`** 개체 *a* 가 개체 *b* 와 같지 않으면를, 그렇지 않으면를 생성 **`false`** 합니다.

두 번째 및 세 번째 연산자는 **`true`** 개체 *a* 가와 같지 않으면를 **`nullptr`** , 그렇지 않으면를 생성 **`false`** 합니다.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a> ComPtr:: operator Microsoft:: WRL::D etails:: BoolType

가 `ComPtr` 인터페이스의 개체 수명을 관리 하 고 있는지 여부를 나타냅니다.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>반환 값

인터페이스가이와 연결 된 경우 `ComPtr` [BoolStruct:: member](boolstruct-structure.md#member) 데이터 멤버의 주소이 고, 그렇지 않으면 **`nullptr`** 입니다.

## <a name="comptrptr_"></a><a name="ptr"></a> ComPtr::p tr_

이에 연결 되어 있고이에서 관리 하는 인터페이스에 대 한 포인터를 포함 `ComPtr` 합니다.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>설명

`ptr_` 는 보호 된 내부 데이터 멤버입니다.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a> ComPtr:: ReleaseAndGetAddressOf

이와 연결 된 인터페이스를 해제 한 `ComPtr` 다음 해제 된 인터페이스에 대 한 포인터를 포함 하는 [ptr_](#ptr) 데이터 멤버의 주소를 검색 합니다.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>반환 값

이의 [ptr_](#ptr) 데이터 멤버 주소입니다 `ComPtr` .

## <a name="comptrreset"></a><a name="reset"></a> ComPtr:: Reset

이와 연결 된 인터페이스를 해제 `ComPtr` 하 고 새 참조 횟수를 반환 합니다.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>반환 값

기본 인터페이스에 남아 있는 경우 참조의 수입니다 (있는 경우).

## <a name="comptrswap"></a><a name="swap"></a> ComPtr:: Swap

현재에 의해 관리 되는 인터페이스를 지정 된에서 관리 하는 `ComPtr` 인터페이스와 교환 합니다 `ComPtr` .

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>매개 변수

*r*<br/>
`ComPtr`
