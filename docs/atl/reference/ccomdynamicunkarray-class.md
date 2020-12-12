---
description: '자세히 알아보기: CComDynamicUnkArray 클래스'
title: CComDynamicUnkArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: fe817b097bbb75c7d09bffdb6883e5ac4a76f966
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152089"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 클래스

이 클래스는 포인터의 배열을 저장 `IUnknown` 합니다.

## <a name="syntax"></a>구문

```
class CComDynamicUnkArray
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|생성자입니다. 컬렉션 값을 NULL로 초기화 하 고 컬렉션 크기를 0으로 초기화 합니다.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|배열에 포인터를 추가 하려면이 메서드를 호출 `IUnknown` 합니다.|
|[CComDynamicUnkArray::begin](#begin)|컬렉션의 첫 번째 포인터에 대 한 포인터를 반환 `IUnknown` 합니다.|
|[CComDynamicUnkArray:: clear](#clear)|배열을 비웁니다.|
|[CComDynamicUnkArray:: end](#end)|컬렉션에서 마지막 포인터를 지난 포인터를 반환 `IUnknown` 합니다.|
|[CComDynamicUnkArray::GetAt](#getat)|지정된 된 인덱스에 요소를 검색 합니다.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|지정 된 포인터와 연결 된 쿠키를 가져오려면이 메서드를 호출 `IUnknown` 합니다.|
|[CComDynamicUnkArray::GetSize](#getsize)|배열의 길이를 반환 합니다.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|지정 된 쿠키와 연결 된 포인터를 가져오려면이 메서드를 호출 `IUnknown` 합니다.|
|[CComDynamicUnkArray:: Remove](#remove)|배열에서 포인터를 제거 하려면이 메서드를 호출 `IUnknown` 합니다.|

## <a name="remarks"></a>설명

`CComDynamicUnkArray``IUnknown`각각 연결 지점에서 인터페이스를 포함 하 여 동적으로 할당 된 포인터 배열을 보유 합니다. `CComDynamicUnkArray`[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 템플릿 클래스에 대 한 매개 변수로 사용할 수 있습니다.

[Begin](#begin) 및 [end](#end)`CComDynamicUnkArray`메서드를 사용하여 모든 연결 지점의 루프를 반복할 수 있습니다 (예: 이벤트가 발생 하는 경우).

연결 지점 프록시 만들기를 자동화 하는 방법에 대 한 자세한 내용은 [개체에 연결 지점 추가](../../atl/adding-connection-points-to-an-object.md) 를 참조 하세요.

> [!NOTE]
> **참고** 클래스는 `CComDynamicUnkArray` 연결 지점이 있는 컨트롤을 만들 때 **클래스 추가** 마법사에서 사용 됩니다. 연결 지점 수를 수동으로 지정 하려는 경우 참조를에서 n으로 변경 합니다 `CComDynamicUnkArray` `CComUnkArray<`  `>` . 여기서 *n* 은 필요한 연결 지점 수입니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a> CComDynamicUnkArray:: Add

배열에 포인터를 추가 하려면이 메서드를 호출 `IUnknown` 합니다.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
`IUnknown`배열에 추가할 포인터입니다.

### <a name="return-value"></a>반환 값

새로 추가 된 포인터와 연결 된 쿠키를 반환 합니다.

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a> CComDynamicUnkArray:: begin

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

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a> CComDynamicUnkArray:: clear

배열을 비웁니다.

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a> CComDynamicUnkArray::CComDynamicUnkArray

생성자입니다.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>설명

컬렉션 크기를 0으로 설정 하 고 값을 NULL로 초기화 합니다. 필요한 경우 소멸자는 컬렉션을 해제 합니다.

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a> CComDynamicUnkArray:: ~ CComDynamicUnkArray

소멸자입니다.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>설명

클래스 생성자에 의해 할당 된 리소스를 해제 합니다.

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a> CComDynamicUnkArray:: end

컬렉션에서 마지막 포인터를 지난 포인터를 반환 `IUnknown` 합니다.

```
IUnknown**
    end();
```

### <a name="return-value"></a>반환 값

인터페이스 포인터에 대 한 포인터 `IUnknown` 입니다.

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a> CComDynamicUnkArray:: GetAt

지정된 된 인덱스에 요소를 검색 합니다.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
검색할 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 인터페이스에 대 한 포인터입니다.

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a> CComDynamicUnkArray:: GetCookie

지정 된 포인터와 연결 된 쿠키를 가져오려면이 메서드를 호출 `IUnknown` 합니다.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>매개 변수

*ppFind*<br/>
`IUnknown`연결 된 쿠키가 필요한 포인터입니다.

### <a name="return-value"></a>반환 값

포인터와 연결 된 쿠키를 반환 `IUnknown` 하거나, 일치 하 `IUnknown` 는 포인터를 찾을 수 없는 경우 0을 반환 합니다.

### <a name="remarks"></a>설명

같은 포인터의 인스턴스가 두 개 이상 있는 경우 `IUnknown` 이 함수는 첫 번째 항목에 대 한 쿠키를 반환 합니다.

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a> CComDynamicUnkArray:: GetSize

배열의 길이를 반환 합니다.

```
int GetSize() const;
```

### <a name="return-value"></a>반환 값

배열의 길이입니다.

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a> CComDynamicUnkArray:: GetUnknown

지정 된 쿠키와 연결 된 포인터를 가져오려면이 메서드를 호출 `IUnknown` 합니다.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>매개 변수

*dwCookie*<br/>
연결 된 포인터가 필요한 쿠키입니다 `IUnknown` .

### <a name="return-value"></a>반환 값

포인터를 반환 `IUnknown` 하거나, 일치 하는 쿠키가 없는 경우 NULL을 반환 합니다.

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a> CComDynamicUnkArray:: Remove

배열에서 포인터를 제거 하려면이 메서드를 호출 `IUnknown` 합니다.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>매개 변수

*dwCookie*<br/>
배열에서 제거할 포인터를 참조 하는 쿠키 `IUnknown` 입니다.

### <a name="return-value"></a>반환 값

포인터가 제거 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

## <a name="see-also"></a>참고 항목

[CComUnkArray 클래스](../../atl/reference/ccomunkarray-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
