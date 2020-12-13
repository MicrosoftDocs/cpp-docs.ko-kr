---
description: '자세히 알아보기: SimpleActivationFactory 클래스'
title: SimpleActivationFactory 클래스
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 83643c69977b887e58e430bbd500fcf7c2e81ca6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135215"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 클래스

Windows 런타임 또는 클래식 COM 기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>매개 변수

*하단*<br/>
기본 클래스입니다.

## <a name="remarks"></a>설명

기본 클래스는 기본 생성자를 제공 해야 합니다.

다음 코드 예제에서는 [ActivatableClassWithFactoryEx](activatableclass-macros.md) 매크로와 함께 SimpleActivationFactory를 사용 하는 방법을 보여 줍니다.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance 메서드](#activateinstance)|지정 된 인터페이스의 인스턴스를 만듭니다.|
|[SimpleActivationFactory::GetRuntimeClassName 메서드](#getruntimeclassname)|*기본* 클래스 템플릿 매개 변수로 지정 된 클래스 인스턴스의 런타임 클래스 이름을 가져옵니다.|
|[SimpleActivationFactory::GetTrustLevel 메서드](#gettrustlevel)|*기본* 클래스 템플릿 매개 변수로 지정 된 클래스 인스턴스의 신뢰 수준을 가져옵니다.|

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

`SimpleActivationFactory`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a> SimpleActivationFactory:: Instance 메서드

지정 된 인터페이스의 인스턴스를 만듭니다.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>매개 변수

*ppvObject*<br/>
이 작업이 완료 되 면 클래스 템플릿 매개 변수로 지정 된 개체의 인스턴스에 대 한 포인터 `Base` 입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

`__WRL_STRICT__`가 정의 된 경우 클래스 템플릿 매개 변수에 지정 된 기본 클래스가 [RuntimeClass](runtimeclass-class.md)에서 파생 되지 않거나 WinRt 또는 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) 열거형 값으로 구성 되지 않은 경우 assert 오류가 발생 합니다.

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a> SimpleActivationFactory:: GetRuntimeClassName 메서드

클래스 템플릿 매개 변수로 지정 된 클래스 인스턴스의 런타임 클래스 이름을 가져옵니다 `Base` .

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>매개 변수

*Runti을 Ame*<br/>
이 작업이 완료 되 면 런타임 클래스 이름입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

`__WRL_STRICT__`가 정의 된 경우 `Base` 클래스 템플릿 매개 변수로 지정 된 클래스가 [RuntimeClass](runtimeclass-class.md)에서 파생 되지 않거나 WinRt 또는 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) 열거형 값으로 구성 되지 않은 경우 assert 오류가 내보내집니다.

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a> SimpleActivationFactory:: GetTrustLevel 메서드

클래스 템플릿 매개 변수로 지정 된 클래스 인스턴스의 신뢰 수준을 가져옵니다 `Base` .

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>매개 변수

*trustLvl*<br/>
이 작업이 완료 되 면 현재 클래스 개체의 신뢰 수준입니다.

### <a name="return-value"></a>반환 값

항상 S_OK 합니다.
