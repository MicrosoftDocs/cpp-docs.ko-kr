---
description: '자세한 정보: ClassFactory 클래스'
title: ClassFactory 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: e6503cba1060c432b2cb85020799b83f0ee16c6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135306"
---
# <a name="classfactory-class"></a>ClassFactory 클래스

`IClassFactory` 인터페이스의 기본 기능을 구현합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
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

`ClassFactory`를 활용 하 여 사용자 정의 팩터리 구현을 제공 합니다.

다음 프로그래밍 패턴에서는 [Implements](implements-structure.md) 구조체를 사용 하 여 클래스 팩터리에 세 개 이상의 인터페이스를 지정 하는 방법을 보여 줍니다.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                        | 설명
------------------------------------------- | -----------
[ClassFactory:: ClassFactory](#classfactory) |

### <a name="public-methods"></a>Public 메서드

이름                                            | 설명
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory:: AddRef](#addref)                 | 현재 개체의 참조 횟수를 증가 시킵니다 `ClassFactory` .
[ClassFactory:: LockServer](#lockserver)         | 현재 개체가 추적 하는 기본 개체의 수를 늘리거나 줄입니다 `ClassFactory` .
[ClassFactory:: QueryInterface](#queryinterface) | 매개 변수로 지정 된 인터페이스에 대 한 포인터를 검색 합니다.
[ClassFactory:: Release](#release)               | 현재 개체의 참조 횟수를 감소 시킵니다 `ClassFactory` .

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

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a> ClassFactory:: AddRef

현재 개체의 참조 횟수를 증가 시킵니다 `ClassFactory` .

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a> ClassFactory:: ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a> ClassFactory:: LockServer

현재 개체가 추적 하는 기본 개체의 수를 늘리거나 줄입니다 `ClassFactory` .

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>매개 변수

*fLock*<br/>
**`true`** 추적 된 개체 수를 증가 시킵니다. **`false`** 추적 된 개체 수를 감소 시킵니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 E_FAIL입니다.

### <a name="remarks"></a>설명

`ClassFactory`[Module](module-class.md) 클래스의 기본 인스턴스에서 개체를 추적 합니다.

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a> ClassFactory:: QueryInterface

매개 변수로 지정 된 인터페이스에 대 한 포인터를 검색 합니다.

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

## <a name="classfactoryrelease"></a><a name="release"></a> ClassFactory:: Release

현재 개체의 참조 횟수를 감소 시킵니다 `ClassFactory` .

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다.
