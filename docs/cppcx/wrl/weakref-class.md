---
description: '자세히 알아보기: WeakRef 클래스'
title: WeakRef 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 9c1c3edf7589dfd08e0ebab5389d2ca108d8e73c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339412"
---
# <a name="weakref-class"></a>WeakRef 클래스

클래식 COM이 아닌 Windows 런타임에서만 사용할 수 있는 *약한 참조* 를 나타냅니다. 약한 참조는 액세스할 수 있거나 액세스할 수 없는 개체를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[WeakRef::WeakRef 생성자](#weakref)|`WeakRef` 클래스의 새 인스턴스를 초기화합니다.|
|[WeakRef::~WeakRef 소멸자](#tilde-weakref)|클래스의 현재 인스턴스를 초기화 `WeakRef` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[WeakRef::As 메서드](#as)|지정 된 인터페이스를 나타내도록 지정 된 `ComPtr` 포인터 매개 변수를 설정 합니다.|
|[WeakRef::AsIID 메서드](#asiid)|지정 된 `ComPtr` 인터페이스 ID를 나타내도록 지정 된 포인터 매개 변수를 설정 합니다.|
|[WeakRef::CopyTo 메서드](#copyto)|사용 가능한 경우 지정된 포인터 변수에 인터페이스에 대한 포인터를 할당합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[WeakRef::operator& 연산자](#operator-ampersand-operator)|`ComPtrRef`현재 개체를 나타내는 개체를 반환 합니다 `WeakRef` .|

## <a name="remarks"></a>설명

`WeakRef`개체는 개체와 연결 된 *강력한 참조* 를 유지 관리 하며 유효 하거나 유효 하지 않을 수 있습니다. `As()`또는 메서드를 호출 `AsIID()` 하 여 강력한 참조를 가져옵니다. 강력한 참조가 유효한 경우 연결된 개체에 액세스할 수 있습니다. 강력한 참조가 잘못 된 경우 ( **`nullptr`** ) 연결 된 개체에 액세스할 수 없습니다.

`WeakRef`개체는 일반적으로 외부 스레드나 응용 프로그램에 의해 해당 존재가 제어 되는 개체를 나타내는 데 사용 됩니다. 예를 들어 `WeakRef` 파일 개체에 대 한 참조에서 개체를 생성 합니다. 파일이 열려 있는 동안 강력한 참조는 유효합니다. 그러나 파일이 닫히면 강력한 참조는 유효하지 않게 됩니다.

Windows 10 SDK에서는 [As](#as), [AsIID](#asiid) 및 [CopyTo](#copyto) 메서드의 동작 변경이 있습니다. 이전에는 이러한 메서드를 호출한 후 `WeakRef` **`nullptr`** 다음 코드와 같이에 대해를 확인 하 여 강력한 참조를 성공적으로 가져왔는지 확인할 수 있습니다.

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

위의 코드는 Windows 10 SDK(이상)를 사용하는 경우 작동하지 않습니다. 대신에 대해 전달 된 포인터를 확인 **`nullptr`** 합니다.

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ComPtr`

`WeakRef`

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임스페이스:** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a> WeakRef:: ~ WeakRef 소멸자

클래스의 현재 인스턴스를 초기화 `WeakRef` 합니다.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a> WeakRef:: As 메서드

지정 된 인터페이스를 나타내도록 지정 된 `ComPtr` 포인터 매개 변수를 설정 합니다.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>매개 변수

*U*<br/>
인터페이스 ID입니다.

*ptr*<br/>
이 작업이 완료 되 면 매개 변수 *U* 를 나타내는 개체입니다.

### <a name="return-value"></a>반환 값

- 이 작업이 성공 하면 S_OK이 고, 그렇지 않으면입니다. 그렇지 않으면 작업이 실패 한 이유를 나타내는 HRESULT와 *ptr* 이로 설정 됩니다 **`nullptr`** .

- 이 작업이 성공 하지만 현재 개체가 이미 해제 된 경우를 S_OK `WeakRef` 합니다. 매개 변수 *ptr* 은로 설정 됩니다 **`nullptr`** .

- 이 작업이 성공 하지만 현재 `WeakRef` 개체가 매개 변수 *U* 에서 파생 되지 않은 경우 S_OK 합니다. 매개 변수 *ptr* 은로 설정 됩니다 **`nullptr`** .

### <a name="remarks"></a>설명

매개 변수 *U* 가 `IWeakReference` 이거나에서 파생 되지 않은 경우 오류가 발생 `IInspectable` 합니다.

첫 번째 템플릿은 코드에서 사용해야 하는 폼입니다. 두 번째 템플릿은 [자동](../../cpp/auto-cpp.md) 형식 추론 키워드와 같은 C++ 언어 기능을 지원하는 내부 도우미 특수화입니다.

Windows 10 SDK 부터는 약한 참조를 가져올 수 없는 경우이 메서드는 인스턴스를로 설정 하지 않으므로 `WeakRef` **`nullptr`** 에 대해를 확인 하는 오류 검사 코드를 사용 하지 않아야 합니다 `WeakRef` **`nullptr`** . 대신 *ptr* 을 선택 **`nullptr`** 합니다.

## <a name="weakrefasiid-method"></a><a name="asiid"></a> WeakRef:: AsIID 메서드

지정 된 `ComPtr` 인터페이스 ID를 나타내도록 지정 된 포인터 매개 변수를 설정 합니다.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID입니다.

*ptr*<br/>
이 작업이 완료 되 면 매개 변수 *riid* 를 나타내는 개체입니다.

### <a name="return-value"></a>반환 값

- 이 작업이 성공 하면 S_OK이 고, 그렇지 않으면입니다. 그렇지 않으면 작업이 실패 한 이유를 나타내는 HRESULT와 *ptr* 이로 설정 됩니다 **`nullptr`** .

- 이 작업이 성공 하지만 현재 개체가 이미 해제 된 경우를 S_OK `WeakRef` 합니다. 매개 변수 *ptr* 은로 설정 됩니다 **`nullptr`** .

- 이 작업이 성공 하지만 현재 `WeakRef` 개체가 매개 변수 *riid* 에서 파생 되지 않은 경우 S_OK 합니다. 매개 변수 *ptr* 은로 설정 됩니다 **`nullptr`** . 자세한 내용은 설명 부분을 참조하세요.

### <a name="remarks"></a>설명

매개 변수 *riid* 가에서 파생 되지 않은 경우 오류가 발생 `IInspectable` 합니다. 이 오류는 반환 값을 대체합니다.

첫 번째 템플릿은 코드에서 사용해야 하는 폼입니다. 두 번째 템플릿(여기에 표시되지 않지만 헤더 파일에서 선언됨)은 [자동](../../cpp/auto-cpp.md) 형식 추론 키워드와 같은 C++ 언어 기능을 지원하는 내부 도우미 특수화입니다.

Windows 10 SDK 부터는 약한 참조를 가져올 수 없는 경우이 메서드는 인스턴스를로 설정 하지 않으므로 `WeakRef` **`nullptr`** 에 대해를 확인 하는 오류 검사 코드를 사용 하지 않아야 합니다 `WeakRef` **`nullptr`** . 대신 *ptr* 을 선택 **`nullptr`** 합니다.

## <a name="weakrefcopyto-method"></a><a name="copyto"></a> WeakRef:: CopyTo 메서드

사용 가능한 경우 지정된 포인터 변수에 인터페이스에 대한 포인터를 할당합니다.

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>매개 변수

*U*<br/>
인터페이스에 대 한 포인터 `IInspectable` 입니다. *U* 가에서 파생 되지 않은 경우 오류가 내보내집니다 `IInspectable` .

*riid*<br/>
인터페이스 ID입니다. *Riid* 가에서 파생 되지 않은 경우 오류가 발생 `IWeakReference` 합니다.

*ptr*<br/>
또는에 대 한 이중 간접 `IInspectable` 포인터 `IWeakReference` 입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다. 자세한 내용은 **설명 부분** 을 참조 하십시오.

### <a name="remarks"></a>설명

반환 값 S_OK는 이 작업이 성공했음을 의미하지만 약한 참조가 강한 참조로 확인되었는지를 나타내지 않습니다. S_OK 반환 되는 경우 *p* 매개 변수를 강력한 참조로 테스트 합니다. 즉, *p* 매개 변수는와 같지 않습니다 **`nullptr`** .

Windows 10 SDK 부터는 약한 참조를 가져올 수 없는 경우이 메서드는 인스턴스를로 설정 하지 않으므로 `WeakRef` **`nullptr`** 에 대해를 확인 하는 오류 검사 코드를 사용 하지 않아야 합니다 `WeakRef` **`nullptr`** . 대신 *ptr* 을 선택 **`nullptr`** 합니다.

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a> WeakRef:: operator &amp; 연산자

`ComPtrRef`현재 개체를 나타내는 개체를 반환 합니다 `WeakRef` .

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>반환 값

`ComPtrRef`현재 개체를 나타내는 개체 `WeakRef` 입니다.

### <a name="remarks"></a>설명

이는 코드에서 사용할 수 없는 내부 도우미 연산자입니다.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a> WeakRef:: WeakRef 생성자

`WeakRef` 클래스의 새 인스턴스를 초기화합니다.

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>매개 변수

*ptr*<br/>
현재 개체를 초기화 하는 기존 개체에 대 한 포인터, 참조 또는 rvalue 참조 `WeakRef` 입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 빈 개체를 초기화 합니다 `WeakRef` . 두 번째 생성자는 `WeakRef` 인터페이스에 대 한 포인터에서 개체를 초기화 합니다 `IWeakReference` . 세 번째 생성자는 개체 `WeakRef` 에 대 한 참조에서 개체를 초기화 `ComPtr<IWeakReference>` 합니다. 네 번째 및 다섯 번째 생성자는 `WeakRef` 다른 개체에서 개체를 초기화 합니다 `WeakRef` .
