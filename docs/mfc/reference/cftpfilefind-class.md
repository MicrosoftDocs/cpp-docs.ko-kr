---
description: '다음에 대 한 자세한 정보: CFtpFileFind 클래스'
title: CFtpFileFind 클래스
ms.date: 05/28/2020
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: 89d8a8232558c3afe9cf2f3a23d02226d8539aaf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184233"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind 클래스

FTP 서버의 인터넷 파일 검색에 유용합니다.

## <a name="syntax"></a>구문

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFtpFileFind:: CFtpFileFind](#cftpfilefind)|`CFtpFileFind` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFtpFileFind:: FindFile](#findfile)|FTP 서버에서 파일을 찾습니다.|
|[CFtpFileFind:: FindNextFile](#findnextfile)|[Findfile](#findfile)에 대 한 이전 호출에서 파일 검색을 계속 합니다.|
|[CGetFileURL Filefind::](#getfileurl)|찾은 파일의 경로를 포함 하는 URL을 가져옵니다.|

## <a name="remarks"></a>설명

`CFtpFileFind` 검색을 시작 하 고, 파일을 찾고, 파일에 대 한 URL 또는 기타 설명 정보를 반환 하는 멤버 함수를 포함 합니다.

인터넷 및 로컬 파일 검색을 위해 디자인 된 다른 MFC 클래스에는 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 및 [cfilefind](../../mfc/reference/cfilefind-class.md)가 포함 됩니다. 와 함께 `CFtpFileFind` 이러한 클래스는 서버 프로토콜 또는 파일 형식 (로컬 컴퓨터 또는 원격 서버)에 관계 없이 클라이언트에서 특정 파일을 찾기 위한 원활한 메커니즘을 제공 합니다. Http는 검색에 필요한 직접 파일 조작을 지원 하지 않으므로 HTTP 서버를 검색할 수 있는 MFC 클래스가 없습니다.

및 기타 WinInet 클래스를 사용 하는 방법에 대 한 자세한 내용은 `CFtpFileFind` wininet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="example"></a>예제

다음 코드에서는 FTP 서버의 현재 디렉터리에 있는 모든 파일을 열거 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a> CFtpFileFind:: CFtpFileFind

이 멤버 함수를 호출 하 여 개체를 생성 `CFtpFileFind` 합니다.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pConnection*<br/>
`CFtpConnection` 개체에 대한 포인터입니다. [Cinternetsession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)을 호출 하 여 FTP 연결을 가져올 수 있습니다.

*dwContext*<br/>
개체에 대 한 컨텍스트 식별자 `CFtpFileFind` 입니다. 자세한 내용은 다음 **설명을** 참조 하세요.

### <a name="remarks"></a>설명

*Dwcontext* 의 기본값은 MFC에서 `CFtpFileFind` 개체를 만든 [cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체의 개체로 보냅니다 `CFtpFileFind` . 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정할 수 있습니다. 컨텍스트 식별자가 식별 된 개체에 대 한 상태를 제공 하기 위해 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 됩니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

### <a name="example"></a>예제

  이 항목의 앞부분에 나오는 클래스 개요의 예제를 참조 하세요.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a> CFtpFileFind:: FindFile

FTP 파일을 찾으려면이 멤버 함수를 호출 합니다.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>매개 변수

*pstrName*<br/>
찾을 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다. NULL 인 경우 호출 시 와일드 카드 검색 (*)이 수행 됩니다.

*dwFlags*<br/>
이 세션을 처리 하는 방법을 설명 하는 플래그입니다. 이러한 플래그는 비트 OR 연산자 (&#124;)와 함께 사용할 수 있으며 다음과 같습니다.

- `INTERNET_FLAG_RELOAD`   로컬로 캐시 된 경우에도 네트워크에서 데이터를 가져옵니다. 이 플래그는 기본 플래그입니다.

- `INTERNET_FLAG_DONT_CACHE`   로컬 또는 게이트웨이에서 데이터를 캐시 하지 않습니다.

- `INTERNET_FLAG_RAW_DATA`   기본값을 재정의 하 여 원시 데이터 (FTP에 대 한 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조)를 반환 합니다.

- `INTERNET_FLAG_SECURE`   SSL(Secure Sockets Layer) 또는 PCT를 사용 하 여 통신 하는 트랜잭션을 보호 합니다. 이 플래그는 HTTP 요청에만 적용 됩니다.

- `INTERNET_FLAG_EXISTING_CONNECT`   가능 하면 `FindFile` 각 요청에 대해 새 세션을 만드는 대신 새 요청에 대 한 기존 연결을 서버에 다시 사용 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다.

### <a name="remarks"></a>설명

를 호출 `FindFile` 하 여 첫 번째 ftp 파일을 검색 한 후 [Findnextfile](#findnextfile) 을 호출 하 여 후속 ftp 파일을 검색할 수 있습니다.

### <a name="example"></a>예제

  이 항목의 이전 예제를 참조 하세요.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a> CFtpFileFind:: FindNextFile

[Findfile](#findfile) 멤버 함수를 호출 하 여 계속 해 서 파일 검색을 시작 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>반환 값

파일이 더 있는 경우 0이 아닙니다. 찾은 파일이 디렉터리의 마지막 파일 이거나 오류가 발생 한 경우 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다. 찾은 파일이 디렉터리의 마지막 파일이 고 일치 하는 파일을 찾을 수 없는 경우이 `GetLastError` 함수는 ERROR_NO_MORE_FILES을 반환 합니다.

### <a name="remarks"></a>설명

특성 함수를 호출 하기 전에이 함수를 한 번 이상 호출 해야 합니다 ( [Cfilefind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)참조).

`FindNextFile` Win32 함수 [Findnextfile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)을 래핑합니다.

### <a name="example"></a>예제

  이 항목의 앞부분에 나오는 예제를 참조 하세요.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a> CGetFileURL Filefind::

이 멤버 함수를 호출 하 여 지정 된 파일의 URL을 가져옵니다.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>반환 값

URL (Universal Resource Locator)의 파일 및 경로입니다.

### <a name="remarks"></a>설명

`GetFileURL` 는 결과를 URL 형식으로 제공 한다는 점을 제외 하 고는 멤버 함수 [Cfilefind:: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) 와 비슷합니다. 와 마찬가지로 `CFileFind::GetFilePath` 결과에는 파일 이름이 포함 되지 않습니다. 예를 들어 `file1.txt` 에 있는는를 `//moose/dir/file1.txt:` 반환 `ftp://moose/dir/` 합니다.

## <a name="see-also"></a>참고 항목

[CFileFind 클래스](../../mfc/reference/cfilefind-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 클래스](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 클래스](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 클래스](../../mfc/reference/chttpfile-class.md)
