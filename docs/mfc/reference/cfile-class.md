---
description: '자세히 알아보기: CFile 클래스'
title: CFile 클래스
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: edccd571edf3594d36679a6c4ed6e52df878a705
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184545"
---
# <a name="cfile-class"></a>CFile 클래스

MFC 파일 클래스의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CFile : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFile:: CFile](#cfile)|`CFile`경로 또는 파일 핸들에서 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFile:: Abort](#abort)|모든 경고 및 오류를 무시 하는 파일을 닫습니다.|
|[CFile:: Close](#close)|파일을 닫고 개체를 삭제 합니다.|
|[CFile::D u)](#duplicate)|이 파일을 기반으로 중복 개체를 생성 합니다.|
|[CFile:: Flush](#flush)|쓸 데이터를 플러시합니다.|
|[CFile:: GetFileName](#getfilename)|선택한 파일의 파일 이름을 검색 합니다.|
|[CFile:: GetFilePath](#getfilepath)|선택한 파일의 전체 파일 경로를 검색 합니다.|
|[CFile:: GetFileTitle](#getfiletitle)|선택한 파일의 제목을 검색 합니다.|
|[CFile:: GetLength](#getlength)|파일의 길이를 검색 합니다.|
|[CFile:: GetPosition](#getposition)|현재 파일 포인터를 검색 합니다.|
|[CFile:: GetStatus](#getstatus)|열려 있는 파일 또는 정적 버전의 상태를 검색 하 여 지정 된 파일의 상태 (정적, 가상 함수)를 검색 합니다.|
|[CFile:: LockRange](#lockrange)|파일의 바이트 범위를 잠급니다.|
|[CFile:: Open](#open)|오류 테스트 옵션을 사용 하 여 파일을 안전 하 게 엽니다.|
|[CFile:: Read](#read)|파일의 현재 파일 위치에서 버퍼링 되지 않은 데이터를 읽습니다.|
|[CFile:: Remove](#remove)|지정 된 파일 (정적 함수)을 삭제 합니다.|
|[CFile:: Rename](#rename)|지정 된 파일의 이름을 바꿉니다 (정적 함수).|
|[CFile:: Seek](#seek)|현재 파일 포인터를 배치 합니다.|
|[CFile:: SeekToBegin](#seektobegin)|현재 파일 포인터를 파일의 시작 부분에 배치 합니다.|
|[CFile:: SeekToEnd](#seektoend)|현재 파일 포인터를 파일의 끝에 배치 합니다.|
|[CFile:: SetFilePath](#setfilepath)|선택한 파일의 전체 파일 경로를 설정 합니다.|
|[CFile:: SetLength](#setlength)|파일의 길이를 변경 합니다.|
|[CFile:: SetStatus](#setstatus)|지정 된 파일의 상태 (정적, 가상 함수)를 설정 합니다.|
|[CFile:: UnlockRange](#unlockrange)|파일의 바이트 범위를 해제 합니다.|
|[CFile:: Write](#write)|파일의 현재 파일 위치에 버퍼링 되지 않은 데이터를 씁니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CFile:: operator 핸들](#operator_handle)|개체에 대 한 핸들 `CFile` 입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFile:: hFileNull](#hfilenull)|개체에 유효한 핸들이 있는지 여부를 확인 `CFile` 합니다.|
|[CFile:: m_hFile](#m_hfile)|일반적으로 운영 체제 파일 핸들을 포함 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFile:: m_pTM](#m_ptm)|`CAtlTransactionManager` 개체에 대한 포인터입니다.|

## <a name="remarks"></a>설명

이 파일은 버퍼링 되지 않은 이진 디스크 입/출력 서비스를 직접 제공 하며 파생 된 클래스를 통해 텍스트 파일 및 메모리 파일을 간접적으로 지원 합니다. `CFile` 는 클래스와 함께 작동 `CArchive` 하 여 Microsoft Foundation class 개체의 serialization을 지원 합니다.

이 클래스와 파생 클래스 간의 계층 관계에서는 프로그램이 다형성 인터페이스를 통해 모든 파일 개체에서 작동할 수 있습니다 `CFile` . 예를 들어 메모리 파일은 디스크 파일 처럼 동작 합니다.

`CFile`및 해당 파생 클래스를 사용 하 여 범용 디스크 i/o를 사용 합니다. `ofstream` `iostream` 디스크 파일에 전송 된 서식 있는 텍스트에 또는 기타 Microsoft 클래스를 사용 합니다.

일반적으로 디스크 파일은 생성 시 자동으로 열리고 `CFile` 소멸 시 닫힙니다. 정적 멤버 함수를 사용 하면 파일을 열지 않고 파일의 상태를 확인할 수 있습니다.

사용에 대 한 자세한 내용은 `CFile` *런타임 라이브러리 참조* 에서 [MFC의 파일](../../mfc/files-in-mfc.md) 및 [파일 처리](../../c-runtime-library/file-handling.md) 문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cfileabort"></a><a name="abort"></a> CFile:: Abort

이 개체와 연결 된 파일을 닫고 파일을 읽거나 쓸 수 없게 만듭니다.

```
virtual void Abort();
```

### <a name="remarks"></a>설명

개체를 삭제 하기 전에 파일을 닫지 않은 경우 소멸자가 파일을 닫습니다.

예외를 처리할 때는 `CFile::Abort` `CFile::Close` 두 가지 중요 한 방법으로와 다릅니다. 첫째,이 `Abort` 함수는에서 오류를 무시 하기 때문에 오류 발생 시 예외를 throw 하지 않습니다 `Abort` . 둘째, `Abort` 파일이 열리지 않았거나 이전에 닫힌 경우 **어설션이** 발생 하지 않습니다.

힙에서 개체를 할당 하는 데를 사용한 경우에는 **`new`** `CFile` 파일을 닫은 후에 삭제 해야 합니다. `Abort` 설정 `m_hFile` 에 `CFile::hFileNull`입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a> CFile:: CFile

`CFile` 개체를 생성하고 초기화합니다.

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>매개 변수

*hFile*<br/>
`CFile` 개체에 연결할 파일의 핸들입니다.

*lpszFileName*<br/>
`CFile` 개체에 연결할 파일의 상대 또는 전체 경로입니다.

*nOpenFlags*<br/>
지정한 파일에 대한 파일 액세스 옵션의 비트 조합(OR)입니다. 사용 가능한 옵션은 설명 섹션을 참조하세요.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="remarks"></a>설명

다음 5 개의 표에서는 *nOpenFlags* 매개 변수에 사용할 수 있는 옵션을 나열 합니다.

다음 파일 액세스 모드 옵션 중 하나만 선택해야 합니다. 기본 파일 액세스 모드는 `CFile::modeRead`(읽기 전용)입니다.

|값|설명|
|-----------|-----------------|
|`CFile::modeRead`|읽기 권한만 요청합니다.|
|`CFile::modeWrite`|쓰기 권한만 요청합니다.|
|`CFile::modeReadWrite`|읽기 및 쓰기 권한을 요청합니다.|

다음 문자 모드 옵션 중 하나를 선택합니다.

|값|설명|
|-----------|-----------------|
|`CFile::typeBinary`|이진 모드를 설정합니다(파생 클래스에만 사용됨).|
|`CFile::typeText`|캐리지 리턴-줄 바꿈 쌍에 대 한 특수 처리를 사용 하 여 텍스트 모드를 설정 합니다 (파생 클래스에만 사용 됨).|
|`CFile::typeUnicode`|유니코드 모드를 설정합니다(파생 클래스에만 사용됨). 애플리케이션을 유니코드 구성에서 빌드할 때는 텍스트가 유니코드 형식으로 파일에 기록됩니다. BOM이 파일에 기록되지 않습니다.|

다음 파일 공유 모드 옵션 중 하나만 선택해야 합니다. 기본 파일 공유 모드는 `CFile::shareExclusive`(단독)입니다.

|값|설명|
|-----------|-----------------|
|`CFile::shareDenyNone`|공유 제한이 없습니다.|
|`CFile::shareDenyRead`|다른 모든 사용자에 대해 읽기 권한을 거부합니다.|
|`CFile::shareDenyWrite`|다른 모든 사용자에 대해 쓰기 권한을 거부합니다.|
|`CFile::shareExclusive`|다른 모든 사용자에 대해 읽기 및 쓰기 권한을 거부합니다.|

다음 파일 만들기 모드 옵션 중 첫 번째 옵션 또는 두 옵션을 모두 선택합니다. 기본 만들기 모드는 `CFile::modeNoTruncate`(기존 파일 열기)입니다.

|값|설명|
|-----------|-----------------|
|`CFile::modeCreate`|파일이 없으면 새 파일을 만듭니다. 파일이 이미 있으면 덮어쓴 후 처음에 길이가 0으로 설정 됩니다.|
|`CFile::modeNoTruncate`|파일이 없으면 새 파일을 만듭니다. 그렇지 않은 경우 파일이 이미 있으면 개체에 연결 `CFile` 됩니다.|

설명에 따라 다음 파일 캐싱 옵션을 선택합니다. 기본적으로 시스템은 옵션으로 사용할 수 없는 범용 캐싱 구성표를 사용 합니다.

|값|설명|
|-----------|-----------------|
|`CFile::osNoBuffer`|시스템에서 파일에 대해 중간 캐시를 사용 하지 않습니다. 이 옵션은 다음 2개 옵션을 취소합니다.|
|`CFile::osRandomAccess`|임의 액세스를 위해 파일 캐시가 최적화됩니다. 이 옵션과 순차 검색 옵션을 모두 사용 하지 마십시오.|
|`CFile::osSequentialScan`|순차 액세스를 위해 파일 캐시가 최적화됩니다. 이 옵션과 임의 액세스 옵션을 모두 사용 하지 마세요.|
|`CFile::osWriteThrough`|쓰기 작업은 지연 없이 수행 됩니다.|

파일 핸들이 상속되지 않도록 하려면 다음 보안 옵션을 선택합니다. 기본적으로 새 자식 프로세스는 파일 핸들을 사용할 수 있습니다.

|값|설명|
|-----------|-----------------|
|`CFile::modeNoInherit`|자식 프로세스가 파일 핸들을 사용하지 못하도록 차단합니다.|

기본 생성자는 멤버를 초기화 하지만 개체에는 파일을 첨부 하지 않습니다 `CFile` . 이 생성자를 사용한 후에는 [CFile:: Open](#open) 메서드를 사용 하 여 파일을 열고 개체에 연결 `CFile` 합니다.

매개 변수가 하나 포함된 생성자는 멤버를 초기화하고 기존 파일을 `CFile` 개체에 연결합니다.

매개 변수가 두 개 포함된 생성자는 멤버를 초기화하고 지정한 파일 열기를 시도합니다. 이 생성자가 지정한 파일을 정상적으로 열면 파일은 `CFile` 개체에 연결되고, 그렇지 않으면 이 생성자가 `CInvalidArgException` 개체에 대한 포인터를 throw합니다. 예외를 처리 하는 방법에 대 한 자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)를 참조 하세요.

개체에서 `CFile` 지정 된 파일을 성공적으로 연 경우 개체가 제거 되 면이 파일은 자동으로 닫힙니다 `CFile` . 그렇지 않으면 개체에 더 이상 연결 되지 않은 파일을 명시적으로 닫아야 합니다 `CFile` .

### <a name="example"></a>예제

다음 코드에서는 `CFile` 사용 방법을 보여줍니다.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a> CFile:: Close

이 개체와 연결 된 파일을 닫고 파일을 읽거나 쓸 수 없게 만듭니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

개체를 삭제 하기 전에 파일을 닫지 않은 경우 소멸자가 파일을 닫습니다.

힙에서 개체를 할당 하는 데를 사용한 경우에는 **`new`** `CFile` 파일을 닫은 후에 삭제 해야 합니다. `Close` 설정 `m_hFile` 에 `CFile::hFileNull`입니다.

### <a name="example"></a>예제

[Cfile:: cfile](#cfile)의 예제를 참조 하세요.

## <a name="cfileduplicate"></a><a name="duplicate"></a> CFile::D u)

`CFile`지정 된 파일에 대해 중복 개체를 생성 합니다.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>반환 값

중복 개체에 대 한 포인터 `CFile` 입니다.

### <a name="remarks"></a>설명

이 함수는 C 런타임 함수와 동일 `_dup` 합니다.

## <a name="cfileflush"></a><a name="flush"></a> CFile:: Flush

파일 버퍼에 남아 있는 모든 데이터를 파일에 기록 하도록 합니다.

```
virtual void Flush();
```

### <a name="remarks"></a>설명

를 사용 하면 `Flush` 버퍼 플러시가 보장 되지 않습니다 `CArchive` . 보관 파일을 사용 하는 경우 먼저 [CArchive:: Flush](../../mfc/reference/carchive-class.md#flush) 를 호출 합니다.

### <a name="example"></a>예제

[CFile:: SetFilePath](#setfilepath)의 예제를 참조 하세요.

## <a name="cfilegetfilename"></a><a name="getfilename"></a> CFile:: GetFileName

이 멤버 함수를 호출 하 여 지정 된 파일의 이름을 검색 합니다.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>반환 값

파일 이름입니다.

### <a name="remarks"></a>설명

예를 들어 `GetFileName` 를 호출 하 여 파일에 대 한 메시지를 사용자에 게 생성 하면 파일 `c:\windows\write\myfile.wri` 이름 `myfile.wri` 이 반환 됩니다.

이름을 포함 하 여 파일의 전체 경로를 반환 하려면 [Getfilepath](#getfilepath)를 호출 합니다. 파일 ()의 제목을 반환 하려면 `myfile` [GetFileTitle](#getfiletitle)를 호출 합니다.

### <a name="example"></a>예제

이 코드 조각은 WINDOWS 디렉터리에서 SYSTEM.INI 파일을 엽니다. 이 예제에서는 출력 아래에 표시 된 것 처럼 이름 및 경로와 제목을 출력 합니다.

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a> CFile:: GetFilePath

이 멤버 함수를 호출 하 여 지정 된 파일의 전체 경로를 검색 합니다.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>반환 값

지정 된 파일의 전체 경로입니다.

### <a name="remarks"></a>설명

예를 들어 `GetFilePath` 를 호출 하 여 파일에 대 한 메시지를 사용자에 게 생성 하면 `c:\windows\write\myfile.wri` 파일 경로가 `c:\windows\write\myfile.wri` 반환 됩니다.

파일 이름 ()만 반환 하려면 `myfile.wri` [getfilename](#getfilename)을 호출 합니다. 파일 ()의 제목을 반환 하려면 `myfile` [GetFileTitle](#getfiletitle)를 호출 합니다.

### <a name="example"></a>예제

[Getfilename](#getfilename)의 예제를 참조 하세요.

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a> CFile:: GetFileTitle

이 멤버 함수를 호출 하 여 파일에 대 한 파일 제목 (표시 이름)을 검색 합니다.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>반환 값

내부 파일의 제목입니다.

### <a name="remarks"></a>설명

이 메서드는 [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) 를 호출 하 여 파일의 제목을 검색 합니다. 성공 하는 경우 메서드는 시스템에서 사용자에 게 파일 이름을 표시 하는 데 사용 하는 문자열을 반환 합니다. 그렇지 않으면 메서드는 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 을 호출 하 여 기본 파일의 파일 이름 (파일 확장명 포함)을 검색 합니다. 즉, 파일 확장명이 항상 반환 된 파일 제목 문자열에 포함 되지 않습니다. 자세한 내용은 Windows SDK에서 [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) 및 [pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 을 참조 하세요.

이름을 포함 하 여 파일의 전체 경로를 반환 하려면 [Getfilepath](#getfilepath)를 호출 합니다. 파일 이름만 반환 하려면 [Getfilename](#getfilename)을 호출 합니다.

### <a name="example"></a>예제

[Getfilename](#getfilename)의 예제를 참조 하세요.

## <a name="cfilegetlength"></a><a name="getlength"></a> CFile:: GetLength

파일의 현재 논리 길이 (바이트)를 가져옵니다.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>반환 값

파일의 길이입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a> CFile:: GetPosition

에 대 한 이후 호출에서 사용할 수 있는 파일 포인터의 현재 값을 가져옵니다 `Seek` .

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>반환 값

파일 포인터입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a> CFile:: GetStatus

이 메서드는 지정 된 `CFile` 개체 인스턴스 또는 지정 된 파일 경로와 관련 된 상태 정보를 검색 합니다.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*rStatus*<br/>
상태 정보를 받을 사용자 제공 구조체에 대 한 참조 `CFileStatus` 입니다. 구조에는 `CFileStatus` 다음과 같은 필드가 있습니다.

- `CTime m_ctime` 파일을 만든 날짜와 시간입니다.

- `CTime m_mtime` 파일이 마지막으로 수정 된 날짜와 시간입니다.

- `CTime m_atime` 읽기 위해 파일에 마지막으로 액세스 한 날짜와 시간입니다.

- `ULONGLONG m_size` DIR 명령에 의해 보고 되는 파일의 논리적 크기 (바이트)입니다.

- `BYTE m_attribute` 파일의 특성 바이트입니다.

- `char m_szFullName[_MAX_PATH]` Windows 문자 집합의 절대 파일 이름입니다.

*lpszFileName*<br/>
원하는 파일의 경로인 Windows 문자 집합의 문자열입니다. 경로는 상대 또는 절대 경로 이거나 네트워크 경로 이름을 포함할 수 있습니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="return-value"></a>반환 값

지정 된 파일에 대 한 상태 정보를 성공적으로 가져온 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

의 비정적 버전은 지정 된 `GetStatus` 개체와 연결 된 열린 파일의 상태 정보를 검색 합니다 `CFile` .  의 정적 버전은 `GetStatus` 파일을 실제로 열지 않고 지정 된 파일 경로에서 파일 상태를 가져옵니다. 이 버전은 파일의 존재 여부 및 액세스 권한을 테스트 하는 데 유용 합니다.

`m_attribute`구조체의 멤버는 `CFileStatus` 파일 특성 집합을 참조 합니다. `CFile`클래스는 파일 특성을 기호로 지정할 수 있도록 **특성** 열거형 형식을 제공 합니다.

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

## <a name="cfilehfilenull"></a><a name="hfilenull"></a> CFile:: hFileNull

개체에 대 한 올바른 파일 핸들이 있는지 확인 합니다 `CFile` .

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>설명

이 상수는 `CFile` 개체에 유효한 파일 핸들이 있는지 여부를 확인 하는 데 사용 됩니다.

다음 예에서는이 작업을 보여 줍니다.

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a> CFile:: LockRange

열려 있는 파일에서 바이트 범위를 잠그고 파일이 이미 잠겨 있는 경우 예외를 throw 합니다.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>매개 변수

*dwPos*<br/>
잠글 바이트 범위의 시작 바이트 오프셋입니다.

*dwCount*<br/>
잠글 범위의 바이트 수입니다.

### <a name="remarks"></a>설명

파일의 바이트를 잠그면 다른 프로세스에서 해당 바이트에 액세스할 수 없습니다. 하나 이상의 파일 영역을 잠글 수 있지만 겹치는 지역은 허용 되지 않습니다.

멤버 함수를 사용 하 여 영역을 잠금 해제할 때 `UnlockRange` 바이트 범위는 이전에 잠긴 지역과 정확히 일치 해야 합니다. `LockRange`함수는 인접 한 영역을 병합 하지 않습니다. 잠긴 두 지역은 인접 한 경우 각 지역의 잠금을 별도로 해제 해야 합니다.

> [!NOTE]
> 이 함수는 파생 클래스에 사용할 수 없습니다 `CMemFile` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a> CFile:: m_hFile

열려 있는 파일에 대 한 운영 체제 파일 핸들을 포함 합니다.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>설명

`m_hFile` 는 UINT 형식의 공용 변수입니다. `CFile::hFileNull`핸들이 할당 되지 않은 경우 운영 체제 독립적 빈 파일 표시기가 포함 됩니다.

`m_hFile`멤버의 의미가 파생 클래스에 따라 달라 지므로를 사용 하지 않는 것이 좋습니다. `m_hFile` 는 클래스의 다형 이외의 사용을 지원 하기 위해 편의상 public 멤버를 만듭니다.

## <a name="cfilem_ptm"></a><a name="m_ptm"></a> CFile:: m_pTM

`CAtlTransactionManager` 개체에 대한 포인터입니다.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>설명

## <a name="cfileopen"></a><a name="open"></a> CFile:: Open

오버로드됨. `Open` 는 기본 생성자와 함께 사용 하도록 설계 되었습니다 `CFile` .

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
원하는 파일의 경로를 포함 하는 문자열입니다. 경로는 상대 경로, 절대 경로 또는 UNC (네트워크 이름) 일 수 있습니다.

*nOpenFlags*<br/>
파일의 공유 및 액세스 모드를 정의 하는 UINT입니다. 파일을 열 때 수행할 작업을 지정 합니다. 비트 or ( **&#124;** ) 연산자를 사용 하 여 옵션을 조합할 수 있습니다. 하나의 액세스 권한 및 하나의 공유 옵션이 필요 합니다. `modeCreate` 및 `modeNoInherit` 모드는 선택 사항입니다. 모드 옵션 목록은 [CFile](#cfile) 생성자를 참조 하세요.

*pError*<br/>
실패 한 작업의 상태를 수신 하는 기존 파일-예외 개체에 대 한 포인터입니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="return-value"></a>반환 값

열기에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다. *PError* 매개 변수는 0이 반환 되는 경우에만 의미가 있습니다.

### <a name="remarks"></a>설명

두 `Open` 함수는 파일을 여는 데 사용할 수 있는 "안전한" 방법입니다. 여기서 오류는 정상적인 정상적인 조건입니다.

생성자는 `CFile` 오류 조건에서 예외를 throw 하지만는 `Open` 오류 조건에 대해 FALSE를 반환 합니다. `Open` 그러나에서는 여전히 [Cfileexception](../../mfc/reference/cfileexception-class.md) 개체를 초기화 하 여 오류를 설명할 수 있습니다. *PError* 매개 변수를 제공 하지 않거나 *PERROR* 에 대해 NULL을 전달 하는 경우 `Open` 는 FALSE를 반환 하 고을 throw 하지 않습니다 `CFileException` . 기존에 포인터를 전달 하 `CFileException` 고 오류가 발생 하는 경우 `Open` 함수는 해당 오류를 설명 하는 정보로이를 채웁니다. `Open` 는 두 경우 모두 예외를 throw 하지 않습니다.

다음 표에서는의 가능한 결과에 대해 설명 합니다 `Open` .

| `pError` | 오류가 발생 했습니다. | 반환 값 | CFileException 콘텐츠 |
|--|--|--|--|
| NULL | 예 | TRUE | 해당 없음 |
| ptr `CFileException` | 아니요 | TRUE | 변경 안 됨 |
| NULL | 예 | FALSE | 해당 없음 |
| ptr `CFileException` | 예 | FALSE | 오류를 설명 하기 위해 초기화 됨 |

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a> CFile:: operator 핸들

이 연산자를 사용 하 여 `CFile` 를 필요로 하는 [Readfileex](/windows/win32/api/fileapi/nf-fileapi-readfileex) 및 [getfiletime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) 과 같은 함수에 개체 핸들을 전달 `HANDLE` 합니다.

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a> CFile:: Read

개체와 연결 된 파일에서 버퍼로 데이터를 읽습니다 `CFile` .

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
파일에서 읽은 데이터를 받을 사용자 제공 버퍼에 대 한 포인터입니다.

*nCount*<br/>
파일에서 읽을 최대 바이트 수입니다. 텍스트 모드 파일의 경우 캐리지 리턴-줄 바꿈 쌍은 단일 문자로 계산 됩니다.

### <a name="return-value"></a>반환 값

버퍼로 전송된 바이트 수입니다. `CFile`파일의 끝에 도달 하는 경우 모든 클래스의 경우 반환 값은 *ncount* 보다 적을 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

다른 예제는 [CFile:: Open](#open)을 참조 하세요.

## <a name="cfileremove"></a><a name="remove"></a> CFile:: Remove

이 정적 함수는 경로에 지정 된 파일을 삭제 합니다.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
원하는 파일의 경로인 문자열입니다. 경로는 상대적 이거나 절대적일 수 있으며 네트워크 이름을 포함할 수 있습니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="remarks"></a>설명

`Remove` 디렉터리를 제거 하지 않습니다.

`Remove`연결 된 파일이 열려 있거나 파일을 제거할 수 없는 경우 멤버 함수는 예외를 throw 합니다. 이 함수는 DEL 명령과 동일 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a> CFile:: Rename

이 정적 함수는 지정 된 파일의 이름을 바꿉니다.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszOldName*<br/>
이전 경로입니다.

*lpszNewName*<br/>
새 경로입니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="remarks"></a>설명

디렉터리의 이름을 바꿀 수 없습니다. 이 함수는 REN 명령과 동일 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a> CFile:: Seek

열려 있는 파일에서 파일 포인터의 위치를 재배치 합니다.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>매개 변수

*lOff*<br/>
파일 포인터를 이동 하는 바이트 수입니다. 양수 값은 파일 포인터를 파일 끝 쪽으로 이동 합니다. 음수 값은 파일 포인터를 파일의 시작 부분으로 이동 합니다.

*nFrom*<br/>
검색할 위치입니다. 가능한 값은 설명 섹션을 참조 하세요.

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 파일 포인터의 위치입니다. 그렇지 않으면 반환 값이 정의 되지 않고 예외에 대 한 포인터가 `CFileException` throw 됩니다.

### <a name="remarks"></a>설명

다음 표에서는 *Nfrom* 매개 변수의 가능한 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|`CFile::begin`|파일의 시작 부분에서 검색 합니다.|
|`CFile::current`|파일 포인터의 현재 위치에서 검색 합니다.|
|`CFile::end`|파일의 끝에서 검색 합니다.|

파일이 열리면 파일 포인터는 파일의 시작 부분에 있는 0에 배치 됩니다.

파일 포인터를 파일의 끝을 벗어난 위치로 설정할 수 있습니다. 이렇게 하면 파일을 쓸 때까지 파일 크기가 증가 하지 않습니다.

이 메서드에 대 한 예외 처리기는 예외를 처리 한 후 예외 개체를 삭제 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a> CFile:: SeekToBegin

파일 포인터의 값을 파일의 시작 부분으로 설정 합니다.

```cpp
void SeekToBegin();
```

### <a name="remarks"></a>설명

`SeekToBegin()`은 `Seek( 0L, CFile::begin )`와 동등합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a> CFile:: SeekToEnd

파일 포인터의 값을 파일의 논리적 끝으로 설정 합니다.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>반환 값

파일의 길이(바이트)입니다.

### <a name="remarks"></a>설명

`SeekToEnd()`은 `CFile::Seek( 0L, CFile::end )`와 동등합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a> CFile:: SetFilePath

이 함수를 호출 하 여 파일의 경로를 지정 합니다. 예를 들어, [CFile](../../mfc/reference/cfile-class.md) 개체가 생성 될 때 파일 경로를 사용할 수 없는 경우를 호출 `SetFilePath` 하 여 해당 경로를 제공 합니다.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>매개 변수

*lpszNewName*<br/>
새 경로를 지정 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> `SetFilePath` 는 파일을 열거나 파일을 만들지 않습니다. 이 메서드는 `CFile` 개체를 경로 이름과 연결한 후 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a> CFile:: SetLength

이 함수를 호출 하 여 파일 길이를 변경 합니다.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>매개 변수

*dwNewLen*<br/>
원하는 파일 길이 (바이트)입니다. 이 값은 파일의 현재 길이 보다 크거나 작을 수 있습니다. 파일은 적절 하 게 확장 되거나 잘립니다.

### <a name="remarks"></a>설명

> [!NOTE]
> `CMemFile`에서이 함수는 개체를 throw 할 수 있습니다 `CMemoryException` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a> CFile:: SetStatus

이 파일 위치와 연결 된 파일의 상태를 설정 합니다.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
원하는 파일의 경로인 문자열입니다. 경로는 상대적 이거나 절대적일 수 있으며 네트워크 이름을 포함할 수 있습니다.

*status*<br/>
새 상태 정보를 포함 하는 버퍼입니다. `GetStatus`멤버 함수를 호출 하 여 구조체를 `CFileStatus` 현재 값으로 미리 채운 다음 필요에 따라 변경 합니다. 값이 0 이면 해당 상태 항목이 업데이트 되지 않습니다. 구조체에 대 한 설명은 [GetStatus](#getstatus) 멤버 함수를 참조 하세요 `CFileStatus` .

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="remarks"></a>설명

시간을 설정 하려면 `m_mtime` *상태* 필드를 수정 합니다.

을 호출 하 여 `SetStatus` 파일의 특성만 변경 하 고 `m_mtime` 파일 상태 구조의 멤버가 0이 아닌 경우에도 특성이 영향을 받을 수 있습니다. 타임 스탬프를 변경 하면 특성에 부작용이 발생할 수 있습니다. 파일의 특성만 변경 하려면 먼저 `m_mtime` 파일 상태 구조의 멤버를 0으로 설정한 다음을 호출 `SetStatus` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a> CFile:: UnlockRange

열려 있는 파일에서 바이트의 범위를 해제 합니다.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>매개 변수

*dwPos*<br/>
잠금을 해제할 바이트 범위의 시작 바이트 오프셋입니다.

*dwCount*<br/>
잠금을 해제할 범위의 바이트 수입니다.

### <a name="remarks"></a>설명

자세한 내용은 [Lockrange](#lockrange) 멤버 함수에 대 한 설명을 참조 하십시오.

> [!NOTE]
> 이 함수는 파생 클래스에 사용할 수 없습니다 `CMemFile` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a> CFile:: Write

버퍼의 데이터를 개체와 연결 된 파일에 씁니다 `CFile` .

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
파일에 쓸 데이터를 포함 하는 사용자 제공 버퍼에 대 한 포인터입니다.

*nCount*<br/>
버퍼에서 전송 될 바이트 수입니다. 텍스트 모드 파일의 경우 캐리지 리턴-줄 바꿈 쌍은 단일 문자로 계산 됩니다.

### <a name="remarks"></a>설명

`Write` 는 디스크 전체 상태를 포함 하 여 여러 조건에 대 한 응답으로 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

또한 [cfile:: cfile](#cfile) 및 [Cfile:: Open](#open)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 클래스](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 클래스](../../mfc/reference/cmemfile-class.md)
