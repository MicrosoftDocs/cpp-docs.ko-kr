---
description: '자세한 정보: CAtlFile 클래스'
title: CAtlFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: d38ab3ad894a589fb59fe03691d6c764414cc8b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147396"
---
# <a name="catlfile-class"></a>CAtlFile 클래스

이 클래스는 Windows 파일 처리 API에 대 한 씬 래퍼를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlFile : public CHandle
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlFile:: CAtlFile](#catlfile)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlFile:: Create](#create)|이 메서드를 호출 하 여 파일을 만들거나 엽니다.|
|[CAtlFile:: Flush](#flush)|파일에 대 한 버퍼를 지우고 버퍼링 된 모든 데이터가 파일에 기록 되도록 하려면이 메서드를 호출 합니다.|
|[CAtlFile:: GetOverlappedResult](#getoverlappedresult)|파일에 대 한 겹쳐진 작업의 결과를 가져오려면이 메서드를 호출 합니다.|
|[CAtlFile:: GetPosition](#getposition)|이 메서드를 호출 하 여 파일에서 현재 파일 포인터 위치를 가져옵니다.|
|[CAtlFile:: GetSize](#getsize)|파일의 크기 (바이트)를 가져오려면이 메서드를 호출 합니다.|
|[CAtlFile:: LockRange](#lockrange)|다른 프로세스에서 액세스할 수 없도록 파일의 영역을 잠그려면이 메서드를 호출 합니다.|
|[CAtlFile:: Read](#read)|파일 포인터가 나타내는 위치에서 시작 하 여 파일에서 데이터를 읽으려면이 메서드를 호출 합니다.|
|[CAtlFile:: Seek](#seek)|파일의 파일 포인터를 이동 하려면이 메서드를 호출 합니다.|
|[CAtlFile:: SetSize](#setsize)|파일의 크기를 설정 하려면이 메서드를 호출 합니다.|
|[CAtlFile:: UnlockRange](#unlockrange)|파일의 영역을 잠금 해제 하려면이 메서드를 호출 합니다.|
|[CAtlFile:: Write](#write)|파일 포인터가 나타내는 위치에서 시작 하 여 파일에 데이터를 쓰려면이 메서드를 호출 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlFile:: m_pTM](#m_ptm)|개체에 대 한 포인터 `CAtlTransactionManager`|

## <a name="remarks"></a>설명

파일 처리 요구 사항이 비교적 단순 하지만 MFC 종속성을 포함 하지 않고 Windows API에서 제공 하는 것 보다 더 많은 추상화가 필요한 경우이 클래스를 사용 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>요구 사항

**헤더:** 이 파일 .h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a> CAtlFile:: CAtlFile

생성자입니다.

```cpp
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>매개 변수

*file*<br/>
파일 개체입니다.

*hFile*<br/>
파일 핸들입니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="remarks"></a>설명

복사 생성자는 파일 핸들의 소유권을 원래 `CAtlFile` 개체에서 새로 생성 된 개체로 전달 합니다.

## <a name="catlfilecreate"></a><a name="create"></a> CAtlFile:: Create

이 메서드를 호출 하 여 파일을 만들거나 엽니다.

```cpp
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*szFilename*<br/>
파일 이름입니다.

*dwDesiredAccess*<br/>
원하는 액세스입니다. Windows SDK의 [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) 에서 *dwDesiredAccess* 을 참조 하세요.

*dwShareMode*<br/>
공유 모드입니다. *DwShareMode* in을 참조 하세요 `CreateFile` .

*dwCreationDisposition*<br/>
만들기 처리입니다. *DwCreationDisposition* in을 참조 하세요 `CreateFile` .

*dwFlagsAndAttributes*<br/>
플래그와 특성입니다. *DwFlagsAndAttributes* in을 참조 하세요 `CreateFile` .

*lpsa*<br/>
보안 특성입니다. 에서 *Lpsecurityattributes* 를 참조 하세요 `CreateFile` .

*H템플릿 파일*<br/>
템플릿 파일입니다. 에서 *H템플릿 파일* 을 참조 하세요 `CreateFile` .

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) 을 호출 하 여 파일을 만들거나 엽니다.

## <a name="catlfileflush"></a><a name="flush"></a> CAtlFile:: Flush

파일에 대 한 버퍼를 지우고 버퍼링 된 모든 데이터가 파일에 기록 되도록 하려면이 메서드를 호출 합니다.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

는 [Flushfilebuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) 를 호출 하 여 버퍼링 된 데이터를 파일에 플러시합니다.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a> CAtlFile:: GetOverlappedResult

파일에 대 한 겹쳐진 작업의 결과를 가져오려면이 메서드를 호출 합니다.

```cpp
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>매개 변수

*pOverlapped*<br/>
겹쳐진 구조체입니다. Windows SDK에서 *lpOverlapped* 의 [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) 을 참조 하세요.

*dwBytesTransferred*<br/>
전송 된 바이트입니다. *LpNumberOfBytesTransferred* in을 참조 하세요 `GetOverlappedResult` .

*bWait*<br/>
Wait 옵션입니다. *Bwait* in을 참조 하세요 `GetOverlappedResult` .

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) 를 호출 하 여 파일에 대 한 겹쳐진 작업의 결과를 가져옵니다.

## <a name="catlfilegetposition"></a><a name="getposition"></a> CAtlFile:: GetPosition

현재 파일 포인터 위치를 가져오려면이 메서드를 호출 합니다.

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
바이트 단위의 위치입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[Setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) 를 호출 하 여 현재 파일 포인터 위치를 가져옵니다.

## <a name="catlfilegetsize"></a><a name="getsize"></a> CAtlFile:: GetSize

파일의 크기 (바이트)를 가져오려면이 메서드를 호출 합니다.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>매개 변수

*nLen*<br/>
파일의 바이트 수입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) 를 호출 하 여 파일의 바이트 크기를 가져옵니다.

## <a name="catlfilelockrange"></a><a name="lockrange"></a> CAtlFile:: LockRange

다른 프로세스에서 액세스할 수 없도록 파일의 영역을 잠그려면이 메서드를 호출 합니다.

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
잠금이 시작 되어야 하는 파일의 위치입니다.

*nCount*<br/>
잠글 바이트 범위의 길이입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[Lockfile](/windows/win32/api/fileapi/nf-fileapi-lockfile) 을 호출 하 여 파일의 영역을 잠급니다. 파일의 바이트를 잠그면 다른 프로세스에서 해당 바이트에 액세스할 수 없습니다. 하나 이상의 파일 영역을 잠글 수 있지만 겹치는 지역은 허용 되지 않습니다. [Catlfile:: UnlockRange](#unlockrange)를 사용 하 여 영역을 잠금 해제할 때 바이트 범위는 이전에 잠긴 지역과 정확히 일치 해야 합니다. `LockRange` 인접 한 영역을 병합 하지 않습니다. 잠긴 두 지역은 인접 한 경우 개별적으로 잠금을 해제 해야 합니다.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a> CAtlFile:: m_pTM

`CAtlTransactionManager` 개체에 대한 포인터입니다.

```cpp
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>설명

## <a name="catlfileread"></a><a name="read"></a> CAtlFile:: Read

파일 포인터가 나타내는 위치에서 시작 하 여 파일에서 데이터를 읽으려면이 메서드를 호출 합니다.

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>매개 변수

*pBuffer*<br/>
파일에서 읽은 데이터를 수신 하는 버퍼에 대 한 포인터입니다.

*nBufSize*<br/>
버퍼 크기(바이트)입니다.

*nBytesRead*<br/>
읽은 바이트 수입니다.

*pOverlapped*<br/>
겹쳐진 구조체입니다. Windows SDK에서 [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) 의 *lpOverlapped* 를 참조 하세요.

*pfnCompletionRoutine*<br/>
완료 루틴입니다. Windows SDK [Readfileex](/windows/win32/api/fileapi/nf-fileapi-readfileex) 의 *lp의 일반 루틴* 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

처음 세 폼은 [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile)을 호출 하 고 마지막 [readfileex](/windows/win32/api/fileapi/nf-fileapi-readfileex) 는 파일에서 데이터를 읽습니다. 이러한 파일 포인터를 이동 하려면 [Catlfile:: Seek](#seek) 를 사용 합니다.

## <a name="catlfileseek"></a><a name="seek"></a> CAtlFile:: Seek

파일의 파일 포인터를 이동 하려면이 메서드를 호출 합니다.

```cpp
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
*Dwfrom에서* 지정 된 시작 지점에서의 오프셋입니다.

*dwFrom*<br/>
시작점 (FILE_BEGIN, FILE_CURRENT 또는 FILE_END)입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[Setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) 를 호출 하 여 파일 포인터를 이동 합니다.

## <a name="catlfilesetsize"></a><a name="setsize"></a> CAtlFile:: SetSize

파일의 크기를 설정 하려면이 메서드를 호출 합니다.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>매개 변수

*nNewLen*<br/>
파일의 새 길이 (바이트)입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[Setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) 및 [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) 를 호출 하 여 파일의 크기를 설정 합니다. 반환 시 파일 포인터는 파일의 끝에 배치 됩니다.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a> CAtlFile:: UnlockRange

파일의 영역을 잠금 해제 하려면이 메서드를 호출 합니다.

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
잠금 해제를 시작할 파일의 위치입니다.

*nCount*<br/>
잠금을 해제할 바이트 범위의 길이입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[Unlockfile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) 을 호출 하 여 파일 영역의 잠금을 해제 합니다.

## <a name="catlfilewrite"></a><a name="write"></a> CAtlFile:: Write

파일 포인터가 나타내는 위치에서 시작 하 여 파일에 데이터를 쓰려면이 메서드를 호출 합니다.

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>매개 변수

*pBuffer*<br/>
파일에 쓸 데이터를 포함 하는 버퍼입니다.

*nBufSize*<br/>
버퍼에서 전송 될 바이트 수입니다.

*pOverlapped*<br/>
겹쳐진 구조체입니다. Windows SDK에서 [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) 의 *lpOverlapped* 를 참조 하세요.

*pfnCompletionRoutine*<br/>
완료 루틴입니다. Windows SDK의 [Writefileex](/windows/win32/api/fileapi/nf-fileapi-writefileex) 에서 *lp# 루틴* 을 참조 하세요.

*pnBytesWritten*<br/>
쓴 바이트입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

처음 세 개의 폼 호출 [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)을 호출 하 고, 마지막으로 [writefileex](/windows/win32/api/fileapi/nf-fileapi-writefileex) 를 호출 하 여 파일에 데이터를 씁니다. 이러한 파일 포인터를 이동 하려면 [Catlfile:: Seek](#seek) 를 사용 합니다.

## <a name="see-also"></a>참고 항목

[Marquee 샘플](../../overview/visual-cpp-samples.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CHandle 클래스](../../atl/reference/chandle-class.md)
