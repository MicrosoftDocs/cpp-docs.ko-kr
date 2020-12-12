---
description: '자세히 알아보기: ChainInterfaces Structure'
title: ChainInterfaces 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: cc943b16d587a3b542e49d72e6bdc24ba2546e16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328867"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces 구조체

인터페이스 ID 집합에 적용할 수 있는 확인 및 초기화 함수를 지정합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>매개 변수

*I0*<br/>
하다 인터페이스 ID 0입니다.

*I1*<br/>
하다 인터페이스 ID 1입니다.

*I2*<br/>
필드 인터페이스 ID 2.

*I3*<br/>
필드 인터페이스 ID 3.

*I4*<br/>
필드 인터페이스 ID 4입니다.

*I5*<br/>
필드 인터페이스 ID 5입니다.

*I6*<br/>
필드 인터페이스 ID 6.

*I7*<br/>
필드 인터페이스 ID 7.

*I8*<br/>
필드 인터페이스 ID 8.

*I9*<br/>
필드 인터페이스 ID 9입니다.

*DerivedType*<br/>
파생 형식입니다.

*BaseType*<br/>
파생 형식의 기본 형식입니다.

*hasImplements*<br/>
인 경우 **`true`** [Implements](implements-structure.md) 구조체에서 파생 되지 않은 클래스와 함께 [MixIn](mixin-structure.md) 구조체를 사용할 수 없음을 의미 하는 부울 값입니다.

## <a name="members"></a>멤버

### <a name="protected-methods"></a>Protected 메서드

Name                                                   | 설명
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces:: CanCastTo](#cancastto)               | 지정 된 인터페이스 ID를 템플릿 매개 변수로 정의 된 각 특수화로 캐스팅할 수 있는지 여부를 나타냅니다 `ChainInterface` .
[ChainInterfaces:: CastToUnknown](#casttounknown)       | *I0* template 매개 변수에 의해 정의 된 형식의 인터페이스 포인터를에 대 한 포인터로 캐스팅 `IUnknown` 합니다.
[ChainInterfaces:: FillArrayWithIid](#fillarraywithiid) | *I0* template 매개 변수에 의해 정의 된 인터페이스 id를 지정 된 인터페이스 id 배열의 지정 된 위치에 저장 합니다.
[ChainInterfaces:: Verify](#verify)                     | *I0* 를 통해 *I9* 템플릿 매개 변수로 정의 된 각 인터페이스가 및/또는에서 상속 되 `IUnknown` `IInspectable` 고 *I0* 이 *I1* 에서 *I9* 로 상속 하는지 확인 합니다.

### <a name="protected-constants"></a>Protected 상수

Name                                   | 설명
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces:: IidCount](#iidcount) | *I9* 을 통해 *I0* 템플릿 매개 변수로 지정 된 인터페이스에 포함 된 인터페이스 id의 총 수입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`I0`

`ChainInterfaces`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a> ChainInterfaces:: CanCastTo

지정 된 인터페이스 ID를 기본이 아닌 템플릿 매개 변수로 정의 된 각 특수화로 캐스팅할 수 있는지 여부를 나타냅니다.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID입니다.

*ppv*<br/>
성공적으로 캐스팅 된 마지막 인터페이스 ID에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**`true`** 모든 캐스트 작업이 성공 했으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a> ChainInterfaces:: CastToUnknown

*I0* template 매개 변수에 의해 정의 된 형식의 인터페이스 포인터를에 대 한 포인터로 캐스팅 `IUnknown` 합니다.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>반환 값

`IUnknown`에 대한 포인터입니다.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a> ChainInterfaces:: FillArrayWithIid

*I0* template 매개 변수에 의해 정의 된 인터페이스 id를 지정 된 인터페이스 id 배열의 지정 된 위치에 저장 합니다.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
*Iid* 배열의 인덱스 값에 대 한 포인터입니다.

*iid*<br/>
인터페이스 Id의 배열입니다.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a> ChainInterfaces:: IidCount

*I9* 을 통해 *I0* 템플릿 매개 변수로 지정 된 인터페이스에 포함 된 인터페이스 id의 총 수입니다.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>반환 값

인터페이스 ID의 총 개수입니다.

### <a name="remarks"></a>설명

템플릿 매개 변수 *I0* 및 *I1* 이 필요 하며, *I9* 를 통한 *I2* 매개 변수는 선택 사항입니다. 각 인터페이스의 IID 수는 일반적으로 1입니다.

## <a name="chaininterfacesverify"></a><a name="verify"></a> ChainInterfaces:: Verify

*I0* 를 통해 *I9* 템플릿 매개 변수로 정의 된 각 인터페이스가 및/또는에서 상속 되 `IUnknown` `IInspectable` 고 *I0* 이 *I1* 에서 *I9* 로 상속 하는지 확인 합니다.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>설명

확인 작업이 실패 하는 경우는 오류 **`static_assert`** 를 설명 하는 오류 메시지를 내보냅니다.

템플릿 매개 변수 *I0* 및 *I1* 이 필요 하며, *I9* 를 통한 *I2* 매개 변수는 선택 사항입니다.
