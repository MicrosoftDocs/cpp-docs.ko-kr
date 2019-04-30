---
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
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403089"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 클래스

기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>매개 변수

*Base*<br/>
기본 클래스입니다.

## <a name="remarks"></a>설명

기본 클래스 기본 생성자를 제공 해야 합니다.

다음 코드 예제에 사용 하는 방법을 보여 줍니다 `SimpleClassFactory` 사용 하 여 합니다 [ActivatableClassWithFactoryEx](activatableclass-macros.md) 매크로입니다.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance 메서드](#createinstance)|지정된 된 인터페이스의 인스턴스를 만듭니다.|

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

**헤더:** module.h

**네임스페이스:** Microsoft::WRL

## <a name="createinstance"></a>Simpleclassfactory:: Createinstance 메서드

지정된 된 인터페이스의 인스턴스를 만듭니다.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>매개 변수

*pUnkOuter*<br/>
해야 `nullptr`고, 그렇지 않으면 반환 값은 CLASS_E_NOAGGREGATION 합니다.

SimpleClassFactory 집계를 지원 하지 않습니다. 집계 된 지원 하 고 생성 되는 개체, 집계의 일부 였던 *pUnkOuter* 에 대 한 포인터를 제어 하는 것 `IUnknown` 집계의 인터페이스입니다.

*riid*<br/>
만들 개체의 ID를 인터페이스입니다.

*ppvObject*<br/>
이 작업이 완료 될 때, 지정 된 개체의 인스턴스에 대 한 포인터를 *riid* 매개 변수입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

하는 경우 `__WRL_STRICT__` 가 정의 된 assert 오류가 내보내집니다 클래스 템플릿 매개 변수에서 지정 된 기본 클래스에서 파생 되지 않습니다 [RuntimeClass](runtimeclass-class.md), 않거나 ClassicCom 또는 WinRtClassicComMix 구성 되지 않았습니다 [ RuntimeClassType](runtimeclasstype-enumeration.md) 열거형 값입니다.
