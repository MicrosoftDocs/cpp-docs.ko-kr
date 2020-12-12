---
description: '자세히 알아보기: CGopherFileFind 클래스'
title: CGopherFileFind 클래스
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 483a0a6221d08cc3821b0dbc44dd1003c0c40114
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184051"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind 클래스

Gopher 서버의 인터넷 파일 검색에 유용합니다.

> [!NOTE]
> 클래스 `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` 및 해당 멤버는 Windows XP 플랫폼에서 작동 하지 않으므로 더 이상 사용 되지 않지만 이전 플랫폼에서는 계속 작동 합니다.

## <a name="syntax"></a>구문

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CGopherFileFind:: CGopherFileFind](#cgopherfilefind)|`CGopherFileFind` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CGopherFileFind:: FindFile](#findfile)|Gopher 서버에서 파일을 찾습니다.|
|[CGopherFileFind:: FindNextFile](#findnextfile)|[Findfile](#findfile)에 대 한 이전 호출에서 파일 검색을 계속 합니다.|
|[CGopherFileFind:: GetCreationTime](#getcreationtime)|지정 된 파일이 만들어진 시간을 가져옵니다.|
|[CGopherFileFind:: GetLastAccessTime](#getlastaccesstime)|지정 된 파일에 마지막으로 액세스 한 시간을 가져옵니다.|
|[CGopherFileFind:: GetLastWriteTime](#getlastwritetime)|지정 된 파일에 마지막으로 쓴 시간을 가져옵니다.|
|[CGopherFileFind:: GetLength](#getlength)|찾은 파일의 길이 (바이트)를 가져옵니다.|
|[CGopherFileFind:: GetLocator](#getlocator)|개체를 가져옵니다 `CGopherLocator` .|
|[CGopherFileFind:: GetScreenName](#getscreenname)|Gopher 화면의 이름을 가져옵니다.|
|[CGopherFileFind:: IsDots](#isdots)|파일을 반복 하는 동안 현재 디렉터리와 부모 디렉터리 표식을 테스트 합니다.|

## <a name="remarks"></a>설명

`CGopherFileFind` 검색을 시작 하 고, 파일을 찾고, 파일의 URL을 반환 하는 멤버 함수를 포함 합니다.

인터넷 및 로컬 파일 검색을 위해 디자인 된 다른 MFC 클래스에는 [Cftpfilefind](../../mfc/reference/cftpfilefind-class.md) 및 [cfilefind](../../mfc/reference/cfilefind-class.md)가 포함 됩니다. 와 함께 `CGopherFileFind` 이러한 클래스는 서버 프로토콜, 파일 형식 또는 위치 (로컬 컴퓨터 또는 원격 서버)에 관계 없이 사용자가 특정 파일을 찾을 수 있는 원활한 메커니즘을 제공 합니다. HTTP는 검색에 필요한 직접 파일 조작을 지원 하지 않으므로 HTTP 서버를 검색 하는 데 MFC 클래스가 없습니다.

> [!NOTE]
> `CGopherFileFind` 는 기본 클래스 [Cfilefind](../../mfc/reference/cfilefind-class.md)의 다음 멤버 함수를 지원 하지 않습니다.

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

또한와 함께 사용 하는 경우 `CGopherFileFind` `CFileFind` 멤버 함수 [isdots](../../mfc/reference/cfilefind-class.md#isdots) 는 항상 FALSE입니다.

및 기타 WinInet 클래스를 사용 하는 방법에 대 한 자세한 내용은 `CGopherFileFind` wininet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a> CGopherFileFind:: CGopherFileFind

이 멤버 함수를 호출 하 여 개체를 생성 `CGopherFileFind` 합니다.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pConnection*<br/>
[CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 개체에 대 한 포인터입니다.

*dwContext*<br/>
작업에 대 한 컨텍스트 식별자입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

### <a name="remarks"></a>설명

*Dwcontext* 의 기본값은 MFC에서 `CGopherFileFind` 개체를 만든 [cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체의 개체로 보냅니다 `CGopherFileFind` . 개체를 생성할 때 `CGopherFileFind` 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정할 수 있습니다. 컨텍스트 식별자가 식별 된 개체에 대 한 상태를 제공 하기 위해 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 됩니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a> CGopherFileFind:: FindFile

이 멤버 함수를 호출 하 여 gopher 파일을 찾습니다.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>매개 변수

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체에 대 한 참조입니다.

*pstrString*<br/>
파일 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwFlags*<br/>
이 세션을 처리 하는 방법을 설명 하는 플래그입니다. 유효한 플래그는 다음과 같습니다.

- 로컬에 캐시 된 경우에도 원격 서버에서 데이터를 가져올 INTERNET_FLAG_RELOAD.

- INTERNET_FLAG_DONT_CACHE는 데이터를 로컬로 또는 게이트웨이에서 캐시 하지 않습니다.

- INTERNET_FLAG_SECURE SSL(Secure Sockets Layer) 또는 PCT를 사용 하 여 통신에 보안 트랜잭션을 요청 합니다. 이 플래그는 HTTP 요청에만 적용 됩니다.

- 가능 하면 `FindFile` 각 요청에 대해 새 세션을 만들지 않고 새 요청에 대해 서버에 대 한 기존 연결을 다시 사용 합니다. INTERNET_FLAG_USE_EXISTING

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다.

### <a name="remarks"></a>설명

`FindFile`첫 번째 gopher 개체를 검색 하기 위해를 호출한 후 [Findnextfile](#findnextfile) 을 호출 하 여 후속 gopher 파일을 검색할 수 있습니다.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a> CGopherFileFind:: FindNextFile

이 멤버 함수를 호출 하 여 [CGopherFileFind:: findfile](#findfile)호출로 시작 된 파일 검색을 계속 합니다.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>반환 값

파일이 더 있는 경우 0이 아닙니다. 찾은 파일이 디렉터리의 마지막 파일 이거나 오류가 발생 한 경우 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다. 찾은 파일이 디렉터리의 마지막 파일이 고 일치 하는 파일을 찾을 수 없는 경우이 `GetLastError` 함수는 ERROR_NO_MORE_FILES을 반환 합니다.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a> CGopherFileFind:: GetCreationTime

현재 파일의 만든 시간을 가져옵니다.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>매개 변수

*pTimeStamp*<br/>
파일이 만들어진 시간을 포함 하는 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조체에 대 한 포인터입니다.

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 실패 한 경우 0입니다. `GetCreationTime` 이 개체에서 [Findnextfile](#findnextfile) 이 호출 되지 않은 경우에만 0을 반환 `CGopherFileFind` 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetCreationTime` 합니다.

> [!NOTE]
> 모든 파일 시스템에서 동일한 의미 체계를 사용 하 여이 함수에서 반환 되는 타임 스탬프를 구현 하는 것은 아닙니다. 이 함수는 기본 파일 시스템이 나 서버가 시간 특성을 유지 하는 것을 지원 하지 않는 경우 다른 타임 스탬프 함수에서 반환 된 것과 동일한 값을 반환할 수 있습니다. 시간 형식에 대 한 자세한 내용은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조를 참조 하세요. 일부 운영 체제에서 반환 된 시간은 파일이 있는 컴퓨터의 로컬 표준 시간대에 있습니다. 자세한 내용은 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API를 참조 하세요.

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a> CGopherFileFind:: GetLastAccessTime

지정 된 파일에 마지막으로 액세스 한 시간을 가져옵니다.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>매개 변수

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 참조입니다.

*pTimeStamp*<br/>
파일에 마지막으로 액세스 한 시간을 포함 하는 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 실패 한 경우 0입니다. `GetLastAccessTime` 이 개체에서 [Findnextfile](#findnextfile) 이 호출 되지 않은 경우에만 0을 반환 `CGopherFileFind` 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetLastAccessTime` 합니다.

> [!NOTE]
> 모든 파일 시스템에서 동일한 의미 체계를 사용 하 여이 함수에서 반환 되는 타임 스탬프를 구현 하는 것은 아닙니다. 이 함수는 기본 파일 시스템이 나 서버가 시간 특성을 유지 하는 것을 지원 하지 않는 경우 다른 타임 스탬프 함수에서 반환 된 것과 동일한 값을 반환할 수 있습니다. 시간 형식에 대 한 자세한 내용은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조를 참조 하세요. 일부 운영 체제에서 반환 된 시간은 파일이 있는 컴퓨터의 로컬 표준 시간대에 있습니다. 자세한 내용은 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API를 참조 하세요.

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a> CGopherFileFind:: GetLastWriteTime

파일이 마지막으로 변경 된 시간을 가져옵니다.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>매개 변수

*pTimeStamp*<br/>
파일에 마지막으로 쓴 시간을 포함 하는 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조체에 대 한 포인터입니다.

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 실패 한 경우 0입니다. `GetLastWriteTime` 이 개체에서 [Findnextfile](#findnextfile) 이 호출 되지 않은 경우에만 0을 반환 `CGopherFileFind` 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetLastWriteTime` 합니다.

> [!NOTE]
> 모든 파일 시스템에서 동일한 의미 체계를 사용 하 여이 함수에서 반환 되는 타임 스탬프를 구현 하는 것은 아닙니다. 이 함수는 기본 파일 시스템이 나 서버가 시간 특성을 유지 하는 것을 지원 하지 않는 경우 다른 타임 스탬프 함수에서 반환 된 것과 동일한 값을 반환할 수 있습니다. 시간 형식에 대 한 자세한 내용은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조를 참조 하세요. 일부 운영 체제에서 반환 된 시간은 파일이 있는 컴퓨터의 로컬 표준 시간대에 있습니다. 자세한 내용은 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API를 참조 하세요.

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a> CGopherFileFind:: GetLength

이 멤버 함수를 호출 하 여 찾은 파일의 길이 (바이트)를 가져옵니다.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>반환 값

찾은 파일의 길이 (바이트)입니다.

### <a name="remarks"></a>설명

`GetLength` 는 Win32 구조 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 를 사용 하 여 파일 크기 (바이트) 값을 가져옵니다.

> [!NOTE]
> MFC 7.0에서는 `GetLength` 64 비트 정수 형식을 지원 합니다. 이전에이 라이브러리의 최신 버전을 사용 하 여 빌드한 기존 코드를 사용 하면 잘림 경고가 발생할 수 있습니다.

### <a name="example"></a>예제

  [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) (기본 클래스 구현)의 예제를 참조 하세요.

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a> CGopherFileFind:: GetLocator

이 멤버 함수를 호출 하 여 [Findfile](#findfile) 에서 gopher 파일을 찾는 데 사용 하는 [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체를 가져옵니다.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>반환 값

`CGopherLocator` 개체입니다.

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a> CGopherFileFind:: GetScreenName

이 멤버 함수를 호출 하 여 gopher 화면의 이름을 가져옵니다.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>반환 값

Gopher 화면의 이름입니다.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a> CGopherFileFind:: IsDots

파일을 반복 하는 동안 현재 디렉터리와 부모 디렉터리 표식을 테스트 합니다.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>반환 값

찾은 파일의 이름이 "." 또는 "." 인 경우 0이 아닌 것으로,이는 찾은 파일이 실제로 디렉터리 임을 나타냅니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsDots` 합니다.

## <a name="see-also"></a>참고 항목

[CFileFind 클래스](../../mfc/reference/cfilefind-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 클래스](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind 클래스](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 클래스](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 클래스](../../mfc/reference/chttpfile-class.md)
