---
description: '자세히 알아보기: CComUnkArray 클래스'
title: CComUnkArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: e03022fb751b487debb9f81d9e3d99ce46f1b9e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142144"
---
# <a name="ccomunkarray-class"></a>CComUnkArray 클래스

이 클래스는 `IUnknown` 포인터를 저장 하며 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 템플릿 클래스에 대 한 매개 변수로 사용 하도록 디자인 되었습니다.

## <a name="syntax"></a>구문

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>매개 변수

*nMaxSize*<br/>
`IUnknown`정적 배열에 보유할 수 있는 최대 포인터 수입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComUnkArray:: Add](#add)|배열에 포인터를 추가 하려면이 메서드를 호출 `IUnknown` 합니다.|
|[CComUnkArray:: begin](#begin)|컬렉션의 첫 번째 포인터에 대 한 포인터를 반환 `IUnknown` 합니다.|
|[CComUnkArray:: end](#end)|컬렉션에서 마지막 포인터를 지난 포인터를 반환 `IUnknown` 합니다.|
|[CComUnkArray:: GetCookie](#getcookie)|지정 된 포인터와 연결 된 쿠키를 가져오려면이 메서드를 호출 `IUnknown` 합니다.|
|[CComUnkArray:: GetUnknown](#getunknown)|지정 된 쿠키와 연결 된 포인터를 가져오려면이 메서드를 호출 `IUnknown` 합니다.|
|[CComUnkArray:: Remove](#remove)|배열에서 포인터를 제거 하려면이 메서드를 호출 `IUnknown` 합니다.|

## <a name="remarks"></a>설명

`CComUnkArray` 연결 지점에서 각 인터페이스에 대 한 고정 된 수의 `IUnknown` 포인터를 보유 합니다. `CComUnkArray`[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 템플릿 클래스에 대 한 매개 변수로 사용할 수 있습니다. `CComUnkArray<1>` 는 `CComUnkArray` 하나의 연결 지점에 대해 최적화 된의 템플릿 특수화입니다.

[Begin](#begin) 및 [end](#end)`CComUnkArray`메서드를 사용하여 모든 연결 지점의 루프를 반복할 수 있습니다 (예: 이벤트가 발생 하는 경우).

연결 지점 프록시 만들기를 자동화 하는 방법에 대 한 자세한 내용은 [개체에 연결 지점 추가](../../atl/adding-connection-points-to-an-object.md) 를 참조 하세요.

> [!NOTE]
> **참고** [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) 클래스는 연결 지점이 있는 컨트롤을 만들 때 **클래스 추가** 마법사에서 사용 됩니다. 연결 지점 수를 수동으로 지정 하려는 경우 참조를에서 n으로 변경 합니다 `CComDynamicUnkArray` `CComUnkArray<`  `>` . 여기서 *n* 은 필요한 연결 지점 수입니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomunkarrayadd"></a><a name="add"></a> CComUnkArray:: Add

배열에 포인터를 추가 하려면이 메서드를 호출 `IUnknown` 합니다.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
배열에 포인터를 추가 하려면이 메서드를 호출 `IUnknown` 합니다.

### <a name="return-value"></a>반환 값

새로 추가 된 포인터와 연결 된 쿠키를 반환 하거나, 배열이 새 포인터를 포함 하기에 충분히 크지 않은 경우 0을 반환 합니다.

## <a name="ccomunkarraybegin"></a><a name="begin"></a> CComUnkArray:: begin

인터페이스 포인터 컬렉션의 시작 부분에 대 한 포인터를 반환 합니다 `IUnknown` .

```
IUnknown**
    begin();
```

### <a name="return-value"></a>반환 값

인터페이스 포인터에 대 한 포인터 `IUnknown` 입니다.

### <a name="remarks"></a>설명

컬렉션은로 로컬에 저장 된 인터페이스에 대 한 포인터를 포함 합니다 `IUnknown` . 각 `IUnknown` 인터페이스를 실제 인터페이스 형식으로 캐스팅 한 다음이를 통해 호출 합니다. 인터페이스를 먼저 쿼리할 필요는 없습니다.

인터페이스를 사용 하기 전에 `IUnknown` NULL이 아닌 인터페이스를 확인 해야 합니다.

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a> CComUnkArray::CComUnkArray

생성자입니다.

```
CComUnkArray();
```

### <a name="remarks"></a>설명

포인터를 포함 하는 컬렉션을 설정 하 `nMaxSize` `IUnknown` 고 NULL에 대 한 포인터를 초기화 합니다.

## <a name="ccomunkarrayend"></a><a name="end"></a> CComUnkArray:: end

컬렉션에서 마지막 포인터를 지난 포인터를 반환 `IUnknown` 합니다.

```
IUnknown**
    end();
```

### <a name="return-value"></a>반환 값

인터페이스 포인터에 대 한 포인터 `IUnknown` 입니다.

### <a name="remarks"></a>설명

`CComUnkArray`및 메서드 `begin` 를 `end` 사용 하 여 이벤트가 발생 하는 경우와 같은 모든 연결 요소를 반복할 수 있습니다.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a> CComUnkArray:: GetCookie

지정 된 포인터와 연결 된 쿠키를 가져오려면이 메서드를 호출 `IUnknown` 합니다.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>매개 변수

*ppFind*<br/>
`IUnknown`연결 된 쿠키가 필요한 포인터입니다.

### <a name="return-value"></a>반환 값

포인터와 연결 된 쿠키를 반환 `IUnknown` 하거나 일치 하는 포인터가 없는 경우 0을 반환 합니다 `IUnknown` .

### <a name="remarks"></a>설명

같은 포인터의 인스턴스가 두 개 이상 있는 경우 `IUnknown` 이 함수는 첫 번째 항목에 대 한 쿠키를 반환 합니다.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a> CComUnkArray:: GetUnknown

지정 된 쿠키와 연결 된 포인터를 가져오려면이 메서드를 호출 `IUnknown` 합니다.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>매개 변수

*dwCookie*<br/>
연결 된 포인터가 필요한 쿠키입니다 `IUnknown` .

### <a name="return-value"></a>반환 값

포인터를 반환 `IUnknown` 하거나, 일치 하는 쿠키가 없는 경우 NULL을 반환 합니다.

## <a name="ccomunkarrayremove"></a><a name="remove"></a> CComUnkArray:: Remove

배열에서 포인터를 제거 하려면이 메서드를 호출 `IUnknown` 합니다.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>매개 변수

*dwCookie*<br/>
배열에서 제거할 포인터를 참조 하는 쿠키 `IUnknown` 입니다.

### <a name="return-value"></a>반환 값

포인터가 제거 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CComDynamicUnkArray 클래스](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
