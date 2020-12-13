---
description: '자세히 알아보기: CMultiLock 클래스'
title: CMultiLock 클래스
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: 1a45c3c302b9f8028061649e2a0d270d47ed58aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331546"
---
# <a name="cmultilock-class"></a>CMultiLock 클래스

다중 스레드 프로그램에 대한 액세스를 제어할 때 사용하는 액세스 제어 메커니즘을 나타냅니다.

## <a name="syntax"></a>구문

```
class CMultiLock
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|`CMultiLock` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMultiLock:: IsLocked](#islocked)|배열에 있는 특정 동기화 개체가 잠겨 있는지 여부를 확인 합니다.|
|[CMultiLock:: Lock](#lock)|동기화 개체의 배열을 대기 합니다.|
|[CMultiLock:: Unlock](#unlock)|소유 된 동기화 개체를 모두 해제 합니다.|

## <a name="remarks"></a>설명

`CMultiLock` 에 기본 클래스가 없습니다.

[CSemaphore](../../mfc/reference/csemaphore-class.md), [Cmutex](../../mfc/reference/cmutex-class.md)및 [CEvent](../../mfc/reference/cevent-class.md)동기화 클래스를 사용 하려면 `CMultiLock` 또는 [csinglelock](../../mfc/reference/csinglelock-class.md) 개체를 만들어 동기화 개체를 대기 하 고 해제할 수 있습니다. `CMultiLock`특정 시간에 사용할 수 있는 개체가 여러 개 있는 경우를 사용 합니다. `CSingleLock`한 번에 하나의 개체만 대기 해야 하는 경우에 사용 합니다.

개체를 사용 하려면 `CMultiLock` 먼저 대기 하려는 동기화 개체의 배열을 만듭니다. 다음으로, `CMultiLock` 제어 된 리소스의 클래스에서 멤버 함수 내에서 개체의 생성자를 호출 합니다. 그런 다음 [Lock](#lock) 멤버 함수를 호출 하 여 리소스를 사용할 수 있는지 (신호 받음) 확인 합니다. 1 인 경우 멤버 함수의 나머지 부분을 계속 진행 합니다. 리소스를 사용할 수 없는 경우에는 지정 된 시간 동안 리소스를 해제할 때까지 기다리거나 실패를 반환 합니다. 리소스 사용이 완료 된 후에는 개체를 [](#unlock) `CMultiLock` 다시 사용 하거나 개체를 소멸 시킬 수 있는 경우 Unlock 함수를 호출 합니다 `CMultiLock` .

`CMultiLock` 개체는 스레드에 응답할 수 있는 많은 수의 개체가 있는 경우 `CEvent` 에 가장 유용 합니다. 모든 포인터를 포함 하는 배열을 만들고를 `CEvent` 호출 `Lock` 합니다. 이렇게 하면 이벤트 중 하나가 신호를 받을 때까지 스레드가 대기 합니다.

개체를 사용 하는 방법에 대 한 자세한 내용은 `CMultiLock` [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CMultiLock`

## <a name="requirements"></a>요구 사항

**헤더:** afxmt

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a> CMultiLock::CMultiLock

`CMultiLock` 개체를 생성합니다.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>매개 변수

*ppObjects*<br/>
대기 시킬 동기화 개체에 대 한 포인터의 배열입니다. NULL이 될 수 없습니다.

*dwCount*<br/>
*PpObjects* 의 개체 수입니다. 0보다 커야 합니다.

*bInitialLock*<br/>
제공 된 개체에 대 한 액세스를 초기에 시도할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

이 함수는 대기 시킬 동기화 개체의 배열을 만든 후에 호출 됩니다. 일반적으로 동기화 개체 중 하나를 사용할 수 있을 때까지 대기 해야 하는 스레드 내에서 호출 됩니다.

## <a name="cmultilockislocked"></a><a name="islocked"></a> CMultiLock:: IsLocked

지정 된 개체가 신호 없음으로 (사용할 수 없음) 인지 여부를 확인 합니다.

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>매개 변수

*dwItem*<br/>
상태를 쿼리하고 있는 개체에 해당 하는 개체 배열의 인덱스입니다.

### <a name="return-value"></a>반환 값

지정 된 개체가 잠겨 있으면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

## <a name="cmultilocklock"></a><a name="lock"></a> CMultiLock:: Lock

생성자에 제공 된 동기화 개체가 제어 하는 하나 이상의 리소스에 대 한 액세스 권한을 얻으려면이 함수를 호출 `CMultiLock` 합니다.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>매개 변수

*dwTimeOut*<br/>
동기화 개체를 사용할 수 있을 때까지 대기 하는 시간을 지정 합니다 (신호 받음). 무한 하면는 `Lock` 반환 하기 전에 개체가 신호를 받을 때까지 대기 합니다.

*bWaitForAll*<br/>
을 반환 하기 전에 대기 중인 모든 개체가 동시에 신호를 받아야 하는지 여부를 지정 합니다. FALSE 이면 `Lock` 대기 중인 개체 중 하나가 신호를 받으면가를 반환 합니다.

*dwWakeMask*<br/>
대기를 중단할 수 있는 다른 조건을 지정 합니다. 이 매개 변수에 사용할 수 있는 옵션의 전체 목록은 Windows SDK의 [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) 를 참조 하세요.

### <a name="return-value"></a>반환 값

에서 `Lock` 오류가 발생 하면-1이 반환 됩니다. 성공 하면 다음 값 중 하나를 반환 합니다.

- WAIT_OBJECT_0와 WAIT_OBJECT_0 + (개체 수-1) 사이

   *Bwaitforall* 이 TRUE 이면 모든 개체 (사용 가능)가 신호를 받을 수 있습니다. *Bwaitforall* 이 FALSE 이면 반환 값-WAIT_OBJECT_0는 신호를 받은 (사용 가능한) 개체의 개체 배열에 있는 인덱스입니다.

- WAIT_OBJECT_0 + (개체 수)

   *DwWakeMask* 에 지정 된 이벤트는 스레드의 입력 큐에서 사용할 수 있습니다.

- WAIT_ABANDONED_0와 WAIT_ABANDONED_0 + (개체 수-1) 사이

   *Bwaitforall* 이 TRUE 이면 모든 개체가 신호를 받은 후 하나 이상의 개체가 중단 된 뮤텍스 개체입니다. *Bwaitforall* 이 FALSE 인 경우 반환 값-WAIT_ABANDONED_0는 대기를 충족 시킨 중단 된 뮤텍스 개체의 개체 배열에 있는 인덱스입니다.

- WAIT_TIMEOUT

   *Dwtimeout* 에 지정 된 시간 제한 간격이 이후에 대기 하지 않고 만료 되었습니다.

### <a name="remarks"></a>설명

*Bwaitforall* 이 TRUE 이면 `Lock` 모든 동기화 개체가 동시에 신호를 받는 즉시가 성공적으로 반환 됩니다. *Bwaitforall* 이 FALSE 인 경우 `Lock` 하나 이상의 동기화 개체가 신호를 받는 즉시이 반환 됩니다.

`Lock`가 즉시 반환할 수 없는 경우에는를 반환 하기 전에 *dwtimeout* 매개 변수에 지정 된 시간 (밀리초) 동안 대기 합니다. *Dwtimeout* 이 무한 인 경우 `Lock` 는 개체에 대 한 액세스를 획득 하거나 *dwWakeMask* 에 지정 된 조건이 충족 될 때까지 반환 되지 않습니다. 그렇지 않으면 `Lock` 가 동기화 개체를 가져올 수 있으면 성공적으로 반환 되 고, 그렇지 않으면 오류가 반환 됩니다.

## <a name="cmultilockunlock"></a><a name="unlock"></a> CMultiLock:: Unlock

에서 소유 하는 동기화 개체를 해제 `CMultiLock` 합니다.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>매개 변수

*lCount*<br/>
해제할 참조 횟수 수입니다. 0보다 커야 합니다. 지정 된 양에 따라 개체 수가 최대값을 초과 하면 개수가 변경 되지 않으며 함수는 FALSE를 반환 합니다.

*lPrevCount*<br/>
동기화 개체의 이전 개수를 받을 변수를 가리킵니다. NULL 인 경우에는 이전 개수가 반환 되지 않습니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는의 소멸자에 의해 호출 됩니다 `CMultiLock` .

의 첫 번째 형태는 `Unlock` 에서 관리 하는 동기화 개체의 잠금을 해제 하려고 `CMultiLock` 합니다. 의 두 번째 형식은 `Unlock` 에서 소유 하는 개체의 잠금을 해제 하려고 시도 합니다 `CSemaphore` `CMultiLock` . `CMultiLock`이 잠긴 개체를 소유 하지 않는 경우 `CSemaphore` 함수는 FALSE를 반환 하 고 그렇지 않으면 TRUE를 반환 합니다. *Lcount* 및 *LpPrevCount* 는 [Csinglelock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)의 매개 변수와 정확히 동일 합니다. 의 두 번째 형식은 `Unlock` multilock 상황에 거의 적용 되지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)
