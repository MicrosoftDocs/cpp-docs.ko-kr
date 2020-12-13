---
description: '자세히 알아보기: CAtlTemporaryFile 클래스'
title: CAtlTemporaryFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: 44431132e4ce1535b29b1b0f9409c095b8fa9fd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152610"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 클래스

이 클래스는 임시 파일을 만들고 사용 하기 위한 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlTemporaryFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|생성자입니다.|
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlTemporaryFile:: Close](#close)|임시 파일을 닫고 해당 내용을 삭제 하거나 지정 된 파일 이름으로 저장 하려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: Create](#create)|임시 파일을 만들려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: Flush](#flush)|파일 버퍼에 남아 있는 모든 데이터가 임시 파일에 기록 되도록 하려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: GetPosition](#getposition)|현재 파일 포인터 위치를 가져오려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: GetSize](#getsize)|임시 파일의 크기 (바이트)를 가져오려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|이 메서드를 호출 하 여 개체에서 파일의 연결을 해제 `CAtlTemporaryFile` 합니다.|
|[CAtlTemporaryFile:: 수동 아들](#handson)|이 메서드를 호출 하 여 기존 임시 파일을 열고 파일 끝에 포인터를 놓습니다.|
|[CAtlTemporaryFile:: LockRange](#lockrange)|다른 프로세스에서 액세스할 수 없도록 파일의 영역을 잠그려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: Read](#read)|파일 포인터가 나타내는 위치에서 시작 하 여 임시 파일에서 데이터를 읽으려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: Seek](#seek)|임시 파일의 파일 포인터를 이동 하려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: SetSize](#setsize)|임시 파일의 크기를 설정 하려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: TempFileName](#tempfilename)|임시 파일의 이름을 반환 하려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: UnlockRange](#unlockrange)|임시 파일의 영역을 잠금 해제 하려면이 메서드를 호출 합니다.|
|[CAtlTemporaryFile:: Write](#write)|파일 포인터가 나타내는 위치에서 시작 하 여 임시 파일에 데이터를 쓰려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAtlTemporaryFile:: operator 핸들](#operator_handle)|임시 파일에 대 한 핸들을 반환 합니다.|

## <a name="remarks"></a>설명

`CAtlTemporaryFile` 를 사용 하면 임시 파일을 쉽게 만들고 사용할 수 있습니다. 파일의 이름이 자동으로 지정 되 고, 열림, 닫힘 및 삭제 됩니다. 파일을 닫은 후 파일 내용이 필요한 경우 지정 된 이름의 새 파일에 파일을 저장할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** 이 파일 .h

## <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a> CAtlTemporaryFile::CAtlTemporaryFile

생성자입니다.

```cpp
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>설명

[CAtlTemporaryFile:: Create](#create)를 호출 하기 전에는 파일이 실제로 열리지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a> CAtlTemporaryFile:: ~ CAtlTemporaryFile

소멸자입니다.

```cpp
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>설명

소멸자는 [CAtlTemporaryFile:: Close](#close)를 호출 합니다.

## <a name="catltemporaryfileclose"></a><a name="close"></a> CAtlTemporaryFile:: Close

임시 파일을 닫고 해당 내용을 삭제 하거나 지정 된 파일 이름으로 저장 하려면이 메서드를 호출 합니다.

```cpp
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*szNewName*<br/>
임시 파일의 내용을 저장할 새 파일의 이름입니다. 이 인수가 NULL 이면 임시 파일의 내용이 삭제 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="catltemporaryfilecreate"></a><a name="create"></a> CAtlTemporaryFile:: Create

임시 파일을 만들려면이 메서드를 호출 합니다.

```cpp
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>매개 변수

*pszDir*<br/>
임시 파일의 경로입니다. NULL 이면 경로를 할당 하기 위해 [Gettemppath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) 가 호출 됩니다.

*dwDesiredAccess*<br/>
원하는 액세스입니다. Windows SDK의 [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) 에서 *dwDesiredAccess* 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="catltemporaryfileflush"></a><a name="flush"></a> CAtlTemporaryFile:: Flush

파일 버퍼에 남아 있는 모든 데이터가 임시 파일에 기록 되도록 하려면이 메서드를 호출 합니다.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[CAtlTemporaryFile:: HandsOff](#handsoff)와 유사 합니다. 단, 파일이 닫혀 있지는 않습니다.

### <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a> CAtlTemporaryFile:: GetPosition

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

파일 포인터 위치를 변경 하려면 [CAtlTemporaryFile:: Seek](#seek)를 사용 합니다.

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a> CAtlTemporaryFile:: GetSize

임시 파일의 크기 (바이트)를 가져오려면이 메서드를 호출 합니다.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>매개 변수

*nLen*<br/>
파일의 바이트 수입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a> CAtlTemporaryFile::HandsOff

이 메서드를 호출 하 여 개체에서 파일의 연결을 해제 `CAtlTemporaryFile` 합니다.

```cpp
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`HandsOff` 및 [CAtlTemporaryFile:: 핸드 son](#handson) 은 개체에서 파일을 분리 하 고 필요한 경우 다시 연결 하는 데 사용 됩니다. `HandsOff` 는 파일 버퍼에 남아 있는 모든 데이터를 임시 파일에 쓴 다음 파일을 닫습니다. 파일을 영구적으로 닫고 삭제 하려면이 고, 파일의 내용을 닫고 지정 된 이름으로 유지 하려면 [CAtlTemporaryFile:: close](#close)를 사용 합니다.

## <a name="catltemporaryfilehandson"></a><a name="handson"></a> CAtlTemporaryFile:: 수동 아들

이 메서드를 호출 하 여 기존 임시 파일을 열고 파일 끝에 포인터를 놓습니다.

```cpp
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[CAtlTemporaryFile:: HandsOff](#handsoff) 및는 `HandsOn` 개체에서 파일을 분리 하 고 필요한 경우 다시 연결 하는 데 사용 됩니다.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a> CAtlTemporaryFile:: LockRange

다른 프로세스에서 액세스할 수 없도록 임시 파일의 영역을 잠그려면이 메서드를 호출 합니다.

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

파일의 바이트를 잠그면 다른 프로세스에서 해당 바이트에 액세스할 수 없습니다. 하나 이상의 파일 영역을 잠글 수 있지만 겹치는 지역은 허용 되지 않습니다. 영역을 성공적으로 잠금 해제 하려면 [CAtlTemporaryFile:: UnlockRange](#unlockrange)를 사용 하 여 바이트 범위가 이전에 잠긴 지역과 정확히 일치 하는지 확인 합니다. `LockRange` 인접 한 영역을 병합 하지 않습니다. 잠긴 두 지역은 인접 한 경우 개별적으로 잠금을 해제 해야 합니다.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a> CAtlTemporaryFile:: operator 핸들

임시 파일에 대 한 핸들을 반환 합니다.

```cpp
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a> CAtlTemporaryFile:: Read

파일 포인터가 나타내는 위치에서 시작 하 여 임시 파일에서 데이터를 읽으려면이 메서드를 호출 합니다.

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>매개 변수

*pBuffer*<br/>
파일에서 읽은 데이터를 수신 하는 버퍼에 대 한 포인터입니다.

*nBufSize*<br/>
버퍼 크기(바이트)입니다.

*nBytesRead*<br/>
읽은 바이트 수입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

를 [호출 합니다.](../../atl/reference/catlfile-class.md#read) 파일 포인터의 위치를 변경 하려면 [CAtlTemporaryFile:: Seek](#seek)를 호출 합니다.

### <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="catltemporaryfileseek"></a><a name="seek"></a> CAtlTemporaryFile:: Seek

임시 파일의 파일 포인터를 이동 하려면이 메서드를 호출 합니다.

```cpp
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
*Dwfrom에서* 지정 된 시작 지점의 오프셋 (바이트)입니다.

*dwFrom*<br/>
시작점 (FILE_BEGIN, FILE_CURRENT 또는 FILE_END)입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

는 [Catlfile:: Seek](../../atl/reference/catlfile-class.md#seek)를 호출 합니다. 현재 파일 포인터 위치를 가져오려면 [CAtlTemporaryFile:: GetPosition](#getposition)을 호출 합니다.

### <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a> CAtlTemporaryFile:: SetSize

임시 파일의 크기를 설정 하려면이 메서드를 호출 합니다.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>매개 변수

*nNewLen*<br/>
파일의 새 길이 (바이트)입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

는 [Catlfile:: SetSize](../../atl/reference/catlfile-class.md#setsize)를 호출 합니다. 반환 시 파일 포인터는 파일의 끝에 배치 됩니다.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a> CAtlTemporaryFile:: TempFileName

임시 파일의 이름을 반환 하려면이 메서드를 호출 합니다.

```cpp
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>반환 값

파일 이름을 가리키는 LPCTSTR를 반환 합니다.

### <a name="remarks"></a>설명

파일 이름은 [Gettempfile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK 함수에 대 한 호출을 사용 하 여 [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile) 에서 생성 됩니다. 임시 파일에 대 한 파일 확장명은 항상 "TFR"입니다.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a> CAtlTemporaryFile:: UnlockRange

임시 파일의 영역을 잠금 해제 하려면이 메서드를 호출 합니다.

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

는 [Catlfile:: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)를 호출 합니다.

## <a name="catltemporaryfilewrite"></a><a name="write"></a> CAtlTemporaryFile:: Write

파일 포인터가 나타내는 위치에서 시작 하 여 임시 파일에 데이터를 쓰려면이 메서드를 호출 합니다.

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*pBuffer*<br/>
파일에 쓸 데이터를 포함 하는 버퍼입니다.

*nBufSize*<br/>
버퍼에서 전송 될 바이트 수입니다.

*pnBytesWritten*<br/>
쓰여진 바이트 수입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

는 [Catlfile:: Write](../../atl/reference/catlfile-class.md#write)를 호출 합니다.

### <a name="example"></a>예제

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CAtlFile 클래스](../../atl/reference/catlfile-class.md)
