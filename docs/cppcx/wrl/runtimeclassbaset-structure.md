---
description: '자세히 알아보기: RuntimeClassBaseT Structure'
title: RuntimeClassBaseT 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 48f03a5d54eba455b60646ed47c48e228f07863e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135293"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>매개 변수

*RuntimeClassTypeT*<br/>
하나 이상의 [RuntimeClassType](runtimeclasstype-enumeration.md) 열거자를 지정 하는 플래그 필드입니다.

## <a name="remarks"></a>설명

작업 및 인터페이스 Id 가져오기에 대 한 도우미 메서드를 제공 `QueryInterface` 합니다.

## <a name="members"></a>멤버

### <a name="protected-methods"></a>Protected 메서드

Name                                                         | 설명
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT:: AsIID](#asiid)                           | 지정 된 인터페이스 ID에 대 한 포인터를 검색 합니다.
[RuntimeClassBaseT:: GetImplementedIIDS](#getimplementediids) | 지정 된 형식에 의해 구현 되는 인터페이스 Id의 배열을 검색 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`RuntimeClassBaseT`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a> RuntimeClassBaseT:: AsIID

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
매개 변수 *riid* 로 지정 된 인터페이스 ID를 구현 하는 형식입니다.

*구현할*<br/>
템플릿 매개 변수 *T* 로 지정 된 형식의 변수입니다.

*riid*<br/>
검색할 인터페이스 ID입니다.

*ppvObject*<br/>
이 작업이 성공적으로 수행 되 면 매개 변수 *riid* 에서 지정 된 인터페이스에 대 한 포인터 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류를 설명 하는 HRESULT입니다.

### <a name="remarks"></a>설명

지정 된 인터페이스 ID에 대 한 포인터를 검색 합니다.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a> RuntimeClassBaseT:: GetImplementedIIDS

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
*구현* 매개 변수의 형식입니다.

*구현할*<br/>
매개 변수 *T* 로 지정 된 형식에 대 한 포인터입니다.

*iidCount*<br/>
검색할 최대 인터페이스 Id 수입니다.

*iid*<br/>
이 작업이 성공적으로 완료 되 면 *T* 형식으로 구현 된 인터페이스 id의 배열입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류를 설명 하는 HRESULT입니다.

### <a name="remarks"></a>설명

지정 된 형식에 의해 구현 되는 인터페이스 Id의 배열을 검색 합니다.
