---
description: '자세히 알아보기: ImplementsHelper Structure'
title: ImplementsHelper 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: 142cc532a89758c35c3387c398311acd077b8385
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249817"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>매개 변수

*RuntimeClassFlagsT*<br/>
하나 이상의 [RuntimeClassType](runtimeclasstype-enumeration.md) 열거자를 지정 하는 플래그 필드입니다.

*ILst*<br/>
인터페이스 Id의 목록입니다.

*IsDelegateToClass*<br/>
**`true`** 의 현재 인스턴스가 `Implements` *ilst* 의 첫 번째 인터페이스 ID의 기본 클래스 이면를 지정 하 고 그렇지 않으면를 지정 **`false`** 합니다.

## <a name="remarks"></a>설명

[구현](implements-structure.md) 구조를 구현 하는 데 도움이 됩니다.

이 템플릿은 인터페이스 목록을 트래버스하 고이를 기본 클래스로 추가 하 고를 사용 하도록 설정 하는 데 필요한 정보로 추가 `QueryInterface` 합니다.

## <a name="members"></a>멤버

### <a name="protected-methods"></a>Protected 메서드

Name                                                    | 설명
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper:: CanCastTo](#cancastto)               | 지정 된 인터페이스 ID에 대 한 포인터를 가져옵니다.
[ImplementsHelper:: CastToUnknown](#casttounknown)       | `IUnknown`현재 구조체의 기본 인터페이스에 대 한 포인터를 가져옵니다 `Implements` .
[ImplementsHelper:: FillArrayWithIid](#fillarraywithiid) | 현재 0 번째 template 매개 변수에 지정 된 인터페이스 ID를 지정 된 배열 요소에 삽입 합니다.
[ImplementsHelper:: IidCount](#iidcount)                 | 현재 개체에서 구현 된 인터페이스 Id의 수를 유지 합니다 `Implements` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ImplementsHelper`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="implementshelpercancastto"></a><a name="cancastto"></a> ImplementsHelper:: CanCastTo

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID에 대 한 참조입니다.

*ppv*<br/>
이 작업이 성공적으로 수행 되 면 *riid* 또는 *iid* 에 의해 지정 된 인터페이스에 대 한 포인터입니다.

*iid*<br/>
인터페이스 ID에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

지정 된 인터페이스 ID에 대 한 포인터를 가져옵니다.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a> ImplementsHelper:: CastToUnknown

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>반환 값

기본 인터페이스에 대 한 포인터 `IUnknown` 입니다.

### <a name="remarks"></a>설명

`IUnknown`현재 구조체의 기본 인터페이스에 대 한 포인터를 가져옵니다 `Implements` .

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a> ImplementsHelper:: FillArrayWithIid

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>매개 변수

*index*<br/>
이 작업의 시작 배열 요소를 나타내는 인덱스 (0부터 시작)입니다. 이 작업이 완료 되 면 *인덱스* 는 1 씩 증가 합니다.

*iid*<br/>
Iid 형식의 배열입니다.

### <a name="remarks"></a>설명

현재 0 번째 template 매개 변수에 지정 된 인터페이스 ID를 지정 된 배열 요소에 삽입 합니다.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a> ImplementsHelper:: IidCount

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>설명

현재 개체에서 구현 된 인터페이스 Id의 수를 유지 합니다 `Implements` .
