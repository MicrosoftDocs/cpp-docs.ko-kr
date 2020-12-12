---
description: '자세히 알아보기: ComPtrRefBase 클래스'
title: ComPtrRefBase 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: 4dce58e8292092084916c24153d543f2a45856fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273139"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
로 표현 되는 인터페이스 뿐만 아니라 [ \<T> ComPtr](comptr-class.md) 형식 또는 여기에서 파생 된 형식 `ComPtr` 입니다.

## <a name="remarks"></a>설명

[Comptrref](comptrref-class.md) 클래스의 기본 클래스를 나타냅니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name            | 설명
--------------- | -------------------------------------------------
`InterfaceType` | 템플릿 매개 변수 *T* 형식의 동의어입니다.

### <a name="public-operators"></a>Public 연산자

Name                                                                       | 설명
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase:: operator IInspectable * *](#operator-iinspectable-star-star) | 현재 [ptr_](#ptr) 데이터 멤버를 인터페이스에 대 한 포인터 포인터로 캐스팅 `IInspectable` 합니다.
[ComPtrRefBase:: operator IUnknown * *](#operator-iunknown-star-star)         | 현재 [ptr_](#ptr) 데이터 멤버를 인터페이스에 대 한 포인터 포인터로 캐스팅 `IUnknown` 합니다.

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                        | 설명
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::p tr_](#ptr) | 현재 템플릿 매개 변수에 지정 된 형식에 대 한 포인터입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ComPtrRefBase`

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase:: operator IInspectable \* \* 연산자

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>설명

현재 [ptr_](#ptr) 데이터 멤버를 인터페이스에 대 한 포인터 포인터로 캐스팅 `IInspectable` 합니다.

현재이 `ComPtrRefBase` 에서 파생 되지 않으면 오류가 내보내집니다 `IInspectable` .

이 캐스트는가 정의 된 경우에만 사용할 수 있습니다 `__WRL_CLASSIC_COM__` .

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a> ComPtrRefBase:: operator IUnknown * * 연산자

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>설명

현재 [ptr_](#ptr) 데이터 멤버를 인터페이스에 대 한 포인터 포인터로 캐스팅 `IUnknown` 합니다.

현재이 `ComPtrRefBase` 에서 파생 되지 않으면 오류가 내보내집니다 `IUnknown` .

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a> ComPtrRefBase::p tr_

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
T* ptr_;
```

### <a name="remarks"></a>설명

현재 템플릿 매개 변수에 지정 된 형식에 대 한 포인터입니다. `ptr_` 보호 된 데이터 멤버입니다.
