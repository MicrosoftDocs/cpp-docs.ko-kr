---
description: '자세히 알아보기: CComApartment 클래스'
title: CComApartment 클래스
ms.date: 11/04/2016
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: de51d1eb04bfa0f0760ad741e19b237a9e72dc8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152323"
---
# <a name="ccomapartment-class"></a>CComApartment 클래스

이 클래스는 스레드 풀링된 EXE 모듈에서 아파트를 관리 하는 기능을 지원 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CComApartment
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComApartment:: 아파트](#apartment)|스레드의 시작 주소를 표시 합니다.|
|[CComApartment:: GetLockCount](#getlockcount)|스레드의 현재 잠금 수를 반환 합니다.|
|[CComApartment:: Lock](#lock)|스레드의 잠금 횟수를 늘립니다.|
|[CComApartment:: Unlock](#unlock)|스레드의 잠금 횟수를 줄입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComApartment:: m_dwThreadID](#m_dwthreadid)|스레드의 식별자를 포함 합니다.|
|[CComApartment:: m_hThread](#m_hthread)|스레드의 핸들을 포함 합니다.|
|[CComApartment:: m_nLockCnt](#m_nlockcnt)|스레드의 현재 잠금 수를 포함 합니다.|

## <a name="remarks"></a>설명

`CComApartment` 는 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 에서 스레드 풀링된 EXE 모듈의 아파트를 관리 하는 데 사용 됩니다. `CComApartment` 스레드의 잠금 수를 증가 및 감소 시키는 메서드를 제공 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a> CComApartment:: 아파트

스레드의 시작 주소를 표시 합니다.

```
DWORD Apartment();
```

### <a name="return-value"></a>반환 값

항상 0입니다.

### <a name="remarks"></a>설명

[CComAutoThreadModule:: Init](../../atl/reference/ccomautothreadmodule-class.md#init)중에 자동으로 설정 됩니다.

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a> CComApartment::CComApartment

생성자입니다.

```
CComApartment();
```

### <a name="remarks"></a>설명

`CComApartment` [M_nLockCnt](#m_nlockcnt) 및 [m_hThread](#m_hthread)데이터 멤버를 초기화 합니다.

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a> CComApartment:: GetLockCount

스레드의 현재 잠금 수를 반환 합니다.

```
LONG GetLockCount();
```

### <a name="return-value"></a>반환 값

스레드의 잠금 수입니다.

## <a name="ccomapartmentlock"></a><a name="lock"></a> CComApartment:: Lock

스레드의 잠금 횟수를 늘립니다.

```
LONG Lock();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

### <a name="remarks"></a>설명

[CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)에 의해 호출 됩니다.

스레드의 잠금 수는 통계 목적으로 사용 됩니다.

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a> CComApartment:: m_dwThreadID

스레드의 식별자를 포함 합니다.

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a> CComApartment:: m_hThread

스레드의 핸들을 포함 합니다.

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a> CComApartment:: m_nLockCnt

스레드의 현재 잠금 수를 포함 합니다.

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a> CComApartment:: Unlock

스레드의 잠금 횟수를 줄입니다.

```
LONG Unlock();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

### <a name="remarks"></a>설명

[CComAutoThreadModule:: Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)에 의해 호출 됩니다.

스레드의 잠금 수는 통계 목적으로 사용 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
