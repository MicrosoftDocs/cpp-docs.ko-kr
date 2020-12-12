---
description: '다음에 대 한 자세한 정보: CFtpConnection 클래스'
title: CFtpConnection 클래스
ms.date: 08/29/2019
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: 97c7c848a5724a670f324e1d1d26ea781265be27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184259"
---
# <a name="cftpconnection-class"></a>CFtpConnection 클래스

인터넷 서버에 대 한 FTP 연결을 관리 하 고 해당 서버에서 디렉터리 및 파일을 직접 조작할 수 있습니다.

## <a name="syntax"></a>구문

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFtpConnection:: CFtpConnection](#cftpconnection)|`CFtpConnection` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFtpConnection:: Command](#command)|FTP 서버에 직접 명령을 보냅니다.|
|[CFtpConnection:: CreateDirectory](#createdirectory)|서버에 디렉터리를 만듭니다.|
|[CFtpConnection:: GetCurrentDirectory](#getcurrentdirectory)|이 연결의 현재 디렉터리를 가져옵니다.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|이 연결의 현재 디렉터리를 URL로 가져옵니다.|
|[CFtpConnection:: GetFile](#getfile)|연결 된 서버에서 파일을 가져옵니다.|
|[Csystem.windows.forms.openfiledialog.openfile Connection::](#openfile)|연결 된 서버에서 파일을 엽니다.|
|[CFtpConnection::P utFile](#putfile)|서버에 파일을 배치 합니다.|
|[CFtpConnection:: Remove](#remove)|서버에서 파일을 제거 합니다.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|지정 된 디렉터리를 서버에서 제거 합니다.|
|[CFtpConnection::Rename](#rename)|서버에서 파일의 이름을 바꿉니다.|
|[CSetCurrentDirectory Connection::](#setcurrentdirectory)|현재 FTP 디렉터리를 설정 합니다.|

## <a name="remarks"></a>설명

FTP는 MFC WinInet 클래스에서 인식 하는 세 가지 인터넷 서비스 중 하나입니다.

FTP 인터넷 서버와 통신 하려면 먼저 [Cinternetsession](../../mfc/reference/cinternetsession-class.md)의 인스턴스를 만든 다음 개체를 만들어야 합니다 `CFtpConnection` . 개체를 직접 만들지는 않습니다. 대신 개체를 `CFtpConnection` 만들고 해당 개체에 대 한 포인터를 반환 하는 [Cinternetsession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)을 호출 `CFtpConnection` 합니다.

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CFtpConnection` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요. 지원 되는 다른 두 서비스 (HTTP 및 gopher)와 통신 하는 방법에 대 한 자세한 내용은 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 및 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)클래스를 참조 하세요.

## <a name="example"></a>예제

  [Cftpfilefind](../../mfc/reference/cftpfilefind-class.md) 클래스 개요의 예제를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a> CFtpConnection:: CFtpConnection

이 멤버 함수를 호출 하 여 개체를 생성 `CFtpConnection` 합니다.

```
CFtpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CFtpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>매개 변수

*pSession*<br/>
관련 된 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에 대 한 포인터입니다.

*hConnected*<br/>
현재 인터넷 세션의 창 핸들입니다.

*pstrServer*<br/>
FTP 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwContext*<br/>
작업에 대 한 컨텍스트 식별자입니다. *Dwcontext* 는 [Cinternetsession:: onstatuscallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)에서 반환 하는 작업의 상태 정보를 식별 합니다. 기본값은 1로 설정 됩니다. 그러나 작업에 대해 특정 컨텍스트 ID를 명시적으로 할당할 수 있습니다. 개체와 해당 개체에서 수행 하는 모든 작업은 해당 컨텍스트 ID와 연결 됩니다.

*pstrUserName*<br/>
로그인 할 사용자의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. NULL 인 경우 기본값은 anonymous입니다.

*pstrPassword*<br/>
로그인 하는 데 사용할 암호를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. *Pstrpassword* 와 *pstrpassword* 이 모두 NULL 인 경우 기본 익명 암호는 사용자의 전자 메일 이름입니다. *Pstrpassword* 가 null 또는 빈 문자열이 고 *PSTRPASSWORD* 이 null이 아닌 경우 빈 암호가 사용 됩니다. 다음 표에서는 *Pstrusername* 및 *pstrusername* 의 네 가지 가능한 설정에 대 한 동작을 설명 합니다.

|*pstrUserName*|*pstrPassword*|FTP 서버에 전송 되는 사용자 이름|FTP 서버로 보낸 암호|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 또는 ""|NULL 또는 ""|"anonymous"|사용자의 전자 메일 이름|
|NULL이 아닌 문자열|NULL 또는 ""|*pstrUserName*|" "|
|Null이 아닌 NULL 문자열입니다.|오류|오류||
|NULL이 아닌 문자열|NULL이 아닌 문자열|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
서버에서 사용할 TCP/IP 포트를 식별 하는 번호입니다.

*bPassive*<br/>
이 FTP 세션의 수동 또는 활성 모드를 지정 합니다. TRUE로 설정 된 경우 Win32 API *Dwflag* 를 INTERNET_FLAG_PASSIVE로 설정 합니다.

### <a name="remarks"></a>설명

개체를 직접 만들지는 않습니다 `CFtpConnection` . 대신, 개체를 만드는 [Cinternetsession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)을 호출 `CFptConnection` 합니다.

## <a name="cftpconnectioncommand"></a><a name="command"></a> CFtpConnection:: Command

FTP 서버에 직접 명령을 보냅니다.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pszCommand*<br/>
보낼 명령을 포함하는 문자열에 대한 포인터입니다.

*eResponse*<br/>
FTP 서버에서 응답이 필요한 지 여부를 지정 합니다. 다음 값 중 하나일 수 있습니다.

- `CmdRespNone` 응답이 필요 하지 않습니다.
- `CmdRespRead` 응답이 필요 합니다.
- `CmdRespWrite` 사용 되지 않습니다.

CmdResponseType은 *afxinet.h* 에 정의 된 CFtpConnection의 멤버입니다.

*dwFlags*<br/>
이 함수를 제어하는 플래그를 포함하는 값입니다. 전체 목록은 [이 항목을 참조 하세요.](/windows/win32/api/wininet/nf-wininet-ftpcommandw)

*dwContext*<br/>
콜백에서 애플리케이션 컨텍스트를 식별하는 데 사용되는 애플리케이션 정의 값을 포함하는 값에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 [함수는 Windows SDK](/windows/win32/api/wininet/nf-wininet-ftpcommandw) 에 설명 된 대로 기능 기능을 에뮬레이션 합니다.

오류가 발생 하는 경우 MFC는 [Cinternetexception](../../mfc/reference/cinternetexception-class.md)형식의 예외를 throw 합니다.

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a> CFtpConnection:: CreateDirectory

이 멤버 함수를 호출 하 여 연결 된 서버에 디렉터리를 만듭니다.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>매개 변수

*pstrDirName*<br/>
만들 디렉터리의 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Windows 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

`GetCurrentDirectory`서버에 대 한이 연결에 대 한 현재 작업 디렉터리를 확인 하는 데 사용 합니다. 원격 시스템이 루트 디렉터리에 연결 되어 있다고 가정 하지 마십시오.

`pstrDirName`매개 변수는 현재 디렉터리를 기준으로 하는 부분 또는 정규화 된 파일 이름 중 하나일 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `CreateDirectory` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a> CFtpConnection:: GetCurrentDirectory

이 멤버 함수를 호출 하 여 현재 디렉터리의 이름을 가져옵니다.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>매개 변수

*strDirName*<br/>
디렉터리의 이름을 받는 문자열에 대 한 참조입니다.

*pstrDirName*<br/>
디렉터리의 이름을 받는 문자열에 대 한 포인터입니다.

*lpdwLen*<br/>
다음 정보를 포함 하는 DWORD에 대 한 포인터입니다.

On entry: *Pstrdirname* 에서 참조 하는 버퍼의 크기입니다.

반환 시: *Pstrdirname* 에 저장 된 문자 수입니다. 멤버 함수가 실패 하 고 ERROR_INSUFFICIENT_BUFFER 반환 되 면, *lpdwLen* 는 응용 프로그램에서 문자열을 받기 위해 할당 해야 하는 바이트 수를 포함 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

대신 디렉터리 이름을 URL로 가져오려면 [Getcurrentdirectoryasurl](#getcurrentdirectoryasurl)을 호출 합니다.

*Pstrdirname* 또는 *strdiname* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적으로 정규화 된 파일 이름일 수도 있고 정규화 된 이름일 수도 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `GetCurrentDirectory` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a> CFtpConnection:: GetCurrentDirectoryAsURL

이 멤버 함수를 호출 하 여 현재 디렉터리의 이름을 URL로 가져옵니다.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>매개 변수

*strDirName*<br/>
디렉터리의 이름을 받는 문자열에 대 한 참조입니다.

*pstrDirName*<br/>
디렉터리의 이름을 받는 문자열에 대 한 포인터입니다.

*lpdwLen*<br/>
다음 정보를 포함 하는 DWORD에 대 한 포인터입니다.

On entry: *Pstrdirname* 에서 참조 하는 버퍼의 크기입니다.

반환 시: *Pstrdirname* 에 저장 된 문자 수입니다. 멤버 함수가 실패 하 고 ERROR_INSUFFICIENT_BUFFER 반환 되 면, *lpdwLen* 는 응용 프로그램에서 문자열을 받기 위해 할당 해야 하는 바이트 수를 포함 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

`GetCurrentDirectoryAsURL`[Getcurrentdirectory](#getcurrentdirectory) 와 동일 하 게 동작 합니다.

*Strdirname* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적으로 정규화 된 파일 이름일 수도 있고 정규화 된 이름일 수도 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `GetCurrentDirectoryAsURL` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a> CFtpConnection:: GetFile

이 멤버 함수를 호출 하 여 FTP 서버에서 파일을 가져오고 로컬 컴퓨터에 저장 합니다.

```
BOOL GetFile(
    LPCTSTR pstrRemoteFile,
    LPCTSTR pstrLocalFile,
    BOOL bFailIfExists = TRUE,
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pstrRemoteFile*<br/>
FTP 서버에서 검색할 파일의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pstrLocalFile*<br/>
로컬 시스템에서 만들 파일의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*bFailIfExists*<br/>
기존 파일에서 파일 이름을 이미 사용할 수 있는지 여부를 나타냅니다. 로컬 파일 이름이 이미 존재 하 고이 매개 변수가 TRUE 이면가 `GetFile` 실패 합니다. 그렇지 않으면는 `GetFile` 파일의 기존 복사본을 지웁니다.

*dwAttributes*<br/>
파일의 특성을 나타냅니다. 다음 FILE_ATTRIBUTE_ * 플래그를 임의로 조합 하 여 사용할 수 있습니다.

- 파일이 보관 파일인 FILE_ATTRIBUTE_ARCHIVE입니다. 응용 프로그램은이 특성을 사용 하 여 파일을 백업 또는 제거로 표시 합니다.

- 파일이 나 디렉터리가 압축 FILE_ATTRIBUTE_COMPRESSED 합니다. 파일의 경우 압축은 파일의 모든 데이터가 압축 됨을 의미 합니다. 디렉터리의 경우 새로 만든 파일과 하위 디렉터리의 기본값이 압축 됩니다.

- 파일이 디렉터리인 FILE_ATTRIBUTE_DIRECTORY 합니다.

- FILE_ATTRIBUTE_NORMAL 파일에 다른 특성이 설정 되지 않았습니다. 이 특성은 단독 으로만 사용 되는 경우에만 유효 합니다. 다른 모든 파일 특성은 FILE_ATTRIBUTE_NORMAL를 재정의 합니다.

- 파일이 숨겨져 FILE_ATTRIBUTE_HIDDEN 합니다. 일반 디렉터리 목록에 포함 되지 않습니다.

- 파일이 읽기 전용인 FILE_ATTRIBUTE_READONLY입니다. 응용 프로그램은 파일을 읽을 수 있지만 파일에 쓰거나 삭제할 수 없습니다.

- 파일이의 일부 이거나 운영 체제에서 독점적으로 사용 FILE_ATTRIBUTE_SYSTEM입니다.

- 임시 저장소에 사용 되는 파일을 FILE_ATTRIBUTE_TEMPORARY 합니다. 응용 프로그램은 반드시 필요한 경우에만 파일에 써야 합니다. 파일을 곧 삭제 하기 때문에 대부분의 파일 데이터는 미디어에 플러시되지 않고 메모리에 유지 됩니다.

*dwFlags*<br/>
전송이 발생 하는 조건을 지정 합니다. 이 매개 변수는 Windows SDK의 *DwFlags* [getfile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) 에 설명 된 모든 값이 될 수 있습니다.

*dwContext*<br/>
파일 검색에 대 한 컨텍스트 식별자입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

`GetFile` 는 FTP 서버에서 파일을 읽고 로컬로 저장 하는 것과 관련 된 모든 오버 헤드를 처리 하는 개략적인 루틴입니다. 파일 데이터만 검색 하거나 파일 전송에 대 한 닫기 제어를 요구 하는 응용 프로그램은 `OpenFile` 및 [Cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read) 를 대신 사용 해야 합니다.

*DwFlags* 가 FILE_TRANSFER_TYPE_ASCII 경우 파일 데이터의 변환은 컨트롤 및 서식 문자를 Windows 해당 항목으로 변환 합니다. 기본 전송은 파일을 서버에 저장 된 것과 같은 형식으로 다운로드 하는 이진 모드입니다.

*Pstrremotefile* 및 *pstrremotefile* 은 모두 현재 디렉터리를 기준으로 하는 부분적으로 정규화 된 파일 이름 이거나 정규화 된 파일 이름이 될 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `GetFile` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

*Dwcontext* 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정 합니다. 컨텍스트 식별자는 `CFtpConnection` 해당 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에서 만든 개체의이 특정 작업과 연결 됩니다. 값은 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 되어 식별 된 작업에 대 한 상태를 제공 합니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a> Csystem.windows.forms.openfiledialog.openfile Connection::

읽기 또는 쓰기를 위해 FTP 서버에 있는 파일을 열려면이 멤버 함수를 호출 합니다.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pstrFileName*<br/>
열 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwAccess*<br/>
파일에 액세스 하는 방법을 결정 합니다. GENERIC_READ 또는 GENERIC_WRITE 중 하나만 가능 합니다.

*dwFlags*<br/>
이후 전송 발생 조건을 지정 합니다. 다음 FTP_TRANSFER_ * 상수 중 하나일 수 있습니다.

- FTP ASCII (유형 A) 전송 메서드를 사용 하 여 파일 전송을 FTP_TRANSFER_TYPE_ASCII 합니다. 컨트롤과 서식 지정 정보를 해당 하는 로컬으로 변환 합니다.

- 파일 FTP_TRANSFER_TYPE_BINARY FTP 이미지 (Type I) 전송 메서드를 사용 하 여 데이터를 전송 합니다. 파일은 변경 없이 데이터를 그대로 전송 합니다. 이는 기본 전송 방법입니다.

*dwContext*<br/>
파일 열기에 대 한 컨텍스트 식별자입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

### <a name="return-value"></a>반환 값

[Cinternetfile](../../mfc/reference/cinternetfile-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`OpenFile` 는 다음과 같은 경우에 사용 해야 합니다.

- 응용 프로그램에 FTP 서버에서 파일로 보내고 생성 해야 하는 데이터가 있지만 해당 데이터는 로컬 파일에 있지 않습니다. `OpenFile`에서 파일을 열면 응용프로그램은 [cinternetfile::Write](../../mfc/reference/cinternetfile-class.md#write)를 사용하여 FTP 파일데이터를 서버로 보냅니다.

- 응용 프로그램은 서버에서 파일을 검색 하 여 디스크에 기록 하는 대신 응용 프로그램 제어 메모리에 넣어야 합니다. 응용 프로그램은를 사용 하 여 파일을 연 후 [Cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read) 를 사용 합니다. `OpenFile`

- 응용 프로그램에는 파일 전송에 대 한 세부적인 제어 수준이 필요 합니다. 예를 들어 응용 프로그램에서 파일을 다운로드 하는 동안 파일 전송 상태를 표시 하는 진행률 컨트롤을 표시 하려고 할 수 있습니다.

`OpenFile`를 호출하고 `CInternetConnection::Close`를 호출할 때까지 응용 프로그램은 [cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read), [cinternetfile:: Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close` 또는 [ccefilefind:: findfile](../../mfc/reference/cftpfilefind-class.md#findfile)만 호출할 수 있습니다. 동일한 FTP 세션의 다른 FTP 함수를 호출 하면 오류가 발생 하 고 오류 코드가 FTP_ETRANSFER_IN_PROGRESS 설정 됩니다.

*Pstrfilename* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적으로 정규화 된 파일 이름 이거나 정규화 된 파일 이름이 될 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `OpenFile` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

*Dwcontext* 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정 합니다. 컨텍스트 식별자는 `CFtpConnection` 해당 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에서 만든 개체의이 특정 작업과 연결 됩니다. 값은 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 되어 식별 된 작업에 대 한 상태를 제공 합니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="cftpconnectionputfile"></a><a name="putfile"></a> CFtpConnection::P utFile

FTP 서버에 파일을 저장 하려면이 멤버 함수를 호출 합니다.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pstrLocalFile*<br/>
로컬 시스템에서 보낼 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrRemoteFile*<br/>
FTP 서버에 만들 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwFlags*<br/>
파일 전송이 발생 하는 조건을 지정 합니다. [System.windows.forms.openfiledialog.openfile](#openfile)에 설명 된 FTP_TRANSFER_ * 상수 중 하나일 수 있습니다.

*dwContext*<br/>
파일을 배치 하기 위한 컨텍스트 식별자입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

`PutFile` 는 FTP 서버에 파일을 저장 하는 것과 관련 된 모든 작업을 처리 하는 상위 수준 루틴입니다. 데이터를 전송 하거나 파일 전송을 더 자세히 제어 해야 하는 응용 프로그램은 [system.windows.forms.openfiledialog.openfile](#openfile) 및 [Cinternetfile:: Write](../../mfc/reference/cinternetfile-class.md#write)를 사용 해야 합니다.

`dwContext` 기본값을 재정의하여 컨텍스트 식별자를 설정한 값으로 설정합니다. 컨텍스트 식별자는 `CFtpConnection` 해당 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에서 만든 개체의이 특정 작업과 연결 됩니다. 값은 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 되어 식별 된 작업에 대 한 상태를 제공 합니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="cftpconnectionremove"></a><a name="remove"></a> CFtpConnection:: Remove

이 멤버 함수를 호출 하 여 연결 된 서버에서 지정 된 파일을 삭제 합니다.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>매개 변수

*pstrFileName*<br/>
제거할 파일 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

*Pstrfilename* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적으로 정규화 된 파일 이름 이거나 정규화 된 파일 이름이 될 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `Remove`함수는 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a> CFtpConnection:: RemoveDirectory

이 멤버 함수를 호출 하 여 연결 된 서버에서 지정한 디렉터리를 제거 합니다.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>매개 변수

*pstrDirName*<br/>
제거할 디렉터리를 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

[Getcurrentdirectory](#getcurrentdirectory) 를 사용 하 여 서버의 현재 작업 디렉터리를 확인 합니다. 원격 시스템이 루트 디렉터리에 연결 되어 있다고 가정 하지 마십시오.

*Pstrdirname* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적 이거나 정규화 된 파일 이름일 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `RemoveDirectory` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

## <a name="cftpconnectionrename"></a><a name="rename"></a> CFtpConnection:: Rename

이 멤버 함수를 호출 하 여 연결 된 서버에서 지정 된 파일의 이름을 바꿉니다.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>매개 변수

*pstrExisting*<br/>
이름을 바꿀 파일의 현재 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrNew*<br/>
파일의 새 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

*PstrExisting* 및 *pstrnew* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적으로 정규화 된 파일 이름 이거나 정규화 된 파일 이름이 될 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `Rename` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a> CSetCurrentDirectory Connection::

FTP 서버에서 다른 디렉터리로 변경 하려면이 멤버 함수를 호출 합니다.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>매개 변수

*pstrDirName*<br/>
디렉터리의 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

*Pstrdirname* 매개 변수는 현재 디렉터리를 기준으로 하는 부분적 이거나 정규화 된 파일 이름일 수 있습니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 두 이름 중 하나에 대 한 디렉터리 구분 기호로 사용할 수 있습니다. `SetCurrentDirectory` 디렉터리 이름 구분 기호를 사용 하기 전에 적절 한 문자로 변환 합니다.

[Getcurrentdirectory](#getcurrentdirectory) 를 사용 하 여 FTP 서버의 현재 작업 디렉터리를 확인 합니다. 원격 시스템이 루트 디렉터리에 연결 되어 있다고 가정 하지 마십시오.

## <a name="see-also"></a>참고 항목

[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession 클래스](../../mfc/reference/cinternetsession-class.md)
