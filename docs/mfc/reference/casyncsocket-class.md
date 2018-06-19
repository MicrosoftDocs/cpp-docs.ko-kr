---
title: CAsyncSocket 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5eaefa40be2a6cf1d57326c2135d848fa08dbc87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357691"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 클래스
Windows 소켓 나타냅니다 — 네트워크 통신의 끝점입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CAsyncSocket : public CObject  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|`CAsyncSocket` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CAsyncSocket::Accept](#accept)|소켓에 대 한 연결을 허용합니다.|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|소켓에 대 한 요청 이벤트 알림입니다.|  
|[CAsyncSocket::Attach](#attach)|연결에 대 한 소켓 핸들을 `CAsyncSocket` 개체입니다.|  
|[CAsyncSocket::Bind](#bind)|로컬 주소 소켓 연결합니다.|  
|[CAsyncSocket::Close](#close)|소켓을 닫습니다.|  
|[CAsyncSocket::Connect](#connect)|피어 소켓에 대 한 연결을 설정합니다.|  
|[CAsyncSocket::Create](#create)|소켓을 만듭니다.|  
|[CAsyncSocket::Detach](#detach)|소켓 핸들을 분리 한 `CAsyncSocket` 개체입니다.|  
|[CAsyncSocket::FromHandle](#fromhandle)|에 대 한 포인터를 반환 합니다.는 `CAsyncSocket` 소켓 핸들을 지정 된 개체입니다.|  
|[CAsyncSocket::GetLastError](#getlasterror)|실패 한 마지막 작업에 대 한 오류 상태를 가져옵니다.|  
|[CAsyncSocket::GetPeerName](#getpeername)|소켓이 연결 되어 피어 소켓의 주소를 가져옵니다.|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|피어 소켓에서 소켓을 연결 된 (핸들 IPv6 주소)의 주소를 가져옵니다.|  
|[CAsyncSocket::GetSockName](#getsockname)|소켓에 대 한 로컬 이름을 가져옵니다.|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|소켓 (핸들 IPv6 주소)에 대 한 로컬 이름을 가져옵니다.|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|소켓 옵션을 검색합니다.|  
|[CAsyncSocket::IOCtl](#ioctl)|소켓의 모드를 제어 합니다.|  
|[CAsyncSocket::Listen](#listen)|들어오는 연결 요청을 수신 하는 소켓을 설정 합니다.|  
|[CAsyncSocket::Receive](#receive)|소켓에서 데이터를 받습니다.|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|데이터 그램을 수신 하 고 소스 주소를 저장 합니다.|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|데이터 그램을 수신 하 고 원본 주소 (IPv6 주소 핸들)를 저장 합니다.|  
|[CAsyncSocket::Send](#send)|데이터를 연결된 소켓으로 전송합니다.|  
|[CAsyncSocket::SendTo](#sendto)|특정 대상에 데이터를 보냅니다.|  
|[CAsyncSocket::SendToEx](#sendtoex)|데이터를 특정 대상 (핸들 IPv6 주소)를 보냅니다.|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|소켓 옵션을 설정합니다.|  
|[CAsyncSocket::ShutDown](#shutdown)|사용 하지 않도록 설정 **보낼** 및/또는 **수신** 소켓에서 호출 합니다.|  
|[CASyncSocket::Socket](#socket)|소켓 핸들을 할당합니다.|  
  
### <a name="protected-methods"></a>보호된 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|호출 하 여 보류 중인 연결 요청 받을 수 있는 수신 대기 소켓 알립니다 **Accept**합니다.|  
|[CAsyncSocket::OnClose](#onclose)|소켓에서 소켓 연결을 닫았습니다에 알립니다.|  
|[CAsyncSocket::OnConnect](#onconnect)|연결 시도가 완전 한지 여부 성공적으로 또는 오류에서 소켓에 연결 하는 알립니다.|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|수신 소켓 긴급 한 메시지는 일반적으로 소켓에서 읽을 수 있는 대역폭을 벗어난 데이터 중임을 알립니다.|  
|[CAsyncSocket::OnReceive](#onreceive)|데이터를 호출 하 여 검색할 수 있다는 것을 수신 대기 소켓에 알립니다 **수신**합니다.|  
|[CAsyncSocket::OnSend](#onsend)|호출 하 여 데이터를 보낼 수 있음을 소켓에 알립니다. **보낼**합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|에 새 값을 할당 한 `CAsyncSocket` 개체입니다.|  
|[CAsyncSocket::operator 소켓](#operator_socket)|이 연산자를 사용 하 여 검색 하는 **소켓** 의 처리는 `CAsyncSocket` 개체입니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|나타냅니다는 **소켓** 이에 연결 된 핸들 `CAsyncSocket` 개체입니다.|  
  
## <a name="remarks"></a>설명  
 클래스 `CAsyncSocket` MFC와 함께에서 Windows 소켓을 사용 하는 프로그래머를 위한 개체 지향 추상화를 제공 하는 Windows 소켓 함수 API를 캡슐화 합니다.  
  
 이 클래스는 가정을 기반으로 네트워크 통신을 이해 해야 합니다. 을 차단 하 고 바이트 순서 차이 처리 하는 것에 대 한 책임이 있으며, 유니코드 및 멀티 바이트 문자 사이의 변환 (MBCS) 문자열을 설정 합니다. 이러한 문제를 관리 하는 보다 편리한 인터페이스 클래스를 참조 하십시오 [CSocket](../../mfc/reference/csocket-class.md)합니다.  
  
 사용 하는 `CAsyncSocket` 개체, 해당 생성자를 호출 호출는 [만들기](#create) 기본 소켓 핸들을 만들 함수입니다 (형식 `SOCKET`), 수락 된 소켓을 제외 하 고 있습니다. 서버 소켓 호출에 대 한는 [수신](#listen) 멤버 함수 및 클라이언트 소켓 호출에 대 한는 [연결](#connect) 멤버 함수입니다. 서버 소켓 호출 해야는 [Accept](#accept) 연결 요청을 받으면 함수입니다. 나머지를 사용 하 여 `CAsyncSocket` 소켓 사이의 통신을 수행 하는 함수입니다. 완료 되 면 삭제는 `CAsyncSocket` 소멸자를 자동으로 호출; 힙에 만들어진 경우 개체는 [닫기](#close) 함수입니다. `SOCKET` 데이터 형식의 문서에 설명 되어 [Windows 소켓: 백그라운드](../../mfc/windows-sockets-background.md)합니다.  
  
> [!NOTE]
>  정적으로 연결 된 MFC 응용 프로그램에서 보조 스레드에서 MFC 소켓을 사용 하는 경우 호출 해야 `AfxSocketInit` 소켓을 사용 하 여 소켓 라이브러리를 초기화 하는 각 스레드에 있습니다. 기본적으로 `AfxSocketInit` 기본 스레드에서만에서 호출 됩니다.  
  
 자세한 내용은 참조 [Windows 소켓: 클래스를 사용 하 여 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) 및 관련 문서.으로 [Windows 소켓 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxsock.h  
  
##  <a name="accept"></a>  CAsyncSocket::Accept  
 이 소켓에 대 한 연결을 수락 하도록 함수를 호출 합니다.  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `rConnectedSocket`  
 연결에 사용할 수 있는 새 소켓을 식별 하는 참조입니다.  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조는 연결의 주소를 받는 소켓 네트워크에 알려져 있습니다. 정확한 형식은 `lpSockAddr` 인수 소켓을 만들 때 설정 된 주소 패밀리에 의해 결정 됩니다. 경우 `lpSockAddr` 및/또는 `lpSockAddrLen` 과 같은 **NULL**, 반환 되 고 받아들인된 소켓의 원격 주소에 대 한 정보가 없습니다.  
  
 `lpSockAddrLen`  
 주소 길이에 대 한 포인터 `lpSockAddr` (바이트)에서입니다. `lpSockAddrLen` 값 결과 매개 변수: 간격에서 가리키는 처음 있어야 `lpSockAddr`; 반환이 반환 되는 주소의 실제 길이 (바이트)에 포함 됩니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수 너무 작습니다 (의 크기 보다 작은 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조).  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 호출이 진행 중입니다.  
  
- **WSAEINVAL** `Listen` 허용 하도록 호출된 전에 없습니다.  
  
- **WSAEMFILE** 큐 적용할 시작 시 비어 있고 사용 가능한 더 설명자 있습니다.  
  
- `WSAENOBUFS` 사용할 수 있는 버퍼 공간이 없습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP** 참조 된 소켓 연결 지향 서비스를 지 원하는 유형이 아닙니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 허용 하는 상태인 연결이 없습니다.  
  
### <a name="remarks"></a>설명  
 이 루틴의 보류 중인 연결 큐에서 첫 번째 연결을 추출, 새 소켓와 동일한 속성에는이 소켓으로 만들고 연결을 `rConnectedSocket`합니다. 연결이 없는 보류 중인 큐에 있는 경우에 **Accept** 0을 반환 하 고 `GetLastError` 에서 오류를 반환 합니다. 받아들인된 소켓 ( *rConnectedSocket)* 더 많은 연결을 허용 하는 데 사용할 수 없습니다. 원래 소켓 열려 있는 상태 수신 대기 합니다.  
  
 인수 `lpSockAddr` 통신 계층에 알려진 소켓에는 연결의 주소를 사용 하 여 입력은 결과 매개 변수입니다. **수락** 와 같은 소켓 연결 기반 형식을 함께 사용 **SOCK_STREAM**합니다.  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 이 소켓에 대 한 이벤트 알림을 요청할 수 함수를 호출 합니다.  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>매개 변수  
 `lEvent`  
 응용 프로그램 interested가 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.  
  
- **작업할** 읽기에 대 한 준비에 대 한 알림을 수신 하려면.  
  
- **FD_WRITE** 데이터를 읽을 수 있는 경우 알림을 수신 하려면.  
  
- **FD_OOB** 밴드의 범위를 벗어난 데이터의 도착에 대 한 알림을 수신 하려면.  
  
- **FD_ACCEPT** 들어오는 연결에 대 한 알림을 수신 하려면.  
  
- **FD_CONNECT** 연결 결과 대 한 알림을 수신 하려면.  
  
- **FD_CLOSE** 피어에서 소켓이 닫히는 경우 알림을 수신 하려면.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEINVAL** 잘못 되었음이 지정된 된 매개 변수 중 하나를 나타냅니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
### <a name="remarks"></a>설명  
 소켓에 대 한 MFC 콜백 알림 함수를 호출할지를 지정 하려면이 함수가 사용 됩니다. `AsyncSelect` 이 소켓 비차단 모드 자동 설정 됩니다. 자세한 내용은 문서 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 연결 하려면이 멤버 함수 호출의 `hSocket` 에 대 한 핸들는 `CAsyncSocket` 개체입니다.  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>매개 변수  
 `hSocket`  
 소켓에 대 한 핸들을 포함합니다.  
  
 `lEvent`  
 응용 프로그램 interested가 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.  
  
- **작업할** 읽기에 대 한 준비에 대 한 알림을 수신 하려면.  
  
- **FD_WRITE** 데이터를 읽을 수 있는 경우 알림을 수신 하려면.  
  
- **FD_OOB** 밴드의 범위를 벗어난 데이터의 도착에 대 한 알림을 수신 하려면.  
  
- **FD_ACCEPT** 들어오는 연결에 대 한 알림을 수신 하려면.  
  
- **FD_CONNECT** 연결 결과 대 한 알림을 수신 하려면.  
  
- **FD_CLOSE** 피어에서 소켓이 닫히는 경우 알림을 수신 하려면.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공하는 경우 0이 아닙니다.  
  
### <a name="remarks"></a>설명  
 **소켓** 핸들 개체의에 저장 된 [m_hSocket](#m_hsocket) 데이터 멤버입니다.  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 로컬 주소 소켓 연결 하려면이 함수를 호출 합니다.  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>매개 변수  
 `nSocketPort`  
 소켓 응용 프로그램을 식별 하는 포트입니다.  
  
 `lpszSocketAddress`  
 네트워크 주소 "128.56.22.8"와 같은 점으로 구분 된 번호입니다. 전달는 **NULL** 문자열을이 매개 변수 나타냅니다는 **CAsyncSocket** 인스턴스는 모든 네트워크 인터페이스에서 클라이언트 활동에 대 한 수신 대기 해야 합니다.  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 이 소켓에 할당할 주소를 포함 하는 구조입니다.  
  
 `nSockAddrLen`  
 주소 길이 `lpSockAddr` (바이트)에서입니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEADDRINUSE** 지정한 주소는 이미 사용 중에서입니다. (참조는 **SO_REUSEADDR** 소켓 옵션 아래에서 [SetSockOpt](#setsockopt).)  
  
- **WSAEFAULT** 는 `nSockAddrLen` 인수 너무 작습니다 (의 크기 보다 작은 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조).  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 호출이 진행 중입니다.  
  
- **WSAEAFNOSUPPORT** 이 포트에서 지정된 된 주소 패밀리를 사용할 수 없습니다.  
  
- **WSAEINVAL** 소켓 주소에 이미 바인딩되어 있습니다.  
  
- `WSAENOBUFS` 부족 합니다. 사용할 수 있는 버퍼를 너무 많은 연결이 있습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 이 루틴은 연결 되지 않은 데이터 그램 또는 스트림 소켓에 전에 사용 후속 **연결** 또는 `Listen` 호출 합니다. 서버 소켓의 수신 대기 포트 번호를 선택 하며 쉽게 알려진 Windows 소켓을 호출 하 여 연결 요청을 허용 하려면, **바인딩할**합니다. **바인딩** 명명 되지 않은 소켓에 대 한 로컬 이름을 지정 하 여 소켓의 로컬 연결 (호스트 주소/포트 번호)을 설정 합니다.  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 빈 소켓 개체를 만듭니다.  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>설명  
 호출 해야 개체를 생성 한 후 해당 **만들기** 만들려는 멤버 함수는 **소켓** 데이터 구조를 해당 주소를 바인딩합니다. (Windows 소켓 통신을 수신 대기 소켓에서 사용 하는 소켓이 생성 하는 경우 서버 쪽에서의 **Accept** 호출을 호출 하지 않으면 **만들기** 해당 소켓에 대 한 합니다.)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 소켓을 닫습니다.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>설명  
 이 함수는 오류와 것에 대 한 참조는 실패 하는 추가 소켓 설명자를 해제 **WSAENOTSOCK**합니다. 내부 소켓에 대 한 마지막 참조 인 경우 연결 된 명명 정보 및 큐에 대기 중인된 데이터 삭제 됩니다. 소켓 개체 소멸자 호출 **닫기** 드립니다.  
  
 에 대 한 `CAsyncSocket`, 아니라 `CSocket`의 의미 체계 **닫기** 소켓 옵션의 영향을 받는 **SO_LINGER** 및 **SO_DONTLINGER**합니다. 자세한 내용은 멤버 함수를 참조 하십시오. `GetSockOpt`합니다.  
  
##  <a name="connect"></a>  CAsyncSocket::Connect  
 연결 되지 않은 스트림 또는 데이터 그램 소켓에 연결 하려면이 멤버 함수를 호출 합니다.  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpszHostAddress`  
 이 개체가 연결 되는 소켓의 네트워크 주소: "형식인" 또는 "128.56.22.8"과 같이 점으로 구분 된 값을 같은 컴퓨터 이름입니다.  
  
 `nHostPort`  
 소켓 응용 프로그램을 식별 하는 포트입니다.  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 연결된 된 소켓의 주소를 포함 하는 구조입니다.  
  
 `nSockAddrLen`  
 주소 길이 `lpSockAddr` (바이트)에서입니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 오류 코드를 나타내는 경우 **WSAEWOULDBLOCK**, 및 응용 프로그램에 재정의 가능한 콜백을 사용 하는 경우 응용 프로그램은 수신는 `OnConnect` 연결 작업이 완료 되었을 때 메시지입니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEADDRINUSE** 지정한 주소는 이미 사용 중에서입니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 호출이 진행 중입니다.  
  
- **WSAEADDRNOTAVAIL** 지정한 주소는 로컬 컴퓨터 사용할 수 없습니다.  
  
- **WSAEAFNOSUPPORT** 이 소켓으로 지정 된 제품군의 주소를 사용할 수 없습니다.  
  
- **WSAECONNREFUSED** 연결 시도가 거부 되었습니다.  
  
- **WSAEDESTADDRREQ** 대상 주소가 필요 합니다.  
  
- **WSAEFAULT** 는 `nSockAddrLen` 인수가 올바르지 않습니다.  
  
- **WSAEINVAL** 잘못 된 호스트 주소입니다.  
  
- **WSAEISCONN** 소켓이 이미 연결 되어 있습니다.  
  
- **WSAEMFILE** 더 이상 파일 설명자를 사용할 수 있습니다.  
  
- **WSAENETUNREACH** 지금이 호스트에서 네트워크에 연결할 수 없습니다.  
  
- `WSAENOBUFS` 사용할 수 있는 버퍼 공간이 없습니다. 소켓을 연결할 수 없습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAETIMEDOUT** 연결 하지 않고 시간 초과 연결을 시도 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 비블로킹 같이 연결을 즉시 완료할 수 없습니다.  
  
### <a name="remarks"></a>설명  
 소켓에 바인딩되어 있지 않습니다, 고유 값은 시스템에서 로컬 연결에 할당 및 소켓으로 표시 되어 바인딩됩니다. 되는 경우 이름 구조체의 주소 필드는 모두 0 **연결** 0을 반환 합니다. 확장 정보를 가져오려면 오류를 호출 하는 `GetLastError` 멤버 함수입니다.  
  
 스트림 소켓에 대 한 (형식 **SOCK_STREAM**), 외부 호스트에 연결 되어 시작 됩니다. 소켓 호출이 성공적으로 완료 되는 소켓은 데이터 보내기/받기 준비가입니다.  
  
 데이터 그램 소켓에 대 한 (형식 **SOCK_DGRAM**), 기본 대상 설정 되어 다음에 사용 될 **보낼** 및 **수신** 호출 합니다.  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 호출 된 **만들기** Windows 소켓을 만들를 연결 하는 소켓 개체를 생성 한 후 멤버 함수입니다.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `nSocketPort`  
 Windows 소켓 포트를 선택 하려는 경우에 소켓 또는 0 함께 사용 되는 잘 알려진 포트입니다.  
  
 `nSocketType`  
 **SOCK_STREAM** 또는 **SOCK_DGRAM**합니다.  
  
 `lEvent`  
 응용 프로그램 interested가 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.  
  
- **작업할** 읽기에 대 한 준비에 대 한 알림을 수신 하려면.  
  
- **FD_WRITE** 쓰기를 위한 준비의 알림을 수신 하려면.  
  
- **FD_OOB** 밴드의 범위를 벗어난 데이터의 도착에 대 한 알림을 수신 하려면.  
  
- **FD_ACCEPT** 들어오는 연결에 대 한 알림을 수신 하려면.  
  
- **FD_CONNECT** 완료 된 연결에 대 한 알림을 수신 하려면.  
  
- **FD_CLOSE** 소켓 닫기를 처리에 대 한 알림을 수신 하려면.  
  
 *lpszSockAddress*  
 "128.56.22.8"과 같은 점으로 구분 된 숫자를 연결된 된 소켓의 네트워크 주소를 포함 하는 문자열에 대 한 포인터입니다. 전달는 **NULL** 문자열을이 매개 변수 나타냅니다는 **CAsyncSocket** 인스턴스는 모든 네트워크 인터페이스에서 클라이언트 활동에 대 한 수신 대기 해야 합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEAFNOSUPPORT** 지정 된 주소 패밀리가 지원 되지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEMFILE** 더 이상 파일 설명자를 사용할 수 있습니다.  
  
- `WSAENOBUFS` 사용할 수 있는 버퍼 공간이 없습니다. 소켓을 만들 수 없습니다.  
  
- **WSAEPROTONOSUPPORT** 지정된 된 포트는 지원 되지 않습니다.  
  
- **WSAEPROTOTYPE** 이 소켓에 대해 잘못 된 형식이 지정된 된 포트입니다.  
  
- **WSAESOCKTNOSUPPORT** 이 주소 패밀리에 지정된 된 소켓 형식이 지원 되지 않습니다.  
  
### <a name="remarks"></a>설명  
 **만들** 호출 [소켓](#socket) 호출 성공 하면 [바인딩할](#bind) 소켓을 바인딩하지 지정된 된 주소에 있습니다. 다음 소켓 유형이 지원 됩니다.  
  
- **SOCK_STREAM** 신뢰할 수 있는, 양방향, 연결 기반 바이트 스트림의 시퀀싱를 제공 합니다. 인터넷 주소 패밀리에 대해 (TCP (Transmission Control Protocol)를 사용합니다.  
  
- **SOCK_DGRAM** 연결 없는 안정적이 지 않은 패킷 (일반적으로 짧지만) 최대 길이가 고정 인 데이터 그램을 지원 합니다. 인터넷 주소 패밀리에 대해 (UDP (User Datagram Protocol)를 사용합니다.  
  
    > [!NOTE]
    >  **Accept** 멤버 함수는 비어 있는 새에 대 한 참조를 사용 `CSocket` 개체를 매개 변수로 합니다. 호출 하기 전에이 개체를 생성 해야 **Accept**합니다. 한다는 점에 유의 하는이 소켓 개체가 범위의 연결 닫기 외부로 이동 하는 경우. 호출 하지 마십시오 **만들기** 이 새 소켓 개체에 대 한 합니다.  
  
> [!IMPORTANT]
> **만들** 은 **하지** 스레드로부터 안전 합니다.  를 호출 하는 것 다중 스레드 환경에서 동시에 다른 스레드에서 호출 될 수 있는 경우 각 호출 뮤텍스 또는 다른 동기화 l으로 보호 해야 합니다.  
  
 스트림 및 데이터 그램 소켓에 대 한 자세한 내용은 문서를 참조 [Windows 소켓: 백그라운드](../../mfc/windows-sockets-background.md) 및 [Windows 소켓: 포트 및 소켓 주소](../../mfc/windows-sockets-ports-and-socket-addresses.md) 및 [Windows 소켓 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 이를 분리 함수를 호출는 **소켓** 에서 처리는 `m_hSocket` 에서 데이터 멤버는 `CAsyncSocket` 개체 및 설정 `m_hSocket` 를 **NULL**합니다.  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 에 대 한 포인터를 반환 합니다.는 `CAsyncSocket` 개체입니다.  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>매개 변수  
 `hSocket`  
 소켓에 대 한 핸들을 포함합니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 `CAsyncSocket` 개체 또는 **NULL** 없는 경우 없는 `CAsyncSocket` 개체에 연결 되어 `hSocket`합니다.  
  
### <a name="remarks"></a>설명  
 지정 된 경우는 **소켓** 경우 처리는 `CAsyncSocket` 멤버 함수가 반환 개체가 핸들에 연결 되지 않은, **NULL**합니다.  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 실패 한 마지막 작업에 대 한 오류 상태를 가져오려면이 함수를 호출 합니다.  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>반환 값  
 반환 값이이 스레드가 수행한 마지막 Windows 소켓 API 루틴에 대 한 오류 코드를 나타냅니다.  
  
### <a name="remarks"></a>설명  
 특정 멤버 함수, 오류가 발생 했음을 나타냅니다 때 `GetLastError` 적절 한 오류 코드를 검색 하려면이 호출 해야 합니다. 적용 가능한 오류 코드의 목록에 대 한 개별 멤버 함수 설명을 참조 하십시오.  
  
 오류 코드에 대 한 자세한 내용은 참조 [Windows 소켓 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)합니다.  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 이이 소켓 연결 된 피어 소켓의 주소를 가져오는 함수를 호출 합니다.  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>매개 변수  
 `rPeerAddress`  
 에 대 한 참조는 `CString` 점선으로 된 숫자 IP 주소를 받는 개체입니다.  
  
 `rPeerPort`  
 에 대 한 참조는 **UINT** 포트를 저장 하는 합니다.  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조체 피어 소켓의 이름입니다.  
  
 `lpSockAddrLen`  
 주소 길이에 대 한 포인터 `lpSockAddr` (바이트)에서입니다. 반환 시,는 `lpSockAddrLen` 의 실제 크기를 포함 하는 인수 `lpSockAddr` 바이트 단위로 반환 합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수 만큼 크지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 호출이 진행 중입니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 IPv6 주소를 처리 하려면 [CAsyncSocket::GetPeerNameEx](#getpeernameex)합니다.  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 이 소켓을 연결 된 (핸들 IPv6 주소) 피어 소켓의 주소를 얻기 위해이 함수를 호출 합니다.  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>매개 변수  
 `rPeerAddress`  
 에 대 한 참조는 `CString` 점선으로 된 숫자 IP 주소를 받는 개체입니다.  
  
 `rPeerPort`  
 에 대 한 참조는 **UINT** 포트를 저장 하는 합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수 만큼 크지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 호출이 진행 중입니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 이 함수는 동일 [CAsyncSocket::GetPeerName](#getpeername) IPv6 처리 한다는 점을 제외 하면 오래 된 파일로 프로토콜을 해결 합니다.  
  
##  <a name="getsockname"></a>  CAsyncSocket::GetSockName  
 소켓에 대 한 로컬 이름을 가져오려면이 함수를 호출 합니다.  
  
```  
BOOL GetSockName(
    CString& rSocketAddress,  
    UINT& rSocketPort);

 
BOOL GetSockName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>매개 변수  
 `rSocketAddress`  
 에 대 한 참조는 `CString` 점선으로 된 숫자 IP 주소를 받는 개체입니다.  
  
 `rSocketPort`  
 에 대 한 참조는 **UINT** 포트를 저장 하는 합니다.  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조체의 소켓 주소입니다.  
  
 `lpSockAddrLen`  
 주소 길이에 대 한 포인터 `lpSockAddr` (바이트)에서입니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수 만큼 크지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEINVAL** 소켓에 있는 주소에 바인딩되어 있지 **바인딩할**합니다.  
  
### <a name="remarks"></a>설명  
 이 호출은 때 특히 유용는 **연결** 호출 수행 하지 않고는 **바인딩할** 이 호출은으로 설정 된 로컬 연결을 확인할 수 있는 유일한 수단을 제공 하는 먼저;는 시스템입니다.  
  
 IPv6 주소를 처리 하려면 [CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 소켓 (핸들 IPv6 주소)에 대 한 로컬 이름을 가져오려면이 함수를 호출 합니다.  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>매개 변수  
 `rSocketAddress`  
 에 대 한 참조는 `CString` 점선으로 된 숫자 IP 주소를 받는 개체입니다.  
  
 `rSocketPort`  
 에 대 한 참조는 **UINT** 포트를 저장 하는 합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수 만큼 크지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEINVAL** 소켓에 있는 주소에 바인딩되어 있지 **바인딩할**합니다.  
  
### <a name="remarks"></a>설명  
 이 호출은와 같습니다 [CAsyncSocket::GetSockName](#getsockname) IPv6 처리 한다는 점을 제외 하면 오래 된 파일로 프로토콜을 해결 합니다.  
  
 이 호출은 때 특히 유용는 **연결** 호출 수행 하지 않고는 **바인딩할** 이 호출은으로 설정 된 로컬 연결을 확인할 수 있는 유일한 수단을 제공 하는 먼저;는 시스템입니다.  
  
##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt  
 소켓 옵션을 검색 하려면이 멤버 함수를 호출 합니다.  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>매개 변수  
 `nOptionName`  
 값은 검색할 소켓 옵션입니다.  
  
 `lpOptionValue`  
 요청 된 옵션의 값을 반환할 버퍼에 대 한 포인터입니다. 버퍼에서 선택한 옵션과 관련 된 값이 반환 됩니다 `lpOptionValue`합니다. 가 가리키는 정수 `lpOptionLen` (바이트)이이 버퍼의 크기를 원래 있어야 하 고 반환 시, 반환 되는 값의 크기를 설정할 수는 있습니다. 에 대 한 **SO_LINGER**, 크기 됩니다는 `LINGER` 구조; 다른 모든 옵션에 대 한 크기의 됩니다는 **BOOL** 또는 `int`옵션에 따라 합니다. 주의 섹션의 크기 및 옵션 목록을 참조 하십시오.  
  
 `lpOptionLen`  
 크기에 대 한 포인터는 `lpOptionValue` 버퍼의 바이트입니다.  
  
 `nLevel`  
 정의 된 수준에는 옵션은; 지원 되는 유일한 수준 **SOL_SOCKET** 및 **IPPROTO_TCP**합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 옵션으로 설정 되지 않았으면 경우 `SetSockOpt`, 다음 `GetSockOpt` 옵션에 대 한 기본값을 반환 합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpOptionLen` 인수가 잘못 되었습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAENOPROTOOPT** 알 수 없거나 지원 되지 않는 옵션입니다. 특히, **SO_BROADCAST** 형식의 소켓에서 지원 되지 않습니다 **SOCK_STREAM**, 동안 **SO_ACCEPTCONN**, **SO_DONTLINGER**,  **SO_KEEPALIVE**, **SO_LINGER**, 및 **SO_OOBINLINE** 형식의 소켓에서 지원 되지 않습니다 **SOCK_DGRAM**합니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 `GetSockOpt` 모든 상태에서 모든 형식의 소켓와 연결 된 소켓 옵션에 대 한 현재 값을 검색 하 고 해당 결과 `lpOptionValue`합니다. 옵션 패킷과 대역폭을 벗어난 데이터 전송 등의 라우팅 등의 소켓 작업을 영향을 줍니다.  
  
 에 대해 다음 옵션은 지원 `GetSockOpt`합니다. 형식으로 주소가 지정 된 데이터의 형식을 식별 `lpOptionValue`합니다. **TCP_NODELAY** 옵션 수준을 사용 하 여 **IPPROTO_TCP**; 다른 모든 옵션에 수준을 사용 하 여 **SOL_SOCKET**합니다.  
  
|값|형식|의미|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|소켓이 수신 중입니다.|  
|**SO_BROADCAST**|**BOOL**|소켓의 브로드캐스트 메시지 전송에 구성 되어 있습니다.|  
|**SO_DEBUG**|**BOOL**|디버깅이 활성화 됩니다.|  
|**SO_DONTLINGER**|**BOOL**|True 이면는 **SO_LINGER** 옵션을 사용할 수 없습니다.|  
|**SO_DONTROUTE**|**BOOL**|라우팅을 사용할 수 없습니다.|  
|**SO_ERROR**|`int`|오류 상태를 검색 하 고 취소 합니다.|  
|**SO_KEEPALIVE**|**BOOL**|연결 유지 보내고 있습니다.|  
|**SO_LINGER**|**LINGER 구조체**|현재 링거 옵션을 반환합니다.|  
|**SO_OOBINLINE**|**BOOL**|일반 데이터 스트림의 대역의 데이터를 받고 합니다.|  
|**SO_RCVBUF**|`int`|버퍼 크기를 받습니다.|  
|**SO_REUSEADDR**|**BOOL**|소켓이 이미 사용 되는 주소에 바인딩할 수 있습니다.|  
|**SO_SNDBUF**|`int`|버퍼 크기를 보냅니다.|  
|**SO_TYPE**|`int`|소켓의 유형 (예를 들어 **SOCK_STREAM**).|  
|**TCP_NODELAY**|**BOOL**|보내기 통합을 위해 Nagle 알고리즘을 비활성화합니다.|  
  
 에 대 한 지원 되지 않는 Berkeley 소프트웨어 배포 (BSD) 옵션 `GetSockOpt` 됩니다.  
  
|값|형식|의미|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|`int`|하위 워터 마크를 수신 합니다.|  
|**SO_RCVTIMEO**|`int`|시간 초과가 수신 합니다.|  
|**SO_SNDLOWAT**|`int`|하위 워터 마크를 보냅니다.|  
|**SO_SNDTIMEO**|`int`|제한 시간을 보냅니다.|  
|**IP_OPTIONS**||IP 헤더에 옵션을 가져옵니다.|  
|**TCP_MAXSEG**|`int`|TCP 최대 세그먼트 크기를 가져옵니다.|  
  
 호출 `GetSockOpt` 는 지원 되지 않는 옵션을 사용 하면 오류 코드 **WSAENOPROTOOPT** 에서 반환 되 고 `GetLastError`합니다.  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 소켓의 모드를 제어 하려면이 멤버 함수를 호출 합니다.  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>매개 변수  
 `lCommand`  
 소켓에서 수행 하는 명령입니다.  
  
 `lpArgument`  
 에 대 한 매개 변수에 대 한 포인터 `lCommand`합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEINVAL** `lCommand` 은 올바른 명령이 아닙니다 또는 `lpArgument` 에 대 한 허용 되는 매개 변수 없는 `lCommand`, 아니거나 명령을 제공 하는 소켓의 형식에 적용할 수 없습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 이 루틴은 모든 상태에서 모든 소켓에서 사용할 수 있습니다. 가져오기 또는 연결 소켓, 프로토콜 및 통신 하위 시스템의 독립 된 작업 매개 변수를 검색 사용 됩니다. 에서는 다음과 같은 명령이 지원 됩니다.  
  
- **FIONBIO** 설정 또는 소켓에 비차단 모드를 해제 합니다. `lpArgument` 매개 변수를 가리키는 `DWORD`는 비차단 모드를 사용 하도록 설정 하면 0이 아니고 지정 되며 경우에는 0을 비활성화할 수 있습니다. 경우 `AsyncSelect` 다음 사용 하려는 모든 시도 소켓에서 실행 된 **IOCtl** 소켓 블로킹 모드 다시 설정 하는 함께 실패 합니다 **WSAEINVAL**합니다. 소켓 블로킹 모드 다시 설정 하 고 방지 하는 **WSAEINVAL** 오류, 응용 프로그램 해제 해야 합니다. `AsyncSelect` 호출 하 여 `AsyncSelect` 와 `lEvent` 매개 변수를 0으로 호출 **IOCtl** .  
  
- **FIONREAD** 하나를 읽을 수 있는 바이트의 최대 수를 확인할 **수신** 이 소켓에서 호출 합니다. `lpArgument` 매개 변수를 가리키는 `DWORD` 는 **IOCtl** 결과 저장 합니다. 이 소켓 형식인 경우 **SOCK_STREAM**, **FIONREAD** 단일에서 읽을 수 있는 데이터의 총 크기를 반환 합니다. **수신**;이 일반적으로 총와 동일 소켓에서 대기 하는 데이터입니다. 이 소켓 형식인 경우 **SOCK_DGRAM**, **FIONREAD** 소켓에서 대기열에 첫 번째 데이터 그램의 크기를 반환 합니다.  
  
- **SIOCATMARK** 모든 대역의 데이터를 읽을 지 여부를 결정 합니다. 이 형식의 소켓에만 적용 됩니다 **SOCK_STREAM** 인라인 ं आ स ा 밴드의 범위를 벗어난 데이터에 구성 되어 있는 ( **SO_OOBINLINE**). 읽을 수 없는 대역폭을 벗어난 데이터를 대기 중인 경우 작업이 0이 아닌 반환 합니다. 그렇지 않으면 0이 고, 다음 반환 **수신** 또는 `ReceiveFrom` 에 대해 수행 소켓 "표시" 앞에 데이터의 일부나 전부를 검색 합니다; 응용 프로그램 사용 해야는 **SIOCATMARK** 작업을 데이터가 남아 있는지 여부를 결정 합니다. "긴급" (대역) 데이터 앞에 있는 일반 데이터를 순서 대로 수신 됩니다. (유의 **수신** 또는 `ReceiveFrom` 밴드의 범위를 벗어난 및 일반 데이터는 동일한 호출에서을 혼합 해서는 안 됩니다.) `lpArgument` 매개 변수를 가리키는 `DWORD` 는 **IOCtl** 결과 저장 합니다.  
  
 이 함수는 하위 집합만 **ioctl()** Berkeley 소켓에서 사용 되는 합니다. 특히 해당 하는 명령이 없기 **FIOASYNC**, 동안 **SIOCATMARK** 지원 되는 소켓 수준 명령입니다.  
  
##  <a name="listen"></a>  CAsyncSocket::Listen  
 들어오는 연결 요청을 수신 하려면이 멤버 함수를 호출 합니다.  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>매개 변수  
 *nConnectionBacklog*  
 보류 중인 연결의 큐 증가할 수 있는 최대 길이입니다. 유효한 범위는 1에서 5 사이입니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEADDRINUSE** 사용 중인 주소에서 수신 하려고 합니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEINVAL** 소켓으로 바인딩되지 않은 **바인딩할** 또는 이미 연결 되어 있습니다.  
  
- **WSAEISCONN** 소켓이 이미 연결 되어 있습니다.  
  
- **WSAEMFILE** 더 이상 파일 설명자를 사용할 수 있습니다.  
  
- `WSAENOBUFS` 사용할 수 있는 버퍼 공간이 없습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP** 참조 된 소켓을 지 원하는 유형이 않습니다는 `Listen` 작업 합니다.  
  
### <a name="remarks"></a>설명  
 연결을 허용 하도록 소켓 처음 만들어질와 **만들기**, 들어오는 연결에 대 한 백로그가 지정 된 `Listen`, 및 연결 된 수락 다음 **Accept**합니다. `Listen` 형식의 속성이 연결을 지원 하므로, 즉 소켓에만 적용 **SOCK_STREAM**합니다. 이 소켓 "수동" 모드 들어오는 연결의 승인 및 프로세스에 의해 승인 보류 중인 큐에 대기 위치에 배치 됩니다.  
  
 이 함수는 일반적으로 서버 (또는 연결을 허용 하는 모든 응용 프로그램)가 사용 되어 한 번에 둘 이상의 연결 요청을 사용할 수 있는: 클라이언트 의표시와함께오류가표시됩니다는큐가꽉찼습니다함께도착한연결요청을하는경우 **WSAECONNREFUSED**합니다.  
  
 `Listen` 에 계속 사용할 수 있는 포트 (설명자) 없는 경우 합리적으로 기능을 시도 합니다. 큐를 비울 때까지 연결을 허용 합니다. 포트 사용 가능 하 게 하는 경우 한 이후의 호출 `Listen` 또는 **Accept** 가능 하면 현재 또는 가장 최근 "백로그에" 큐를 다시 채우는 하 고 들어오는 연결을 수신 대기를 다시 시작 됩니다.  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 포함 된 **소켓** 이 캡슐화 된 소켓에 대 한 처리 `CAsyncSocket` 개체입니다.  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 호출 하 여 보류 중인 연결 요청 받을 수 있는 수신 대기 소켓에 알리기 위해 프레임 워크에서 호출 된 [Accept](#accept) 멤버 함수입니다.  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>매개 변수  
 `nErrorCode`  
 소켓에 대 한 가장 최근의 오류입니다. 다음 오류 코드에 적용 된 `OnAccept` 멤버 함수:  
  
- **0** 성공적으로 실행 하는 함수입니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 해당 프로세스에 의해 연결 된 소켓 닫았는지이 소켓에 알리기 위해 프레임 워크에서 호출 됩니다.  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>매개 변수  
 `nErrorCode`  
 소켓에 대 한 가장 최근의 오류입니다. 다음 오류 코드에 적용 된 `OnClose` 멤버 함수:  
  
- **0** 성공적으로 실행 하는 함수입니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAECONNRESET** 원격측에서 연결을 다시 설정 합니다.  
  
- **WSAECONNABORTED** 연결이 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 이 소켓에 연결에 해당 연결 시도가 완료 되 면 성공적으로 또는 오류가 있는지 여부를 알리기 위해 프레임 워크에서 호출 됩니다.  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>매개 변수  
 `nErrorCode`  
 소켓에 대 한 가장 최근의 오류입니다. 다음 오류 코드에 적용 된 `OnConnect` 멤버 함수:  
  
- **0** 성공적으로 실행 하는 함수입니다.  
  
- **WSAEADDRINUSE** 지정한 주소는 이미 사용 중에서입니다.  
  
- **WSAEADDRNOTAVAIL** 지정한 주소는 로컬 컴퓨터 사용할 수 없습니다.  
  
- **WSAEAFNOSUPPORT** 이 소켓으로 지정 된 제품군의 주소를 사용할 수 없습니다.  
  
- **WSAECONNREFUSED** 연결 시도가 강제로 거부 되었습니다.  
  
- **WSAEDESTADDRREQ** 대상 주소가 필요 합니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수가 올바르지 않습니다.  
  
- **WSAEINVAL** 소켓 주소에 이미 바인딩되어 있습니다.  
  
- **WSAEISCONN** 소켓이 이미 연결 되어 있습니다.  
  
- **WSAEMFILE** 더 이상 파일 설명자를 사용할 수 있습니다.  
  
- **WSAENETUNREACH** 지금이 호스트에서 네트워크에 연결할 수 없습니다.  
  
- `WSAENOBUFS` 사용할 수 있는 버퍼 공간이 없습니다. 소켓을 연결할 수 없습니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다.  
  
- **WSAENOTSOCK** 설명자가 파일을 소켓에 없습니다.  
  
- **WSAETIMEDOUT** 연결 하지 않고 연결 시도 시간이 초과 되었습니다.  
  
### <a name="remarks"></a>설명  
  
> [!NOTE]
>  [CSocket](../../mfc/reference/csocket-class.md), `OnConnect` 알림 함수는 호출 되지 않습니다. 연결에 대해 호출 하면 **연결**, (성공적으로 또는 오류가) 연결이 완료 되 면 반환 반환 됩니다. MFC 구현 정보는 연결 알림을 처리 하는 방법입니다.  
  
 자세한 내용은 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 보내는 소켓에 밴드의 범위를 벗어난 보낼 데이터를 받는 소켓에 알리기 위해 프레임 워크에서 호출 됩니다.  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>매개 변수  
 `nErrorCode`  
 소켓에 대 한 가장 최근의 오류입니다. 다음 오류 코드에 적용 된 `OnOutOfBandData` 멤버 함수:  
  
- **0** 성공적으로 실행 하는 함수입니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
### <a name="remarks"></a>설명  
 대역폭을 벗어난 데이터는 각 형식의 연결 된 소켓 쌍과 연결 된 논리적으로 독립 채널 **SOCK_STREAM**합니다. 채널은 일반적으로 긴급 한 데이터를 보내는 데 사용 됩니다.  
  
 MFC 지원 있지만 클래스의 사용자가 대역폭을 벗어난 데이터 `CAsyncSocket` 사용 해서는 안 됩니다. 쉬운 방법이 이러한 데이터를 전달 하기 위한 두 번째 소켓을 만드는 것입니다. 대역폭을 벗어난 데이터에 대 한 자세한 내용은 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 호출 하 여 검색할 수 있는 버퍼의 데이터는이 소켓에 알리기 위해 프레임 워크에서 호출 된 **수신** 멤버 함수입니다.  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>매개 변수  
 `nErrorCode`  
 소켓에 대 한 가장 최근의 오류입니다. 다음 오류 코드에 적용 된 `OnReceive` 멤버 함수:  
  
- **0** 성공적으로 실행 하는 함수입니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 호출 하 여 데이터 보내기 이제 수 소켓에 알리기 위해 프레임 워크에서 호출 된 **보낼** 멤버 함수입니다.  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>매개 변수  
 `nErrorCode`  
 소켓에 대 한 가장 최근의 오류입니다. 다음 오류 코드에 적용 된 `OnSend` 멤버 함수:  
  
- **0** 성공적으로 실행 하는 함수입니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 참조 [Windows 소켓: 소켓 알림](../../mfc/windows-sockets-socket-notifications.md)합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 에 새 값을 할당 한 `CAsyncSocket` 개체입니다.  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>매개 변수  
 `rSrc`  
 기존에 대 한 참조 `CAsyncSocket` 개체입니다.  
  
### <a name="remarks"></a>설명  
 이 함수는 기존 복사를 호출 `CAsyncSocket` 개체를 다른 `CAsyncSocket` 개체입니다.  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator 소켓  
 이 연산자를 사용 하 여 검색 하는 **소켓** 의 처리는 `CAsyncSocket` 개체입니다.  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>반환 값  
 성공 하면의 핸들은 **소켓** 개체; 그렇지 않으면 **NULL**합니다.  
  
### <a name="remarks"></a>설명  
 Windows Api를 직접 호출 하는 핸들을 사용할 수 있습니다.  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 이 소켓에서 데이터를 받는 함수를 호출 합니다.  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpBuf`  
 들어오는 데이터에 대 한 버퍼입니다.  
  
 `nBufLen`  
 길이가 `lpBuf` (바이트)에서입니다.  
  
 `nFlags`  
 호출이 수행 된 방식을 지정 합니다. 이 함수의의 의미 체계 소켓 옵션에 따라 결정 되 고 `nFlags` 매개 변수. 다음 값 중 하나는 c + +와 결합 하 여 생성 되 고 후자 `OR` 연산자:  
  
- **MSG_PEEK** 들어오는 데이터를 봅니다. 데이터 버퍼에 복사 되지만 입력된 큐에서 제거 되지 않습니다.  
  
- **MSG_OOB** 대역의 데이터를 처리 합니다.  
  
### <a name="return-value"></a>반환 값  
 오류가 발생 하지 않으면, **수신** 받은 바이트 수를 반환 합니다. 연결이 닫힌 경우 0을 반환 합니다. 그렇지 않으면 값이 **SOCKET_ERROR** 반환 되 면 호출 하 여 특정 오류 코드를 검색할 수 있습니다 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP MSG_OOB** 지정 소켓 형식의 되지 않은 **SOCK_STREAM**합니다.  
  
- **WSAESHUTDOWN** 소켓이 종료 된; 호출 수 없으면 **수신** 후 소켓에서 `ShutDown` 를 호출 했습니다 `nHow` 0 또는 2로 설정 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 및 **수신** 작업이 중단 됩니다.  
  
- **WSAEMSGSIZE** 데이터 그램 너무 커서 지정된 된 버퍼에 맞지 및 잘렸습니다.  
  
- **WSAEINVAL** 소켓으로 바인딩되지 않은 **바인딩할**합니다.  
  
- **WSAECONNABORTED** 가상 회로가 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
- **WSAECONNRESET** 원격측에서 가상 회로가 재설정 되었습니다.  
  
### <a name="remarks"></a>설명  
 이 함수는 연결 된 스트림 또는 데이터 그램 소켓에 사용 하며 들어오는 데이터를 읽는 데 사용 됩니다.  
  
 형식의 소켓에 대 한 **SOCK_STREAM**에서 많은 정보 크기 지정 된 버퍼의 최대는 현재 사용할 수 있는 그대로 반환 됩니다. 소켓 대역폭을 벗어난 데이터의 인라인 수신에 구성 된 경우 (소켓 옵션 **SO_OOBINLINE**) 및 대역폭을 벗어난 데이터를 읽지, 밴드를만 데이터가 반환 됩니다. 응용 프로그램에서 사용할 수는 **IOCtlSIOCATMARK** 옵션 또는 [OnOutOfBandData](#onoutofbanddata) 밴드를 더 데이터가 남아를 읽을 수 있는지 여부를 확인 하려면.  
  
 데이터 그램 소켓에 대 한 크기 지정 된 버퍼의 최대는 첫 큐에 대기 된 데이터 그램에서 데이터를 추출 합니다. 데이터 그램 지정 된 버퍼 보다 클 경우 데이터 그램의 첫 번째 부분으로 된 버퍼가 채워집니다, 초과 데이터는 손실 및 **수신** 의 값을 반환 **SOCKET_ERROR** 오류 코드로 설정 **WSAEMSGSIZE**합니다. 값이 소켓에 없는 들어오는 데이터를 사용할 수 **SOCKET_ERROR** 로 설정 하는 오류 코드와 함께 반환 되는지 **WSAEWOULDBLOCK**합니다. [OnReceive](#onreceive) 더 많은 데이터가 도착할 시기를 결정 하는 콜백 함수를 사용할 수 있습니다.  
  
 소켓 형식인 경우 **SOCK_STREAM** 원격측에 연결이 정상적으로 종료, 및는 **수신** 받은 0 바이트와 함께 즉시 완료 됩니다. 연결 다시 설정 하는 경우는 **수신** 오류와 함께 실패 합니다 **WSAECONNRESET**합니다.  
  
 **수신** 각 시간에 대해 한 번만 호출 해야 [CAsyncSocket::OnReceive](#onreceive) 호출 됩니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CAsyncSocket::OnReceive](#onreceive)합니다.  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 데이터 그램을 수신 하 고에 소스 주소를 저장 하려면이 함수 호출의 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조 또는 `rSocketAddress`합니다.  
  
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
 `lpBuf`  
 들어오는 데이터에 대 한 버퍼입니다.  
  
 `nBufLen`  
 길이가 `lpBuf` (바이트)에서입니다.  
  
 `rSocketAddress`  
 에 대 한 참조는 `CString` 점선으로 된 숫자 IP 주소를 받는 개체입니다.  
  
 `rSocketPort`  
 에 대 한 참조는 **UINT** 포트를 저장 하는 합니다.  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 반환 되 면 소스 주소를 보유 하는 구조입니다.  
  
 `lpSockAddrLen`  
 소스 주소에서의 길이에 대 한 포인터 `lpSockAddr` (바이트)에서입니다.  
  
 `nFlags`  
 호출이 수행 된 방식을 지정 합니다. 이 함수의의 의미 체계 소켓 옵션에 따라 결정 되 고 `nFlags` 매개 변수. 다음 값 중 하나는 c + +와 결합 하 여 생성 되 고 후자 `OR` 연산자:  
  
- **MSG_PEEK** 들어오는 데이터를 봅니다. 데이터 버퍼에 복사 되지만 입력된 큐에서 제거 되지 않습니다.  
  
- **MSG_OOB** 대역의 데이터를 처리 합니다.  
  
### <a name="return-value"></a>반환 값  
 오류가 발생 하지 않으면, `ReceiveFrom` 받은 바이트 수를 반환 합니다. 연결이 닫힌 경우 0을 반환 합니다. 그렇지 않으면 값이 **SOCKET_ERROR** 반환 되 면 호출 하 여 특정 오류 코드를 검색할 수 있습니다 `GetLastError`합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수가 잘못 되었습니다:는 `lpSockAddr` 버퍼가 너무 작아서 피어 주소에 맞게 합니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEINVAL** 소켓으로 바인딩되지 않은 **바인딩할**합니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다 ( **SOCK_STREAM** 만).  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP MSG_OOB** 지정 소켓 형식의 되지 않은 **SOCK_STREAM**합니다.  
  
- **WSAESHUTDOWN** 소켓이 종료 된; 호출 수 없으면 `ReceiveFrom` 후 소켓에서 `ShutDown` 를 호출 했습니다 `nHow` 0 또는 2로 설정 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 및 `ReceiveFrom` 작업이 중단 됩니다.  
  
- **WSAEMSGSIZE** 데이터 그램 너무 커서 지정된 된 버퍼에 맞지 및 잘렸습니다.  
  
- **WSAECONNABORTED** 가상 회로가 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
- **WSAECONNRESET** 원격측에서 가상 회로가 재설정 되었습니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 (연결된 수)는 소켓에서 들어오는 데이터를 읽고 데이터를 보낸 주소 캡처 사용 됩니다.  
  
 IPv6 주소를 처리 하려면 [CAsyncSocket::ReceiveFromEx](#receivefromex)합니다.  
  
 형식의 소켓에 대 한 **SOCK_STREAM**에서 많은 정보 크기 지정 된 버퍼의 최대는 현재 사용할 수 있는 그대로 반환 됩니다. 소켓 대역폭을 벗어난 데이터의 인라인 수신에 구성 된 경우 (소켓 옵션 **SO_OOBINLINE**) 및 대역폭을 벗어난 데이터를 읽지, 밴드를만 데이터가 반환 됩니다. 응용 프로그램에서 사용할 수는 **IOCtlSIOCATMARK** 옵션 또는 `OnOutOfBandData` 밴드를 더 데이터가 남아를 읽을 수 있는지 여부를 확인 하려면. `lpSockAddr` 및 `lpSockAddrLen` 에 대 한 매개 변수는 무시 **SOCK_STREAM** 소켓 합니다.  
  
 데이터 그램 소켓에 대 한 크기 지정 된 버퍼의 최대는 첫 큐에 대기 된 데이터 그램에서 데이터를 추출 합니다. 데이터 그램 지정 된 버퍼 보다 클 경우 메시지의 첫 번째 부분으로 된 버퍼가 채워집니다, 초과 데이터는 손실 및 `ReceiveFrom` 의 값을 반환 **SOCKET_ERROR** 오류 코드로 설정  **WSAEMSGSIZE**합니다.  
  
 경우 `lpSockAddr` 이 값은 0 고 소켓 형식이 **SOCK_DGRAM**, 데이터를 보낸 소켓의 네트워크 주소에 해당 요소에 복사 되 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조입니다. 값에서 가리키는 `lpSockAddrLen` 이 구조체의 크기로으로 초기화 되 고 저장 된 주소의 실제 크기를 나타내는 반환이 수정 됩니다. 들어오는 데이터가 없는 소켓에서 사용할 수 있는 경우는 `ReceiveFrom` 소켓이 아닌 경우 도착 하는 데이터에 대 한 호출이 대기 비블로킹 합니다. 이 경우 값은 **SOCKET_ERROR** 로 설정 하는 오류 코드와 함께 반환 되는지 **WSAEWOULDBLOCK**합니다. `OnReceive` 콜백 도착 시간을 확인할 더 많은 데이터를 사용할 수 있습니다.  
  
 소켓 형식인 경우 **SOCK_STREAM** 원격측에 연결이 정상적으로 종료, 및는 `ReceiveFrom` 받은 0 바이트와 함께 즉시 완료 됩니다.  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 데이터 그램을 수신 하 고에 소스 주소를 저장 하려면이 함수 호출의 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조 또는 `rSocketAddress` (IPv6 주소 처리).  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpBuf`  
 들어오는 데이터에 대 한 버퍼입니다.  
  
 `nBufLen`  
 길이가 `lpBuf` (바이트)에서입니다.  
  
 `rSocketAddress`  
 에 대 한 참조는 `CString` 점선으로 된 숫자 IP 주소를 받는 개체입니다.  
  
 `rSocketPort`  
 에 대 한 참조는 **UINT** 포트를 저장 하는 합니다.  
  
 `nFlags`  
 호출이 수행 된 방식을 지정 합니다. 이 함수의의 의미 체계 소켓 옵션에 따라 결정 되 고 `nFlags` 매개 변수. 다음 값 중 하나는 c + +와 결합 하 여 생성 되 고 후자 `OR` 연산자:  
  
- **MSG_PEEK** 들어오는 데이터를 봅니다. 데이터 버퍼에 복사 되지만 입력된 큐에서 제거 되지 않습니다.  
  
- **MSG_OOB** 대역의 데이터를 처리 합니다.  
  
### <a name="return-value"></a>반환 값  
 오류가 발생 하지 않으면, `ReceiveFromEx` 받은 바이트 수를 반환 합니다. 연결이 닫힌 경우 0을 반환 합니다. 그렇지 않으면 값이 **SOCKET_ERROR** 반환 되 면 호출 하 여 특정 오류 코드를 검색할 수 있습니다 `GetLastError`합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** 는 `lpSockAddrLen` 인수가 잘못 되었습니다:는 `lpSockAddr` 버퍼가 너무 작아서 피어 주소에 맞게 합니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEINVAL** 소켓으로 바인딩되지 않은 **바인딩할**합니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다 ( **SOCK_STREAM** 만).  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP MSG_OOB** 지정 소켓 형식의 되지 않은 **SOCK_STREAM**합니다.  
  
- **WSAESHUTDOWN** 소켓이 종료 된; 호출 수 없으면 `ReceiveFromEx` 후 소켓에서 `ShutDown` 를 호출 했습니다 `nHow` 0 또는 2로 설정 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 및 `ReceiveFromEx` 작업이 중단 됩니다.  
  
- **WSAEMSGSIZE** 데이터 그램 너무 커서 지정된 된 버퍼에 맞지 및 잘렸습니다.  
  
- **WSAECONNABORTED** 가상 회로가 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
- **WSAECONNRESET** 원격측에서 가상 회로가 재설정 되었습니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 (연결된 수)는 소켓에서 들어오는 데이터를 읽고 데이터를 보낸 주소 캡처 사용 됩니다.  
  
 이 함수는 동일 [CAsyncSocket::ReceiveFrom](#receivefrom) IPv6 처리 한다는 점을 제외 하면 오래 된 파일로 프로토콜을 해결 합니다.  
  
 형식의 소켓에 대 한 **SOCK_STREAM**에서 많은 정보 크기 지정 된 버퍼의 최대는 현재 사용할 수 있는 그대로 반환 됩니다. 소켓 대역폭을 벗어난 데이터의 인라인 수신에 구성 된 경우 (소켓 옵션 **SO_OOBINLINE**) 및 대역폭을 벗어난 데이터를 읽지, 밴드를만 데이터가 반환 됩니다. 응용 프로그램에서 사용할 수는 **IOCtlSIOCATMARK** 옵션 또는 `OnOutOfBandData` 밴드를 더 데이터가 남아를 읽을 수 있는지 여부를 확인 하려면. `lpSockAddr` 및 `lpSockAddrLen` 에 대 한 매개 변수는 무시 **SOCK_STREAM** 소켓 합니다.  
  
 데이터 그램 소켓에 대 한 크기 지정 된 버퍼의 최대는 첫 큐에 대기 된 데이터 그램에서 데이터를 추출 합니다. 데이터 그램 지정 된 버퍼 보다 클 경우 메시지의 첫 번째 부분으로 된 버퍼가 채워집니다, 초과 데이터는 손실 및 `ReceiveFromEx` 의 값을 반환 **SOCKET_ERROR** 오류 코드로 설정  **WSAEMSGSIZE**합니다.  
  
 경우 `lpSockAddr` 이 값은 0 고 소켓 형식이 **SOCK_DGRAM**, 데이터를 보낸 소켓의 네트워크 주소에 해당 요소에 복사 되 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조입니다. 값에서 가리키는 `lpSockAddrLen` 이 구조체의 크기로으로 초기화 되 고 저장 된 주소의 실제 크기를 나타내는 반환이 수정 됩니다. 들어오는 데이터가 없는 소켓에서 사용할 수 있는 경우는 `ReceiveFromEx` 소켓이 아닌 경우 도착 하는 데이터에 대 한 호출이 대기 비블로킹 합니다. 이 경우 값은 **SOCKET_ERROR** 로 설정 하는 오류 코드와 함께 반환 되는지 **WSAEWOULDBLOCK**합니다. `OnReceive` 콜백 도착 시간을 확인할 더 많은 데이터를 사용할 수 있습니다.  
  
 소켓 형식인 경우 **SOCK_STREAM** 원격측에 연결이 정상적으로 종료, 및는 `ReceiveFromEx` 받은 0 바이트와 함께 즉시 완료 됩니다.  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 연결된 된 소켓에서 데이터를 전송 하려면이 멤버 함수를 호출 합니다.  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpBuf`  
 전송 될 데이터를 포함 하는 버퍼입니다.  
  
 `nBufLen`  
 에 있는 데이터의 길이 `lpBuf` (바이트)에서입니다.  
  
 `nFlags`  
 호출이 수행 된 방식을 지정 합니다. 이 함수의의 의미 체계 소켓 옵션에 따라 결정 되 고 `nFlags` 매개 변수. 다음 값 중 하나는 c + +와 결합 하 여 생성 되 고 후자 `OR` 연산자:  
  
- **MSG_DONTROUTE** 데이터 라우팅 적용 되어서는 안 되도록 지정 합니다. Windows 소켓 공급 업체가 제공한이이 플래그를 무시 하도록 선택할 수 있습니다.  
  
- **MSG_OOB** 밴드의 범위를 벗어난 데이터 전송 ( **SOCK_STREAM** 만).  
  
### <a name="return-value"></a>반환 값  
 오류가 발생 하지 않으면, **보낼** 전송 된 문자의 총 수를 반환 합니다. (으로 표시 된 수보다 작을 수 있습니다이 `nBufLen`.) 그렇지 않으면 값이 **SOCKET_ERROR** 반환 되 면 호출 하 여 특정 오류 코드를 검색할 수 있습니다 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEACCES** 요청된 된 주소는 브로드캐스트 주소 이지만, 적절 한 플래그 설정 되지 않았습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEFAULT** 는 `lpBuf` 인수는 사용자 주소 공간의 유효한 부분에 없습니다.  
  
- **WSAENETRESET** Windows 소켓 구현을 삭제 하기 때문에 연결을 다시 설정 해야 합니다.  
  
- `WSAENOBUFS` Windows 소켓 구현이 버퍼 교착 상태를 보고합니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP MSG_OOB** 지정 소켓 형식의 되지 않은 **SOCK_STREAM**합니다.  
  
- **WSAESHUTDOWN** 소켓이 종료 된; 호출 수 없으면 **보낼** 후 소켓에서 `ShutDown` 를 호출 했습니다 `nHow` 1 또는 2로 설정 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 및 요청 된 작업이 중단 됩니다.  
  
- **WSAEMSGSIZE** 소켓 유형임 **SOCK_DGRAM**, 데이터 그램 및 Windows 소켓 구현에서 지원 되는 최대 길이 보다 큰 합니다.  
  
- **WSAEINVAL** 소켓으로 바인딩되지 않은 **바인딩할**합니다.  
  
- **WSAECONNABORTED** 가상 회로가 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
- **WSAECONNRESET** 원격측에서 가상 회로가 재설정 되었습니다.  
  
### <a name="remarks"></a>설명  
 **보내기** 연결 된 스트림 또는 데이터 그램 소켓에 보내는 데이터를 작성 하는 데 사용 됩니다. 데이터 그램 소켓에 대 한 주의 해야 하 여 제공 된 원본으로 사용 하는 서브넷의 최대 IP 패킷 크기를 초과 하지는 **iMaxUdpDg** 요소에는 [WSADATA](../../mfc/reference/wsadata-structure.md) 에서 반환 된 구조 `AfxSocketInit`합니다. 데이터가 너무 길어 원자 단위로 오류 기본 프로토콜을 통해 전달할 경우 **WSAEMSGSIZE** 를 통해 반환 `GetLastError`, 데이터가 전송 됩니다.  
  
 데이터 그램에 소켓 성공적으로 완료 하는 **보낼** 성공적으로 전달 된 데이터를 나타내지 않습니다.  
  
 `CAsyncSocket` 유형의 개체 **SOCK_STREAM**, 쓴 바이트 수는 1부터 로컬 및 외부 호스트의 버퍼 가용성에 따라 요청 된 길이 수 있습니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CAsyncSocket::OnSend](#onsend)합니다.  
  
##  <a name="sendto"></a>  CAsyncSocket::SendTo  
 이 데이터를 특정 대상에 보내도록 함수를 호출 합니다.  
  
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
 `lpBuf`  
 전송 될 데이터를 포함 하는 버퍼입니다.  
  
 `nBufLen`  
 에 있는 데이터의 길이 `lpBuf` (바이트)에서입니다.  
  
 `nHostPort`  
 소켓 응용 프로그램을 식별 하는 포트입니다.  
  
 `lpszHostAddress`  
 이 개체가 연결 되는 소켓의 네트워크 주소: "형식인" 또는 "128.56.22.8"과 같이 점으로 구분 된 값을 같은 컴퓨터 이름입니다.  
  
 `nFlags`  
 호출이 수행 된 방식을 지정 합니다. 이 함수의의 의미 체계 소켓 옵션에 따라 결정 되 고 `nFlags` 매개 변수. 다음 값 중 하나는 c + +와 결합 하 여 생성 되 고 후자 `OR` 연산자:  
  
- **MSG_DONTROUTE** 데이터 라우팅 적용 되어서는 안 되도록 지정 합니다. Windows 소켓 공급 업체가 제공한이이 플래그를 무시 하도록 선택할 수 있습니다.  
  
- **MSG_OOB** 밴드의 범위를 벗어난 데이터 전송 ( **SOCK_STREAM** 만).  
  
 `lpSockAddr`  
 에 대 한 포인터는 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 대상 소켓의 주소를 포함 하는 구조입니다.  
  
 `nSockAddrLen`  
 주소 길이 `lpSockAddr` (바이트)에서입니다.  
  
### <a name="return-value"></a>반환 값  
 오류가 발생 하지 않으면, `SendTo` 전송 된 문자의 총 수를 반환 합니다. (으로 표시 된 수보다 작을 수 있습니다이 `nBufLen`.) 그렇지 않으면 값이 **SOCKET_ERROR** 반환 되 면 호출 하 여 특정 오류 코드를 검색할 수 있습니다 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEACCES** 요청된 된 주소는 브로드캐스트 주소 이지만, 적절 한 플래그 설정 되지 않았습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEFAULT** 는 `lpBuf` 또는 `lpSockAddr` 매개 변수는 사용자 주소 공간에 포함 되지 않은 또는 `lpSockAddr` 인수 너무 작습니다 (의 크기 보다 작은 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조).  
  
- **WSAEINVAL** 호스트 이름이 잘못 되었습니다.  
  
- **WSAENETRESET** Windows 소켓 구현을 삭제 하기 때문에 연결을 다시 설정 해야 합니다.  
  
- `WSAENOBUFS` Windows 소켓 구현이 버퍼 교착 상태를 보고합니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다 ( **SOCK_STREAM** 만).  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP MSG_OOB** 지정 소켓 형식의 되지 않은 **SOCK_STREAM**합니다.  
  
- **WSAESHUTDOWN** 소켓이 종료 된; 호출 수 없으면 `SendTo` 후 소켓에서 `ShutDown` 를 호출 했습니다 `nHow` 1 또는 2로 설정 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 및 요청 된 작업이 중단 됩니다.  
  
- **WSAEMSGSIZE** 소켓 유형임 **SOCK_DGRAM**, 데이터 그램 및 Windows 소켓 구현에서 지원 되는 최대 길이 보다 큰 합니다.  
  
- **WSAECONNABORTED** 가상 회로가 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
- **WSAECONNRESET** 원격측에서 가상 회로가 재설정 되었습니다.  
  
- **WSAEADDRNOTAVAIL** 지정한 주소는 로컬 컴퓨터 사용할 수 없습니다.  
  
- **WSAEAFNOSUPPORT** 이 소켓으로 지정 된 제품군의 주소를 사용할 수 없습니다.  
  
- **WSAEDESTADDRREQ** 대상 주소가 필요 합니다.  
  
- **WSAENETUNREACH** 지금이 호스트에서 네트워크에 연결할 수 없습니다.  
  
### <a name="remarks"></a>설명  
 `SendTo` 데이터 그램 또는 스트림 소켓에 사용 되 고 소켓에 보내는 데이터를 쓰는 데 사용 되 합니다. 데이터 그램 소켓에 대 한 주의 해야 하 여 제공 된 원본으로 사용 하는 서브넷의 최대 IP 패킷 크기를 초과 하지는 **iMaxUdpDg** 요소에는 [WSADATA](../../mfc/reference/wsadata-structure.md) 구조 여 채울 [ AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)합니다. 데이터가 너무 길어 원자 단위로 오류 기본 프로토콜을 통해 전달할 경우 **WSAEMSGSIZE** 반환 되 면 데이터가 전송 됩니다.  
  
 성공적으로 완료 한 `SendTo` 성공적으로 전달 된 데이터를 나타내지 않습니다.  
  
 `SendTo` 에 사용 되는 **SOCK_DGRAM** 는 데이터 그램을 보낼 특정 소켓으로 식별 하는 소켓의 `lpSockAddr` 매개 변수입니다.  
  
 브로드캐스트를 보내도록 (에 **SOCK_DGRAM** 만)에 있는 주소는 `lpSockAddr` 특수 IP 주소를 사용 하 여 매개 변수를 생성 해야 **INADDR_BROADCAST** (Windows 소켓 헤더에 정의 합니다. WINSOCK 파일입니다. H)와 함께 의도 한 포트 번호입니다. 또는 경우에는 `lpszHostAddress` 매개 변수는 **NULL**, 소켓 브로드캐스트에 구성 되어 있습니다. 일반적으로 조각화가 발생할 수 크기를 초과 하는 브로드캐스트 데이터 그램에 바람직하지 않습니다 데이터 그램 (머리글은 제외)의 데이터 부분 512 바이트를 넘지 않아야을 의미 합니다.  
  
 IPv6 주소를 처리 하려면 [CAsyncSocket::SendToEx](#sendtoex)합니다.  
  
##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx  
 데이터를 특정 대상 (핸들 IPv6 주소)를 전송 하려면이 멤버 함수를 호출 합니다.  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpBuf`  
 전송 될 데이터를 포함 하는 버퍼입니다.  
  
 `nBufLen`  
 에 있는 데이터의 길이 `lpBuf` (바이트)에서입니다.  
  
 `nHostPort`  
 소켓 응용 프로그램을 식별 하는 포트입니다.  
  
 `lpszHostAddress`  
 이 개체가 연결 되는 소켓의 네트워크 주소: "형식인" 또는 "128.56.22.8"과 같이 점으로 구분 된 값을 같은 컴퓨터 이름입니다.  
  
 `nFlags`  
 호출이 수행 된 방식을 지정 합니다. 이 함수의의 의미 체계 소켓 옵션에 따라 결정 되 고 `nFlags` 매개 변수. 다음 값 중 하나는 c + +와 결합 하 여 생성 되 고 후자 `OR` 연산자:  
  
- **MSG_DONTROUTE** 데이터 라우팅 적용 되어서는 안 되도록 지정 합니다. Windows 소켓 공급 업체가 제공한이이 플래그를 무시 하도록 선택할 수 있습니다.  
  
- **MSG_OOB** 밴드의 범위를 벗어난 데이터 전송 ( **SOCK_STREAM** 만).  
  
### <a name="return-value"></a>반환 값  
 오류가 발생 하지 않으면, `SendToEx` 전송 된 문자의 총 수를 반환 합니다. (으로 표시 된 수보다 작을 수 있습니다이 `nBufLen`.) 그렇지 않으면 값이 **SOCKET_ERROR** 반환 되 면 호출 하 여 특정 오류 코드를 검색할 수 있습니다 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEACCES** 요청된 된 주소는 브로드캐스트 주소 이지만, 적절 한 플래그 설정 되지 않았습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEFAULT** 는 `lpBuf` 또는 `lpSockAddr` 매개 변수는 사용자 주소 공간에 포함 되지 않은 또는 `lpSockAddr` 인수 너무 작습니다 (의 크기 보다 작은 [SOCKADDR](../../mfc/reference/sockaddr-structure.md) 구조).  
  
- **WSAEINVAL** 호스트 이름이 잘못 되었습니다.  
  
- **WSAENETRESET** Windows 소켓 구현을 삭제 하기 때문에 연결을 다시 설정 해야 합니다.  
  
- `WSAENOBUFS` Windows 소켓 구현이 버퍼 교착 상태를 보고합니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다 ( **SOCK_STREAM** 만).  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
- **WSAEOPNOTSUPP MSG_OOB** 지정 소켓 형식의 되지 않은 **SOCK_STREAM**합니다.  
  
- **WSAESHUTDOWN** 소켓이 종료 된; 호출 수 없으면 `SendToEx` 후 소켓에서 `ShutDown` 를 호출 했습니다 `nHow` 1 또는 2로 설정 합니다.  
  
- **WSAEWOULDBLOCK** 소켓 표시 되어 같이 비블로킹 및 요청 된 작업이 중단 됩니다.  
  
- **WSAEMSGSIZE** 소켓 유형임 **SOCK_DGRAM**, 데이터 그램 및 Windows 소켓 구현에서 지원 되는 최대 길이 보다 큰 합니다.  
  
- **WSAECONNABORTED** 가상 회로가 시간 초과 또는 기타 오류로 인해 중단 되었습니다.  
  
- **WSAECONNRESET** 원격측에서 가상 회로가 재설정 되었습니다.  
  
- **WSAEADDRNOTAVAIL** 지정한 주소는 로컬 컴퓨터 사용할 수 없습니다.  
  
- **WSAEAFNOSUPPORT** 이 소켓으로 지정 된 제품군의 주소를 사용할 수 없습니다.  
  
- **WSAEDESTADDRREQ** 대상 주소가 필요 합니다.  
  
- **WSAENETUNREACH** 지금이 호스트에서 네트워크에 연결할 수 없습니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 동일 [CAsyncSocket::SendTo](#sendto) IPv6 처리 한다는 점을 제외 하면 오래 된 파일로 프로토콜을 해결 합니다.  
  
 `SendToEx` 데이터 그램 또는 스트림 소켓에 사용 되 고 소켓에 보내는 데이터를 쓰는 데 사용 되 합니다. 데이터 그램 소켓에 대 한 주의 해야 하 여 제공 된 원본으로 사용 하는 서브넷의 최대 IP 패킷 크기를 초과 하지는 **iMaxUdpDg** 요소에는 [WSADATA](../../mfc/reference/wsadata-structure.md) 구조 여 채울 [ AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)합니다. 데이터가 너무 길어 원자 단위로 오류 기본 프로토콜을 통해 전달할 경우 **WSAEMSGSIZE** 반환 되 면 데이터가 전송 됩니다.  
  
 성공적으로 완료 한 `SendToEx` 성공적으로 전달 된 데이터를 나타내지 않습니다.  
  
 `SendToEx` 에 사용 되는 **SOCK_DGRAM** 는 데이터 그램을 보낼 특정 소켓으로 식별 하는 소켓의 `lpSockAddr` 매개 변수입니다.  
  
 브로드캐스트를 보내도록 (에 **SOCK_DGRAM** 만)에 있는 주소는 `lpSockAddr` 특수 IP 주소를 사용 하 여 매개 변수를 생성 해야 **INADDR_BROADCAST** (Windows 소켓 헤더에 정의 합니다. WINSOCK 파일입니다. H)와 함께 의도 한 포트 번호입니다. 또는 경우에는 `lpszHostAddress` 매개 변수는 **NULL**, 소켓 브로드캐스트에 구성 되어 있습니다. 일반적으로 조각화가 발생할 수 크기를 초과 하는 브로드캐스트 데이터 그램에 바람직하지 않습니다 데이터 그램 (머리글은 제외)의 데이터 부분 512 바이트를 넘지 않아야을 의미 합니다.  
  
##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt  
 이 소켓 옵션을 설정 하려면 함수를 호출 합니다.  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>매개 변수  
 `nOptionName`  
 값이 설정 되어야 하는 소켓 옵션입니다.  
  
 `lpOptionValue`  
 요청된 된 옵션에 대 한 값은 지정 된 버퍼에 대 한 포인터입니다.  
  
 `nOptionLen`  
 크기는 `lpOptionValue` 버퍼의 바이트입니다.  
  
 `nLevel`  
 정의 된 수준에는 옵션은; 지원 되는 유일한 수준 **SOL_SOCKET** 및 **IPPROTO_TCP**합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEFAULT** `lpOptionValue` 프로세스 주소 공간의 유효한 부분에 아닙니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAEINVAL** `nLevel` 유효 하지 않을 경우 또는에 있는 정보 `lpOptionValue` 올바르지 않습니다.  
  
- **WSAENETRESET** 연결 시간이 초과 될 때 **SO_KEEPALIVE** 설정 됩니다.  
  
- **WSAENOPROTOOPT** 알 수 없거나 지원 되지 않는 옵션입니다. 특히, **SO_BROADCAST** 형식의 소켓에서 지원 되지 않습니다 **SOCK_STREAM**, 동안 **SO_DONTLINGER**, **SO_KEEPALIVE**,  **SO_LINGER**, 및 **SO_OOBINLINE** 형식의 소켓에서 지원 되지 않습니다 **SOCK_DGRAM**합니다.  
  
- **WSAENOTCONN** 연결이 다시 설정 될 때 **SO_KEEPALIVE** 설정 됩니다.  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 `SetSockOpt` 모든 상태에서 모든 형식의 소켓와 연결 된 소켓 옵션에 대 한 현재 값을 설정 합니다. 여러 프로토콜 수준에서 옵션 수 있어도이 사양은 맨 위 "소켓" 수준에 존재 하는 옵션을 정의 합니다. 옵션 여부 브로드캐스트 메시지는 소켓에 보낼 수 있습니다 및 등 일반 데이터 스트림의 발송 된 데이터가 수신 되는 여부와 같은 소켓 작업을 영향을 줍니다.  
  
 소켓 옵션에 두 가지: 기능 또는 동작을 활성화 또는 비활성화 하는 부울 옵션 및 옵션은 정수 값 또는 구조를 요구 합니다. 부울 옵션을 사용 하도록 설정 하려면 `lpOptionValue` 0이 아닌 정수를 가리킵니다. 옵션을 사용 하지 않도록 설정 하려면 `lpOptionValue` 0과 같은 정수를 가리킵니다. `nOptionLen` 같아야 하 **sizeof(BOOL)** 부울 옵션에 대 한 합니다. 다른 옵션에 대 한 `lpOptionValue` 클래스 또는 구조체에 대 한 옵션을 원하는 값을 포함 하는 정수를 가리키는 및 `nOptionLen` 시간은 클래스 또는 구조체는 정수입니다.  
  
 **SO_LINGER** 때 수행 되는 작업 보내지 데이터는 큐에 대기 소켓에서 컨트롤 및 **닫습니다** 소켓을 닫을 수 함수를 호출 합니다.  
  
 기본적으로 소켓을 바인딩할 수 없습니다 (참조 [바인딩할](#bind))은 이미 사용 되는 로컬 주소입니다. 그러나 경우에 따라는 것이 좋습니다 이러한 방식으로 주소를 "다시"입니다. 없기 때문에 모든 연결이 로컬 및 원격 주소의 조합으로 고유 하 게 식별 됩니다, 원격 주소는 다른으로 동일한 로컬 주소에 바인딩된 두 개의 소켓을 사용 하 여 문제가 되지 않습니다.  
  
 Windows 소켓을 알리기 위해 하 한 **바인딩할** 소켓에서 호출 하 여 원하는 주소 이미 다른 소켓에서 사용 중 이므로 허용 되지 해야 응용 프로그램 설정 해야 합니다는 **SO_REUSEADDR**소켓 옵션은 소켓에 대해 실행 하기 전에 **바인딩할** 호출 합니다. 옵션의 시에만 해석 됩니다는 **바인딩할** 호출: 필요한 경우가 아니라면 따라서 심각해) (않음 하지는 기존 주소에 바인딩해야 하는 소켓 옵션을 설정 하려면 및 설정 하거나 다시 설정 후 옵션은 **바인딩할** 호출에 다른 소켓 또는이에 영향을 주지 않습니다.  
  
 Windows 소켓 구현이 설정 하 여 "연결 유지" 패킷이 전송 TCP (Control Protocol) 연결에 사용 하도록 설정할 응용 프로그램이 요청할 수는 **SO_KEEPALIVE** 소켓 옵션입니다. Windows 소켓 구현이 필요 keep-alive의 사용을 지원 하지: 정확한 의미는 구현과 관련 있지만 4.2.3.6 RFC 1122의를 준수 해야 헤더가 있으면: "인터넷 호스트에 대 한 요구 사항 — 통신 계층입니다." 연결이 끊어질 경우 "연결 유지"의 결과로 오류 코드 **WSAENETRESET** 소켓에서 진행 중인 모든 호출에 반환 되 고 이후의 모든 호출와 함께 실패 합니다 **WSAENOTCONN**합니다.  
  
 **TCP_NODELAY** 옵션 Nagle 알고리즘을 비활성화 합니다. Nagle 알고리즘은 전체 크기 패킷을 보낼 수 있습니다 때까지 승인 되지 않은 송신 데이터를 버퍼링 하 여 호스트를 통해 전송 된 작은 패킷의 수를 줄이기 위해 사용 됩니다. 그러나 일부 응용 프로그램에 대 한이 알고리즘에 방해가 될 수 성능 및 **TCP_NODELAY** 는 기능을 해제 하는 데 사용할 수 있습니다. 응용 프로그램 기록기를 설정 하지 않아야 **TCP_NODELAY** 아닌 경우이 따른 영향을 잘 이해 하 고 원하는 설정을 이후 **TCP_NODELAY** 네트워크 성능에 중요 한 부정적인 영향을 미칠 수 있습니다 . **TCP_NODELAY** 는 유일 하 게 지원 되는 수준을 사용 하는 소켓 옵션 **IPPROTO_TCP**; 다른 모든 옵션에 수준을 사용 하 여 **SOL_SOCKET**합니다.  
  
 Windows 소켓 중 일부 구현의 경우에 디버그 정보를 출력는 **SO_DEBUG** 옵션은 응용 프로그램으로 설정 합니다.  
  
 에 대해 다음 옵션은 지원 `SetSockOpt`합니다. 형식으로 주소가 지정 된 데이터의 형식을 식별 `lpOptionValue`합니다.  
  
|값|형식|의미|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|소켓의 브로드캐스트 메시지의 전송을 허용 합니다.|  
|**SO_DEBUG**|**BOOL**|디버깅 정보를 기록합니다.|  
|**SO_DONTLINGER**|**BOOL**|차단 되지 않도록 **닫기** 보내지 않은 데이터를 보낼 수에 대 한 대기 합니다. 이 옵션을 설정 하는 것이 설정에 해당 하 **SO_LINGER** 와 **l_onoff** 0으로 설정 합니다.|  
|**SO_DONTROUTE**|**BOOL**|라우팅할 안 함: 인터페이스에 직접 보내기.|  
|**SO_KEEPALIVE**|**BOOL**|연결 유지 메시지를 보냅니다.|  
|**SO_LINGER**|**LINGER 구조체**|지연 됩니다 **닫기** 데이터는 보내지 않은 경우.|  
|**SO_OOBINLINE**|**BOOL**|정상 데이터 스트림에 대역폭을 벗어난 데이터를 수신 합니다.|  
|**SO_RCVBUF**|`int`|수신 버퍼 크기를 지정 합니다.|  
|**SO_REUSEADDR**|**BOOL**|소켓에 이미 사용 되는 주소에 바인딩할 수를 허용 합니다. (참조 [바인딩할](#bind).)|  
|**SO_SNDBUF**|`int`|전송에 대 한 버퍼 크기를 지정 합니다.|  
|**TCP_NODELAY**|**BOOL**|보내기 통합을 위해 Nagle 알고리즘을 비활성화합니다.|  
  
 에 대 한 지원 되지 않는 Berkeley 소프트웨어 배포 (BSD) 옵션 `SetSockOpt` 됩니다.  
  
|값|형식|의미|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|소켓이 수신 중입니다.|  
|**SO_ERROR**|`int`|오류 상태를 가져오고의 선택을 취소 합니다.|  
|**SO_RCVLOWAT**|`int`|하위 워터 마크를 수신 합니다.|  
|**SO_RCVTIMEO**|`int`|시간 초과가 수신|  
|**SO_SNDLOWAT**|`int`|하위 워터 마크를 보냅니다.|  
|**SO_SNDTIMEO**|`int`|제한 시간을 보냅니다.|  
|**SO_TYPE**|`int`|소켓의 형식입니다.|  
|**IP_OPTIONS**||IP 헤더에 옵션 필드를 설정 합니다.|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 사용 하지 않도록 설정 하려면이 멤버 함수를 통해로 호출 받는 소켓에 또는 둘 다 합니다.  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>매개 변수  
 `nHow`  
 어떤 유형의 작업에 설명 하는 플래그를 더 이상 허용 되도록 다음 열거형된 값을 사용 하 여:  
  
- **수신 = 0**  
  
- **보냅니다 = 1**  
  
- **모두 = 2**  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 0이 아닌 0이 고, 특정 오류 코드를 호출 하 여 검색할 수 있습니다 그렇지 않으면 [GetLastError](#getlasterror)합니다. 이 멤버 함수에 다음과 같은 오류가 적용 됩니다.  
  
- **WSANOTINITIALISED** 성공적인 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 이 API를 사용 하기 전에 발생 해야 합니다.  
  
- **WSAENETDOWN** The Windows 소켓 구현이 네트워크 하위 시스템의 실패 했음을 검색 했습니다.  
  
- **WSAEINVAL** `nHow` 올바르지 않습니다.  
  
- **WSAEINPROGRESS** 차단 Windows 소켓 작업이 진행 중입니다.  
  
- **WSAENOTCONN** 소켓 연결 되어 있지 않습니다 ( **SOCK_STREAM** 만).  
  
- **WSAENOTSOCK** 설명자 소켓 아닙니다.  
  
### <a name="remarks"></a>설명  
 `ShutDown` आ स ा, 전송, 또는 둘 다 사용 하지 않도록 설정 하는 소켓의 모든 형식에 사용 됩니다. 경우 `nHow` 0 일에서 받는 후속 소켓을 사용할 수 없습니다. 이 구문은 아무 효과가 하위 프로토콜 계층에 있습니다.  
  
 에 대 한 프로토콜 TCP (Transmission Control), TCP 창 변경 되지 않은 들어오는 유지 되며 데이터가 창이 가득 찰 때까지 하지 확인) (않음 허용 합니다. 에 대 한 프로토콜 UDP (User Datagram), 들어오는 데이터 그램은 허용 되 고 큐에 대기 합니다. 없는 경우 오류 ICMP 패킷을 생성 됩니다. 경우 `nHow` 는 1, 후속 보냅니다는 허용 되지 않습니다. TCP 소켓에 대 한 한 FIN 전송 됩니다. 설정 `nHow` 2를 모두 사용 하지 않도록 설정 하 고 위에서 설명한 대로 받습니다.  
  
 `ShutDown` 않습니다 하지 닫기 소켓과 소켓에 연결 된 리소스가 해제 되지 것입니다까지 **닫습니다** 호출 됩니다. 응용 프로그램을 종료 한 후에 소켓을 다시 사용 되지는지 않습니다. 사용을 지 원하는 Windows 소켓 구현이 필요 하지는 특히 **연결** 이러한 소켓에 있습니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CAsyncSocket::OnReceive](#onreceive)합니다.  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 소켓 핸들을 할당합니다.  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>매개 변수  
 `nSocketType`  
 지정 `SOCK_STREAM` 또는 `SOCK_DGRAM`합니다.  
  
 `lEvent`  
 응용 프로그램 interested가 네트워크 이벤트의 조합을 지정 하는 비트 마스크입니다.  
  
- `FD_READ`:를 읽기 위한 준비 상태에 대 한 알림을 보낼입니다.  
  
- `FD_WRITE`:를 작성 하기 위한 준비에 대 한 알림을 보낼입니다.  
  
- `FD_OOB`: 밴드의 범위를 벗어난 데이터의 도착에 대 한 알림을 수신 하려고 합니다.  
  
- `FD_ACCEPT`:를 들어오는 연결에 대 한 알림을 보낼입니다.  
  
- `FD_CONNECT`: 완료 된 연결에 대 한 알림을 수신 하려고 합니다.  
  
- `FD_CLOSE`: 소켓 닫기를 처리에 대 한 알림을 수신 하려고 합니다.  
  
 `nProtocolType`  
 표시 된 주소 패밀리에만 적용 되는 소켓에서 사용 되는 프로토콜입니다.  
  
 `nAddressFormat`  
 주소 패밀리 사양입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 `TRUE`를 반환하고 실패하면 `FALSE`를 반환합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 소켓 핸들을 할당합니다. 호출 하지 않습니다 [CAsyncSocket::Bind](#bind) 소켓을 바인딩하지 지정된 된 주소에를 호출 해야 하므로 `Bind` 나중 소켓을 바인딩하지 지정된 된 주소에 있습니다. 사용할 수 있습니다 [CAsyncSocket::SetSockOpt](#setsockopt) 연결 되기 전에 소켓 옵션을 설정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CObject 클래스](../../mfc/reference/cobject-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CSocket 클래스](../../mfc/reference/csocket-class.md)   
 [CSocketFile 클래스](../../mfc/reference/csocketfile-class.md)
