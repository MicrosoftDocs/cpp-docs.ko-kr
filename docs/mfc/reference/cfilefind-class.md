---
description: '자세히 알아보기: CFileFind 클래스'
title: CFileFind 클래스
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: d47c45ac86386a6748ca212c569aeef568ca2a8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184506"
---
# <a name="cfilefind-class"></a>CFileFind 클래스

로컬 파일 검색을 수행 하 고, 인터넷 파일 검색을 수행 하는 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 및 [c filefind](../../mfc/reference/cftpfilefind-class.md)의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CFileFind : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFileFind:: CFileFind](#cfilefind)|`CFileFind` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFileFind:: Close](#close)|검색 요청을 닫습니다.|
|[CFileFind:: FindFile](#findfile)|디렉터리에서 지정 된 파일 이름을 검색 합니다.|
|[CFileFind:: FindNextFile](#findnextfile)|[Findfile](#findfile)에 대 한 이전 호출에서 파일 검색을 계속 합니다.|
|[CFileFind:: GetCreationTime](#getcreationtime)|파일이 만들어진 시간을 가져옵니다.|
|[CFileFind:: GetFileName](#getfilename)|찾은 파일의 확장명을 포함 하는 이름을 가져옵니다.|
|[CFileFind:: GetFilePath](#getfilepath)|찾은 파일의 전체 경로를 가져옵니다.|
|[CFileFind:: GetFileTitle](#getfiletitle)|찾은 파일의 제목을 가져옵니다. 제목에는 확장명이 포함 되지 않습니다.|
|[CFileFind:: GetFileURL](#getfileurl)|찾은 파일의 URL (파일 경로 포함)을 가져옵니다.|
|[CFileFind:: GetLastAccessTime](#getlastaccesstime)|파일에 마지막으로 액세스 한 시간을 가져옵니다.|
|[CFileFind:: GetLastWriteTime](#getlastwritetime)|파일이 마지막으로 변경 되 고 저장 된 시간을 가져옵니다.|
|[CFileFind:: GetLength](#getlength)|찾은 파일의 길이 (바이트)를 가져옵니다.|
|[CFileFind:: GetRoot](#getroot)|찾은 파일의 루트 디렉터리를 가져옵니다.|
|[CFileFind:: IsArchived](#isarchived)|찾은 파일이 보관 되었는지 여부를 확인 합니다.|
|[CFileFind:: IsCompressed](#iscompressed)|찾은 파일이 압축 되었는지 여부를 확인 합니다.|
|[CFileFind:: IsDirectory](#isdirectory)|찾은 파일이 디렉터리 인지 여부를 확인 합니다.|
|[CFileFind:: IsDots](#isdots)|찾은 파일의 이름에 "." 또는 "..." 라는 이름이 있는지 여부를 확인 합니다 .이 디렉터리는 실제로 디렉터리 임을 나타냅니다.|
|[CFileFind:: IsHidden](#ishidden)|찾은 파일이 숨겨지는지 여부를 확인 합니다.|
|[CFileFind:: IsNormal](#isnormal)|찾은 파일이 일반 파일 인지 여부를 확인 합니다. 즉, 다른 특성은 없습니다.|
|[CFileFind:: IsReadOnly](#isreadonly)|찾은 파일이 읽기 전용인 지 여부를 확인 합니다.|
|[CFileFind:: IsSystem](#issystem)|찾은 파일이 시스템 파일 인지 여부를 확인 합니다.|
|[CFileFind:: Istem\stin](#istemporary)|찾은 파일이 임시 파일 인지 여부를 확인 합니다.|
|[CFileFind:: MatchesMask](#matchesmask)|찾을 파일의 원하는 파일 특성을 나타냅니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CFileFind:: CloseContext](#closecontext)|현재 검색 핸들에서 지정 된 파일을 닫습니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFileFind:: m_pTM](#m_ptm)|`CAtlTransactionManager` 개체에 대한 포인터입니다.|

## <a name="remarks"></a>설명

`CFileFind` 검색을 시작 하 고 파일을 찾은 다음 파일의 제목, 이름 또는 경로를 반환 하는 멤버 함수를 포함 합니다. 인터넷 검색의 경우 멤버 함수 [GetFileURL](#getfileurl) 는 파일의 URL을 반환 합니다.

`CFileFind` 는 특정 서버 유형을 검색 하도록 디자인 된 다른 두 MFC 클래스의 기본 클래스입니다. `CGopherFileFind` 특히 gopher 서버에서 작동 하며 `CFtpFileFind` FTP 서버에서 특히 작동 합니다. 이러한 세 클래스는 로컬 컴퓨터 또는 원격 서버에서 서버 프로토콜, 파일 형식 또는 위치에 관계 없이 클라이언트에서 파일을 찾을 수 있는 원활한 메커니즘을 제공 합니다.

다음 코드는 현재 디렉터리의 모든 파일을 열거 하 고 각 파일의 이름을 인쇄 합니다.

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

예제를 간단 하 게 유지 하기 위해이 코드에서는 c + + 표준 라이브러리 클래스를 사용 `cout` 합니다. `cout`그래픽 사용자 인터페이스를 사용 하는 프로그램에서와 같이 줄을에 대 한 호출로 바꿀 수 있습니다 `CListBox::AddString` .

및 기타 WinInet 클래스를 사용 하는 방법에 대 한 자세한 내용은 `CFileFind` wininet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a> CFileFind:: CFileFind

이 멤버 함수는 개체가 생성 될 때 호출 됩니다 `CFileFind` .

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>매개 변수

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="example"></a>예제

  [Cfilefind:: GetFileName](#getfilename)의 예제를 참조 하세요.

## <a name="cfilefindclose"></a><a name="close"></a> CFileFind:: Close

이 멤버 함수를 호출 하 여 검색을 종료 하 고 컨텍스트를 다시 설정 하 고 모든 리소스를 해제 합니다.

```cpp
void Close();
```

### <a name="remarks"></a>설명

를 호출한 후에는 `Close` `CFileFind` [findfile](#findfile) 을 호출 하 여 새 검색을 시작 하기 전에 새 인스턴스를 만들 필요가 없습니다.

### <a name="example"></a>예제

  [Cfilefind:: GetFileName](#getfilename)의 예제를 참조 하세요.

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a> CFileFind:: CloseContext

현재 검색 핸들에서 지정 된 파일을 닫습니다.

```
virtual void CloseContext();
```

### <a name="remarks"></a>설명

검색 핸들의 현재 값으로 지정 된 파일을 닫습니다. 기본 동작을 변경 하려면이 함수를 재정의 합니다.

올바른 검색 핸들을 검색 하려면 [findfile](#findfile) 또는 [findnextfile](#findnextfile) 함수를 한 번 이상 호출 해야 합니다. `FindFile`및 `FindNextFile` 함수는 검색 핸들을 사용 하 여 이름이 지정 된 이름과 일치 하는 파일을 찾습니다.

## <a name="cfilefindfindfile"></a><a name="findfile"></a> CFileFind:: FindFile

이 멤버 함수를 호출 하 여 파일 검색을 엽니다.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>매개 변수

*pstrName*<br/>
찾을 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다. *Pstrname* 에 대해 NULL을 전달 하는 경우는 `FindFile` 와일드 카드 (*. \* ) 검색을 수행 합니다.

*dwUnused*<br/>
`FindFile`파생 클래스를 사용 하 여 다형 되도록 예약 되었습니다. 0이어야 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다.

### <a name="remarks"></a>설명

`FindFile`파일 검색을 시작 하기 위해를 호출한 후 [Findnextfile](#findnextfile) 을 호출 하 여 후속 파일을 검색 합니다. `FindNextFile`다음 특성 멤버 함수 중 하나를 호출 하기 전에를 한 번 이상 호출 해야 합니다.

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>예제

  [Cfilefind:: IsDirectory](#isdirectory)의 예제를 참조 하세요.

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a> CFileFind:: FindNextFile

[Findfile](#findfile)에 대 한 이전 호출에서 파일 검색을 계속 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>반환 값

파일이 더 있는 경우 0이 아닙니다. 찾은 파일이 디렉터리의 마지막 파일 이거나 오류가 발생 한 경우 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다. 찾은 파일이 디렉터리의 마지막 파일이 고 일치 하는 파일을 찾을 수 없는 경우이 `GetLastError` 함수는 ERROR_NO_MORE_FILES을 반환 합니다.

### <a name="remarks"></a>설명

`FindNextFile`다음 특성 멤버 함수 중 하나를 호출 하기 전에를 한 번 이상 호출 해야 합니다.

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile` Win32 함수 [Findnextfile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)을 래핑합니다.

### <a name="example"></a>예제

  [Cfilefind:: IsDirectory](#isdirectory)의 예제를 참조 하세요.

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a> CFileFind:: GetCreationTime

지정 된 파일이 만들어진 시간을 가져오려면이 멤버 함수를 호출 합니다.

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

성공 하면 0이 아닌 값 실패 한 경우 0입니다. `GetCreationTime` 이 개체에서 [Findnextfile](#findnextfile) 이 호출 되지 않은 경우에만 0을 반환 `CFileFind` 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetCreationTime` 합니다.

> [!NOTE]
> 모든 파일 시스템에서 동일한 의미 체계를 사용 하 여이 함수에서 반환 되는 타임 스탬프를 구현 하는 것은 아닙니다. 이 함수는 기본 파일 시스템이 나 서버가 시간 특성을 유지 하는 것을 지원 하지 않는 경우 다른 타임 스탬프 함수에서 반환 된 것과 동일한 값을 반환할 수 있습니다. 시간 형식에 대 한 자세한 내용은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조를 참조 하세요. 일부 운영 체제에서 반환 된 시간은 파일이 있는 컴퓨터의 로컬 표준 시간대에 있습니다. 자세한 내용은 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a> CFileFind:: GetFileName

이 멤버 함수를 호출 하 여 찾은 파일의 이름을 가져옵니다.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>반환 값

가장 최근에 찾은 파일의 이름입니다.

### <a name="remarks"></a>설명

GetFileName을 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 합니다.

`GetFileName` 는 `CFileFind` 파일 이름의 일부 형식을 반환 하는 세 개의 멤버 함수 중 하나입니다. 다음 목록에서는 세 가지 방법과이를 어떻게 변경 하는지 설명 합니다.

- `GetFileName` 확장명을 포함 하는 파일 이름을 반환 합니다. 예를 들어 `GetFileName` *c:\myhtml\myfile.txt* 파일에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 *myfile.txt* 파일 이름이 반환 됩니다.

- [Getfilepath](#getfilepath) 는 파일의 전체 경로를 반환 합니다. 예를 들어 `GetFilePath` 파일 *c:\myhtml\myfile.txt* 에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 *c:\myhtml\myfile.txt* 파일 경로가 반환 됩니다.

- [GetFileTitle](#getfiletitle) 는 파일 확장명을 제외한 파일 이름을 반환 합니다. 예를 들어 `GetFileTitle` 파일 *c:\myhtml\myfile.txt* 에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 파일 제목 *myfile* 이 반환 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a> CFileFind:: GetFilePath

이 멤버 함수를 호출 하 여 지정 된 파일의 전체 경로를 가져옵니다.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>반환 값

지정 된 파일의 경로입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetFilePath` 합니다.

`GetFilePath` 는 `CFileFind` 파일 이름의 일부 형식을 반환 하는 세 개의 멤버 함수 중 하나입니다. 다음 목록에서는 세 가지 방법과이를 어떻게 변경 하는지 설명 합니다.

- [Getfilename](#getfilename) 은 확장명을 포함 하 여 파일 이름을 반환 합니다. 예를 들어 `GetFileName` *c:\myhtml\myfile.txt* 파일에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 *myfile.txt* 파일 이름이 반환 됩니다.

- `GetFilePath` 파일의 전체 경로를 반환 합니다. 예를 들어 `GetFilePath` 파일에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 `c:\myhtml\myfile.txt` 파일 경로가 반환 `c:\myhtml\myfile.txt` 됩니다.

- [GetFileTitle](#getfiletitle) 는 파일 확장명을 제외한 파일 이름을 반환 합니다. 예를 들어 `GetFileTitle` 파일 *c:\myhtml\myfile.txt* 에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 파일 제목 *myfile* 이 반환 됩니다.

### <a name="example"></a>예제

  [Cfilefind:: GetFileName](#getfilename)의 예제를 참조 하세요.

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a> CFileFind:: GetFileTitle

이 멤버 함수를 호출 하 여 찾은 파일의 제목을 가져옵니다.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>반환 값

파일의 제목입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetFileTitle` 합니다.

`GetFileTitle` 는 `CFileFind` 파일 이름의 일부 형식을 반환 하는 세 개의 멤버 함수 중 하나입니다. 다음 목록에서는 세 가지 방법과이를 어떻게 변경 하는지 설명 합니다.

- [Getfilename](#getfilename) 은 확장명을 포함 하 여 파일 이름을 반환 합니다. 예를 들어 `GetFileName` *c:\myhtml\myfile.txt* 파일에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 *myfile.txt* 파일 이름이 반환 됩니다.

- [Getfilepath](#getfilepath) 는 파일의 전체 경로를 반환 합니다. 예를 들어 `GetFilePath` 파일 *c:\myhtml\myfile.txt* 에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 *c:\myhtml\myfile.txt* 파일 경로가 반환 됩니다.

- `GetFileTitle` 파일 확장명을 제외한 파일 이름을 반환 합니다. 예를 들어 `GetFileTitle` 파일 *c:\myhtml\myfile.txt* 에 대 한 사용자 메시지를 생성 하기 위해를 호출 하면 파일 제목 *myfile* 이 반환 됩니다.

### <a name="example"></a>예제

  [Cfilefind:: GetFileName](#getfilename)의 예제를 참조 하세요.

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a> CFileFind:: GetFileURL

이 멤버 함수를 호출 하 여 지정 된 URL을 검색 합니다.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>반환 값

전체 URL입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetFileURL` 합니다.

`GetFileURL` 는 폼에서 URL을 반환 한다는 점을 제외 하 고는 멤버 함수 [Getfilepath](#getfilepath)와 비슷합니다 `file://path` . 예를 들어 `GetFileURL` *myfile.txt* 의 전체 url을 가져오기 위해를 호출 하면 url이 반환 `file://c:\myhtml\myfile.txt` 됩니다.

### <a name="example"></a>예제

  [Cfilefind:: GetFileName](#getfilename)의 예제를 참조 하세요.

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a> CFileFind:: GetLastAccessTime

이 멤버 함수를 호출 하 여 지정 된 파일에 마지막으로 액세스 한 시간을 가져옵니다.

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

성공 하면 0이 아닌 값 실패 한 경우 0입니다. `GetLastAccessTime` 이 개체에서 [Findnextfile](#findnextfile) 이 호출 되지 않은 경우에만 0을 반환 `CFileFind` 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetLastAccessTime` 합니다.

> [!NOTE]
> 모든 파일 시스템에서 동일한 의미 체계를 사용 하 여이 함수에서 반환 되는 타임 스탬프를 구현 하는 것은 아닙니다. 이 함수는 기본 파일 시스템이 나 서버가 시간 특성을 유지 하는 것을 지원 하지 않는 경우 다른 타임 스탬프 함수에서 반환 된 것과 동일한 값을 반환할 수 있습니다. 시간 형식에 대 한 자세한 내용은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조를 참조 하세요. 일부 운영 체제에서 반환 된 시간은 파일이 있는 컴퓨터의 로컬 표준 시간대에 있습니다. 자세한 내용은 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a> CFileFind:: GetLastWriteTime

이 멤버 함수를 호출 하 여 파일이 마지막으로 변경 된 시간을 가져옵니다.

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

성공 하면 0이 아닌 값 실패 한 경우 0입니다. `GetLastWriteTime` 이 개체에서 [Findnextfile](#findnextfile) 이 호출 되지 않은 경우에만 0을 반환 `CFileFind` 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetLastWriteTime` 합니다.

> [!NOTE]
> 모든 파일 시스템에서 동일한 의미 체계를 사용 하 여이 함수에서 반환 되는 타임 스탬프를 구현 하는 것은 아닙니다. 이 함수는 기본 파일 시스템이 나 서버가 시간 특성을 유지 하는 것을 지원 하지 않는 경우 다른 타임 스탬프 함수에서 반환 된 것과 동일한 값을 반환할 수 있습니다. 시간 형식에 대 한 자세한 내용은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조를 참조 하세요. 일부 운영 체제에서 반환 된 시간은 파일이 있는 컴퓨터의 로컬 표준 시간대에 있습니다. 자세한 내용은 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindgetlength"></a><a name="getlength"></a> CFileFind:: GetLength

이 멤버 함수를 호출 하 여 찾은 파일의 길이 (바이트)를 가져옵니다.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>반환 값

찾은 파일의 길이 (바이트)입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetLength` 합니다.

`GetLength` 는 Win32 구조 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 를 사용 하 여 파일 크기 (바이트)의 값을 가져오고 반환 합니다.

> [!NOTE]
> MFC 7.0에서는 `GetLength` 64 비트 정수 형식을 지원 합니다. 이전에 라이브러리의 최신 버전을 사용 하 여 빌드한 기존 코드는 잘림 경고를 발생 시킬 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a> CFileFind:: GetRoot

이 멤버 함수를 호출 하 여 찾은 파일의 루트를 가져옵니다.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>반환 값

활성 검색의 루트입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `GetRoot` 합니다.

이 멤버 함수는 검색을 시작 하는 데 사용 되는 드라이브 지정자와 경로 이름을 반환 합니다. 예를 들어를 사용 하 여 [Findfile](#findfile) 을 호출 하면 `*.dat` `GetRoot` 빈 문자열이 반환 됩니다. 을 `c:\windows\system\*.dll` 반환 하는 결과에와 같은 경로 전달 `FindFile` `GetRoot` `c:\windows\system\`

### <a name="example"></a>예제

  [Cfilefind:: GetFileName](#getfilename)의 예제를 참조 하세요.

## <a name="cfilefindisarchived"></a><a name="isarchived"></a> CFileFind:: IsArchived

찾은 파일이 보관 되었는지 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 백업 또는 제거 되는 보관 파일을 FILE_ATTRIBUTE_ARCHIVE 하 여 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성을 표시 합니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsArchived` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a> CFileFind:: IsCompressed

찾은 파일이 압축 되었는지 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

압축 된 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성인 FILE_ATTRIBUTE_COMPRESSED로 표시 됩니다. 파일의 경우이 특성은 파일의 모든 데이터가 압축 됨을 나타냅니다. 디렉터리의 경우이 특성은 압축이 새로 만든 파일 및 하위 디렉터리에 대 한 기본값 임을 나타냅니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsCompressed` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a> CFileFind:: IsDirectory

찾은 파일이 디렉터리 인지 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

디렉터리인 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성 FILE_ATTRIBUTE_DIRECTORY 표시 됩니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsDirectory` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

이 작은 프로그램은 C:\의 모든 디렉터리를 루트로. 디렉터리의 이름을 드라이브에 출력 합니다.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a> CFileFind:: IsDots

파일을 반복 하는 동안 현재 디렉터리와 부모 디렉터리 표식을 테스트 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>반환 값

찾은 파일의 이름이 "." 또는 "." 인 경우 0이 아닌 것으로,이는 찾은 파일이 실제로 디렉터리 임을 나타냅니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsDots` 합니다.

### <a name="example"></a>예제

  [Cfilefind:: IsDirectory](#isdirectory)의 예제를 참조 하세요.

## <a name="cfilefindishidden"></a><a name="ishidden"></a> CFileFind:: IsHidden

찾은 파일이 숨겨지는지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

FILE_ATTRIBUTE_HIDDEN 표시 되는 숨겨진 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성입니다. 숨겨진 파일은 일반 디렉터리 목록에 포함 되지 않습니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsHidden` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindisnormal"></a><a name="isnormal"></a> CFileFind:: IsNormal

찾은 파일이 일반 파일 인지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

FILE_ATTRIBUTE_NORMAL 표시 된 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성입니다. 일반 파일에는 다른 특성이 설정 되지 않습니다. 다른 모든 파일 특성은이 특성을 재정의 합니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsNormal` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a> CFileFind:: IsReadOnly

찾은 파일이 읽기 전용인 지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

읽기 전용 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성인 FILE_ATTRIBUTE_READONLY로 표시 됩니다. 응용 프로그램은 이러한 파일을 읽을 수 있지만 파일에 쓰거나 삭제할 수 없습니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsReadOnly` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindissystem"></a><a name="issystem"></a> CFileFind:: IsSystem

찾은 파일이 시스템 파일 인지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

시스템 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성인 FILE_ATTRIBUTE_SYSTEM로 표시 됩니다. 시스템 파일이의 일부 이거나 운영 체제에서 독점적으로 사용 되는 경우

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsSystem` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindistemporary"></a><a name="istemporary"></a> CFileFind:: Istem\stin

찾은 파일이 임시 파일 인지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

임시 파일은 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 파일 특성인 FILE_ATTRIBUTE_TEMPORARY로 표시 됩니다. 임시 파일은 임시 저장소에 사용 됩니다. 응용 프로그램은 반드시 필요한 경우에만 파일에 써야 합니다. 파일을 곧 삭제 하기 때문에 대부분의 파일 데이터는 미디어에 플러시되지 않고 메모리에 유지 됩니다.

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `IsTemporary` 합니다.

파일 특성의 전체 목록은 멤버 함수 [MatchesMask](#matchesmask) 를 참조 하세요.

### <a name="example"></a>예제

  [Cfilefind:: GetLength](#getlength)의 예제를 참조 하세요.

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a> CFileFind:: m_pTM

`CAtlTransactionManager` 개체에 대한 포인터입니다.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>설명

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a> CFileFind:: MatchesMask

찾은 파일의 파일 특성을 테스트 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>매개 변수

*dwMask*<br/>
찾은 파일에 대해 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) 구조에서 식별 된 하나 이상의 파일 특성을 지정 합니다. 여러 특성을 검색 하려면 비트 or (&#124;) 연산자를 사용 합니다. 다음 특성을 임의로 조합 하 여 사용할 수 있습니다.

- 파일이 보관 파일인 FILE_ATTRIBUTE_ARCHIVE입니다. 응용 프로그램은이 특성을 사용 하 여 파일을 백업 또는 제거로 표시 합니다.

- 파일이 나 디렉터리가 압축 FILE_ATTRIBUTE_COMPRESSED 합니다. 파일의 경우이는 파일의 모든 데이터가 압축 됨을 의미 합니다. 디렉터리의 경우이는 압축이 새로 만든 파일과 하위 디렉터리에 대 한 기본값 임을 의미 합니다.

- 파일이 디렉터리인 FILE_ATTRIBUTE_DIRECTORY 합니다.

- FILE_ATTRIBUTE_NORMAL 파일에 다른 특성이 설정 되지 않았습니다. 이 특성은 단독 으로만 사용 되는 경우에만 유효 합니다. 다른 모든 파일 특성은이 특성을 재정의 합니다.

- 파일이 숨겨져 FILE_ATTRIBUTE_HIDDEN 합니다. 일반 디렉터리 목록에 포함 되지 않습니다.

- 파일이 읽기 전용인 FILE_ATTRIBUTE_READONLY입니다. 응용 프로그램은 파일을 읽을 수 있지만 파일에 쓰거나 삭제할 수 없습니다.

- 파일이의 일부 이거나 운영 체제에서 독점적으로 사용 FILE_ATTRIBUTE_SYSTEM입니다.

- 임시 저장소에 사용 되는 파일을 FILE_ATTRIBUTE_TEMPORARY 합니다. 응용 프로그램은 반드시 필요한 경우에만 파일에 써야 합니다. 파일을 곧 삭제 하기 때문에 대부분의 파일 데이터는 미디어에 플러시되지 않고 메모리에 유지 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 확장 오류 정보를 가져오려면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)를 호출 합니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [Findnextfile](#findnextfile) 을 한 번 이상 호출 해야 `MatchesMask` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 클래스](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind 클래스](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 클래스](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 클래스](../../mfc/reference/chttpfile-class.md)
