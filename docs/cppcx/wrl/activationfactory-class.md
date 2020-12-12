---
description: '자세히 알아보기: ActivationFactory 클래스'
title: ActivationFactory 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 7204a3c2f981947a03efba648dd91b69d582fee1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287842"
---
# <a name="activationfactory-class"></a>ActivationFactory 클래스

Windows 런타임으로 활성화할 클래스를 하나 이상 사용합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>매개 변수

*I0*<br/>
0 번째 인터페이스입니다.

*I1*<br/>
첫 번째 인터페이스입니다.

*I2*<br/>
두 번째 인터페이스입니다.

## <a name="remarks"></a>설명

`ActivationFactory` 인터페이스에 대 한 등록 메서드 및 기본 기능을 제공 `IActivationFactory` 합니다. `ActivationFactory` 사용자 지정 팩터리 구현을 제공할 수도 있습니다.

다음 코드 조각 기호로는 ActivationFactory를 사용 하는 방법을 보여 줍니다.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

다음 코드 조각에서는 [Implements](implements-structure.md) 구조체를 사용 하 여 세 개 이상의 인터페이스 id를 지정 하는 방법을 보여 줍니다.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                       | 설명
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory:: ActivationFactory](#activationfactory) | `ActivationFactory` 클래스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                           | 설명
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory:: AddRef](#addref)                           | 현재 개체의 참조 횟수를 늘립니다 `ActivationFactory` .
[ActivationFactory:: GetIids](#getiids)                         | 구현된 인터페이스 ID의 배열을 가져옵니다.
[ActivationFactory:: GetRuntimeClassName](#getruntimeclassname) | 현재에서 인스턴스화하는 개체의 런타임 클래스 이름을 가져옵니다 `ActivationFactory` .
[ActivationFactory:: GetTrustLevel](#gettrustlevel)             | 현재가 인스턴스화하는 개체의 신뢰 수준을 가져옵니다 `ActivationFactory` .
[ActivationFactory:: QueryInterface](#queryinterface)           | 지정 된 인터페이스에 대 한 포인터를 검색 합니다.
[ActivationFactory:: Release](#release)                         | 현재 개체의 참조 횟수를 감소 시킵니다 `ActivationFactory` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a> ActivationFactory:: ActivationFactory

`ActivationFactory` 클래스를 초기화합니다.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a> ActivationFactory:: AddRef

현재 개체의 참조 횟수를 늘립니다 `ActivationFactory` .

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다.

## <a name="activationfactorygetiids"></a><a name="getiids"></a> ActivationFactory:: GetIids

구현된 인터페이스 ID의 배열을 가져옵니다.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>매개 변수

*iidCount*<br/>
이 작업이 완료 되 면 *iid* 배열의 인터페이스 id 수입니다.

*iid*<br/>
이 작업이 완료될 대 구현된 인터페이스 ID의 배열입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다. E_OUTOFMEMORY는 가능한 실패 HRESULT입니다.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a> ActivationFactory:: GetRuntimeClassName

현재에서 인스턴스화하는 개체의 런타임 클래스 이름을 가져옵니다 `ActivationFactory` .

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>매개 변수

*Runti을 Ame*<br/>
이 작업이 완료 되 면 현재에서 인스턴스화하는 개체의 런타임 클래스 이름을 포함 하는 문자열에 대 한 핸들입니다 `ActivationFactory` .

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a> ActivationFactory:: GetTrustLevel

현재가 인스턴스화하는 개체의 신뢰 수준을 가져옵니다 `ActivationFactory` .

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>매개 변수

*trustLvl*<br/>
이 작업이 완료 되 면에서 인스턴스화하는 런타임 클래스의 신뢰 수준입니다 `ActivationFactory` .

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 어설션 오류가 내보내지고 *Trustlvl* 이로 설정 됩니다 `FullTrust` .

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a> ActivationFactory:: QueryInterface

지정 된 인터페이스에 대 한 포인터를 검색 합니다.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID입니다.

*ppvObject*<br/>
이 작업이 완료 되 면 매개 변수 *riid* 에서 지정 하는 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다.

## <a name="activationfactoryrelease"></a><a name="release"></a> ActivationFactory:: Release

현재 개체의 참조 횟수를 감소 시킵니다 `ActivationFactory` .

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다.
