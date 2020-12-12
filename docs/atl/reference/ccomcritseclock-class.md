---
description: '자세히 알아보기: CComCritSecLock 클래스'
title: CComCritSecLock 클래스
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 7cad44f062fe75418da1f948c5f180283142779b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152102"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 클래스

이 클래스는 임계 영역 개체를 잠그고 잠금 해제 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>매개 변수

*TLock*<br/>
잠그거나 잠금을 해제할 개체입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|생성자입니다.|
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComCritSecLock:: Lock](#lock)|이 메서드를 호출 하 여 임계 영역 개체를 잠급니다.|
|[CComCritSecLock:: Unlock](#unlock)|임계 영역 개체의 잠금을 해제 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스를 사용 하 여 [CComCriticalSection 클래스](../../atl/reference/ccomcriticalsection-class.md) 또는 [CComAutoCriticalSection 클래스](../../atl/reference/ccomautocriticalsection-class.md)를 사용 하는 것과는 다른 방식으로 개체를 잠그고 잠금 해제할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a> CComCritSecLock::CComCritSecLock

생성자입니다.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>매개 변수

*양방향*<br/>
임계 영역 개체입니다.

*bInitialLock*<br/>
초기 잠금 상태: **`true`** 잠김을 의미 합니다.

### <a name="remarks"></a>설명

임계 영역 개체를 초기화 합니다.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a> CComCritSecLock:: ~ CComCritSecLock

소멸자입니다.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>설명

임계 영역 개체의 잠금을 해제 합니다.

## <a name="ccomcritseclocklock"></a><a name="lock"></a> CComCritSecLock:: Lock

이 메서드를 호출 하 여 임계 영역 개체를 잠급니다.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>반환 값

개체가 성공적으로 잠겨 있으면 S_OK을 반환 하 고, 실패 하면 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

개체가 이미 잠겨 있는 경우 디버그 빌드에서 ASSERT 오류가 발생 합니다.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a> CComCritSecLock:: Unlock

임계 영역 개체의 잠금을 해제 하려면이 메서드를 호출 합니다.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>설명

개체의 잠금이 이미 해제 된 경우 디버그 빌드에서 ASSERT 오류가 발생 합니다.

## <a name="see-also"></a>참고 항목

[CComCriticalSection 클래스](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection 클래스](../../atl/reference/ccomautocriticalsection-class.md)
