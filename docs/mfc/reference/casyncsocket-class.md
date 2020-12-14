---
description: '다음에 대 한 자세한 정보: CAsyncSocket 클래스'
title: CAsyncSocket 클래스
ms.date: 06/25/2020
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
ms.openlocfilehash: a9b020a93d4d0f279b5b79fa76a9f6b94e4f9f03
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234334"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 클래스

네트워크 통신의 끝점 인 Windows 소켓을 나타냅니다.

## <a name="syntax"></a>구문

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAsyncSocket:: CAsyncSocket](#casyncsocket)|`CAsyncSocket` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAsyncSocket:: Accept](#accept)|소켓에 대 한 연결을 허용 합니다.|
|[CAsyncSocket:: AsyncSelect](#asyncselect)|소켓에 대 한 이벤트 알림을 요청 합니다.|
|[CAsyncSocket:: Attach](#attach)|소켓 핸들을 개체에 연결 `CAsyncSocket` 합니다.|
|[CAsyncSocket:: Bind](#bind)|로컬 주소를 소켓과 연결 합니다.|
|[CAsyncSocket:: Close](#close)|소켓을 닫습니다.|
|[CAsyncSocket:: Connect](#connect)|피어 소켓에 대 한 연결을 설정 합니다.|
|[CAsyncSocket::Create](#create)|소켓을 만듭니다.|
|[CAsyncSocket:: CreateEx](#createex)|고급 옵션을 사용 하 여 소켓을 만듭니다.|
|[CAsyncSocket::D etach](#detach)|개체에서 소켓 핸들을 분리 `CAsyncSocket` 합니다.|
|[CAsyncSocket:: FromHandle](#fromhandle)|`CAsyncSocket`지정 된 소켓 핸들을 지정 하 여 개체에 대 한 포인터를 반환 합니다.|
|[CAsyncSocket:: GetLastError](#getlasterror)|실패 한 마지막 작업의 오류 상태를 가져옵니다.|
|[CAsyncSocket:: GetPeerName](#getpeername)|소켓이 연결 된 피어 소켓의 주소를 가져옵니다.|
|[CAsyncSocket:: GetPeerNameEx](#getpeernameex)|소켓이 연결 된 피어 소켓의 주소를 가져옵니다 (IPv6 주소를 처리).|
|[CAsyncSocket:: GetSockName](#getsockname)|소켓의 로컬 이름을 가져옵니다.|
|[CAsyncSocket:: GetSockNameEx](#getsocknameex)|소켓의 로컬 이름을 가져옵니다 (IPv6 주소 처리).|
|[CAsyncSocket:: GetSockOpt](#getsockopt)|소켓 옵션을 검색 합니다.|
|[CAsyncSocket:: IOCtl](#ioctl)|소켓의 모드를 제어 합니다.|
|[CAsyncSocket:: 수신 대기](#listen)|들어오는 연결 요청을 수신 하는 소켓을 설정 합니다.|
|[CAsyncSocket:: Receive](#receive)|소켓에서 데이터를 수신 합니다.|
|[CAsyncSocket:: ReceiveFrom](#receivefrom)|데이터 그램을 받고 원본 주소를 저장 합니다.|
|[CAsyncSocket:: ReceiveFromEx](#receivefromex)|데이터 그램을 받고 원본 주소 (IPv6 주소 처리)를 저장 합니다.|
|[CAsyncSocket:: Send](#send)|데이터를 연결된 소켓으로 전송합니다.|
|[CAsyncSocket:: SendTo](#sendto)|데이터를 특정 대상으로 보냅니다.|
|[CAsyncSocket:: SendToEx](#sendtoex)|특정 대상으로 데이터를 보냅니다 (IPv6 주소 처리).|
|[CAsyncSocket:: SetSockOpt](#setsockopt)|소켓 옵션을 설정 합니다.|
|[CAsyncSocket:: ShutDown](#shutdown)|`Send`소켓에서 및/또는 호출을 비활성화 `Receive` 합니다.|
|[CASyncSocket:: 소켓](#socket)|소켓 핸들을 할당 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAsyncSocket:: OnAccept](#onaccept)|을 호출 하 여 보류 중인 연결 요청을 허용할 수 있음을 수신 소켓에 알립니다 `Accept` .|
|[CAsyncSocket:: OnClose](#onclose)|연결 된 소켓이 닫 았 음을 소켓에 알립니다.|
|[CAsyncSocket:: OnConnect](#onconnect)|성공 여부에 관계 없이 연결 소켓에 연결 시도가 완료 되었음을 알립니다.|
|[CAsyncSocket:: OnOutOfBandData](#onoutofbanddata)|소켓에서 읽을 대역 외 데이터 (일반적으로 긴급 메시지)가 수신 소켓에 게 알립니다.|
|[CAsyncSocket:: OnReceive](#onreceive)|을 호출 하 여 검색할 데이터가 있음을 수신 소켓에 알립니다 `Receive` .|
|[CAsyncSocket:: OnSend](#onsend)|을 호출 하 여 데이터를 보낼 수 있음을 소켓에 알립니다 `Send` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAsyncSocket:: operator =](#operator_eq)|개체에 새 값을 할당 `CAsyncSocket` 합니다.|
|[CAsyncSocket:: operator SOCKET](#operator_socket)|이 연산자를 사용 하 여 개체의 소켓 핸들을 검색 `CAsyncSocket` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAsyncSocket:: m_hSocket](#m_hsocket)|이 개체에 연결 된 소켓 핸들을 나타냅니다 `CAsyncSocket` .|

## <a name="remarks"></a>설명

클래스 `CAsyncSocket` 는 Windows 소켓 함수 API를 캡슐화 하 여 MFC와 함께 Windows 소켓을 사용 하려는 프로그래머를 위한 개체 지향 추상화를 제공 합니다.

이 클래스는 네트워크 통신을 이해 한다는 가정을 기반으로 합니다. 블로킹, 바이트 순서 차이점, 유니코드 및 MBCS (멀티 바이트 문자 집합) 문자열 간의 변환을 처리 해야 합니다. 이러한 문제를 관리 하는 더 편리한 인터페이스가 필요한 [경우 클래스 클래스를 참조 하세요.](../../mfc/reference/csocket-class.md)

개체를 사용 하려면 `CAsyncSocket` 해당 생성자를 호출한 다음 [create](#create) 함수를 호출 하 여 허용 되는 소켓을 제외 하 고 기본 소켓 핸들 (형식 `SOCKET` )을 만듭니다. 서버 소켓에서 [Listen](#listen) 멤버 함수를 호출 하 고, 클라이언트 소켓이 [Connect](#connect) 멤버 함수를 호출 합니다. 서버 소켓은 연결 요청을 받을 때 [Accept](#accept) 함수를 호출 해야 합니다. 나머지 함수를 사용 `CAsyncSocket` 하 여 소켓 간의 통신을 수행 합니다. 완료 되 면 개체를 `CAsyncSocket` 힙에서 만든 경우 삭제 하 고, 소멸자는 자동으로 [Close](#close) 함수를 호출 합니다. 소켓 데이터 형식은 [Windows 소켓: 배경](../../mfc/windows-sockets-background.md)문서에 설명 되어 있습니다.

> [!NOTE]
> 정적으로 연결 된 MFC 응용 프로그램의 보조 스레드에서 MFC 소켓을 사용 하는 경우 소켓 `AfxSocketInit` 라이브러리를 초기화 하는 데 소켓을 사용 하는 각 스레드에서를 호출 해야 합니다. 기본적으로 `AfxSocketInit` 는 주 스레드에서만 호출 됩니다.

자세한 내용은 [Windows 소켓: CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) 및 관련 문서 사용 및 [WINDOWS 소켓 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>요구 사항

**헤더:** afxsock

## <a name="casyncsocketaccept"></a><a name="accept"></a> CAsyncSocket:: Accept

소켓에 대 한 연결을 허용 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>매개 변수

*rConnectedSocket*<br/>
연결에 사용할 수 있는 새 소켓을 식별 하는 참조입니다.

*lpSockAddr*<br/>
네트워크에서 알 수 있는 연결 소켓의 주소를 수신 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다. *LpSockAddr* 인수의 정확한 형식은 소켓이 생성 될 때 설정 된 주소 패밀리에 의해 결정 됩니다. *LpSockAddr* 및/또는 *lpSockAddrLen* 가 NULL 이면 허용 된 소켓의 원격 주소에 대 한 정보가 반환 되지 않습니다.

*lpSockAddrLen*<br/>
*LpSockAddr* 의 주소 길이에 대 한 포인터입니다 (바이트). *LpSockAddrLen* 는 값-결과 매개 변수입니다. 처음에는 *lpSockAddr* 가 가리키는 공간의 크기가 포함 되어야 합니다. 반환 시 반환 되는 주소의 실제 길이 (바이트)를 포함 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 너무 작습니다 ( [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조의 크기 보다 작음).

- WSAEINPROGRESS Windows 소켓 호출을 차단 하는 중입니다.

- WSAEINVAL를 `Listen` 수락 하기 전에 호출 하지 않았습니다.

- 허용 되는 항목에 대 한 큐가 비어 WSAEMFILE 사용 가능한 설명자가 없습니다.

- WSAENOBUFS 버퍼 공간을 사용할 수 없습니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP 참조 된 소켓이 연결 지향 서비스를 지 원하는 형식이 아닙니다.

- WSAEWOULDBLOCK 소켓이 비블로킹 상태로 표시 되 고 허용 되는 연결이 없습니다.

### <a name="remarks"></a>설명

이 루틴은 보류 중인 연결의 큐에 있는 첫 번째 연결을 추출 하 고,이 소켓과 동일한 속성을 사용 하 여 새 소켓을 만들고, *rConnectedSocket* 에 연결 합니다. 보류 중인 연결이 큐에 없는 경우는 0을 `Accept` 반환 하 고 `GetLastError` 오류를 반환 합니다. 허용 되는 소켓 ( *rConnectedSocket)* 을 사용 하 여 더 많은 연결을 허용할 수 없습니다. 원래 소켓은 열려 있고 수신 대기 상태로 유지 됩니다.

*LpSockAddr* 인수는 통신 계층에 알려진 연결 소켓의 주소로 채워지는 결과 매개 변수입니다. `Accept` 는 SOCK_STREAM와 같은 연결 기반 소켓 유형에 사용 됩니다.

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a> CAsyncSocket:: AsyncSelect

소켓에 대 한 이벤트 알림을 요청 하려면이 멤버 함수를 호출 합니다.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>매개 변수

*lEvent*<br/>
응용 프로그램에 관심이 있는 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.

- 읽기 준비에 대 한 알림을 수신 하 고 FD_READ 합니다.

- 데이터를 읽을 수 있는 경우 알림을 받으려는 FD_WRITE 합니다.

- FD_OOB 대역 외 데이터 도착에 대 한 알림을 받을 수 있습니다.

- 들어오는 연결에 대 한 알림을 수신 하 고 FD_ACCEPT 합니다.

- FD_CONNECT 연결 결과에 대 한 알림을 받을 수 있습니다.

- 소켓이 피어에 의해 닫힌 경우 알림을 받으려는 FD_CLOSE 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEINVAL는 지정 된 매개 변수 중 하나가 잘못 되었음을 나타냅니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

### <a name="remarks"></a>설명

이 함수는 소켓에 대해 호출 되는 MFC 콜백 알림 함수를 지정 하는 데 사용 됩니다. `AsyncSelect` 에서이 소켓을 비블로킹 모드로 자동 설정 합니다. 자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)문서를 참조 하세요.

## <a name="casyncsocketattach"></a><a name="attach"></a> CAsyncSocket:: Attach

이 멤버 함수를 호출 하 여 *Hsocket* 핸들을 개체에 연결 `CAsyncSocket` 합니다.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>매개 변수

*hSocket*<br/>
소켓에 대 한 핸들을 포함 합니다.

*lEvent*<br/>
응용 프로그램에 관심이 있는 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.

- 읽기 준비에 대 한 알림을 수신 하 고 FD_READ 합니다.

- 데이터를 읽을 수 있는 경우 알림을 받으려는 FD_WRITE 합니다.

- FD_OOB 대역 외 데이터 도착에 대 한 알림을 받을 수 있습니다.

- 들어오는 연결에 대 한 알림을 수신 하 고 FD_ACCEPT 합니다.

- FD_CONNECT 연결 결과에 대 한 알림을 받을 수 있습니다.

- 소켓이 피어에 의해 닫힌 경우 알림을 받으려는 FD_CLOSE 합니다.

### <a name="return-value"></a>반환 값

함수가 성공하는 경우 0이 아닙니다.

### <a name="remarks"></a>설명

소켓 핸들은 개체의 [m_hSocket](#m_hsocket) 데이터 멤버에 저장 됩니다.

## <a name="casyncsocketbind"></a><a name="bind"></a> CAsyncSocket:: Bind

이 멤버 함수를 호출 하 여 로컬 주소를 소켓과 연결 합니다.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>매개 변수

*nSocketPort*<br/>
소켓 응용 프로그램을 식별 하는 포트입니다.

*lpszSocketAddress*<br/>
네트워크 주소 이며, "128.56.22.8"와 같은 점으로 표시 되는 숫자입니다. 이 매개 변수에 대 한 NULL 문자열을 전달 하면 `CAsyncSocket` 인스턴스가 모든 네트워크 인터페이스에서 클라이언트 작업을 수신 대기 해야 함을 나타냅니다.

*lpSockAddr*<br/>
이 소켓에 할당할 주소를 포함 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다.

*nSockAddrLen*<br/>
*LpSockAddr* 의 주소 길이 (바이트)입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 다음 목록에서는 반환 될 수 있는 몇 가지 오류에 대해 설명 합니다. 전체 목록은 [Windows 소켓 오류 코드](/windows/win32/winsock/windows-sockets-error-codes-2)를 참조 하세요.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEADDRINUSE 지정 된 주소가 이미 사용 중입니다. [SetSockOpt](#setsockopt)의 SO_REUSEADDR 소켓 옵션을 참조 하십시오.

- WSAEFAULT *nSockAddrLen* 인수가 너무 작습니다 ( [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조의 크기 보다 작음).

- WSAEINPROGRESS Windows 소켓 호출을 차단 하는 중입니다.

- WSAEAFNOSUPPORT 지정 된 주소 패밀리가이 포트에서 지원 되지 않습니다.

- WSAEINVAL 소켓이 이미 주소에 바인딩되어 있습니다.

- WSAENOBUFS 사용할 수 있는 버퍼가 부족 합니다. 연결 수가 너무 많습니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

이 루틴은 후속 또는 호출 전에 연결 되지 않은 데이터 그램 또는 스트림 소켓에서 사용 됩니다 `Connect` `Listen` . 수신 대기 서버 소켓은 연결 요청을 수락 하기 전에 포트 번호를 선택 하 고를 호출 하 여 Windows 소켓에 알려 두어야 합니다 `Bind` . `Bind` 이름 없는 소켓에 로컬 이름을 할당 하 여 소켓의 로컬 연결 (호스트 주소/포트 번호)을 설정 합니다.

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a> CAsyncSocket:: CAsyncSocket

빈 소켓 개체를 생성 합니다.

```
CAsyncSocket();
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 해당 `Create` 멤버 함수를 호출 하 여 소켓 데이터 구조를 만들고 해당 주소를 바인딩해야 합니다. Windows 소켓 통신의 서버 쪽에서 수신 대기 소켓이 호출에 사용할 소켓을 만드는 경우 `Accept` `Create` 해당 소켓에 대해를 호출 하지 않습니다.

## <a name="casyncsocketclose"></a><a name="close"></a> CAsyncSocket:: Close

소켓을 닫습니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

이 함수는 소켓 설명자를 해제 하므로 WSAENOTSOCK 오류와 함께 실패 하는 추가 참조가 실패 합니다. 기본 소켓에 대 한 마지막 참조 인 경우 연결 된 명명 정보 및 대기 중인 데이터가 삭제 됩니다. 소켓 개체의 소멸자는를 호출 합니다 `Close` .

의 경우 `CAsyncSocket` `CSocket` 의 의미 체계는 `Close` SO_LINGER 및 SO_DONTLINGER 소켓 옵션의 영향을 받습니다. 자세한 내용은 멤버 함수를 참조 하세요 `GetSockOpt` .

## <a name="casyncsocketconnect"></a><a name="connect"></a> CAsyncSocket:: Connect

이 멤버 함수를 호출 하 여 연결 되지 않은 스트림이나 데이터 그램 소켓에 대 한 연결을 설정 합니다.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>매개 변수

*lpszHostAddress*<br/>
이 개체가 연결 된 소켓의 네트워크 주소: "ftp.microsoft.com"와 같은 컴퓨터 이름 또는 "128.56.22.8"와 같은 점으로 구분 된 숫자입니다.

*nHostPort*<br/>
소켓 응용 프로그램을 식별 하는 포트입니다.

*lpSockAddr*<br/>
연결 된 소켓의 주소를 포함 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다.

*nSockAddrLen*<br/>
*LpSockAddr* 의 주소 길이 (바이트)입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이로 인해 WSAEWOULDBLOCK 오류 코드가 표시 되 고 응용 프로그램에서 재정의 가능한 콜백을 사용 하는 경우 연결 작업이 완료 되 면 응용 프로그램에서 메시지를 받게 됩니다 `OnConnect` . 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEADDRINUSE 지정 된 주소가 이미 사용 중입니다.

- WSAEINPROGRESS Windows 소켓 호출을 차단 하는 중입니다.

- WSAEADDRNOTAVAIL 지정 된 주소를 로컬 컴퓨터에서 사용할 수 없습니다.

- 지정 된 패밀리의 WSAEAFNOSUPPORT 주소는이 소켓과 함께 사용할 수 없습니다.

- WSAECONNREFUSED 연결 시도가 거부 되었습니다.

- WSAEDESTADDRREQ 대상 주소가 필요 합니다.

- WSAEFAULT *nSockAddrLen* 인수가 잘못 되었습니다.

- WSAEINVAL 잘못 된 호스트 주소입니다.

- WSAEISCONN 소켓이 이미 연결 되어 있습니다.

- WSAEMFILE 더 이상 파일 설명자를 사용할 수 없습니다.

- WSAENETUNREACH이 호스트에서 네트워크에 연결할 수 없습니다.

- WSAENOBUFS 버퍼 공간을 사용할 수 없습니다. 소켓을 연결할 수 없는 경우

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- 연결을 설정 하지 않고 WSAETIMEDOUT 연결 시도 시간이 초과 되었습니다.

- WSAEWOULDBLOCK 소켓이 비블로킹 상태로 표시 되 고 연결을 즉시 완료할 수 없습니다.

### <a name="remarks"></a>설명

소켓이 바인딩되지 않은 경우 고유 값은 시스템에 의해 로컬 연결에 할당 되 고 소켓이 bound로 표시 됩니다. 이름 구조체의 주소 필드가 모두 0 이면는 `Connect` 0을 반환 합니다. 확장 오류 정보를 가져오려면 `GetLastError` 멤버 함수를 호출 합니다.

스트림 소켓 (유형 SOCK_STREAM)의 경우 활성 연결이 외래 호스트로 시작 됩니다. 소켓 호출이 성공적으로 완료 되 면 소켓이 데이터를 보내고 받을 준비가 된 것입니다.

데이터 그램 소켓 (유형 SOCK_DGRAM)의 경우 기본 대상은 set 이며 이후 및 호출에 사용 됩니다 `Send` `Receive` .

## <a name="casyncsocketcreate"></a><a name="create"></a> CAsyncSocket:: Create

`Create`소켓 개체를 생성 한 후 멤버 함수를 호출 하 여 Windows 소켓을 만들고 연결 합니다.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>매개 변수

*nSocketPort*<br/>
소켓에서 사용 되는 잘 알려진 포트 이거나, Windows 소켓이 포트를 선택 하도록 하려면 0입니다.

*nSocketType*<br/>
SOCK_STREAM 또는 SOCK_DGRAM.

*lEvent*<br/>
응용 프로그램에 관심이 있는 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.

- 읽기 준비에 대 한 알림을 수신 하 고 FD_READ 합니다.

- 쓰기 준비에 대 한 알림을 수신 하 고 FD_WRITE 합니다.

- FD_OOB 대역 외 데이터 도착에 대 한 알림을 받을 수 있습니다.

- 들어오는 연결에 대 한 알림을 수신 하 고 FD_ACCEPT 합니다.

- 완료 된 연결에 대 한 알림을 수신 하려고 FD_CONNECT.

- 소켓 클로저의 알림을 받으려는 FD_CLOSE.

*lpszSockAddress*<br/>
연결 된 소켓의 네트워크 주소를 포함 하는 문자열에 대 한 포인터입니다 (예: "128.56.22.8"). 이 매개 변수에 대 한 NULL 문자열을 전달 하면 `CAsyncSocket` 인스턴스가 모든 네트워크 인터페이스에서 클라이언트 작업을 수신 대기 해야 함을 나타냅니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEAFNOSUPPORT 지정 된 주소 패밀리가 지원 되지 않습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAEMFILE 더 이상 파일 설명자를 사용할 수 없습니다.

- WSAENOBUFS 버퍼 공간을 사용할 수 없습니다. 소켓을 만들 수 없습니다.

- WSAEPROTONOSUPPORT 지정 된 포트는 지원 되지 않습니다.

- WSAEPROTOTYPE 지정 된 포트가이 소켓에 대해 잘못 된 유형입니다.

- 지정 된 소켓 유형이이 주소 WSAESOCKTNOSUPPORT 지원 되지 않습니다.

### <a name="remarks"></a>설명

`Create` 는 [소켓](#socket) 을 호출 하 고 성공 하면 [bind](#bind) 를 호출 하 여 소켓을 지정 된 주소에 바인딩합니다. 다음 소켓 형식이 지원 됩니다.

- SOCK_STREAM은 시퀀스 되 고 신뢰할 수 있는 전이중 연결 기반 바이트 스트림을 제공 합니다. 인터넷 주소 제품군에 대해 TCP (전송 제어 프로토콜)를 사용 합니다.

- SOCK_DGRAM은 고정 (일반적으로 작은) 최대 길이에서 연결 되지 않은 신뢰할 수 없는 패킷 인 데이터 그램을 지원 합니다. 인터넷 주소 제품군에 대해 UDP (사용자 데이터 그램 프로토콜)를 사용 합니다.

    > [!NOTE]
    >  `Accept`멤버 함수는 비어 있는 새 개체에 대 한 참조를 `CSocket` 매개 변수로 사용 합니다. 을 호출 하기 전에이 개체를 생성 해야 `Accept` 합니다. 이 소켓 개체가 범위를 벗어나면 연결이 닫힙니다. `Create`이 새 소켓 개체에 대해를 호출 하지 마세요.

> [!IMPORTANT]
> `Create` 는 스레드로부터 안전 **하지 않습니다** .  서로 다른 스레드에서 동시에 호출 될 수 있는 다중 스레드 환경에서 호출 하는 경우 뮤텍스 또는 다른 동기화 잠금을 사용 하 여 각 호출을 보호 해야 합니다.

스트림 및 데이터 그램 소켓에 대 한 자세한 내용은 [Windows 소켓: 배경](../../mfc/windows-sockets-background.md) 및 [Windows 소켓: 포트 및 소켓 주소](../../mfc/windows-sockets-ports-and-socket-addresses.md) 와 [windows 소켓 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)문서를 참조 하세요.

## <a name="casyncsocketcreateex"></a><a name="createex"></a> CAsyncSocket:: CreateEx

`CreateEx`소켓 개체를 생성 한 후 멤버 함수를 호출 하 여 Windows 소켓을 만들고 연결 합니다.

소켓 형식과 같은 고급 옵션을 제공 해야 하는 경우이 함수를 사용 합니다.

```
BOOL CreateEx(
    ADDRINFOT* pAI,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>매개 변수

*pAI*<br/>
패밀리 및 소켓 유형과 같은 소켓 정보를 저장할 [ADDRINFOT](/windows/win32/api/ws2def/ns-ws2def-addrinfoa) 에 대 한 포인터입니다.

*lEvent*<br/>
응용 프로그램에 관심이 있는 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.

- 읽기 준비에 대 한 알림을 수신 하 고 FD_READ 합니다.

- 쓰기 준비에 대 한 알림을 수신 하 고 FD_WRITE 합니다.

- FD_OOB 대역 외 데이터 도착에 대 한 알림을 받을 수 있습니다.

- 들어오는 연결에 대 한 알림을 수신 하 고 FD_ACCEPT 합니다.

- 완료 된 연결에 대 한 알림을 수신 하려고 FD_CONNECT.

- 소켓 클로저의 알림을 받으려는 FD_CLOSE.

### <a name="return-value"></a>반환 값

[Create ()](#return-value-5)의 반환 값을 참조 하세요.

### <a name="remarks"></a>설명

[Create ()](#remarks-8)에 대 한 설명을 참조 하십시오.

## <a name="casyncsocketdetach"></a><a name="detach"></a> CAsyncSocket::D etach

개체에서 *m_hSocket* 데이터 멤버의 소켓 핸들을 분리 하 고 M_HSOCKET을 NULL로 설정 하려면이 멤버 함수를 호출 `CAsyncSocket` 합니다. 

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a> CAsyncSocket:: FromHandle

개체에 대 한 포인터를 반환 `CAsyncSocket` 합니다.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>매개 변수

*hSocket*<br/>
소켓에 대 한 핸들을 포함 합니다.

### <a name="return-value"></a>반환 값

개체에 대 한 포인터 `CAsyncSocket` 이거나 `CAsyncSocket` *hsocket* 에 연결 된 개체가 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

소켓 핸들이 지정 된 경우 `CAsyncSocket` 개체가 핸들에 연결 되지 않은 경우 멤버 함수는 NULL을 반환 합니다.

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a> CAsyncSocket:: GetLastError

실패 한 마지막 작업의 오류 상태를 가져오려면이 멤버 함수를 호출 합니다.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>반환 값

반환 값은이 스레드에서 수행한 마지막 Windows 소켓 API 루틴에 대 한 오류 코드를 나타냅니다.

### <a name="remarks"></a>설명

특정 멤버 함수에서 오류가 발생 했음을 나타내는 경우를 `GetLastError` 호출 하 여 적절 한 오류 코드를 검색 합니다. 해당 하는 오류 코드 목록은 개별 멤버 함수 설명을 참조 하십시오.

오류 코드에 대 한 자세한 내용은 [Windows 소켓 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)를 참조 하세요.

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a> CAsyncSocket:: GetPeerName

이 소켓이 연결 된 피어 소켓의 주소를 가져오려면이 멤버 함수를 호출 합니다.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>매개 변수

*rPeerAddress*<br/>
`CString`점으로 구분 된 숫자 IP 주소를 받는 개체에 대 한 참조입니다.

*rPeerPort*<br/>
포트를 저장 하는 UINT에 대 한 참조입니다.

*lpSockAddr*<br/>
피어 소켓의 이름을 수신 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다.

*lpSockAddrLen*<br/>
*LpSockAddr* 의 주소 길이에 대 한 포인터입니다 (바이트). 반환 시 *lpSockAddrLen* 인수는 반환 된 *lpSockAddr* 의 실제 크기 (바이트)를 포함 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 크지 않습니다.

- WSAEINPROGRESS Windows 소켓 호출을 차단 하는 중입니다.

- 소켓이 연결 되지 WSAENOTCONN.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

IPv6 주소를 처리 하려면 [Casyncsocket:: GetPeerNameEx](#getpeernameex)를 사용 합니다.

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a> CAsyncSocket:: GetPeerNameEx

이 멤버 함수를 호출 하 여이 소켓이 연결 된 피어 소켓의 주소를 가져옵니다 (IPv6 주소 처리).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>매개 변수

*rPeerAddress*<br/>
`CString`점으로 구분 된 숫자 IP 주소를 받는 개체에 대 한 참조입니다.

*rPeerPort*<br/>
포트를 저장 하는 UINT에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 크지 않습니다.

- WSAEINPROGRESS Windows 소켓 호출을 차단 하는 중입니다.

- 소켓이 연결 되지 WSAENOTCONN.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

이 함수는 IPv6 주소와 이전 프로토콜을 모두 처리 한다는 점을 제외 하 고 [Casyncsocket:: GetPeerName](#getpeername) 과 동일 합니다.

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a> CAsyncSocket:: GetSockName

이 멤버 함수를 호출 하 여 소켓의 로컬 이름을 가져옵니다.

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>매개 변수

*rSocketAddress*<br/>
`CString`점으로 구분 된 숫자 IP 주소를 받는 개체에 대 한 참조입니다.

*rSocketPort*<br/>
포트를 저장 하는 UINT에 대 한 참조입니다.

*lpSockAddr*<br/>
소켓의 주소를 수신 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다.

*lpSockAddrLen*<br/>
*LpSockAddr* 의 주소 길이에 대 한 포인터입니다 (바이트).

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 크지 않습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEINVAL가 있는 주소에 바인딩되지 않은 소켓 `Bind` 입니다.

### <a name="remarks"></a>설명

이 호출은를 먼저 수행 하지 않고 호출 하는 경우에 특히 유용 합니다 `Connect` `Bind` .이 호출은 시스템에 의해 설정 된 로컬 연결을 확인할 수 있는 유일한 수단을 제공 합니다.

IPv6 주소를 처리 하려면 [Casyncsocket:: GetSockNameEx](#getsocknameex) 를 사용 합니다.

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a> CAsyncSocket:: GetSockNameEx

이 멤버 함수를 호출 하 여 소켓 (IPv6 주소 처리)의 로컬 이름을 가져옵니다.

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>매개 변수

*rSocketAddress*<br/>
`CString`점으로 구분 된 숫자 IP 주소를 받는 개체에 대 한 참조입니다.

*rSocketPort*<br/>
포트를 저장 하는 UINT에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 크지 않습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEINVAL가 있는 주소에 바인딩되지 않은 소켓 `Bind` 입니다.

### <a name="remarks"></a>설명

이 호출은 IPv6 주소와 이전 프로토콜을 모두 처리 한다는 점을 제외 하 고 [Casyncsocket:: GetSockName](#getsockname) 와 동일 합니다.

이 호출은를 먼저 수행 하지 않고 호출 하는 경우에 특히 유용 합니다 `Connect` `Bind` .이 호출은 시스템에 의해 설정 된 로컬 연결을 확인할 수 있는 유일한 수단을 제공 합니다.

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a> CAsyncSocket:: GetSockOpt

소켓 옵션을 검색 하려면이 멤버 함수를 호출 합니다.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>매개 변수

*nOptionName*<br/>
값을 검색할 소켓 옵션입니다.

*lpOptionValue*<br/>
요청 된 옵션의 값이 반환 될 버퍼에 대 한 포인터입니다. 선택한 옵션과 연결 된 값이 buffer *lpOptionValue* 에서 반환 됩니다. *LpOptionLen* 가 가리키는 정수는 원래이 버퍼의 크기 (바이트)를 포함 해야 합니다. 반환 될 때 반환 되는 값의 크기로 설정 됩니다. SO_LINGER의 경우이는 구조의 크기가 됩니다 `LINGER` . 다른 모든 옵션의 경우 **`int`** 옵션에 따라 BOOL 또는의 크기가 됩니다. 설명 섹션에서 옵션 및 해당 크기의 목록을 참조 하세요.

*lpOptionLen*<br/>
*LpOptionValue* 버퍼의 크기에 대 한 포인터입니다 (바이트).

*n 수준*<br/>
옵션이 정의 되는 수준입니다. 유일 하 게 지원 되는 수준은 SOL_SOCKET 및 IPPROTO_TCP입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 옵션을로 설정 하지 않은 경우 `SetSockOpt` `GetSockOpt` 은 옵션에 대 한 기본값을 반환 합니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpOptionLen* 인수가 잘못 되었습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAENOPROTOOPT 옵션을 알 수 없거나 지원 되지 않습니다. 특히 SOCK_STREAM 형식의 소켓에서는 SO_BROADCAST 지원 되지 않지만, SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER 및 SO_OOBINLINE는 SOCK_DGRAM 형식의 소켓에서 지원 되지 않습니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

`GetSockOpt` 모든 형식의 소켓과 연결 된 소켓 옵션에 대 한 현재 값을 검색 하 고 그 결과를 *lpOptionValue* 에 저장 합니다. 옵션은 패킷 라우팅, 대역 외 데이터 전송 등의 소켓 작업에 영향을 줍니다.

에 대해 지원 되는 옵션은 다음과 같습니다 `GetSockOpt` . 형식은 *lpOptionValue* 로 주소를 지정 하는 데이터 형식을 식별 합니다. TCP_NODELAY 옵션은 수준 IPPROTO_TCP를 사용 합니다. 다른 모든 옵션은 수준 SOL_SOCKET를 사용 합니다.

|값|Type|의미|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|소켓이 수신 대기 중입니다.|
|SO_BROADCAST|BOOL|소켓은 브로드캐스트 메시지의 전송에 대해 구성 됩니다.|
|SO_DEBUG|BOOL|디버깅을 사용할 수 있습니다.|
|SO_DONTLINGER|BOOL|True 이면 SO_LINGER 옵션을 사용할 수 없습니다.|
|SO_DONTROUTE|BOOL|라우팅이 사용 하지 않도록 설정 되었습니다.|
|SO_ERROR|**`int`**|오류 상태를 검색 하 고 선택을 취소 합니다.|
|SO_KEEPALIVE|BOOL|연결 유지를 보내고 있습니다.|
|SO_LINGER|`struct LINGER`|현재 링거 옵션을 반환 합니다.|
|SO_OOBINLINE|BOOL|Out-of-band 데이터는 일반 데이터 스트림에서 수신 됩니다.|
|SO_RCVBUF|int|수신에 대 한 버퍼 크기입니다.|
|SO_REUSEADDR|BOOL|소켓이 이미 사용 중인 주소에 바인딩될 수 있습니다.|
|SO_SNDBUF|**`int`**|보낼 버퍼 크기입니다.|
|SO_TYPE|**`int`**|소켓 형식입니다 (예: SOCK_STREAM).|
|TCP_NODELAY|BOOL|보내기 통합을 위해 Nagle 알고리즘을 비활성화합니다.|

에 대해 지원 되지 않는 BSD (Berkeley Software 배포판) 옵션 `GetSockOpt` 은 다음과 같습니다.

|값|Type|의미|
|-----------|----------|-------------|
|SO_RCVLOWAT|**`int`**|낮은 워터 마크를 받습니다.|
|SO_RCVTIMEO|**`int`**|수신 제한 시간입니다.|
|SO_SNDLOWAT|**`int`**|낮은 워터 마크를 보냅니다.|
|SO_SNDTIMEO|**`int`**|송신 제한 시간입니다.|
|IP_OPTIONS||IP 헤더의 옵션을 가져옵니다.|
|TCP_MAXSEG|**`int`**|TCP 최대 세그먼트 크기를 가져옵니다.|

`GetSockOpt`지원 되지 않는 옵션을 사용 하 여를 호출 하면에서 반환 되는 오류 코드 WSAENOPROTOOPT이 반환 됩니다 `GetLastError` .

## <a name="casyncsocketioctl"></a><a name="ioctl"></a> CAsyncSocket:: IOCtl

소켓의 모드를 제어 하려면이 멤버 함수를 호출 합니다.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>매개 변수

*lCommand*<br/>
소켓에서 수행할 명령입니다.

*lpArgument*<br/>
*Lcommand* 에 대 한 매개 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEINVAL *Lcommand* 가 유효한 명령이 아니거나, *LpArgument* 가 *lcommand* 에 사용할 수 있는 매개 변수가 아니거나, 제공 된 소켓 유형에 해당 명령이 적용 되지 않습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

이 루틴은 모든 상태의 모든 소켓에서 사용할 수 있습니다. 프로토콜 및 통신 하위 시스템과는 독립적으로 소켓과 연결 된 운영 매개 변수를 가져오거나 검색 하는 데 사용 됩니다. 지원되는 명령은 다음과 같습니다.

- FIONBIO은 소켓에서 비블로킹 모드를 사용 하거나 사용 하지 않도록 설정 합니다. *LpArgument* 매개 변수는 `DWORD` 비블로킹 모드를 사용 하도록 설정 하는 경우 0이 아니고 사용 하지 않도록 설정 된 경우 0이 아닌을 가리킵니다. `AsyncSelect`가 소켓에서 실행 된 경우 WSAEINVAL를 사용 하 여 소켓을 `IOCtl` 차단 모드로 다시 설정 하려고 하면 실패 합니다. 소켓을 차단 모드로 설정 하 고 WSAEINVAL 오류를 방지 하려면 응용 프로그램에서 먼저 LEvent 매개 변수를 0으로 설정 하 여를 호출 하 고를 호출 하 여를 사용 하지 않도록 설정 해야 `AsyncSelect` `AsyncSelect`  `IOCtl` 합니다.

- FIONREAD는이 소켓에서 한 번의 호출로 읽을 수 있는 최대 바이트 수를 결정 합니다 `Receive` . *LpArgument* 매개 변수는 `DWORD` 에서 결과를 저장 하는를 가리킵니다 `IOCtl` . 이 소켓이 SOCK_STREAM 형식이 면 FIONREAD는 단일에서 읽을 수 있는 총 데이터 양을 반환 합니다 `Receive` . 일반적으로이 값은 소켓에서 큐에 대기 중인 총 데이터 양과 동일 합니다. 이 소켓이 SOCK_DGRAM 형식이 면 FIONREAD는 소켓에서 대기 중인 첫 번째 데이터 그램의 크기를 반환 합니다.

- SIOCATMARK는 대역 외 데이터를 모두 읽 었는 지 여부를 확인 합니다. 이는 대역 외 데이터 (SO_OOBINLINE)의 인라인 수신에 대해 구성 된 SOCK_STREAM 형식의 소켓에만 적용 됩니다. 읽기 대기 중인 대역 외 데이터가 없으면 작업은 0이 아닌 값을 반환 합니다. 그렇지 않으면 0을 반환 하 고, `Receive` `ReceiveFrom` 소켓에서 다음 또는 수행 된 작업은 "mark" 앞에 오는 데이터의 일부 또는 전체를 검색 합니다. 응용 프로그램은 SIOCATMARK 작업을 사용 하 여 데이터가 남아 있는지 확인 해야 합니다. "긴급" (대역 외) 데이터 이전에 일반 데이터가 있는 경우 순서 대로 수신 됩니다. `Receive`또는는 `ReceiveFrom` 동일한 호출에서 대역 외 및 일반 데이터를 혼합 하지 않습니다. *LpArgument* 매개 변수는 `DWORD` 에서 결과를 저장 하는를 가리킵니다 `IOCtl` .

이 함수는 `ioctl()` Berkeley 소켓에서 사용 되는의 하위 집합입니다. 특히 FIOASYNC와 동일한 명령이 없으며 SIOCATMARK는 지원 되는 유일한 소켓 수준 명령입니다.

## <a name="casyncsocketlisten"></a><a name="listen"></a> CAsyncSocket:: 수신 대기

들어오는 연결 요청을 수신 하려면이 멤버 함수를 호출 합니다.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>매개 변수

*nConnectionBacklog*<br/>
보류 중인 연결의 큐가 증가할 수 있는 최대 길이입니다. 유효한 범위는 1에서 5 사이입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEADDRINUSE 사용 중인 주소에서 수신 대기 하려고 했습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAEINVAL 소켓이 바인딩되어 있지 않거나 `Bind` 이미 연결 되어 있습니다.

- WSAEISCONN 소켓이 이미 연결 되어 있습니다.

- WSAEMFILE 더 이상 파일 설명자를 사용할 수 없습니다.

- WSAENOBUFS 버퍼 공간을 사용할 수 없습니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP 참조 된 소켓이 작업을 지 원하는 형식이 아닙니다 `Listen` .

### <a name="remarks"></a>설명

연결을 허용 하기 위해 먼저 소켓이로 생성 되 고, `Create` 들어오는 연결에 대 한 백로그가로 지정 된 `Listen` 다음,와의 연결이 허용 됩니다 `Accept` . `Listen` 연결을 지 원하는 소켓, 즉 SOCK_STREAM 형식의 경우에만 적용 됩니다. 이 소켓은 들어오는 연결이 승인 되 고 프로세스에 의해 보류 중인 보류 중인 보류 중인 "수동" 모드로 전환 됩니다.

이 함수는 일반적으로 한 번에 둘 이상의 연결 요청을 포함할 수 있는 서버 (또는 연결을 허용 하려는 응용 프로그램)에서 사용 됩니다. 큐 가득 찬 연결 요청이 도착 하면 클라이언트에서 WSAECONNREFUSED 표시와 함께 오류가 발생 합니다.

`Listen` 사용 가능한 포트 (설명자)가 없는 경우 균형점 기능을 계속 시도 합니다. 큐를 비울 때까지 연결을 허용 합니다. 포트를 사용할 수 있는 경우 나중에 또는에 대 한 호출이 `Listen` `Accept` 큐를 현재 또는 가장 최근 "백로그"로 다시 연결 하 고, 가능한 경우 들어오는 연결에 대 한 수신을 다시 시작 합니다.

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a> CAsyncSocket:: m_hSocket

이 개체로 캡슐화 된 소켓의 소켓 핸들을 포함 `CAsyncSocket` 합니다.

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a> CAsyncSocket:: OnAccept

[Accept](#accept) 멤버 함수를 호출 하 여 보류 중인 연결 요청을 수락할 수 있음을 수신 대기 소켓에 알리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>매개 변수

*nErrorCode*<br/>
소켓에서 가장 최근의 오류입니다. 다음 오류 코드는 멤버 함수에 적용 됩니다 `OnAccept` .

- **0** 함수가 성공적으로 실행 되었습니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

### <a name="remarks"></a>설명

자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

## <a name="casyncsocketonclose"></a><a name="onclose"></a> CAsyncSocket:: OnClose

이 소켓에 연결 된 소켓이 프로세스에 의해 닫 혔 음을 알리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>매개 변수

*nErrorCode*<br/>
소켓에서 가장 최근의 오류입니다. 다음 오류 코드는 멤버 함수에 적용 됩니다 `OnClose` .

- **0** 함수가 성공적으로 실행 되었습니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAECONNRESET 원격 측에 의해 연결이 다시 설정 되었습니다.

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 연결이 중단 되었습니다.

### <a name="remarks"></a>설명

자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a> CAsyncSocket:: OnConnect

성공적으로 또는 오류가 발생 한 경우이 연결 소켓에 연결 시도가 완료 되었음을 알리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>매개 변수

*nErrorCode*<br/>
소켓에서 가장 최근의 오류입니다. 다음 오류 코드는 멤버 함수에 적용 됩니다 `OnConnect` .

- **0** 함수가 성공적으로 실행 되었습니다.

- WSAEADDRINUSE 지정 된 주소가 이미 사용 중입니다.

- WSAEADDRNOTAVAIL 지정 된 주소를 로컬 컴퓨터에서 사용할 수 없습니다.

- 지정 된 패밀리의 WSAEAFNOSUPPORT 주소는이 소켓과 함께 사용할 수 없습니다.

- 연결 시도가 강제로 거부 WSAECONNREFUSED.

- WSAEDESTADDRREQ 대상 주소가 필요 합니다.

- WSAEFAULT *lpSockAddrLen* 인수가 잘못 되었습니다.

- WSAEINVAL 소켓이 이미 주소에 바인딩되어 있습니다.

- WSAEISCONN 소켓이 이미 연결 되어 있습니다.

- WSAEMFILE 더 이상 파일 설명자를 사용할 수 없습니다.

- WSAENETUNREACH이 호스트에서 네트워크에 연결할 수 없습니다.

- WSAENOBUFS 버퍼 공간을 사용할 수 없습니다. 소켓을 연결할 수 없는 경우

- 소켓이 연결 되지 WSAENOTCONN.

- WSAENOTSOCK 설명자는 소켓이 아닌 파일입니다.

- 연결을 설정 하지 않고 연결 시도 시간이 WSAETIMEDOUT.

### <a name="remarks"></a>설명

> [!NOTE]
> [CSocket](../../mfc/reference/csocket-class.md)에서 `OnConnect` 알림 함수는 호출 되지 않습니다. 연결의 경우에는를 호출 하기만 하면 됩니다 `Connect` .이는 연결이 완료 될 때 (성공 또는 오류 발생)를 반환 합니다. 연결 알림이 처리 되는 방법은 MFC 구현에 자세히 설명 되어 있습니다.

자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a> CAsyncSocket:: OnOutOfBandData

송신 소켓에 보낼 대역 외 데이터가 있음을 수신 소켓에 알리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>매개 변수

*nErrorCode*<br/>
소켓에서 가장 최근의 오류입니다. 다음 오류 코드는 멤버 함수에 적용 됩니다 `OnOutOfBandData` .

- **0** 함수가 성공적으로 실행 되었습니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

### <a name="remarks"></a>설명

대역외 데이터는 SOCK_STREAM 형식의 연결 된 각 소켓 쌍과 연결 된 논리적으로 독립적인 채널입니다. 채널은 일반적으로 긴급 한 데이터를 보내는 데 사용 됩니다.

MFC는 대역 외 데이터를 지원 하지만 클래스의 사용자 `CAsyncSocket` 는 사용 하지 않는 것이 좋습니다. 이러한 데이터를 전달 하기 위한 두 번째 소켓을 만드는 것이 더 쉬운 방법입니다. 대역외 데이터에 대 한 자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a> CAsyncSocket:: OnReceive

이 소켓에 멤버 함수를 호출 하 여 검색할 수 있는 데이터가 있음을이 소켓에 알리기 위해 프레임 워크에서 호출 `Receive` 됩니다.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>매개 변수

*nErrorCode*<br/>
소켓에서 가장 최근의 오류입니다. 다음 오류 코드는 멤버 함수에 적용 됩니다 `OnReceive` .

- **0** 함수가 성공적으로 실행 되었습니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

### <a name="remarks"></a>설명

자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a> CAsyncSocket:: OnSend

이제 멤버 함수를 호출 하 여 데이터를 보낼 수 있음을 소켓에 알리기 위해 프레임 워크에서 호출 `Send` 됩니다.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>매개 변수

*nErrorCode*<br/>
소켓에서 가장 최근의 오류입니다. 다음 오류 코드는 멤버 함수에 적용 됩니다 `OnSend` .

- **0** 함수가 성공적으로 실행 되었습니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

### <a name="remarks"></a>설명

자세한 내용은 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a> CAsyncSocket:: operator =

개체에 새 값을 할당 `CAsyncSocket` 합니다.

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
기존 개체에 대 한 참조 `CAsyncSocket` 입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하 여 기존 `CAsyncSocket` 개체를 다른 `CAsyncSocket` 개체에 복사 합니다.

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a> CAsyncSocket:: operator SOCKET

이 연산자를 사용 하 여 개체의 소켓 핸들을 검색 `CAsyncSocket` 합니다.

```
operator SOCKET() const;
```

### <a name="return-value"></a>반환 값

성공 하면 소켓 개체의 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

핸들을 사용 하 여 Windows Api를 직접 호출할 수 있습니다.

## <a name="casyncsocketreceive"></a><a name="receive"></a> CAsyncSocket:: Receive

소켓에서 데이터를 수신 하려면이 멤버 함수를 호출 합니다.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
들어오는 데이터에 대 한 버퍼입니다.

*nBufLen*<br/>
*Lpbuf* 의 길이 (바이트)입니다.

*nFlags*<br/>
호출을 수행 하는 방법을 지정 합니다. 이 함수의 의미 체계는 소켓 옵션 및 *Nflags* 매개 변수에 의해 결정 됩니다. 후자는 c + + **또는** 연산자와 다음 값을 결합 하 여 생성 됩니다.

- 들어오는 데이터를 피킹 (Peeking)을 MSG_PEEK 합니다. 데이터가 버퍼에 복사 되지만 입력 큐에서 제거 되지 않습니다.

- MSG_OOB 대역 외 데이터를 처리 합니다.

### <a name="return-value"></a>반환 값

오류가 발생 하지 않으면 `Receive` 받은 바이트 수를 반환 합니다. 연결이 닫힌 경우 0을 반환 합니다. 그렇지 않으면 SOCKET_ERROR 값이 반환 되 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- 소켓이 연결 되지 WSAENOTCONN.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP MSG_OOB 지정 되었지만 소켓이 SOCK_STREAM 형식이 아닙니다.

- WSAESHUTDOWN 소켓이 종료 되었습니다. `Receive` `ShutDown` 가 0 또는 2로 설정 된 *경우를 호출* 하 고 나면 소켓에서를 호출할 수 없습니다.

- WSAEWOULDBLOCK는 소켓이 비블로킹 상태로 표시 되 고 `Receive` 작업은 차단 됩니다.

- WSAEMSGSIZE 데이터 그램이 너무 커서 지정 된 버퍼에 맞지 않아 잘렸습니다.

- WSAEINVAL 소켓이 바인딩되지 않았습니다 `Bind` .

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 가상 회로가 중단 되었습니다.

- WSAECONNRESET 가상 회로가 원격 측에 의해 다시 설정 되었습니다.

### <a name="remarks"></a>설명

이 함수는 연결 된 스트림 또는 데이터 그램 소켓에 사용 되며 들어오는 데이터를 읽는 데 사용 됩니다.

SOCK_STREAM 형식의 소켓의 경우 제공 된 버퍼의 크기까지 현재 사용할 수 있는 정보는 반환 됩니다. 대역 외 데이터의 인라인 수신에 대해 소켓이 구성 된 경우 (소켓 옵션 SO_OOBINLINE) 대역 외 데이터는 읽지 않은 경우 out-of-band 데이터만 반환 됩니다. 응용 프로그램은 `IOCtlSIOCATMARK` 옵션 또는 [OnOutOfBandData](#onoutofbanddata) 를 사용 하 여 더 이상 대역 외 데이터를 읽을 수 있는지 여부를 결정할 수 있습니다.

데이터 그램 소켓의 경우 첫 번째 큐에 넣은 데이터 그램에서 제공 된 버퍼 크기까지 데이터를 추출 합니다. 데이터 그램이 제공 된 버퍼 보다 큰 경우 버퍼는 데이터 그램의 첫 번째 부분으로 채워지고 초과 데이터는 손실 되며 `Receive` WSAEMSGSIZE로 설정 된 오류 코드와 함께 SOCKET_ERROR 값을 반환 합니다. 소켓에서 들어오는 데이터를 사용할 수 없는 경우 WSAEWOULDBLOCK로 설정 된 오류 코드와 함께 SOCKET_ERROR 값이 반환 됩니다. [OnReceive](#onreceive) callback 함수를 사용 하 여 더 많은 데이터가 도착할 때를 확인할 수 있습니다.

소켓이 SOCK_STREAM 형식이 고 원격 쪽에서 연결을 정상적으로 종료 한 경우는 `Receive` 0 바이트가 수신 되 면 즉시 완료 됩니다. 연결이 다시 설정 된 경우 `Receive` WSAECONNRESET 오류와 함께 실패 합니다.

`Receive`[Casyncsocket:: OnReceive](#onreceive) 가 호출 될 때마다 한 번만 호출 해야 합니다.

### <a name="example"></a>예제

  [Casyncsocket:: OnReceive](#onreceive)에 대 한 예제를 참조 하세요.

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a> CAsyncSocket:: ReceiveFrom

이 멤버 함수를 호출 하 여 데이터 그램을 받고 원본 주소를 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체 또는 *rsocketaddress* 에 저장 합니다.

```
int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);

int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
들어오는 데이터에 대 한 버퍼입니다.

*nBufLen*<br/>
*Lpbuf* 의 길이 (바이트)입니다.

*rSocketAddress*<br/>
`CString`점으로 구분 된 숫자 IP 주소를 받는 개체에 대 한 참조입니다.

*rSocketPort*<br/>
포트를 저장 하는 UINT에 대 한 참조입니다.

*lpSockAddr*<br/>
반환 될 때 원본 주소를 보유 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다.

*lpSockAddrLen*<br/>
*LpSockAddr* 에서 소스 주소의 길이에 대 한 포인터입니다 (바이트).

*nFlags*<br/>
호출을 수행 하는 방법을 지정 합니다. 이 함수의 의미 체계는 소켓 옵션 및 *Nflags* 매개 변수에 의해 결정 됩니다. 후자는 c + + **또는** 연산자와 다음 값을 결합 하 여 생성 됩니다.

- 들어오는 데이터를 피킹 (Peeking)을 MSG_PEEK 합니다. 데이터가 버퍼에 복사 되지만 입력 큐에서 제거 되지 않습니다.

- MSG_OOB 대역 외 데이터를 처리 합니다.

### <a name="return-value"></a>반환 값

오류가 발생 하지 않으면 `ReceiveFrom` 받은 바이트 수를 반환 합니다. 연결이 닫힌 경우 0을 반환 합니다. 그렇지 않으면 SOCKET_ERROR 값이 반환 되 고를 호출 하 여 특정 오류 코드를 검색할 수 있습니다 `GetLastError` . 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 잘못 되었습니다. *lpSockAddr* 버퍼가 너무 작아서 피어 주소를 수용할 수 없습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAEINVAL 소켓이 바인딩되지 않았습니다 `Bind` .

- WSAENOTCONN 소켓이 연결 되지 않았습니다 (SOCK_STREAM에만 해당).

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP MSG_OOB 지정 되었지만 소켓이 SOCK_STREAM 형식이 아닙니다.

- WSAESHUTDOWN 소켓이 종료 되었습니다. `ReceiveFrom` `ShutDown` 가 0 또는 2로 설정 된 *경우를 호출* 하 고 나면 소켓에서를 호출할 수 없습니다.

- WSAEWOULDBLOCK는 소켓이 비블로킹 상태로 표시 되 고 `ReceiveFrom` 작업은 차단 됩니다.

- WSAEMSGSIZE 데이터 그램이 너무 커서 지정 된 버퍼에 맞지 않아 잘렸습니다.

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 가상 회로가 중단 되었습니다.

- WSAECONNRESET 가상 회로가 원격 측에 의해 다시 설정 되었습니다.

### <a name="remarks"></a>설명

이 함수는 연결 된 소켓에서 들어오는 데이터를 읽고 데이터가 전송 된 주소를 캡처하는 데 사용 됩니다.

IPv6 주소를 처리 하려면 [Casyncsocket:: ReceiveFromEx](#receivefromex)를 사용 합니다.

SOCK_STREAM 형식의 소켓의 경우 제공 된 버퍼의 크기까지 현재 사용할 수 있는 정보는 반환 됩니다. 대역 외 데이터의 인라인 수신에 대해 소켓이 구성 된 경우 (소켓 옵션 SO_OOBINLINE) 대역 외 데이터는 읽지 않은 경우 out-of-band 데이터만 반환 됩니다. 응용 프로그램은 옵션을 사용 `IOCtlSIOCATMARK` 하거나, `OnOutOfBandData` 대역 외 데이터를 계속 읽을 수 있는지 여부를 결정할 수 있습니다. *LpSockAddr* 및 *lpSockAddrLen* 매개 변수는 SOCK_STREAM 소켓에 대해 무시 됩니다.

데이터 그램 소켓의 경우 첫 번째 큐에 넣은 데이터 그램에서 제공 된 버퍼 크기까지 데이터를 추출 합니다. 데이터 그램이 제공 된 버퍼 보다 큰 경우 버퍼는 메시지의 첫 번째 부분으로 채워지고 초과 데이터는 손실 되며 `ReceiveFrom` WSAEMSGSIZE로 설정 된 오류 코드와 함께 SOCKET_ERROR 값을 반환 합니다.

*LpSockAddr* 가 0이 아니고 소켓이 SOCK_DGRAM 형식이 면 데이터를 보낸 소켓의 네트워크 주소가 해당 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체로 복사 됩니다. *LpSockAddrLen* 가 가리키는 값은이 구조체의 크기로 초기화 되며 반환 시 수정 되어 저장 된 주소의 실제 크기를 표시 합니다. 소켓에서 들어오는 데이터를 사용할 수 없는 경우에는 `ReceiveFrom` 소켓이 비블로킹 되지 않는 한 호출이 데이터가 도착할 때까지 대기 합니다. 이 경우 WSAEWOULDBLOCK로 설정 된 오류 코드와 함께 SOCKET_ERROR 값이 반환 됩니다. `OnReceive`콜백은 추가 데이터가 도착할 때를 결정 하는 데 사용할 수 있습니다.

소켓이 SOCK_STREAM 형식이 고 원격 쪽에서 연결을 정상적으로 종료 한 경우는 `ReceiveFrom` 0 바이트가 수신 되 면 즉시 완료 됩니다.

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a> CAsyncSocket:: ReceiveFromEx

이 멤버 함수를 호출 하 여 데이터 그램을 받고 원본 주소를 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체 또는 *rsocketaddress* (IPv6 주소 처리)에 저장 합니다.

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
들어오는 데이터에 대 한 버퍼입니다.

*nBufLen*<br/>
*Lpbuf* 의 길이 (바이트)입니다.

*rSocketAddress*<br/>
`CString`점으로 구분 된 숫자 IP 주소를 받는 개체에 대 한 참조입니다.

*rSocketPort*<br/>
포트를 저장 하는 UINT에 대 한 참조입니다.

*nFlags*<br/>
호출을 수행 하는 방법을 지정 합니다. 이 함수의 의미 체계는 소켓 옵션 및 *Nflags* 매개 변수에 의해 결정 됩니다. 후자는 c + + **또는** 연산자와 다음 값을 결합 하 여 생성 됩니다.

- 들어오는 데이터를 피킹 (Peeking)을 MSG_PEEK 합니다. 데이터가 버퍼에 복사 되지만 입력 큐에서 제거 되지 않습니다.

- MSG_OOB 대역 외 데이터를 처리 합니다.

### <a name="return-value"></a>반환 값

오류가 발생 하지 않으면 `ReceiveFromEx` 받은 바이트 수를 반환 합니다. 연결이 닫힌 경우 0을 반환 합니다. 그렇지 않으면 SOCKET_ERROR 값이 반환 되 고를 호출 하 여 특정 오류 코드를 검색할 수 있습니다 `GetLastError` . 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpSockAddrLen* 인수가 잘못 되었습니다. *lpSockAddr* 버퍼가 너무 작아서 피어 주소를 수용할 수 없습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAEINVAL 소켓이 바인딩되지 않았습니다 `Bind` .

- WSAENOTCONN 소켓이 연결 되지 않았습니다 (SOCK_STREAM에만 해당).

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP MSG_OOB 지정 되었지만 소켓이 SOCK_STREAM 형식이 아닙니다.

- WSAESHUTDOWN 소켓이 종료 되었습니다. `ReceiveFromEx` `ShutDown` 가 0 또는 2로 설정 된 *경우를 호출* 하 고 나면 소켓에서를 호출할 수 없습니다.

- WSAEWOULDBLOCK는 소켓이 비블로킹 상태로 표시 되 고 `ReceiveFromEx` 작업은 차단 됩니다.

- WSAEMSGSIZE 데이터 그램이 너무 커서 지정 된 버퍼에 맞지 않아 잘렸습니다.

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 가상 회로가 중단 되었습니다.

- WSAECONNRESET 가상 회로가 원격 측에 의해 다시 설정 되었습니다.

### <a name="remarks"></a>설명

이 함수는 연결 된 소켓에서 들어오는 데이터를 읽고 데이터가 전송 된 주소를 캡처하는 데 사용 됩니다.

이 함수는 IPv6 주소와 이전 프로토콜을 모두 처리 한다는 점을 제외 하 고 [Casyncsocket:: ReceiveFrom](#receivefrom) 와 동일 합니다.

SOCK_STREAM 형식의 소켓의 경우 제공 된 버퍼의 크기까지 현재 사용할 수 있는 정보는 반환 됩니다. 대역 외 데이터의 인라인 수신에 대해 소켓이 구성 된 경우 (소켓 옵션 SO_OOBINLINE) 대역 외 데이터는 읽지 않은 경우 out-of-band 데이터만 반환 됩니다. 응용 프로그램은 옵션을 사용 `IOCtlSIOCATMARK` 하거나, `OnOutOfBandData` 대역 외 데이터를 계속 읽을 수 있는지 여부를 결정할 수 있습니다. *LpSockAddr* 및 *lpSockAddrLen* 매개 변수는 SOCK_STREAM 소켓에 대해 무시 됩니다.

데이터 그램 소켓의 경우 첫 번째 큐에 넣은 데이터 그램에서 제공 된 버퍼 크기까지 데이터를 추출 합니다. 데이터 그램이 제공 된 버퍼 보다 큰 경우 버퍼는 메시지의 첫 번째 부분으로 채워지고 초과 데이터는 손실 되며 `ReceiveFromEx` WSAEMSGSIZE로 설정 된 오류 코드와 함께 SOCKET_ERROR 값을 반환 합니다.

*LpSockAddr* 가 0이 아니고 소켓이 SOCK_DGRAM 형식이 면 데이터를 보낸 소켓의 네트워크 주소가 해당 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체로 복사 됩니다. *LpSockAddrLen* 가 가리키는 값은이 구조체의 크기로 초기화 되며 반환 시 수정 되어 저장 된 주소의 실제 크기를 표시 합니다. 소켓에서 들어오는 데이터를 사용할 수 없는 경우에는 `ReceiveFromEx` 소켓이 비블로킹 되지 않는 한 호출이 데이터가 도착할 때까지 대기 합니다. 이 경우 WSAEWOULDBLOCK로 설정 된 오류 코드와 함께 SOCKET_ERROR 값이 반환 됩니다. `OnReceive`콜백은 추가 데이터가 도착할 때를 결정 하는 데 사용할 수 있습니다.

소켓이 SOCK_STREAM 형식이 고 원격 쪽에서 연결을 정상적으로 종료 한 경우는 `ReceiveFromEx` 0 바이트가 수신 되 면 즉시 완료 됩니다.

## <a name="casyncsocketsend"></a><a name="send"></a> CAsyncSocket:: Send

이 멤버 함수를 호출 하 여 연결 된 소켓에서 데이터를 전송 합니다.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
전송할 데이터를 포함 하는 버퍼입니다.

*nBufLen*<br/>
*Lpbuf* 의 데이터 길이 (바이트)입니다.

*nFlags*<br/>
호출을 수행 하는 방법을 지정 합니다. 이 함수의 의미 체계는 소켓 옵션 및 *Nflags* 매개 변수에 의해 결정 됩니다. 후자는 c + + **또는** 연산자와 다음 값을 결합 하 여 생성 됩니다.

- MSG_DONTROUTE는 데이터에 라우팅이 적용 되지 않도록 지정 합니다. Windows 소켓 공급자는이 플래그를 무시 하도록 선택할 수 있습니다.

- MSG_OOB 대역 외 데이터를 전송 합니다 (SOCK_STREAM에만 해당).

### <a name="return-value"></a>반환 값

오류가 발생 하지 않으면 `Send` 전송 된 총 문자 수를 반환 합니다. 이는 *Nbuflen* 이 나타내는 숫자 보다 적을 수 있습니다. 그렇지 않으면 SOCKET_ERROR 값이 반환 되 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- 요청 된 주소가 브로드캐스트 주소 WSAEACCES 적절 한 플래그가 설정 되지 않았습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAEFAULT *Lpbuf* 인수가 사용자 주소 공간의 올바른 부분에 없습니다.

- WSAENETRESET Windows 소켓 구현에서 연결을 삭제 했으므로 연결을 다시 설정 해야 합니다.

- WSAENOBUFS는 Windows 소켓 구현에서 버퍼 교착 상태를 보고 합니다.

- 소켓이 연결 되지 WSAENOTCONN.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP MSG_OOB 지정 되었지만 소켓이 SOCK_STREAM 형식이 아닙니다.

- WSAESHUTDOWN 소켓이 종료 되었습니다. `Send` `ShutDown` 가 1 또는 2로 설정 된 경우를 사용 하 여를 호출한  후 소켓에서를 호출할 수 없습니다.

- WSAEWOULDBLOCK는 소켓이 비블로킹 상태로 표시 되 고 요청 된 작업이 차단 됩니다.

- WSAEMSGSIZE는 SOCK_DGRAM 유형이 며, 데이터 그램이 Windows 소켓 구현에서 지 원하는 최대 크기 보다 큽니다.

- WSAEINVAL 소켓이 바인딩되지 않았습니다 `Bind` .

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 가상 회로가 중단 되었습니다.

- WSAECONNRESET 가상 회로가 원격 측에 의해 다시 설정 되었습니다.

### <a name="remarks"></a>설명

`Send` 는 연결 된 스트림 또는 데이터 그램 소켓에서 나가는 데이터를 쓰는 데 사용 됩니다. 데이터 그램 소켓의 경우 기본 서브넷의 최대 IP 패킷 크기를 초과 하지 않도록 주의를 기울여야 합니다 .이 크기는 `iMaxUdpDg` 에서 반환 하는 [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) 구조의 요소에 의해 제공 됩니다 `AfxSocketInit` . 데이터가 너무 길어서 기본 프로토콜을 통해 원자 단위로 전달할 수 없는 경우 WSAEMSGSIZE 오류는를 통해 반환 되 `GetLastError` 고 데이터가 전송 되지 않습니다.

데이터 그램 소켓의 경우 성공적으로 완료 되 면 `Send` 데이터가 성공적으로 배달 된 것으로 표시 되지 않습니다.

`CAsyncSocket`SOCK_STREAM 형식의 개체에서 기록 되는 바이트 수는 로컬 및 외부 호스트의 버퍼 가용성에 따라 1에서 요청 된 길이 사이에 있을 수 있습니다.

### <a name="example"></a>예제

  [Casyncsocket:: OnSend](#onsend)의 예제를 참조 하세요.

## <a name="casyncsocketsendto"></a><a name="sendto"></a> CAsyncSocket:: SendTo

이 멤버 함수를 호출 하 여 데이터를 특정 대상으로 보냅니다.

```
int SendTo(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);

int SendTo(
    const void* lpBuf,
    int nBufLen,
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
전송할 데이터를 포함 하는 버퍼입니다.

*nBufLen*<br/>
*Lpbuf* 의 데이터 길이 (바이트)입니다.

*nHostPort*<br/>
소켓 응용 프로그램을 식별 하는 포트입니다.

*lpszHostAddress*<br/>
이 개체가 연결 된 소켓의 네트워크 주소: "ftp.microsoft.com"와 같은 컴퓨터 이름 또는 "128.56.22.8"와 같은 점으로 구분 된 숫자입니다.

*nFlags*<br/>
호출을 수행 하는 방법을 지정 합니다. 이 함수의 의미 체계는 소켓 옵션 및 *Nflags* 매개 변수에 의해 결정 됩니다. 후자는 c + + **또는** 연산자와 다음 값을 결합 하 여 생성 됩니다.

- MSG_DONTROUTE는 데이터에 라우팅이 적용 되지 않도록 지정 합니다. Windows 소켓 공급자는이 플래그를 무시 하도록 선택할 수 있습니다.

- MSG_OOB 대역 외 데이터를 전송 합니다 (SOCK_STREAM에만 해당).

*lpSockAddr*<br/>
대상 소켓의 주소를 포함 하는 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조체에 대 한 포인터입니다.

*nSockAddrLen*<br/>
*LpSockAddr* 의 주소 길이 (바이트)입니다.

### <a name="return-value"></a>반환 값

오류가 발생 하지 않으면 `SendTo` 전송 된 총 문자 수를 반환 합니다. 이는 *Nbuflen* 이 나타내는 숫자 보다 적을 수 있습니다. 그렇지 않으면 SOCKET_ERROR 값이 반환 되 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- 요청 된 주소가 브로드캐스트 주소 WSAEACCES 적절 한 플래그가 설정 되지 않았습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- *Lpbuf* 또는 *lpSockAddr* 매개 변수가 사용자 주소 공간의 일부가 아니거나 *LpSockAddr* 인수가 너무 작습니다 ( [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조의 크기 보다 작음) WSAEFAULT.

- WSAEINVAL 호스트 이름이 잘못 되었습니다.

- WSAENETRESET Windows 소켓 구현에서 연결을 삭제 했으므로 연결을 다시 설정 해야 합니다.

- WSAENOBUFS는 Windows 소켓 구현에서 버퍼 교착 상태를 보고 합니다.

- WSAENOTCONN 소켓이 연결 되지 않았습니다 (SOCK_STREAM에만 해당).

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP MSG_OOB 지정 되었지만 소켓이 SOCK_STREAM 형식이 아닙니다.

- WSAESHUTDOWN 소켓이 종료 되었습니다. `SendTo` `ShutDown` 가 1 또는 2로 설정 된 경우를 사용 하 여를 호출한  후 소켓에서를 호출할 수 없습니다.

- WSAEWOULDBLOCK는 소켓이 비블로킹 상태로 표시 되 고 요청 된 작업이 차단 됩니다.

- WSAEMSGSIZE는 SOCK_DGRAM 유형이 며, 데이터 그램이 Windows 소켓 구현에서 지 원하는 최대 크기 보다 큽니다.

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 가상 회로가 중단 되었습니다.

- WSAECONNRESET 가상 회로가 원격 측에 의해 다시 설정 되었습니다.

- WSAEADDRNOTAVAIL 지정 된 주소를 로컬 컴퓨터에서 사용할 수 없습니다.

- 지정 된 패밀리의 WSAEAFNOSUPPORT 주소는이 소켓과 함께 사용할 수 없습니다.

- WSAEDESTADDRREQ 대상 주소가 필요 합니다.

- WSAENETUNREACH이 호스트에서 네트워크에 연결할 수 없습니다.

### <a name="remarks"></a>설명

`SendTo` 는 데이터 그램 또는 스트림 소켓에서 사용 되며 소켓에서 나가는 데이터를 쓰는 데 사용 됩니다. 데이터 그램 소켓의 경우 기본 서브넷의 최대 IP 패킷 크기를 초과 하지 않도록 주의를 기울여야 합니다 .이 크기는 AfxSocketInit에서 `iMaxUdpDg` 입력 한 [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) 구조의 요소에 의해 제공 [](../../mfc/reference/application-information-and-management.md#afxsocketinit)됩니다. 데이터가 너무 길어서 기본 프로토콜을 통해 원자 단위로 전달할 수 없는 경우 WSAEMSGSIZE 오류가 반환 되 고 데이터가 전송 되지 않습니다.

성공적으로 완료 되 면 `SendTo` 데이터가 성공적으로 배달 된 것으로 표시 되지 않습니다.

`SendTo` 는 *lpSockAddr* 매개 변수로 식별 되는 특정 소켓에 데이터 그램을 보내기 위해 SOCK_DGRAM 소켓 에서만 사용 됩니다.

브로드캐스트를 전송 하려면 (SOCK_DGRAM에만 해당) *lpSockAddr* 매개 변수의 주소는 Windows 소켓 헤더 파일 WINSOCK에 정의 된 특수 IP 주소 INADDR_BROADCAST를 사용 하 여 생성 해야 합니다. H)와 함께 원하는 포트 번호를 사용 합니다. 또는 *lpszHostAddress* 매개 변수가 NULL 이면 소켓이 브로드캐스트에 대해 구성 됩니다. 일반적으로 브로드캐스트 데이터 그램이 조각화가 발생할 수 있는 크기를 초과 하는 것을 것,이는 데이터 그램의 데이터 부분 (헤더 제외)이 512 바이트를 초과할 수 없음을 의미 합니다.

IPv6 주소를 처리 하려면 [Casyncsocket:: SendToEx](#sendtoex)를 사용 합니다.

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a> CAsyncSocket:: SendToEx

이 멤버 함수를 호출 하 여 데이터를 특정 대상으로 보냅니다 (IPv6 주소 처리).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
전송할 데이터를 포함 하는 버퍼입니다.

*nBufLen*<br/>
*Lpbuf* 의 데이터 길이 (바이트)입니다.

*nHostPort*<br/>
소켓 응용 프로그램을 식별 하는 포트입니다.

*lpszHostAddress*<br/>
이 개체가 연결 된 소켓의 네트워크 주소: "ftp.microsoft.com"와 같은 컴퓨터 이름 또는 "128.56.22.8"와 같은 점으로 구분 된 숫자입니다.

*nFlags*<br/>
호출을 수행 하는 방법을 지정 합니다. 이 함수의 의미 체계는 소켓 옵션 및 *Nflags* 매개 변수에 의해 결정 됩니다. 후자는 c + + **또는** 연산자와 다음 값을 결합 하 여 생성 됩니다.

- MSG_DONTROUTE는 데이터에 라우팅이 적용 되지 않도록 지정 합니다. Windows 소켓 공급자는이 플래그를 무시 하도록 선택할 수 있습니다.

- MSG_OOB 대역 외 데이터를 전송 합니다 (SOCK_STREAM에만 해당).

### <a name="return-value"></a>반환 값

오류가 발생 하지 않으면 `SendToEx` 전송 된 총 문자 수를 반환 합니다. 이는 *Nbuflen* 이 나타내는 숫자 보다 적을 수 있습니다. 그렇지 않으면 SOCKET_ERROR 값이 반환 되 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- 요청 된 주소가 브로드캐스트 주소 WSAEACCES 적절 한 플래그가 설정 되지 않았습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- *Lpbuf* 또는 *lpSockAddr* 매개 변수가 사용자 주소 공간의 일부가 아니거나 *LpSockAddr* 인수가 너무 작습니다 ( [SOCKADDR](/windows/win32/winsock/sockaddr-2) 구조의 크기 보다 작음) WSAEFAULT.

- WSAEINVAL 호스트 이름이 잘못 되었습니다.

- WSAENETRESET Windows 소켓 구현에서 연결을 삭제 했으므로 연결을 다시 설정 해야 합니다.

- WSAENOBUFS는 Windows 소켓 구현에서 버퍼 교착 상태를 보고 합니다.

- WSAENOTCONN 소켓이 연결 되지 않았습니다 (SOCK_STREAM에만 해당).

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

- WSAEOPNOTSUPP MSG_OOB 지정 되었지만 소켓이 SOCK_STREAM 형식이 아닙니다.

- WSAESHUTDOWN 소켓이 종료 되었습니다. `SendToEx` `ShutDown` 가 1 또는 2로 설정 된 경우를 사용 하 여를 호출한  후 소켓에서를 호출할 수 없습니다.

- WSAEWOULDBLOCK는 소켓이 비블로킹 상태로 표시 되 고 요청 된 작업이 차단 됩니다.

- WSAEMSGSIZE는 SOCK_DGRAM 유형이 며, 데이터 그램이 Windows 소켓 구현에서 지 원하는 최대 크기 보다 큽니다.

- WSAECONNABORTED 시간 초과 또는 다른 오류로 인해 가상 회로가 중단 되었습니다.

- WSAECONNRESET 가상 회로가 원격 측에 의해 다시 설정 되었습니다.

- WSAEADDRNOTAVAIL 지정 된 주소를 로컬 컴퓨터에서 사용할 수 없습니다.

- 지정 된 패밀리의 WSAEAFNOSUPPORT 주소는이 소켓과 함께 사용할 수 없습니다.

- WSAEDESTADDRREQ 대상 주소가 필요 합니다.

- WSAENETUNREACH이 호스트에서 네트워크에 연결할 수 없습니다.

### <a name="remarks"></a>설명

이 메서드는 IPv6 주소와 이전 프로토콜을 모두 처리 한다는 점을 제외 하 고 [Casyncsocket:: SendTo](#sendto) 와 동일 합니다.

`SendToEx` 는 데이터 그램 또는 스트림 소켓에서 사용 되며 소켓에서 나가는 데이터를 쓰는 데 사용 됩니다. 데이터 그램 소켓의 경우 기본 서브넷의 최대 IP 패킷 크기를 초과 하지 않도록 주의를 기울여야 합니다 .이 크기는 AfxSocketInit에서 `iMaxUdpDg` 입력 한 [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) 구조의 요소에 의해 제공 [](../../mfc/reference/application-information-and-management.md#afxsocketinit)됩니다. 데이터가 너무 길어서 기본 프로토콜을 통해 원자 단위로 전달할 수 없는 경우 WSAEMSGSIZE 오류가 반환 되 고 데이터가 전송 되지 않습니다.

성공적으로 완료 되 면 `SendToEx` 데이터가 성공적으로 배달 된 것으로 표시 되지 않습니다.

`SendToEx` 는 *lpSockAddr* 매개 변수로 식별 되는 특정 소켓에 데이터 그램을 보내기 위해 SOCK_DGRAM 소켓 에서만 사용 됩니다.

브로드캐스트를 전송 하려면 (SOCK_DGRAM에만 해당) *lpSockAddr* 매개 변수의 주소는 Windows 소켓 헤더 파일 WINSOCK에 정의 된 특수 IP 주소 INADDR_BROADCAST를 사용 하 여 생성 해야 합니다. H)와 함께 원하는 포트 번호를 사용 합니다. 또는 *lpszHostAddress* 매개 변수가 NULL 이면 소켓이 브로드캐스트에 대해 구성 됩니다. 일반적으로 브로드캐스트 데이터 그램이 조각화가 발생할 수 있는 크기를 초과 하는 것을 것,이는 데이터 그램의 데이터 부분 (헤더 제외)이 512 바이트를 초과할 수 없음을 의미 합니다.

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a> CAsyncSocket:: SetSockOpt

소켓 옵션을 설정 하려면이 멤버 함수를 호출 합니다.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>매개 변수

*nOptionName*<br/>
값을 설정할 소켓 옵션입니다.

*lpOptionValue*<br/>
요청 된 옵션의 값이 제공 되는 버퍼에 대 한 포인터입니다.

*nOptionLen*<br/>
*LpOptionValue* 버퍼의 크기 (바이트)입니다.

*n 수준*<br/>
옵션이 정의 되는 수준입니다. 유일 하 게 지원 되는 수준은 SOL_SOCKET 및 IPPROTO_TCP입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEFAULT *lpOptionValue* 가 프로세스 주소 공간의 올바른 부분에 없습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAEINVAL *Nlevel* 이 잘못 되었거나 *lpOptionValue* 의 정보가 잘못 되었습니다.

- SO_KEEPALIVE 설정 된 경우 WSAENETRESET 연결 시간이 초과 되었습니다.

- WSAENOPROTOOPT 옵션을 알 수 없거나 지원 되지 않습니다. 특히 SOCK_STREAM 형식의 소켓에서는 SO_BROADCAST 지원 되지 않지만 SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER 및 SO_OOBINLINE는 SOCK_DGRAM 형식의 소켓에서 지원 되지 않습니다.

- SO_KEEPALIVE 설정 되 면 WSAENOTCONN 연결이 다시 설정 되었습니다.

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

`SetSockOpt` 모든 형식의 소켓에 연결 된 소켓 옵션에 대 한 현재 값을 모든 상태로 설정 합니다. 옵션은 여러 프로토콜 수준에서 존재할 수 있지만이 사양은 맨 위 "소켓" 수준에 있는 옵션만 정의 합니다. 옵션은 일반 데이터 스트림에서 긴급 한 데이터를 받았는지 여부, 소켓에서 브로드캐스트 메시지를 보낼 수 있는지 여부 등의 소켓 작업에 영향을 줍니다.

소켓 옵션에는 기능이 나 동작을 사용 하거나 사용 하지 않도록 설정 하는 부울 옵션과 정수 값 또는 구조를 필요로 하는 옵션이 있습니다. 부울 옵션을 사용 하도록 설정 하려면 *lpOptionValue* 가 0이 아닌 정수를 가리킵니다. *LpOptionValue* 옵션을 사용 하지 않도록 설정 하려면 0과 같은 정수를 가리킵니다. *nOptionLen* 는 부울 옵션과 동일 해야 합니다 `sizeof(BOOL)` . 다른 옵션의 경우 *lpOptionValue* 는 옵션에 원하는 값이 포함 된 정수 또는 구조체를 가리키며 *nOptionLen* 은 정수 또는 구조체의 길이입니다.

SO_LINGER은 전송 되지 않은 데이터가 소켓에서 큐에 대기 되 고 함수를 호출 하 여 소켓을 닫을 때 수행 되는 동작을 제어 합니다 `Close` .

기본적으로 소켓은 이미 사용 중인 로컬 주소에 바인딩할 수 없습니다 ( [바인딩](#bind)참조). 그러나 이런 방식으로 주소를 "재사용" 하는 것이 좋을 수도 있습니다. 모든 연결은 로컬 및 원격 주소를 조합 하 여 고유 하 게 식별 되므로 원격 주소가 서로 다른 경우 두 개의 소켓이 동일한 로컬 주소에 바인딩되어야 하는 문제는 발생 하지 않습니다.

`Bind`원하는 주소를 다른 소켓에서 이미 사용 하 고 있으므로 소켓에 대 한 호출을 허용 하지 않아야 하는 Windows 소켓 구현을 알리기 위해 응용 프로그램은 호출을 실행 하기 전에 소켓에 대해 SO_REUSEADDR 소켓 옵션을 설정 해야 합니다 `Bind` . 옵션은 호출 시에만 해석 됩니다 `Bind` . 따라서 기존 주소에 바인딩하지 않을 소켓에 옵션을 설정 하는 것은 필요 하지 않으며, 호출 후에는 옵션을 설정 하거나 다시 설정 하는 것 `Bind` 이 나 다른 소켓에는 영향을 주지 않습니다.

응용 프로그램은 SO_KEEPALIVE 소켓 옵션을 설정 하 여 Windows 소켓 구현에서 TCP (전송 제어 프로토콜) 연결에 "keep-alive" 패킷을 사용 하도록 요청할 수 있습니다. Windows 소켓 구현에서는 연결 유지를 지원 하지 않아도 됩니다 .이 경우 정확한 의미 체계가 구현에 따라 다르지만 RFC 1122: "인터넷 호스트에 대 한 요구 사항-통신 계층"의 섹션 4.2.3.6을 준수 해야 합니다. "연결 유지"의 결과로 연결이 끊어지는 경우 소켓에서 진행 중인 모든 호출에 대 한 오류 코드 WSAENETRESET이 반환 되 고 모든 후속 호출은 WSAENOTCONN로 실패 합니다.

TCP_NODELAY 옵션은 Nagle 알고리즘을 사용 하지 않도록 설정 합니다. Nagle 알고리즘은 전체 크기 패킷을 보낼 수 있을 때까지 승인 되지 않은 송신 데이터를 버퍼링 하 여 호스트에서 전송 하는 작은 패킷 수를 줄이는 데 사용 됩니다. 그러나 일부 응용 프로그램의 경우이 알고리즘으로 인해 성능이 저하 될 수 있으며, TCP_NODELAY을 사용 하 여 해제할 수 있습니다. TCP_NODELAY 설정으로 인해 네트워크 성능이 상당히 저하 될 수 있으므로 응용 프로그램 작성자는 TCP_NODELAY 설정 하면 안 됩니다. TCP_NODELAY는 수준 IPPROTO_TCP를 사용 하는 유일 하 게 지원 되는 소켓 옵션입니다. 다른 모든 옵션은 수준 SOL_SOCKET를 사용 합니다.

응용 프로그램에서 SO_DEBUG 옵션이 설정 된 경우 Windows 소켓의 일부 구현에서 출력 디버그 정보를 제공 합니다.

에 대해 지원 되는 옵션은 다음과 같습니다 `SetSockOpt` . 형식은 *lpOptionValue* 로 주소를 지정 하는 데이터 형식을 식별 합니다.

|값|Type|의미|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|소켓에서 브로드캐스트 메시지의 전송을 허용 합니다.|
|SO_DEBUG|BOOL|디버깅 정보를 기록합니다.|
|SO_DONTLINGER|BOOL|보내지 않은 `Close` 데이터가 전송 될 때까지 기다리지 않도록 차단 하지 않습니다. 이 옵션을 설정 하는 것은를 0으로 설정 하 여 SO_LINGER 설정 하는 것과 같습니다 `l_onoff` .|
|SO_DONTROUTE|BOOL|라우팅되지 않음: 인터페이스로 직접 보냅니다.|
|SO_KEEPALIVE|BOOL|연결 유지를 전송 합니다.|
|SO_LINGER|`struct LINGER`|`Close`보내지 않은 데이터가 있으면 링거 합니다.|
|SO_OOBINLINE|BOOL|일반 데이터 스트림에서 대역 외 데이터를 수신 합니다.|
|SO_RCVBUF|**`int`**|수신에 대 한 버퍼 크기를 지정 합니다.|
|SO_REUSEADDR|BOOL|소켓이 이미 사용 중인 주소에 바인딩될 수 있도록 허용 합니다. [바인딩](#bind)을 참조 하십시오.|
|SO_SNDBUF|**`int`**|보낼 버퍼 크기를 지정 합니다.|
|TCP_NODELAY|BOOL|보내기 통합을 위해 Nagle 알고리즘을 비활성화합니다.|

에 대해 지원 되지 않는 BSD (Berkeley Software 배포판) 옵션 `SetSockOpt` 은 다음과 같습니다.

|값|Type|의미|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|소켓이 수신 대기 중입니다.|
|SO_ERROR|**`int`**|오류 상태를 확인 하 고 선택을 취소 합니다.|
|SO_RCVLOWAT|**`int`**|낮은 워터 마크를 받습니다.|
|SO_RCVTIMEO|**`int`**|수신 시간 제한|
|SO_SNDLOWAT|**`int`**|낮은 워터 마크를 보냅니다.|
|SO_SNDTIMEO|**`int`**|송신 제한 시간입니다.|
|SO_TYPE|**`int`**|소켓의 유형입니다.|
|IP_OPTIONS||IP 헤더의 옵션 필드를 설정 합니다.|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a> CAsyncSocket:: ShutDown

소켓에서 송신, 수신 또는 둘 다를 사용 하지 않도록 설정 하려면이 멤버 함수를 호출 합니다.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>매개 변수

*n 방법*<br/>
다음 열거형 값을 사용 하 여 더 이상 허용 되지 않는 작업 유형을 설명 하는 플래그입니다.

- **수신 = 0**

- **송신 = 1**

- **= 2**

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0이 고, [GetLastError](#getlasterror)를 호출 하 여 특정 오류 코드를 검색할 수 있습니다. 이 멤버 함수에는 다음 오류가 적용 됩니다.

- 이 API를 사용 하기 전에 WSANOTINITIALISED 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 발생 해야 합니다.

- Windows 소켓 구현에서 네트워크 하위 시스템에 오류가 WSAENETDOWN 검색 되었습니다.

- WSAEINVAL *n* 이 잘못 되었습니다.

- Windows 소켓 차단 작업을 WSAEINPROGRESS 하는 중입니다.

- WSAENOTCONN 소켓이 연결 되지 않았습니다 (SOCK_STREAM에만 해당).

- WSAENOTSOCK 설명자가 소켓이 아닙니다.

### <a name="remarks"></a>설명

`ShutDown` 는 모든 소켓 유형에 서 수신, 전송 또는 둘 다를 사용 하지 않도록 설정 하는 데 사용 됩니다. *Nhow* 가 0 인 경우 소켓에서 후속 수신은 허용 되지 않습니다. 이는 하위 프로토콜 계층에는 영향을 주지 않습니다.

TCP (전송 제어 프로토콜)의 경우 TCP 창이 변경 되지 않으며 창이 모두 사용 될 때까지 들어오는 데이터를 수락 (승인 되지 않음) 할 수 있습니다. UDP (사용자 데이터 그램 프로토콜)의 경우 들어오는 데이터 그램이 수락 되 고 큐에 대기 됩니다. 어떤 경우에도 ICMP 오류 패킷이 생성 됩니다. *Nhow* 가 1 인 경우 후속 보내기가 허용 되지 않습니다. TCP 소켓의 경우 FIN이 전송 됩니다. *Nhow* to 2를 설정 하면 위에서 설명한 대로 송신 및 받기를 모두 사용 하지 않도록 설정 합니다.

는 `ShutDown` 소켓을 닫지 않으며 소켓에 연결 된 리소스는를 호출할 때까지 해제 되지 않습니다 `Close` . 응용 프로그램이 종료 된 후 소켓을 다시 사용할 수 있도록 하는 데 의존해 서는 안 됩니다. 특히 이러한 소켓에서의 사용을 지원 하기 위해 Windows 소켓 구현이 필요 하지는 않습니다 `Connect` .

### <a name="example"></a>예제

  [Casyncsocket:: OnReceive](#onreceive)에 대 한 예제를 참조 하세요.

## <a name="casyncsocketsocket"></a><a name="socket"></a> CASyncSocket:: 소켓

소켓 핸들을 할당 합니다.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>매개 변수

*nSocketType*<br/>
`SOCK_STREAM`또는를 지정 합니다 `SOCK_DGRAM` .

*lEvent*<br/>
응용 프로그램에 관심이 있는 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.

- `FD_READ`: 읽기 준비 상태 알림을 받고 싶습니다.

- `FD_WRITE`: 쓰기 준비 상태 알림을 받고 싶습니다.

- `FD_OOB`: 대역 외 데이터 도착에 대 한 알림을 수신 하려고 합니다.

- `FD_ACCEPT`: 들어오는 연결에 대 한 알림을 수신 하려고 합니다.

- `FD_CONNECT`: 완료 된 연결에 대 한 알림을 수신 하려고 합니다.

- `FD_CLOSE`: 소켓 닫기 알림을 수신 하려고 합니다.

*nProtocolType*<br/>
표시 된 주소 패밀리와 관련 된 소켓에 사용할 프로토콜입니다.

*nAddressFormat*<br/>
주소 패밀리 사양입니다.

### <a name="return-value"></a>반환 값

성공하면 `TRUE`를 반환하고 실패하면 `FALSE`를 반환합니다.

### <a name="remarks"></a>설명

이 메서드는 소켓 핸들을 할당 합니다. [Casyncsocket:: Bind](#bind) 를 호출 하 여 소켓을 지정 된 주소에 바인딩하지 않으므로 나중에를 호출 하 여 `Bind` 소켓을 지정 된 주소에 바인딩해야 합니다. [Casyncsocket:: SetSockOpt](#setsockopt) 를 사용 하 여 바인딩 전에 소켓 옵션을 설정할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CSocket 클래스](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 클래스](../../mfc/reference/csocketfile-class.md)
