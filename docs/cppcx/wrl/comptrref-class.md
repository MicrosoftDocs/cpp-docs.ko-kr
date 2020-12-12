---
description: '자세히 알아보기: ComPtrRef 클래스'
title: ComPtrRef 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: 42a0698c8eb393c84422b52ee112013b91fe39e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273152"
---
# <a name="comptrref-class"></a>ComPtrRef 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
로 표현 되는 인터페이스 뿐만 아니라 [ \<T> ComPtr](comptr-class.md) 형식 또는 여기에서 파생 된 형식 `ComPtr` 입니다.

## <a name="remarks"></a>설명

형식의 개체에 대 한 참조를 나타냅니다 `ComPtr<T>` .

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                               | 설명
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef:: ComPtrRef](#comptrref) | `ComPtrRef`지정 된 포인터에서 다른 개체에 대 한 클래스의 새 인스턴스를 초기화 `ComPtrRef` 합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                         | 설명
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef:: GetAddressOf](#getaddressof)                     | 현재 개체가 나타내는 인터페이스에 대 한 포인터의 주소를 검색 합니다 `ComPtrRef` .
[ComPtrRef:: ReleaseAndGetAddressOf](#releaseandgetaddressof) | 현재 개체를 삭제 `ComPtrRef` 하 고 개체가 나타내는 인터페이스에 대 한 포인터 포인터를 반환 합니다 `ComPtrRef` .

### <a name="public-operators"></a>Public 연산자

Name                                                                     | 설명
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef:: operator InterfaceType * *](#operator-interfacetype-star-star) | 현재 개체를 삭제 `ComPtrRef` 하 고 개체가 나타내는 인터페이스에 대 한 포인터 포인터를 반환 합니다 `ComPtrRef` .
[ComPtrRef:: operator T *](#operator-t-star)                               | 현재 ComPtrRef 개체의 [ptr_](comptrrefbase-class.md#ptr) 데이터 멤버 값을 반환 합니다.
[ComPtrRef:: operator void * *](#operator-void-star-star)                   | 현재 개체를 삭제 하 고, 개체로 표시 된 인터페이스에 대 한 포인터를 포인터로 `ComPtrRef` 캐스팅 한 `ComPtrRef` **`void`** 다음 캐스트 포인터를 반환 합니다.
[ComPtrRef:: operator *](#operator-star)                                   | 현재 개체가 나타내는 인터페이스에 대 한 포인터를 검색 합니다 `ComPtrRef` .
[ComPtrRef:: operator = =](#operator-equality)                              | 두 `ComPtrRef` 개체가 같은지를 나타냅니다.
[ComPtrRef:: operator! =](#operator-inequality)                            | 두 `ComPtrRef` 개체가 같지 않은지를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a> ComPtrRef:: ComPtrRef

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>매개 변수

*ptr*<br/>
다른 개체의 내부 값입니다 `ComPtrRef` .

### <a name="remarks"></a>설명

`ComPtrRef`지정 된 포인터에서 다른 개체에 대 한 클래스의 새 인스턴스를 초기화 `ComPtrRef` 합니다.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a> ComPtrRef:: GetAddressOf

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>반환 값

현재 개체가 나타내는 인터페이스에 대 한 포인터의 주소입니다 `ComPtrRef` .

### <a name="remarks"></a>설명

현재 개체가 나타내는 인터페이스에 대 한 포인터의 주소를 검색 합니다 `ComPtrRef` .

## <a name="comptrrefoperator"></a><a name="operator-equality"></a> ComPtrRef:: operator = =

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>매개 변수

*은*<br/>
`ComPtrRef` 개체에 대한 참조입니다.

*b*<br/>
다른 개체에 대 한 참조 `ComPtrRef` 또는 익명 형식에 대 한 포인터 ( **`void*`** )

### <a name="return-value"></a>반환 값

첫 번째 연산자는 **`true`** 개체 *a* 가 개체 *b* 와 같으면를, 그렇지 않으면를 생성 **`false`** 합니다.

두 번째 및 세 번째 연산자는 **`true`** 개체 *a* 가와 같으면 **`nullptr`** 이 고, 그렇지 않으면 **`false`** 입니다.

네 번째 및 다섯 번째 연산자는 **`true`** 개체 *a* 가 개체 *b* 와 같으면이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

두 `ComPtrRef` 개체가 같은지를 나타냅니다.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a> ComPtrRef:: operator! =

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>매개 변수

*은*<br/>
`ComPtrRef` 개체에 대한 참조입니다.

*b*<br/>
다른 개체에 대 한 참조 `ComPtrRef` 또는 익명 개체에 대 한 포인터 ( **`void*`** )

### <a name="return-value"></a>반환 값

첫 번째 연산자는 **`true`** 개체 *a* 가 개체 *b* 와 같지 않으면를, 그렇지 않으면를 생성 **`false`** 합니다.

두 번째 및 세 번째 연산자는 **`true`** 개체 *a* 가와 같지 않으면를 **`nullptr`** , 그렇지 않으면를 생성 **`false`** 합니다.

네 번째 및 다섯 번째 연산자는 **`true`** 개체 *a* 가 개체 *b* 와 같지 않으면를, 그렇지 않으면를 생성 **`false`** 합니다.

### <a name="remarks"></a>설명

두 `ComPtrRef` 개체가 같지 않은지를 나타냅니다.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a> ComPtrRef:: operator InterfaceType\*\*

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>설명

현재 개체를 삭제 `ComPtrRef` 하 고 개체가 나타내는 인터페이스에 대 한 포인터 포인터를 반환 합니다 `ComPtrRef` .

## <a name="comptrrefoperator"></a><a name="operator-star"></a> ComPtrRef:: operator *

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>반환 값

현재 개체가 나타내는 인터페이스에 대 한 포인터 `ComPtrRef` 입니다.

### <a name="remarks"></a>설명

현재 개체가 나타내는 인터페이스에 대 한 포인터를 검색 합니다 `ComPtrRef` .

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a> ComPtrRef:: operator T *

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
operator T*();
```

### <a name="remarks"></a>설명

현재 개체의 [ptr_](comptrrefbase-class.md#ptr) 데이터 멤버 값을 반환 합니다 `ComPtrRef` .

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a> ComPtrRef:: operator void\*\*

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
operator void**() const;
```

### <a name="remarks"></a>설명

현재 개체를 삭제 하 고, 개체로 표시 된 인터페이스에 대 한 포인터를 포인터로 `ComPtrRef` 캐스팅 한 `ComPtrRef` **`void`** 다음 캐스트 포인터를 반환 합니다.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a> ComPtrRef:: ReleaseAndGetAddressOf

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>반환 값

삭제 된 개체가 나타내는 인터페이스에 대 한 포인터입니다 `ComPtrRef` .

### <a name="remarks"></a>설명

현재 개체를 삭제 `ComPtrRef` 하 고 개체가 나타내는 인터페이스에 대 한 포인터 포인터를 반환 합니다 `ComPtrRef` .
