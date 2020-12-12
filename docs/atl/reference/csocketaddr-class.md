---
description: '자세한 정보: CSocketAddr 클래스'
title: CSocketAddr 클래스
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: eff93b6a8e6d0ea487e3571cd52973d9e17115d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140531"
---
# <a name="csocketaddr-class"></a>CSocketAddr 클래스

이 클래스는 호스트 이름을 호스트 주소로 변환 하 고 IPv4 및 IPV6 형식을 둘 다 지원 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CSocketAddr
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSocketAddr:: CSocketAddr](#csocketaddr)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSocketAddr:: FindAddr](#findaddr)|제공 된 호스트 이름을 호스트 주소로 변환 하려면이 메서드를 호출 합니다.|
|[CSocketAddr:: FindINET4Addr](#findinet4addr)|IPv4 호스트 이름을 호스트 주소로 변환 하려면이 메서드를 호출 합니다.|
|[CSocketAddr:: FindINET6Addr](#findinet6addr)|IPv6 호스트 이름을 호스트 주소로 변환 하려면이 메서드를 호출 합니다.|
|[CSocketAddr:: GetAddrInfo](#getaddrinfo)|목록의 특정 요소에 대 한 포인터를 반환 하려면이 메서드를 호출 `addrinfo` 합니다.|
|[CSocketAddr:: GetAddrInfoList](#getaddrinfolist)|목록에 대 한 포인터를 반환 하려면이 메서드를 호출 `addrinfo` 합니다.|

## <a name="remarks"></a>설명

이 클래스는 Windows 소켓 API 함수 및 라이브러리의 소켓 래퍼에 사용할 네트워크 주소를 조회 하는 IP 버전에 관계 없는 방법을 제공 합니다.

네트워크 주소를 조회 하는 데 사용 되는이 클래스의 멤버는 Win32 API 함수 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)을 사용 합니다. Ansi 또는 유니코드 버전의 함수는 코드가 ANSI 또는 유니코드에 대해 컴파일 되었는지 여부에 따라 호출 됩니다.

이 클래스는 IPv4 andIPv6 네트워크 주소를 모두 지원 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a> CSocketAddr:: CSocketAddr

생성자입니다.

```
CSocketAddr();
```

### <a name="remarks"></a>설명

새 개체를 만들고 `CSocketAddr` 호스트에 대 한 응답 정보를 포함 하는 연결 된 목록을 초기화 합니다.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a> CSocketAddr:: FindAddr

제공 된 호스트 이름을 호스트 주소로 변환 하려면이 메서드를 호출 합니다.

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>매개 변수

*szHost*<br/>
호스트 이름 또는 점으로 표시 되는 IP 주소입니다.

*szPortOrServiceName*<br/>
호스트의 포트 번호 또는 서비스 이름입니다.

*nPortNo*<br/>
포트 번호.

*flags*<br/>
0 또는 AI_PASSIVE AI_CANONNAME 또는 AI_NUMERICHOST 조합입니다.

*addr_family*<br/>
주소 패밀리 (예: PF_INET).

*sock_type*<br/>
소켓 유형 (예: SOCK_STREAM).

*ai_proto*<br/>
프로토콜 (예: IPPROTO_IP 또는 IPPROTO_IPV6).

### <a name="return-value"></a>반환 값

주소가 성공적으로 계산 되 면 0을 반환 합니다. 오류가 발생 하면 0이 아닌 Windows 소켓 오류 코드를 반환 합니다. 성공 하면 계산 된 주소가 및를 사용 하 여 참조 될 수 있는 연결 된 목록에 저장 됩니다 `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo` .

### <a name="remarks"></a>설명

호스트 이름 매개 변수는 IPv4 또는 IPv6 형식일 수 있습니다. 이 메서드 Win32 API는 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) 함수를 호출 하 여 변환을 수행 합니다.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a> CSocketAddr:: FindINET4Addr

IPv4 호스트 이름을 호스트 주소로 변환 하려면이 메서드를 호출 합니다.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>매개 변수

*szHost*<br/>
호스트 이름 또는 점으로 표시 되는 IP 주소입니다.

*nPortNo*<br/>
포트 번호.

*flags*<br/>
0 또는 AI_PASSIVE AI_CANONNAME 또는 AI_NUMERICHOST 조합입니다.

*sock_type*<br/>
소켓 유형 (예: SOCK_STREAM).

### <a name="return-value"></a>반환 값

주소가 성공적으로 계산 되 면 0을 반환 합니다. 오류가 발생 하면 0이 아닌 Windows 소켓 오류 코드를 반환 합니다. 성공 하면 계산 된 주소가 및를 사용 하 여 참조 될 수 있는 연결 된 목록에 저장 됩니다 `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo` .

### <a name="remarks"></a>설명

이 메서드 Win32 API는 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) 함수를 호출 하 여 변환을 수행 합니다.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a> CSocketAddr:: FindINET6Addr

IPv6 호스트 이름을 호스트 주소로 변환 하려면이 메서드를 호출 합니다.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>매개 변수

*szHost*<br/>
호스트 이름 또는 점으로 표시 되는 IP 주소입니다.

*nPortNo*<br/>
포트 번호.

*flags*<br/>
0 또는 AI_PASSIVE AI_CANONNAME 또는 AI_NUMERICHOST 조합입니다.

*sock_type*<br/>
소켓 유형 (예: SOCK_STREAM).

### <a name="return-value"></a>반환 값

주소가 성공적으로 계산 되 면 0을 반환 합니다. 오류가 발생 하면 0이 아닌 Windows 소켓 오류 코드를 반환 합니다. 성공 하면 계산 된 주소가 및를 사용 하 여 참조 될 수 있는 연결 된 목록에 저장 됩니다 `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo` .

### <a name="remarks"></a>설명

이 메서드 Win32 API는 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) 함수를 호출 하 여 변환을 수행 합니다.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a> CSocketAddr:: GetAddrInfo

목록의 특정 요소에 대 한 포인터를 반환 하려면이 메서드를 호출 `addrinfo` 합니다.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
[Addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow) 목록에 있는 특정 요소에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

`addrinfo`호스트에 대 한 응답 정보를 포함 하는 연결 된 목록의 *n 인덱스* 에서 참조 하는 구조에 대 한 포인터를 반환 합니다.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a> CSocketAddr:: GetAddrInfoList

목록에 대 한 포인터를 반환 하려면이 메서드를 호출 `addrinfo` 합니다.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>반환 값

`addrinfo`호스트에 대 한 응답 정보를 포함 하는 하나 이상의 구조체의 연결 된 목록에 대 한 포인터입니다. 자세한 내용은 [addrinfo 구조체](/windows/win32/api/ws2def/ns-ws2def-addrinfow)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
