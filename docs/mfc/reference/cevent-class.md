---
description: '자세히 알아보기: CEvent 클래스'
title: CEvent 클래스
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: 0db33c89b52c3c6cb3dbf37cb3ea3da96e6c6c71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184701"
---
# <a name="cevent-class"></a>CEvent 클래스

한 스레드에서 이벤트가 발생 했음을 다른 스레드에 알릴 수 있도록 하는 동기화 개체인 이벤트를 나타냅니다.

## <a name="syntax"></a>구문

```
class CEvent : public CSyncObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|`CEvent` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CEvent::P ulseEvent](#pulseevent)|이벤트를 사용 가능 (신호 받음)으로 설정 하 고, 대기 스레드를 해제 하 고, 이벤트를 사용할 수 없도록 설정 합니다 (신호 없음으로).|
|[CEvent::ResetEvent](#resetevent)|이벤트를 사용할 수 없음 (신호 없음으로)으로 설정 합니다.|
|[CEvent::SetEvent](#setevent)|이벤트를 사용 가능 (신호 받음)으로 설정 하 고 대기 중인 스레드를 모두 해제 합니다.|
|[CEvent:: Unlock](#unlock)|이벤트 개체를 해제 합니다.|

## <a name="remarks"></a>설명

이벤트는 스레드가 태스크를 수행할 시기를 알아야 하는 경우에 유용 합니다. 예를 들어 데이터를 데이터 보관에 복사 하는 스레드는 새 데이터를 사용할 수 있을 때이를 알려 두어야 합니다. `CEvent`새 데이터를 사용할 수 있는 경우 개체를 사용 하 여 복사 스레드를 알리기 때문에 스레드는 가능한 한 빨리 해당 태스크를 수행할 수 있습니다.

`CEvent` 개체에는 수동 및 자동 이라는 두 가지 유형이 있습니다.

자동 `CEvent` 개체는 하나 이상의 스레드가 해제 된 후 신호를 받지 않는 (사용할 수 없음) 상태로 자동으로 반환 됩니다. 기본적으로 개체는 `CEvent` 생성 하는 `TRUE` 동안 *bManualReset* 매개 변수에 대해를 전달 하지 않는 한 자동입니다.

수동 `CEvent` 개체는 다른 함수가 호출 될 때까지 [SetEvent](#setevent) 또는 [ResetEvent](#resetevent) 에 의해 설정 된 상태로 유지 됩니다. 수동 개체를 만들려면 `CEvent` `TRUE` `bManualReset` 생성 중에 매개 변수를 전달 합니다.

개체를 사용 하려면 `CEvent` `CEvent` 필요한 경우 개체를 구성 합니다. 대기 하려는 이벤트의 이름을 지정 하 고 응용 프로그램에서 처음에 해당 이벤트를 소유 하도록 지정 합니다. 그런 다음 생성자가를 반환할 때 이벤트에 액세스할 수 있습니다. [SetEvent](#setevent) 을 호출 하 여 이벤트 개체를 신호 (사용 가능 하 게 설정) 한 다음 제어 되는 리소스에 대 한 액세스를 마치면 [잠금 해제](#unlock) 를 호출 합니다.

개체를 사용 하는 다른 방법은 `CEvent` 제어 하려는 클래스에 형식의 변수를 데이터 멤버로 추가 하는 것입니다 `CEvent` . 제어 되는 개체를 생성 하는 동안 데이터 멤버의 생성자를 호출 하 `CEvent` 고, 이벤트가 처음에 신호를 받도록 할지 여부를 지정 하 고, 이벤트의 이름 (프로세스 경계에서 사용 되는 경우) 및 원하는 모든 보안 특성을 specifythe 지정 합니다.

이러한 방식으로 개체에 의해 제어 되는 리소스에 액세스 하려면 `CEvent` 먼저 리소스의 액세스 메서드에 [Csinglelock](../../mfc/reference/csinglelock-class.md) 형식의 변수 또는 [CMultiLock](../../mfc/reference/cmultilock-class.md) 를 만듭니다. 그런 다음 `Lock` lock 개체의 메서드 (예 [: CMultiLock:: lock](../../mfc/reference/cmultilock-class.md#lock))를 호출 합니다. 이 시점에서 스레드는 리소스에 대 한 액세스 권한을 획득 하 고, 리소스를 해제 하 고 액세스할 때까지 기다리거나, 리소스가 해제 될 때까지 기다리거나 시간이 초과 되 고 리소스에 대 한 액세스 권한을 얻는 데 실패 합니다. 어떤 경우 든 리소스는 스레드로부터 안전한 방식으로 액세스 됩니다. 리소스를 해제 하려면를 호출 `SetEvent` 하 여 이벤트 개체에 신호를 보내고 `Unlock` lock 개체의 메서드 (예 [: CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock))를 사용 하거나 잠금 개체의 범위를 벗어나는 것을 허용 합니다.

개체를 사용 하는 방법에 대 한 자세한 내용은 `CEvent` [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)을 참조 하세요.

## <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>요구 사항

**헤더:** afxmt

## <a name="ceventcevent"></a><a name="cevent"></a> CEvent::CEvent

명명 되거나 명명 되지 않은 `CEvent` 개체를 생성 합니다.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>매개 변수

*bInitiallyOwn*<br/>
TRUE 이면 `CMultilock` 또는 개체의 스레드가 `CSingleLock` 사용 됩니다. 그렇지 않으면 리소스에 액세스 하려는 모든 스레드가 대기 해야 합니다.

*bManualReset*<br/>
TRUE 이면 이벤트 개체가 수동 이벤트 임을 지정 하 고, 그렇지 않으면 이벤트 개체가 자동 이벤트 임을 지정 합니다.

*lpszName*<br/>
`CEvent` 개체의 이름입니다. 개체를 프로세스 경계에서 사용할 경우에는를 제공 해야 합니다. 이름이 기존 이벤트와 일치 하는 경우 생성자는 해당 이름의 이벤트를 참조 하는 새 개체를 빌드합니다 `CEvent` . 이름이 이벤트가 아닌 기존 동기화 개체와 일치 하는 경우 생성이 실패 합니다. NULL 인 경우에는 이름이 null이 됩니다.

*lpsaAttribute*<br/>
이벤트 개체의 보안 특성입니다. 이 구조에 대 한 자세한 내용은 Windows SDK [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 을 참조 하십시오.

### <a name="remarks"></a>설명

개체를 액세스 하거나 해제 하려면 `CEvent` [CMultiLock](../../mfc/reference/cmultilock-class.md) 또는 [csinglelock](../../mfc/reference/csinglelock-class.md) 개체를 만들고 해당 [잠금](../../mfc/reference/csinglelock-class.md#lock) 및 잠금 [해제](../../mfc/reference/csinglelock-class.md#unlock) 멤버 함수를 호출 합니다.

개체의 상태를 `CEvent` 신호 받음으로 변경 하려면 (스레드가 대기 하지 않아도 되는 경우) [SetEvent](#setevent) 또는 [PulseEvent](#pulseevent)를 호출 합니다. 개체의 상태를 `CEvent` 신호 없음으로 (스레드가 대기 해야 함)로 설정 하려면 [ResetEvent](#resetevent)를 호출 합니다.

> [!IMPORTANT]
> 개체를 만든 후 `CEvent` 에는 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 사용 하 여 뮤텍스가 아직 존재 하지 않는지 확인 합니다. 뮤텍스가 예기치 않게 존재 하는 경우 rogue 프로세스가 squatting을 나타낼 수 있으며 뮤텍스를 악의적으로 사용 하려고 할 수 있습니다. 이 경우에 권장 되는 보안 인식 절차는 핸들을 닫고 개체를 만드는 동안 오류가 발생 한 것 처럼 계속 진행 하는 것입니다.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a> CEvent::P ulseEvent

이벤트 상태를 신호 받음 (사용 가능)으로 설정 하 고, 대기 중인 모든 스레드를 해제 하 고, 자동으로 신호 없음으로 (사용할 수 없음)로 다시 설정 합니다.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이벤트가 수동 이면 대기 중인 모든 스레드가 해제 되 고 이벤트가 신호 없음으로로 설정 되 고이 `PulseEvent` 반환 됩니다. 이벤트가 자동 인 경우 단일 스레드가 해제 되 고 이벤트가 신호 없음으로로 설정 되 고이 `PulseEvent` 반환 됩니다.

대기 중인 스레드가 없거나 즉시 스레드를 해제할 수 없으면 `PulseEvent` 이벤트의 상태를 신호 없음으로로 설정 하 고를 반환 합니다.

`PulseEvent` 는 `PulseEvent` 커널 모드 비동기 프로시저 호출을 통해 대기 상태에서 일시적으로 제거할 수 있는 기본 Win32 함수를 사용 합니다. 따라서 `PulseEvent` 는 안정적이 지 않으므로 새 응용 프로그램에서 사용 하면 안 됩니다. 자세한 내용은 [PulseEvent 함수](/windows/win32/api/winbase/nf-winbase-pulseevent)를 참조 하세요.

## <a name="ceventresetevent"></a><a name="resetevent"></a> CEvent::ResetEvent

[SetEvent](#setevent) 멤버 함수에서 신호를 받는로 명시적으로 설정할 때까지 이벤트의 상태를 신호 없음으로 설정 합니다.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이로 인해이 이벤트에 액세스 하는 모든 스레드가 대기 합니다.

이 멤버 함수는 자동 이벤트에서 사용 되지 않습니다.

## <a name="ceventsetevent"></a><a name="setevent"></a> CEvent::SetEvent

대기 중인 스레드를 해제 하 여 이벤트 상태를 신호 받음으로 설정 합니다.

```
BOOL SetEvent();
```

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이벤트가 수동 인 경우에는 [ResetEvent](#resetevent) 가 호출 될 때까지 이벤트가 신호를 받은 상태로 유지 됩니다. 이 경우 둘 이상의 스레드를 해제할 수 있습니다. 이벤트가 자동 인 경우 이벤트는 단일 스레드가 해제 될 때까지 신호를 받은 상태로 유지 됩니다. 그러면 시스템에서 이벤트의 상태를 신호 없음으로로 설정 합니다. 대기 중인 스레드가 없는 경우 스레드 하나를 해제할 때까지 상태는 신호 받음 상태로 유지 됩니다.

## <a name="ceventunlock"></a><a name="unlock"></a> CEvent:: Unlock

이벤트 개체를 해제 합니다.

```
BOOL Unlock();
```

### <a name="return-value"></a>반환 값

이벤트 개체를 소유한 스레드와 이벤트가 자동 이벤트 인 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 현재 자동 이벤트를 소유 하 고 있는 스레드에서 호출 하 여 잠금 개체를 다시 사용 해야 하는 경우 해당 작업을 해제 합니다. 잠금 개체를 다시 사용 하지 않는 경우이 함수는 lock 개체의 소멸자에 의해 호출 됩니다.

## <a name="see-also"></a>참고 항목

[CSyncObject 클래스](../../mfc/reference/csyncobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
