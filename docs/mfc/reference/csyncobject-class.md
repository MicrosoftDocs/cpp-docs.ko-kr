---
description: '자세히 알아보기: CSyncObject 클래스'
title: CSyncObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: 5743f632f9a8c482ac15995e8d2429851ba015d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318600"
---
# <a name="csyncobject-class"></a>CSyncObject 클래스

Win32의 동기화 개체에 일반적인 기능을 제공하는 순수 가상 클래스입니다.

## <a name="syntax"></a>구문

```
class CSyncObject : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|`CSyncObject` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSyncObject:: Lock](#lock)|동기화 개체에 대 한 액세스 권한을 얻습니다.|
|[CSyncObject:: Unlock](#unlock)|동기화 개체에 대 한 액세스 권한을 얻습니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CSyncObject:: operator 핸들](#operator_handle)|동기화 개체에 대 한 액세스를 제공 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CSyncObject:: m_hObject](#m_hobject)|내부 동기화 개체에 대 한 핸들입니다.|

## <a name="remarks"></a>설명

MFC 라이브러리는에서 파생 된 여러 클래스를 제공 합니다 `CSyncObject` . [CEvent](../../mfc/reference/cevent-class.md), [cmutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)및 [CSemaphore](../../mfc/reference/csemaphore-class.md)입니다.

동기화 개체를 사용 하는 방법에 대 한 자세한 내용은 [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>요구 사항

**헤더:** afxmt

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a> CSyncObject::CSyncObject

제공 된 이름을 사용 하 여 동기화 개체를 생성 합니다.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>매개 변수

*pstrName*<br/>
개체의 이름입니다. NULL 인 경우 *Pstrname* 은 null입니다.

## <a name="csyncobjectlock"></a><a name="lock"></a> CSyncObject:: Lock

동기화 개체에 의해 제어 되는 리소스에 대 한 액세스 권한을 얻으려면이 함수를 호출 합니다.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>매개 변수

*dwTimeout*<br/>
동기화 개체를 사용할 수 있을 때까지 대기 하는 시간 (밀리초)을 지정 합니다. 무한 하면는 `Lock` 반환 하기 전에 개체가 신호를 받을 때까지 대기 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

동기화 개체가 신호를 받으면가 `Lock` 성공적으로 반환 되 고 이제 스레드가 개체를 소유 합니다. 동기화 개체가 신호 없음으로 (사용할 수 없음) 인 경우는 `Lock` 동기화 개체가 *dwtimeout* 매개 변수에 지정 된 시간 (밀리초)까지 신호를 받을 때까지 기다립니다. 동기화 개체가 지정 된 시간 내에 신호를 받지 못한 경우는 오류를 `Lock` 반환 합니다.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a> CSyncObject:: m_hObject

내부 동기화 개체에 대 한 핸들입니다.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a> CSyncObject:: operator 핸들

이 연산자를 사용 하 여 개체의 핸들을 가져옵니다 `CSyncObject` .

```
operator HANDLE() const;
```

### <a name="return-value"></a>반환 값

성공 하면 동기화 개체의 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

핸들을 사용 하 여 Windows Api를 직접 호출할 수 있습니다.

## <a name="csyncobjectunlock"></a><a name="unlock"></a> CSyncObject:: Unlock

`Unlock`매개 변수가 없는의 선언은 순수 가상 함수 이며에서 파생 되는 모든 클래스에 의해 재정의 되어야 합니다 `CSyncObject` .

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>매개 변수

*lCount*<br/>
기본 구현에서는 사용 되지 않습니다.

*lpPrevCount*<br/>
기본 구현에서는 사용 되지 않습니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

두 매개 변수가 있는 선언의 기본 구현은 항상 TRUE를 반환 합니다. 이 함수는 호출 스레드가 소유한 동기화 개체에 대 한 액세스를 해제 하기 위해 호출 됩니다. 두 번째 선언은 제어 되는 리소스에 대 한 액세스를 둘 이상 허용 하는 세마포어와 같은 동기화 개체에 대해 제공 됩니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
