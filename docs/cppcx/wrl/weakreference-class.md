---
description: '자세히 알아보기: WeakReference 클래스'
title: WeakReference 클래스
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: 743a705fae93d015d190df24d2534de62613e542
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116551"
---
# <a name="weakreference-class"></a>WeakReference 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class WeakReference;
```

## <a name="remarks"></a>설명

Windows 런타임 또는 클래식 COM과 함께 사용할 수 있는 *약한 참조* 를 나타냅니다. 약한 참조는 액세스할 수 있거나 액세스할 수 없는 개체를 나타냅니다.

`WeakReference`개체는 개체에 대 한 포인터인 *강력한 참조* 및 메서드에 의해 배포 된 강력한 참조의 복사본 수 인 강력한 참조 *횟수* 를 유지 관리 합니다 `Resolve()` . 강력한 참조 수가 0이 아닌 경우에는 강력한 참조가 유효 하 고 개체에 액세스할 수 있습니다. 강력한 참조 수가 0이 되 면 강력한 참조가 유효 하지 않으며 개체에 액세스할 수 없습니다.

`WeakReference`개체는 일반적으로 외부 스레드나 응용 프로그램에 의해 해당 존재가 제어 되는 개체를 나타내는 데 사용 됩니다. 예를 들어 `WeakReference` 파일 개체에 대 한 참조에서 개체를 생성 합니다. 파일이 열려 있는 동안 강력한 참조는 유효합니다. 그러나 파일이 닫히면 강력한 참조는 유효하지 않게 됩니다.

`WeakReference`메서드는 스레드로부터 안전 합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                  | 설명
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference:: WeakReference](#weakreference)        | `WeakReference` 클래스의 새 인스턴스를 초기화합니다.
[WeakReference:: ~ WeakReference](#tilde-weakreference) | 클래스의 현재 인스턴스를 초기화 (소멸) `WeakReference` 합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                                 | 설명
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::D ecrementStrongReference](#decrementstrongreference) | 현재 개체의 강력한 참조 횟수를 감소 시킵니다 `WeakReference` .
[WeakReference:: IncrementStrongReference](#incrementstrongreference) | 현재 개체의 강력한 참조 횟수를 늘립니다 `WeakReference` .
[WeakReference:: Resolve](#resolve)                                   | 강력한 참조 수가 0이 아닌 경우 현재 강력한 참조 값에 대 한 지정 된 포인터를 설정 합니다.
[WeakReference:: SetUnknown](#setunknown)                             | 현재 개체의 강력한 참조를 `WeakReference` 지정 된 인터페이스 포인터로 설정 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`WeakReference`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a> WeakReference:: ~ WeakReference

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

클래스의 현재 인스턴스를 초기화 `WeakReference` 합니다.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a> WeakReference::D ecrementStrongReference

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>설명

현재 개체의 강력한 참조 횟수를 감소 시킵니다 `WeakReference` .

강력한 참조 수가 0이 되 면 강력한 참조가로 설정 됩니다 **`nullptr`** .

### <a name="return-value"></a>반환 값

감소 된 강한 참조 수입니다.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a> WeakReference:: IncrementStrongReference

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>반환 값

증가 된 강한 참조 수입니다.

### <a name="remarks"></a>설명

현재 개체의 강력한 참조 횟수를 늘립니다 `WeakReference` .

## <a name="weakreferenceresolve"></a><a name="resolve"></a> WeakReference:: Resolve

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID입니다.

*ppvObject*<br/>
이 작업이 완료 되 면 강력한 참조 수가 0이 아닌 경우 현재 강력한 참조의 복사본입니다.

### <a name="return-value"></a>반환 값

- 이 작업이 성공 하 고 강력한 참조 수가 0 이면 S_OK 합니다. *Ppvobject* 매개 변수는로 설정 됩니다 **`nullptr`** .

- 이 작업이 성공 하 고 강력한 참조 수가 0이 아닌 경우 S_OK 합니다. *Ppvobject* 매개 변수는 강력한 참조로 설정 됩니다.

- 그렇지 않으면이 작업이 실패 한 이유를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

강력한 참조 수가 0이 아닌 경우 현재 강력한 참조 값에 대 한 지정 된 포인터를 설정 합니다.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a> WeakReference:: SetUnknown

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>매개 변수

*unk*<br/>
개체의 인터페이스에 대 한 포인터 `IUnknown` 입니다.

### <a name="remarks"></a>설명

현재 개체의 강력한 참조를 `WeakReference` 지정 된 인터페이스 포인터로 설정 합니다.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a> WeakReference:: WeakReference

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
WeakReference();
```

### <a name="remarks"></a>설명

`WeakReference` 클래스의 새 인스턴스를 초기화합니다.

개체에 대 한 강력한 참조 포인터는 `WeakReference` 로 초기화 되 **`nullptr`** 고 강력한 참조 수는 1로 초기화 됩니다.
