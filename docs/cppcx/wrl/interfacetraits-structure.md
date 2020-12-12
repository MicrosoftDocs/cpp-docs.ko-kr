---
description: '자세히 알아보기: InterfaceTraits Structure'
title: InterfaceTraits 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: 8dfa540119b0a120ea7b8d9365a0e8b8203939b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124529"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>매개 변수

*I0*<br/>
인터페이스의 이름입니다.

*CloakedType*<br/>
`RuntimeClass`, 및의 경우 `Implements` `ChainInterfaces` 지원 되는 인터페이스 id 목록에 없는 인터페이스입니다.

## <a name="remarks"></a>설명

인터페이스의 공통 특성을 구현 합니다.

두 번째 템플릿은 숨겨진 인터페이스에 대 한 특수화입니다. 세 번째 템플릿은 Nil 매개 변수에 대 한 특수화입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a><a name="public-typedefs"></a> Public Typedef

Name   | 설명
------ | ------------------------------------------
`Base` | *I0* 템플릿 매개 변수의 동의어입니다.

### <a name="public-methods"></a>Public 메서드

이름                                                   | 설명
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits:: CanCastTo](#cancastto)               | 지정 된 포인터를에 대 한 포인터로 캐스팅할 수 있는지 여부를 나타냅니다 `Base` .
[InterfaceTraits:: CastToBase](#casttobase)             | 지정 된 포인터를에 대 한 포인터로 캐스팅 `Base` 합니다.
[InterfaceTraits:: CastToUnknown](#casttounknown)       | 지정 된 포인터를에 대 한 포인터로 캐스팅 `IUnknown` 합니다.
[InterfaceTraits:: FillArrayWithIid](#fillarraywithiid) | 의 인터페이스 ID를 `Base` 인덱스 인수로 지정 된 배열 요소에 할당 합니다.
[InterfaceTraits:: Verify](#verify)                     | `Base`가 올바르게 파생 되었는지 확인 합니다.

### <a name="public-constants"></a>공용 상수

Name                                   | 설명
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits:: IidCount](#iidcount) | 현재 개체와 연결 된 인터페이스 Id의 수를 유지 합니다 `InterfaceTraits` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`InterfaceTraits`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a> InterfaceTraits:: CanCastTo

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>매개 변수

*ptr*<br/>
형식에 대 한 포인터의 이름입니다.

*riid*<br/>
의 인터페이스 ID `Base` 입니다.

*ppv*<br/>
이 작업에 성공 하면 *ppv* 는로 지정 된 인터페이스를 가리킵니다 `Base` . 그렇지 않으면 *ppv* 가로 설정 됩니다 **`nullptr`** .

### <a name="return-value"></a>반환 값

**`true`** 이 작업이 성공 하 고 *ptr* 이에 대 한 포인터로 캐스팅 되 면이 고 `Base` , 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

지정 된 포인터를에 대 한 포인터로 캐스팅할 수 있는지 여부를 나타냅니다 `Base` .

에 대 한 자세한 내용은 `Base` [Public typedef](#public-typedefs) 섹션을 참조 하십시오.

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a> InterfaceTraits:: CastToBase

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
매개 변수 *ptr* 의 유형입니다.

*ptr*<br/>
*T* 형식에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`Base`에 대한 포인터입니다.

### <a name="remarks"></a>설명

지정 된 포인터를에 대 한 포인터로 캐스팅 `Base` 합니다.

에 대 한 자세한 내용은 `Base` [Public typedef](#public-typedefs) 섹션을 참조 하십시오.

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a> InterfaceTraits:: CastToUnknown

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
매개 변수 *ptr* 의 유형입니다.

*ptr*<br/>
*T* 형식에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

가 파생 된 IUnknown에 대 한 포인터 `Base` 입니다.

### <a name="remarks"></a>설명

지정 된 포인터를에 대 한 포인터로 캐스팅 `IUnknown` 합니다.

에 대 한 자세한 내용은 `Base` [Public typedef](#public-typedefs) 섹션을 참조 하십시오.

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a> InterfaceTraits:: FillArrayWithIid

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
0부터 시작 하는 인덱스 값을 포함 하는 필드에 대 한 포인터입니다.

*iid*<br/>
인터페이스 Id의 배열입니다.

### <a name="remarks"></a>설명

의 인터페이스 ID를 `Base` 인덱스 인수로 지정 된 배열 요소에 할당 합니다.

이 API의 이름과 반대로 하나의 배열 요소만 수정 됩니다. 전체 배열이 아닙니다.

에 대 한 자세한 내용은 `Base` [Public typedef](#public-typedefs) 섹션을 참조 하십시오.

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a> InterfaceTraits:: IidCount

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>설명

현재 개체와 연결 된 인터페이스 Id의 수를 유지 합니다 `InterfaceTraits` .

## <a name="interfacetraitsverify"></a><a name="verify"></a> InterfaceTraits:: Verify

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>설명

`Base`가 올바르게 파생 되었는지 확인 합니다.

에 대 한 자세한 내용은 `Base` [Public typedef](#public-typedefs) 섹션을 참조 하십시오.
