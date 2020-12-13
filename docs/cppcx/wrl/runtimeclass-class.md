---
description: '자세히 알아보기: RuntimeClass 클래스'
title: RuntimeClass 클래스
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: f62eec0b5ac9b8fc8ecac390ea07077743fdcb51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330756"
---
# <a name="runtimeclass-class"></a>RuntimeClass 클래스

지정 된 인터페이스를 상속 하 고 지정 된 Windows 런타임, 클래식 COM 및 약한 참조 지원을 제공 하는 WinRT 또는 COM 클래스를 나타냅니다.

이 클래스는 WinRT 및 COM 클래스의 상용구 구현을 제공 하 고, 등의 구현을 제공 하 여 `QueryInterface` `AddRef` `Release` 모듈의 참조 횟수를 관리 하며 활성화 가능한 개체에 대해 클래스 팩터리를 제공 하도록 지원 합니다.

## <a name="syntax"></a>구문

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>매개 변수

*classFlags*<br/>
선택적 매개 변수입니다. 하나 이상의 [RuntimeClassType](runtimeclasstype-enumeration.md) 열거형 값의 조합입니다. `__WRL_CONFIGURATION_LEGACY__`매크로를 정의 하 여 프로젝트의 모든 런타임 클래스에 대 한 classFlags의 기본값을 변경할 수 있습니다. 정의 된 경우 RuntimeClass 인스턴스는 기본적으로 agile이 아닙니다. 정의 되지 않은 경우 RuntimeClass 인스턴스는 기본적으로 agile입니다. 모호성을 방지 하려면 또는에서 항상를 지정 합니다 `Microsoft::WRL::FtmBase` `TInterfaces` `RuntimeClassType::InhibitFtmBase` . InhibitFtmBase 및 FtmBase를 모두 사용 하는 경우 개체는 agile이 됩니다.

*TInterfaces*<br/>
개체에서 구현 하는 인터페이스 목록 `IUnknown` `IInspectable` 또는 [RuntimeClassType](runtimeclasstype-enumeration.md)에서 제어 하는 다른 인터페이스입니다. 또한 개체를 agile로 만들고 구현 하도록 하는 등에서 파생 될 다른 클래스를 나열할 수도 있습니다 `Microsoft::WRL::FtmBase` `IMarshal` .

## <a name="members"></a>멤버

`RuntimeClassInitialize`<br/>
`MakeAndInitialize`템플릿 함수를 사용 하 여 개체를 생성 하는 경우 개체를 초기화 하는 함수입니다. 개체가 성공적으로 초기화 된 경우 S_OK을 반환 하 고, 초기화에 실패 한 경우 COM 오류 코드를 반환 합니다. COM 오류 코드는의 반환 값으로 전파 됩니다 `MakeAndInitialize` . `RuntimeClassInitialize` `Make` 템플릿 함수를 사용 하 여 개체를 생성 하는 경우 메서드가 호출 되지 않습니다.

### <a name="public-constructors"></a>Public 생성자

| 이름                                               | 설명                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass:: RuntimeClass](#runtimeclass)        | 클래스의 현재 인스턴스를 초기화 `RuntimeClass` 합니다.   |
| [RuntimeClass:: ~ RuntimeClass](#tilde-runtimeclass) | 클래스의 현재 인스턴스를 초기화 `RuntimeClass` 합니다. |

### <a name="public-methods"></a>Public 메서드

| 이름                                                      | 설명                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass:: AddRef](#addref)                           | 현재 개체의 참조 횟수를 증가 시킵니다 `RuntimeClass` .                              |
| [RuntimeClass::D ecrementReference](#decrementreference)   | 현재 개체의 참조 횟수를 감소 시킵니다 `RuntimeClass` .                              |
| [RuntimeClass:: GetIids](#getiids)                         | 현재 개체에서 구현 하는 인터페이스 Id를 포함할 수 있는 배열을 가져옵니다 `RuntimeClass` . |
| [RuntimeClass:: GetRuntimeClassName](#getruntimeclassname) | 현재 개체의 런타임 클래스 이름을 가져옵니다 `RuntimeClass` .                                  |
| [RuntimeClass:: GetTrustLevel](#gettrustlevel)             | 현재 개체의 신뢰 수준을 가져옵니다 `RuntimeClass` .                                         |
| [RuntimeClass:: GetWeakReference](#getweakreference)       | 현재 개체에 대 한 약한 참조 개체에 대 한 포인터를 가져옵니다 `RuntimeClass` .                 |
| [RuntimeClass:: InternalAddRef](#internaladdref)           | 참조 횟수를 현재 `RuntimeClass` 개체로 늘립니다.                               |
| [RuntimeClass:: QueryInterface](#queryinterface)           | 지정 된 인터페이스 ID에 대 한 포인터를 검색 합니다.                                                 |
| [RuntimeClass:: Release](#release)                         | 현재 개체에서 COM 해제 작업을 수행 `RuntimeClass` 합니다.                             |

## <a name="inheritance-hierarchy"></a>상속 계층 구조

이 구현 세부 정보입니다.

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a> RuntimeClass:: ~ RuntimeClass

클래스의 현재 인스턴스를 초기화 `RuntimeClass` 합니다.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a> RuntimeClass:: AddRef

현재 개체의 참조 횟수를 증가 시킵니다 `RuntimeClass` .

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a> RuntimeClass::D ecrementReference

현재 개체의 참조 횟수를 감소 시킵니다 `RuntimeClass` .

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a> RuntimeClass:: GetIids

현재 개체에서 구현 하는 인터페이스 Id를 포함할 수 있는 배열을 가져옵니다 `RuntimeClass` .

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>매개 변수

*iidCount*<br/>
이 작업이 완료 되 면 배열 *iid* 의 총 요소 수입니다.

*iid*<br/>
이 작업이 완료될 때 인터페이스 ID 배열에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 E_OUTOFMEMORY입니다.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a> RuntimeClass:: GetRuntimeClassName

현재 개체의 런타임 클래스 이름을 가져옵니다 `RuntimeClass` .

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>매개 변수

*Runti을 Ame*<br/>
이 작업이 완료 되 면 런타임 클래스 이름입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

`__WRL_STRICT__`또는이 정의 되지 않은 경우 assert 오류가 내보내집니다 `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` .

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a> RuntimeClass:: GetTrustLevel

현재 개체의 신뢰 수준을 가져옵니다 `RuntimeClass` .

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>매개 변수

*trustLvl*<br/>
이 작업이 완료 되 면 현재 개체의 신뢰 수준 `RuntimeClass` 입니다.

### <a name="return-value"></a>반환 값

항상 S_OK 합니다.

### <a name="remarks"></a>설명

`__WRL_STRICT__`또는이 정의 되지 않은 경우 assert 오류가 내보내집니다 `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` .

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a> RuntimeClass:: GetWeakReference

현재 개체에 대 한 약한 참조 개체에 대 한 포인터를 가져옵니다 `RuntimeClass` .

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>매개 변수

*weakReference*<br/>
이 작업이 완료 되 면 약한 참조 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

항상 S_OK 합니다.

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a> RuntimeClass:: InternalAddRef

참조 횟수를 현재 `RuntimeClass` 개체로 늘립니다.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>반환 값

결과 참조 횟수입니다.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a> RuntimeClass:: QueryInterface

지정 된 인터페이스 ID에 대 한 포인터를 검색 합니다.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID입니다.

*ppvObject*<br/>
이 작업이 완료 되 면 *riid* 매개 변수로 지정 된 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="runtimeclassrelease"></a><a name="release"></a> RuntimeClass:: Release

현재 개체에서 COM 해제 작업을 수행 `RuntimeClass` 합니다.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

참조 횟수가 0이 되 면 `RuntimeClass` 개체가 삭제 됩니다.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a> RuntimeClass:: RuntimeClass

클래스의 현재 인스턴스를 초기화 `RuntimeClass` 합니다.

```cpp
RuntimeClass();
```
