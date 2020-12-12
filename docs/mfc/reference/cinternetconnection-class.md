---
description: CInternetConnection 클래스에 대해 자세히 알아보세요.
title: CInternetConnection 클래스
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 2ae869e8cbf3bbfb3ce19e78088a465ae1d6aa65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143548"
---
# <a name="cinternetconnection-class"></a>CInternetConnection 클래스

인터넷 서버와의 연결을 관리합니다.

## <a name="syntax"></a>구문

```
class CInternetConnection : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CInternetConnection:: CInternetConnection](#cinternetconnection)|`CInternetConnection` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CInternetConnection:: GetContext](#getcontext)|이 연결 개체의 컨텍스트 ID를 가져옵니다.|
|[CInternetConnection:: GetServerName](#getservername)|연결과 관련 된 서버의 이름을 가져옵니다.|
|[CInternetConnection:: GetSession](#getsession)|연결과 관련 된 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에 대 한 포인터를 가져옵니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CInternetConnection:: operator HINTERNET](#operator_hinternet)|인터넷 세션에 대 한 핸들입니다.|

## <a name="remarks"></a>설명

이 클래스는 MFC 클래스 [cCHttpConnection connection](../../mfc/reference/cftpconnection-class.md), [](../../mfc/reference/chttpconnection-class.md)및 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)에 대 한 기본 클래스입니다. 이러한 각 클래스는 해당 FTP, HTTP 또는 gopher 서버와 통신 하기 위한 추가 기능을 제공 합니다.

인터넷 서버와 직접 통신 하려면 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체와 개체가 있어야 합니다 `CInternetConnection` .

WinInet 클래스의 작동 방식에 대 한 자세한 내용은 [wininet을 사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a> CInternetConnection:: CInternetConnection

이 멤버 함수는 개체를 만들 때 호출 됩니다 `CInternetConnection` .

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pSession*<br/>
[Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에 대 한 포인터입니다.

*pstrServer*<br/>
서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*nPort*<br/>
이 연결에 대 한 인터넷 포트를 식별 하는 번호입니다.

*dwContext*<br/>
개체에 대 한 컨텍스트 식별자 `CInternetConnection` 입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

### <a name="remarks"></a>설명

직접 호출 하지는 않습니다 `CInternetConnection` . 대신 설정 하려는 연결 형식에 대 한 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 멤버 함수를 호출 합니다.

- [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

*Dwcontext* 의 기본값은 `CInternetConnection` **internetconnection** 파생 개체를 만든 [CINTERNETSESSION](../../mfc/reference/cinternetsession-class.md) 개체에서 파생 된 개체로 MFC에 전송 됩니다. 기본값은 1로 설정 됩니다. 그러나 연결에 대 한 [Cinternetsession](../../mfc/reference/cinternetsession-class.md#cinternetsession) 생성자에서 특정 컨텍스트 식별자를 명시적으로 할당할 수 있습니다. 개체와 해당 개체에서 수행 하는 모든 작업은 해당 컨텍스트 ID와 연결 됩니다. 컨텍스트 식별자가 식별 된 개체에 대 한 상태를 제공 하기 위해 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 됩니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a> CInternetConnection:: GetContext

이 멤버 함수를 호출 하 여이 세션의 컨텍스트 ID를 가져옵니다.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>반환 값

응용 프로그램에서 할당 한 컨텍스트 ID입니다.

### <a name="remarks"></a>설명

컨텍스트 ID는 원래 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 에 지정 되 고, `CInternetConnection` 연결을 여는 함수에 대 한 호출에 다르게 지정 되지 않는 한-및 [cinternetsession](../../mfc/reference/cinternetfile-class.md)파생 클래스에 전파 됩니다. 컨텍스트 ID는 지정 된 개체의 작업과 연결 되며 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)에서 반환 된 작업 상태 정보를 식별 합니다.

에서 다른 WinInet 클래스를 사용 하 여 사용자 상태 정보를 제공 하는 방법에 대 한 자세한 내용은 `GetContext` [인터넷 첫 번째 단계: WinInet](../../mfc/wininet-basics.md) 에서 컨텍스트 식별자에 대 한 자세한 내용을 참조 하세요.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a> CInternetConnection:: GetServerName

이 멤버 함수를 호출 하 여이 인터넷 연결과 관련 된 서버의 이름을 가져옵니다.

```
CString GetServerName() const;
```

### <a name="return-value"></a>반환 값

이 연결 개체가 사용 되는 서버의 이름입니다.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a> CInternetConnection:: GetSession

이 멤버 함수를 호출 하 여이 연결과 관련 된 개체에 대 한 포인터를 가져옵니다 `CInternetSession` .

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>반환 값

이 인터넷 연결 개체와 연결 된 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에 대 한 포인터입니다.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a> CInternetConnection:: operator HINTERNET

이 연산자를 사용 하 여 현재 인터넷 세션에 대 한 API 수준 핸들을 가져옵니다.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
