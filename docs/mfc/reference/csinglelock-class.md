---
description: '자세한 정보: CSingleLock 클래스'
title: CSingleLock 클래스
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 7fa4fe32ce38bf47ede1b6ac133d1a057907f9c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342858"
---
# <a name="csinglelock-class"></a>CSingleLock 클래스

다중 스레드 프로그램에서 한 리소스에 대한 액세스를 제어할 때 사용하는 액세스 제어 메커니즘을 나타냅니다.

## <a name="syntax"></a>구문

```
class CSingleLock
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSingleLock:: CSingleLock](#csinglelock)|`CSingleLock` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSingleLock:: IsLocked](#islocked)|개체가 잠겨 있는지 여부를 확인 합니다.|
|[CSingleLock:: Lock](#lock)|동기화 개체를 대기 합니다.|
|[CSingleLock:: Unlock](#unlock)|동기화 개체를 해제 합니다.|

## <a name="remarks"></a>설명

`CSingleLock` 에 기본 클래스가 없습니다.

[CSemaphore](../../mfc/reference/csemaphore-class.md), [cmutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)및 [CEvent](../../mfc/reference/cevent-class.md)동기화 클래스를 사용 하려면 `CSingleLock` 대기 하 고 동기화 개체를 해제 하기 위해 또는 [CMultiLock](../../mfc/reference/cmultilock-class.md) 개체를 만들어야 합니다. `CSingleLock`한 번에 하나의 개체만 대기 해야 하는 경우에 사용 합니다. `CMultiLock`특정 시간에 사용할 수 있는 개체가 여러 개 있는 경우를 사용 합니다.

개체를 사용 하려면 `CSingleLock` 제어 되는 리소스의 클래스에서 멤버 함수 내에서 해당 생성자를 호출 합니다. 그런 다음 [Islocked](#islocked) 멤버 함수를 호출 하 여 리소스를 사용할 수 있는지 확인 합니다. 이 경우 멤버 함수의 나머지 부분을 계속 진행 합니다. 리소스를 사용할 수 없는 경우 리소스를 해제 하기 위해 지정 된 시간 동안 기다리거나 실패를 반환 합니다. 리소스 사용이 완료 된 후에는 개체를 [](#unlock) `CSingleLock` 다시 사용 하거나 개체를 소멸 시킬 수 있는 경우 Unlock 함수를 호출 합니다 `CSingleLock` .

`CSingleLock` 개체는 [CSyncObject](../../mfc/reference/csyncobject-class.md)에서 파생 된 개체가 있어야 합니다. 이는 일반적으로 제어 되는 리소스의 클래스에 대 한 데이터 멤버입니다. 개체를 사용 하는 방법에 대 한 자세한 내용은 `CSingleLock` [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CSingleLock`

## <a name="requirements"></a>요구 사항

**헤더:** afxmt

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a> CSingleLock:: CSingleLock

`CSingleLock` 개체를 생성합니다.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>매개 변수

*pObject*<br/>
액세스할 동기화 개체를 가리킵니다. NULL이 될 수 없습니다.

*bInitialLock*<br/>
처음에 제공 된 개체에 대 한 액세스를 시도할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 제어 되는 리소스의 액세스 멤버 함수 내에서 호출 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a> CSingleLock:: IsLocked

개체와 연결 된 개체가 `CSingleLock` 신호 없음으로 (사용할 수 없음) 인지 여부를 확인 합니다.

```
BOOL IsLocked();
```

### <a name="return-value"></a>반환 값

개체가 잠겨 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a> CSingleLock:: Lock

생성자에 제공 된 동기화 개체가 제어 하는 리소스에 액세스 하려면이 함수를 호출 `CSingleLock` 합니다.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>매개 변수

*dwTimeOut*<br/>
동기화 개체를 사용할 수 있을 때까지 대기 하는 시간을 지정 합니다 (신호 받음). 무한 하면는 `Lock` 반환 하기 전에 개체가 신호를 받을 때까지 대기 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

동기화 개체가 신호를 받으면가 `Lock` 성공적으로 반환 되 고 이제 스레드가 개체를 소유 합니다. 동기화 개체가 신호 없음으로 (사용할 수 없음) 인 경우는 `Lock` 동기화 개체가 *dwtimeout* 매개 변수에 지정 된 시간 (밀리초)까지 신호를 받을 때까지 기다립니다. 동기화 개체가 지정 된 시간 내에 신호를 받지 못한 경우는 오류를 `Lock` 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a> CSingleLock:: Unlock

에서 소유 하는 동기화 개체를 해제 `CSingleLock` 합니다.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>매개 변수

*lCount*<br/>
릴리스에 대 한 액세스 수입니다. 0보다 커야 합니다. 지정 된 양에 따라 개체 수가 최대값을 초과 하면 개수가 변경 되지 않으며 함수는 FALSE를 반환 합니다.

*lPrevCount*<br/>
동기화 개체의 이전 개수를 수신 하는 변수를 가리킵니다. NULL 인 경우에는 이전 개수가 반환 되지 않습니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는의 소멸자에 의해 호출 됩니다 `CSingleLock` .

두 개 이상의 세마포에 대 한 액세스 횟수를 해제 해야 하는 경우의 두 번째 형태를 사용 `Unlock` 하 고 해제할 액세스 수를 지정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock 클래스](../../mfc/reference/cmultilock-class.md)
