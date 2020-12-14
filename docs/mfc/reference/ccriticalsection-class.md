---
description: '자세히 알아보기: CCriticalSection 클래스'
title: CCriticalSection 클래스
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: 0041eea4453ec02159b26805bd5e7a264a410504
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227795"
---
# <a name="ccriticalsection-class"></a>CCriticalSection 클래스

한 번에 한 스레드만 리소스 또는 코드 섹션에 액세스할 수 있도록 하는 동기화 개체인 "임계 섹션"을 나타냅니다.

## <a name="syntax"></a>구문

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|`CCriticalSection` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCriticalSection:: Lock](#lock)|를 사용 하 여 개체에 대 한 액세스 권한을 얻습니다 `CCriticalSection` .|
|[CCriticalSection:: Unlock](#unlock)|`CCriticalSection` 개체를 해제합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CCriticalSection:: operator CRITICAL_SECTION *](#operator_critical_section_star)|내부 CRITICAL_SECTION 개체에 대 한 포인터를 검색 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CCriticalSection:: m_sect](#m_sect)|CRITICAL_SECTION 개체입니다.|

## <a name="remarks"></a>설명

중요 섹션은 한 번에 하나의 스레드만 데이터 또는 다른 제어 된 리소스를 수정할 수 있는 경우에 유용 합니다. 예를 들어 연결 된 목록에 노드를 추가 하는 프로세스는 한 번에 하나의 스레드에서만 허용 해야 하는 프로세스입니다. 개체를 사용 하 여 `CCriticalSection` 연결 된 목록을 제어 하면 한 번에 하나의 스레드만 목록에 액세스할 수 있습니다.

> [!NOTE]
> 클래스의 기능은 `CCriticalSection` 실제 Win32 CRITICAL_SECTION 개체에서 제공 됩니다.

중요 섹션은 속도가 중요 하 고 프로세스 경계에서 리소스가 사용 되지 않을 때 뮤텍스 ( [Cmutex](../../mfc/reference/cmutex-class.md)참조) 대신 사용 됩니다.

개체를 사용 하는 방법에는 `CCriticalSection` 독립 실행형과 클래스에 포함 된 두 가지 방법이 있습니다.

- 독립 실행형 메서드 독립 실행형 개체를 사용 하 여 `CCriticalSection` `CCriticalSection` 필요한 경우 개체를 생성 합니다. 생성자에서 성공적으로 반환 된 후 [잠금](#lock)에 대 한 호출을 사용 하 여 개체를 명시적으로 잠급니다. 임계 영역에 대 한 액세스가 완료 되 면 [잠금 해제](#unlock) 를 호출 합니다. 이 메서드는 소스 코드를 읽는 사람에 게는 액세스 전후에 임계 영역을 잠그거나 잠금 해제 하는 것을 염두에 두어야 하므로 오류가 발생 하기 쉽습니다.

   더 나은 방법은 [Csinglelock](../../mfc/reference/csinglelock-class.md) 클래스를 사용 하는 것입니다. 또한 `Lock` 및 `Unlock` 메서드가 있지만 예외가 발생 하는 경우 리소스의 잠금을 해제 하는 것에 대해 걱정 하지 않아도 됩니다.

- 포함 된 메서드 `CCriticalSection` -형식 데이터 멤버를 클래스에 추가 하 고 필요한 경우 데이터 멤버를 잠가 여러 스레드를 사용 하 여 클래스를 공유할 수도 있습니다.

개체를 사용 하는 방법에 대 한 자세한 내용은 `CCriticalSection` [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>요구 사항

**헤더:** afxmt

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a> CCriticalSection::CCriticalSection

`CCriticalSection` 개체를 생성합니다.

```
CCriticalSection();
```

### <a name="remarks"></a>설명

개체에 액세스 하거나 해제 하려면 `CCriticalSection` [csinglelock](../../mfc/reference/csinglelock-class.md) 개체를 만들고 해당 [잠금](../../mfc/reference/csinglelock-class.md#lock) 및 잠금 [해제](../../mfc/reference/csinglelock-class.md#unlock) 멤버 함수를 호출 합니다. `CCriticalSection`개체가 독립 실행형으로 사용 되는 경우 해당 [잠금 해제](#unlock) 멤버 함수를 호출 하 여 해제 합니다.

생성자가 필요한 시스템 메모리를 할당 하지 못하면 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md)형식의 메모리 예외가 자동으로 throw 됩니다.

### <a name="example"></a>예제

  [CCriticalSection:: Lock](#lock)의 예제를 참조 하세요.

## <a name="ccriticalsectionlock"></a><a name="lock"></a> CCriticalSection:: Lock

이 멤버 함수를 호출 하 여 임계 영역 개체에 대 한 액세스 권한을 얻습니다.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>매개 변수

*dwTimeout*<br/>
`Lock` 이 매개 변수 값을 무시 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Lock` 는 임계 영역 개체를 신호 받음 (사용할 수 있음) 할 때까지 반환 되지 않는 차단 호출입니다.

시간이 지정 된 대기 시간이 필요한 경우에는 개체 대신 [Cmutex](../../mfc/reference/cmutex-class.md) 개체를 사용할 수 있습니다 `CCriticalSection` .

에서 `Lock` 필요한 시스템 메모리를 할당 하지 못하면 [cmemoryexception](../../mfc/reference/cmemoryexception-class.md)형식의 메모리 예외가 자동으로 throw 됩니다.

### <a name="example"></a>예제

이 예제에서는 공유 개체를 사용 하 여 공유 리소스 (정적 개체)에 대 한 액세스를 제어 하 여 중첩 된 임계 영역 접근 방식을 보여 줍니다 `_strShared` `CCriticalSection` . `SomeMethod`함수는 안전한 방식으로 공유 리소스를 업데이트 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a> CCriticalSection:: m_sect

모든 메서드에서 사용 하는 임계 영역 개체를 포함 `CCriticalSection` 합니다.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a> CCriticalSection:: operator CRITICAL_SECTION *

CRITICAL_SECTION 개체를 검색 합니다.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>설명

내부 CRITICAL_SECTION 개체에 대 한 포인터를 검색 하려면이 함수를 호출 합니다.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a> CCriticalSection:: Unlock

`CCriticalSection`다른 스레드에서 사용할 개체를 해제 합니다.

```
BOOL Unlock();
```

### <a name="return-value"></a>반환 값

`CCriticalSection`스레드가 개체를 소유 하 고 있으며 릴리스가 성공적으로 수행 되었으면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 독립 실행형으로 사용 되는 경우 `CCriticalSection` 에는 `Unlock` 임계 영역에서 제어 하는 리소스의 사용을 완료 한 후 즉시를 호출 해야 합니다. [Csinglelock](../../mfc/reference/csinglelock-class.md) 개체를 사용 하는 경우 `CCriticalSection::Unlock` 은 잠금 개체의 멤버 함수에 의해 호출 됩니다 `Unlock` .

### <a name="example"></a>예제

  [CCriticalSection:: Lock](#lock)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CSyncObject 클래스](../../mfc/reference/csyncobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMutex 클래스](../../mfc/reference/cmutex-class.md)
