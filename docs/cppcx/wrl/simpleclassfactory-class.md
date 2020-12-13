---
description: '자세히 알아보기: SimpleClassFactory 클래스'
title: SimpleClassFactory 클래스
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: cd771909790f80048d8fee678b842f820e2f7be2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135202"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 클래스

기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>매개 변수

*하단*<br/>
기본 클래스입니다.

## <a name="remarks"></a>설명

기본 클래스는 기본 생성자를 제공 해야 합니다.

다음 코드 예제에서는 `SimpleClassFactory` [ActivatableClassWithFactoryEx](activatableclass-macros.md) 매크로와 함께를 사용 하는 방법을 보여 줍니다.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance 메서드](#createinstance)|지정 된 인터페이스의 인스턴스를 만듭니다.|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a> SimpleClassFactory:: CreateInstance 메서드

지정 된 인터페이스의 인스턴스를 만듭니다.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>매개 변수

*pUnkOuter*<br/>
이어야 합니다. **`nullptr`** 그렇지 않으면 반환 값이 CLASS_E_NOAGGREGATION 됩니다.

SimpleClassFactory는 집계를 지원 하지 않습니다. 집계가 지원 되 고 생성 되는 개체가 집계의 일부인 경우 *pUnkOuter* 는 집계의 제어 인터페이스에 대 한 포인터입니다 `IUnknown` .

*riid*<br/>
만들 개체의 인터페이스 ID입니다.

*ppvObject*<br/>
이 작업이 완료 되 면 *riid* 매개 변수로 지정 된 개체의 인스턴스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

`__WRL_STRICT__`가 정의 된 경우 클래스 템플릿 매개 변수에 지정 된 기본 클래스가 [RuntimeClass](runtimeclass-class.md)에서 파생 되지 않거나 ClassicCom 또는 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) 열거형 값으로 구성 되지 않은 경우 assert 오류가 발생 합니다.
