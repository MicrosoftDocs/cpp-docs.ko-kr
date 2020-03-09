---
title: CSocket 클래스
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854557"
---
# <a name="csocket-class"></a>CSocket 클래스

는 `CAsyncSocket`에서 파생 되며 Windows 소켓 API의 캡슐화를 상속 하며, `CAsyncSocket` 개체 보다 높은 수준의 추상화를 나타냅니다.

## <a name="syntax"></a>구문

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>구성원

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CSocket:: CSocket](#csocket)|`CSocket` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CSocket:: Attach](#attach)|소켓 핸들을 `CSocket` 개체에 연결 합니다.|
|[CSocket:: CancelBlockingCall](#cancelblockingcall)|현재 진행 중인 차단 호출을 취소 합니다.|
|[CSocket:: Create](#create)|소켓을 만듭니다.|
|[CSocket:: FromHandle](#fromhandle)|지정 된 소켓 핸들을 지정 하 여 `CSocket` 개체에 대 한 포인터를 반환 합니다.|
|[CSocket:: IsBlocking](#isblocking)|차단 호출이 진행 중인지 여부를 확인 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|속성|Description|
|----------|-----------------|
|[CSocket:: OnMessagePending](#onmessagepending)|차단 호출이 완료 될 때까지 대기 하는 동안 보류 중인 메시지를 처리 하기 위해 호출 됩니다.|

## <a name="remarks"></a>설명

`CSocket`는 `CSocketFile` 및 `CArchive` 클래스에서 작동 하 여 데이터의 전송과 수신을 관리 합니다.

`CSocket` 개체는 `CArchive`의 동기 작업에 필수적인 차단도 제공 합니다. `Receive`, `Send`, `ReceiveFrom`, `SendTo`, `Accept` (`CAsyncSocket`에서 모두 상속 된 모두)와 같은 블로킹 함수는 `WSAEWOULDBLOCK`에서 `CSocket`오류를 반환 하지 않습니다. 대신 이러한 함수는 작업이 완료 될 때까지 대기 합니다. 또한 이러한 함수 중 하나가 차단 되는 동안 `CancelBlockingCall`가 호출 되는 경우 원래 호출은 오류 WSAEINTR와 함께 종료 됩니다.

`CSocket` 개체를 사용 하려면 생성자를 호출한 다음 `Create`를 호출 하 여 기본 소켓 핸들 (형식 소켓)을 만듭니다. `Create`의 기본 매개 변수는 스트림 소켓을 만들지만 `CArchive` 개체를 사용 하 여 소켓을 사용 하지 않는 경우에는 매개 변수를 지정 하 여 데이터 그램 소켓을 대신 만들거나 특정 포트에 바인딩하여 서버 소켓을 만들 수 있습니다. 클라이언트 쪽에서 `Connect`를 사용 하 여 클라이언트 소켓에 연결 하 고 서버 쪽에서 `Accept` 합니다. 그런 다음 `CSocketFile` 개체를 만들어 `CSocketFile` 생성자의 `CSocket` 개체에 연결 합니다. 다음으로, 전송 하기 위한 `CArchive` 개체와 데이터를 받는 데 필요한 개체 (필요한 경우)를 만든 다음이 개체를 `CArchive` 생성자의 `CSocketFile` 개체와 연결 합니다. 통신이 완료 되 면 `CArchive`, `CSocketFile`및 `CSocket` 개체를 삭제 합니다. 소켓 데이터 형식은 [Windows 소켓: 배경](../../mfc/windows-sockets-background.md)문서에 설명 되어 있습니다.

`CSocketFile` 및 `CSocket`에서 `CArchive`를 사용 하는 경우 요청 된 바이트 크기를 기다리는 루프 (`PumpMessages(FD_READ)`)를 `CSocket::Receive` 입력 하는 상황이 발생할 수 있습니다. 이는 Windows 소켓에서 FD_READ 알림 당 하나의 수신 호출만 허용 하기 때문입니다. 하지만 `CSocketFile` 및 `CSocket`는 FD_READ 당 여러 recv 호출을 허용 합니다. 읽을 데이터가 없는 경우 FD_READ 발생 하면 응용 프로그램이 중단 됩니다. 다른 FD_READ를 얻지 못한 경우 응용 프로그램은 소켓을 통한 통신을 중지 합니다.

이 문제는 다음과 같이 해결할 수 있습니다. 소켓 클래스의 `OnReceive` 메서드에서 소켓에서 읽을 예상 데이터가 하나의 TCP 패킷 크기를 초과 하는 경우 (일반적으로 1096 바이트 이상 네트워크 미디어의 최대 전송 단위) 메시지 클래스의 `Serialize` 메서드를 호출 하기 전에 `CAsyncSocket::IOCtl(FIONREAD, ...)`를 호출 합니다. 사용 가능한 데이터의 크기가 필요한 것 보다 작은 경우 모든 데이터를 받을 때까지 기다렸다가 읽기 작업을 시작 합니다.

다음 예제에서 `m_dwExpected`은 사용자가 받으려는 예상 바이트 수입니다. 코드의 다른 곳에서 선언 하는 것으로 가정 합니다.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  정적으로 연결 된 MFC 응용 프로그램의 보조 스레드에서 MFC 소켓을 사용 하는 경우 소켓 라이브러리를 초기화 하는 데 소켓을 사용 하는 각 스레드에서 `AfxSocketInit`를 호출 해야 합니다. 기본적으로 `AfxSocketInit`는 주 스레드에서만 호출 됩니다.

자세한 내용은 [MFC의 Windows 소켓](../../mfc/windows-sockets-in-mfc.md), [Windows 소켓: 보관 파일에 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md), [windows 소켓:](../../mfc/windows-sockets-how-sockets-with-archives-work.md)보관 파일의 소켓 사용, windows 소켓: [작업 시퀀스](../../mfc/windows-sockets-sequence-of-operations.md), [Windows 소켓: 아카이브를 사용 하는 소켓 예](../../mfc/windows-sockets-example-of-sockets-using-archives.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>요구 사항

**헤더:** afxsock

##  <a name="attach"></a>CSocket:: Attach

`CSocket` 개체에 `hSocket` 핸들을 연결 하려면이 멤버 함수를 호출 합니다.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>매개 변수

*hSocket*<br/>
소켓에 대 한 핸들을 포함 합니다.

### <a name="return-value"></a>Return Value

함수가 성공하는 경우 0이 아닙니다.

### <a name="remarks"></a>설명

소켓 핸들은 개체의 [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) 데이터 멤버에 저장 됩니다.

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket:: CancelBlockingCall

현재 진행 중인 차단 호출을 취소 하려면이 멤버 함수를 호출 합니다.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>설명

이 함수는이 소켓에 대해 처리 중인 모든 차단 작업을 취소 합니다. 원래 차단 호출은 오류 WSAEINTR를 사용 하 여 가능한 한 빨리 종료 됩니다.

블로킹 `Connect` 작업의 경우 Windows 소켓 구현은 가능한 한 빨리 차단 호출을 종료 하지만 연결이 완료 된 후 다시 설정 되거나 시간이 초과 될 때까지 소켓 리소스를 해제 하는 것이 불가능할 수 있습니다. 이는 응용 프로그램이 즉시 새 소켓을 열거나 (소켓을 사용할 수 없는 경우) 동일한 피어에 연결 하는 경우에만 발생할 수 있습니다.

`Accept` 이외의 작업을 취소 하면 소켓이 결정 되지 않은 상태로 유지 될 수 있습니다. 응용 프로그램이 소켓에서 차단 작업을 취소 하는 경우 일부 Windows 소켓 구현에서 다른 작업이 작동할 수 있지만 응용 프로그램이 소켓에서 수행할 수 있는 작업을 수행할 수 있는 유일한 작업은 `Close`에 대 한 호출입니다. 응용 프로그램에 대 한 최대 이식성을 원하는 경우 취소 후 작업 수행에 의존 하지 않도록 주의 해야 합니다.

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

##  <a name="create"></a>CSocket:: Create

소켓 개체를 생성 한 후 **create** member 함수를 호출 하 여 Windows 소켓을 만들고 연결 합니다.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>매개 변수

*nSocketPort*<br/>
소켓에 사용할 특정 포트 이거나, MFC에서 포트를 선택 하도록 하려면 0입니다.

*nSocketType*<br/>
SOCK_STREAM 또는 SOCK_DGRAM.

*lpszSocketAddress*<br/>
연결 된 소켓의 네트워크 주소를 포함 하는 문자열에 대 한 포인터입니다 (예: "128.56.22.8"). 이 매개 변수에 대 한 NULL 문자열을 전달 하면 `CSocket` 인스턴스가 모든 네트워크 인터페이스에서 클라이언트 작업을 수신 대기 해야 함을 나타냅니다.

### <a name="return-value"></a>Return Value

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고 `GetLastError`를 호출 하 여 특정 오류 코드를 검색할 수 있습니다.

### <a name="remarks"></a>설명

그런 다음 `Create` `Bind`를 호출 하 여 소켓을 지정 된 주소에 바인딩합니다. 다음 소켓 형식이 지원 됩니다.

- SOCK_STREAM는 시퀀싱 되 고 신뢰할 수 있는 양방향 연결 기반 바이트 스트림을 제공 합니다. 인터넷 주소 제품군에 대해 TCP (전송 제어 프로토콜)를 사용 합니다.

- SOCK_DGRAM은 고정 (일반적으로 작은) 최대 길이에서 연결 되지 않은 불안정 한 버퍼 인 데이터 그램을 지원 합니다. 인터넷 주소 제품군에 대해 UDP (사용자 데이터 그램 프로토콜)를 사용 합니다. 이 옵션을 사용 하려면 `CArchive` 개체가 있는 소켓을 사용 하면 안 됩니다.

    > [!NOTE]
    >  `Accept` 멤버 함수는 비어 있는 새 `CSocket` 개체에 대 한 참조를 매개 변수로 사용 합니다. `Accept`를 호출 하기 전에이 개체를 생성 해야 합니다. 이 소켓 개체가 범위를 벗어나면 연결이 닫힙니다. 이 새 소켓 개체에 대해 `Create`를 호출 하지 마세요.

스트림 및 데이터 그램 소켓에 대 한 자세한 내용은 [Windows 소켓: 배경](../../mfc/windows-sockets-background.md), windows 소켓: [포트 및 소켓 주소](../../mfc/windows-sockets-ports-and-socket-addresses.md)및 [windows 소켓: 보관 파일에 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)문서를 참조 하세요.

##  <a name="csocket"></a>CSocket:: CSocket

`CSocket` 개체를 생성합니다.

```
CSocket();
```

### <a name="remarks"></a>설명

생성 후 `Create` 멤버 함수를 호출 해야 합니다.

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

##  <a name="fromhandle"></a>CSocket:: FromHandle

`CSocket` 개체에 대 한 포인터를 반환 합니다.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>매개 변수

*hSocket*<br/>
소켓에 대 한 핸들을 포함 합니다.

### <a name="return-value"></a>Return Value

`CSocket` 개체에 대 한 포인터 이거나 *Hsocket*에 연결 된 `CSocket` 개체가 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

소켓 핸들을 지정 하면 `CSocket` 개체가 핸들에 연결 되지 않은 경우 멤버 함수는 NULL을 반환 하 고 임시 개체를 만들지 않습니다.

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

##  <a name="isblocking"></a>CSocket:: IsBlocking

차단 호출이 진행 되 고 있는지 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Return Value

소켓이 차단 되 고 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

##  <a name="onmessagepending"></a>CSocket:: OnMessagePending

이 멤버 함수를 재정의 하 여 Windows에서 특정 메시지를 검색 하 고 소켓에서 해당 메시지에 응답 합니다.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Return Value

메시지가 처리 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이는 고급 재정의 가능입니다.

응용 프로그램에 대 한 중요 한 메시지를 처리할 수 있는 기회를 제공 하기 위해 소켓이 Windows 메시지를 펌프 하는 동안 프레임 워크는 `OnMessagePending`를 호출 합니다. `OnMessagePending`를 사용 하는 방법에 대 한 예제는 [Windows 소켓: 소켓 클래스에서 파생](../../mfc/windows-sockets-deriving-from-socket-classes.md)문서를 참조 하세요.

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CAsyncSocket 클래스](../../mfc/reference/casyncsocket-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 클래스](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile 클래스](../../mfc/reference/csocketfile-class.md)
