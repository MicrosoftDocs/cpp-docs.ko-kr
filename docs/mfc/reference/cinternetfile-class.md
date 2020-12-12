---
description: CInternetFile 클래스에 대해 자세히 알아보세요.
title: CInternetFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
ms.openlocfilehash: 486b5869d0773351443a923ceef345591131036c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143483"
---
# <a name="cinternetfile-class"></a>CInternetFile 클래스

인터넷 프로토콜을 사용 하는 원격 시스템의 파일에 대 한 액세스를 허용 합니다.

## <a name="syntax"></a>구문

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CInternetFile:: CInternetFile](#cinternetfile)|`CInternetFile` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CInternetFile::Abort](#abort)|모든 경고 및 오류를 무시 하 고 파일을 닫습니다.|
|[CInternetFile::Close](#close)|을 닫고 `CInternetFile` 해당 리소스를 해제 합니다.|
|[CInternetFile:: Flush](#flush)|쓰기 버퍼의 내용을 플러시하고 메모리의 데이터가 대상 컴퓨터에 기록 되는지 확인할 수 있습니다.|
|[CInternetFile:: GetLength](#getlength)|파일의 크기를 반환 합니다.|
|[CInternetFile::Read](#read)|지정 된 바이트 수를 읽습니다.|
|[CInternetFile::ReadString](#readstring)|문자 스트림을 읽습니다.|
|[CInternetFile::Seek](#seek)|열려 있는 파일에서 포인터의 위치를 재배치 합니다.|
|[CInternetFile:: SetReadBufferSize](#setreadbuffersize)|데이터를 읽을 버퍼의 크기를 설정 합니다.|
|[CInternetFile:: SetWriteBufferSize](#setwritebuffersize)|데이터가 기록 되는 버퍼의 크기를 설정 합니다.|
|[CInternetFile:: Write](#write)|지정 된 바이트 수를 씁니다.|
|[CInternetFile:: WriteString](#writestring)|Null로 끝나는 문자열을 파일에 씁니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CInternetFile:: operator HINTERNET](#operator_hinternet)|인터넷 핸들의 캐스팅 연산자입니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|파일에 대 한 핸들입니다.|

## <a name="remarks"></a>설명

[CHttpFile](../../mfc/reference/chttpfile-class.md) 및 [CGopherFile](../../mfc/reference/cgopherfile-class.md) 파일 클래스에 대 한 기본 클래스를 제공 합니다. 개체를 직접 만들지는 않습니다 `CInternetFile` . 대신 [CGopherConnection:: system.windows.forms.openfiledialog.openfile](../../mfc/reference/cgopherconnection-class.md#openfile) 또는 [CHttpConnection:: openrequest](../../mfc/reference/chttpconnection-class.md#openrequest)를 호출 하 여 파생 클래스 중 하나의 개체를 만듭니다. `CInternetFile` [Csystem.windows.forms.openfiledialog.openfile connection::](../../mfc/reference/cftpconnection-class.md#openfile)를 호출 하 여 개체를 만들 수도 있습니다.

`CInternetFile`멤버 함수 `Open` ,, `LockRange` 및는 `UnlockRange` `Duplicate` 에 대해 구현 되지 않습니다 `CInternetFile` . 개체에서 이러한 함수를 호출 하면 `CInternetFile` [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)이 발생 합니다.

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CInternetFile` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a> CInternetFile:: Abort

이 개체와 연결 된 파일을 닫고 파일을 읽거나 쓸 수 없게 만듭니다.

```
virtual void Abort();
```

### <a name="remarks"></a>설명

개체를 삭제 하기 전에 파일을 닫지 않은 경우 소멸자가 파일을 닫습니다.

예외를 처리할 때는 `Abort` 두 가지 중요 한 측면에서 [거의](#close) 차이가 있습니다. 첫째, `Abort` 함수는 오류를 무시 하기 때문에 오류 발생 시 예외를 throw 하지 않습니다. 두 번째는 `Abort` 파일이 열려 있지 않거나 이전에 닫힌 경우를 **어설션** 하지 않습니다.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a> CInternetFile:: CInternetFile

이 멤버 함수는 개체를 만들 때 호출 됩니다 `CInternetFile` .

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>매개 변수

*hFile*<br/>
인터넷 파일에 대 한 핸들입니다.

*pstrFileName*<br/>
파일 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pConnection*<br/>
[Cinternetconnection](../../mfc/reference/cinternetconnection-class.md) 개체에 대 한 포인터입니다.

*bReadMode*<br/>
파일이 읽기 전용인 지 여부를 나타냅니다.

*hSession*<br/>
인터넷 세션에 대 한 핸들입니다.

*pstrServer*<br/>
서버 이름이 포함 된 문자열에 대 한 포인터입니다.

*dwContext*<br/>
개체에 대 한 컨텍스트 식별자 `CInternetFile` 입니다. 컨텍스트 식별자에 대 한 자세한 내용은 [WinInet 기본 사항](../../mfc/wininet-basics.md) 을 참조 하세요.

### <a name="remarks"></a>설명

개체를 직접 만들지는 않습니다 `CInternetFile` . 대신 [CGopherConnection:: system.windows.forms.openfiledialog.openfile](../../mfc/reference/cgopherconnection-class.md#openfile) 또는 [CHttpConnection:: openrequest](../../mfc/reference/chttpconnection-class.md#openrequest)를 호출 하 여 파생 클래스 중 하나의 개체를 만듭니다. `CInternetFile` [Csystem.windows.forms.openfiledialog.openfile connection::](../../mfc/reference/cftpconnection-class.md#openfile)를 호출 하 여 개체를 만들 수도 있습니다.

## <a name="cinternetfileclose"></a><a name="close"></a> CInternetFile:: Close

을 닫고 `CInternetFile` 모든 리소스를 해제 합니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

파일이 쓰기용으로 열려 있는 [경우에는](#flush) 모든 버퍼링 된 데이터를 호스트에 쓰도록 암시적 호출이 발생 합니다. 파일 사용을 마쳤을 때를 호출 해야 합니다 `Close` .

## <a name="cinternetfileflush"></a><a name="flush"></a> CInternetFile:: Flush

이 멤버 함수를 호출 하 여 쓰기 버퍼의 콘텐츠를 플러시합니다.

```
virtual void Flush();
```

### <a name="remarks"></a>설명

`Flush`를 사용 하 여 메모리의 모든 데이터가 실제로 대상 컴퓨터에 기록 되었는지와 호스트 컴퓨터에 대 한 트랜잭션이 완료 되었는지를 보장 합니다. `Flush` 는 쓰기용으로 열린 개체에만 적용 됩니다 `CInternetFile` .

## <a name="cinternetfilegetlength"></a><a name="getlength"></a> CInternetFile:: GetLength

파일의 크기를 반환 합니다.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a> CInternetFile:: m_hFile

이 개체와 연결 된 파일에 대 한 핸들입니다.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a> CInternetFile:: operator HINTERNET

이 연산자를 사용 하 여 현재 인터넷 세션에 대 한 Windows 핸들을 가져옵니다.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a> CInternetFile:: Read

이 멤버 함수를 호출 하 여 *Lpvbuf* 에서 시작 하 여 지정 된 바이트 수 인 *ncount* 에서 시작 하는 지정 된 메모리를 읽습니다.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
파일 데이터를 읽을 메모리 주소에 대한 포인터입니다.

*nCount*<br/>
쓸 바이트 수 입니다.

### <a name="return-value"></a>반환 값

버퍼로 전송된 바이트 수입니다. 파일의 끝에 도달 하는 경우 반환 값은 *Ncount* 보다 적을 수 있습니다.

### <a name="remarks"></a>설명

함수는 실제로 읽은 바이트 수를 반환 합니다 .이 수는 파일이 종료 되는 경우 *Ncount* 보다 적을 수 있습니다. 파일을 읽는 동안 오류가 발생 하는 경우 함수는 오류를 설명 하는 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 throw 합니다. 파일의 끝을 지나서 읽는 것은 오류로 간주되지 않으며 예외가 throw되지 않습니다.

모든 데이터가 검색 되도록 하려면 `CInternetFile::Read` 메서드가 0을 반환할 때까지 응용 프로그램에서 메서드를 계속 호출 해야 합니다.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a> CInternetFile:: ReadString

이 멤버 함수를 호출 하 여 줄 바꿈 문자를 찾을 때까지 문자 스트림을 읽습니다.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>매개 변수

*pstr*<br/>
읽고 있는 줄을 받는 문자열에 대 한 포인터입니다.

*nMax*<br/>
읽을 최대 문자 수입니다.

*rString*<br/>
읽기 줄을 받는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

[Cinternetfile](../../mfc/reference/cinternetfile-class.md) 개체에서 검색 된 일반 데이터를 포함 하는 버퍼에 대 한 포인터입니다. 이 메서드에 전달 된 버퍼의 데이터 형식에 관계 없이, 데이터에 대 한 조작을 수행 하지 않습니다 (예: 유니코드로의 변환) **`void`** . 따라서 형식이 반환 된 것 처럼 반환 된 데이터를 필요한 구조에 매핑해야 합니다 <strong>\*</strong> .

데이터를 읽지 않고 파일의 끝에 도달한 경우 NULL입니다. 또는 부울 인 경우 데이터를 읽지 않고 파일의 끝에 도달한 경우 FALSE입니다.

### <a name="remarks"></a>설명

함수는 *pstr* 매개 변수에서 참조 하는 메모리에 결과 줄을 배치 합니다. *N 일별 최대* 로 지정 된 최대 문자 수에 도달 하면 문자 읽기를 중지 합니다. 버퍼는 항상 종료 null 문자를 받습니다.

`ReadString` [Setreadbuffersize](#setreadbuffersize)를 먼저 호출 하지 않고를 호출 하는 경우 4096 바이트의 버퍼를 가져옵니다.

## <a name="cinternetfileseek"></a><a name="seek"></a> CInternetFile:: Seek

이전에 연 파일에서 포인터의 위치를 변경 하려면이 멤버 함수를 호출 합니다.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>매개 변수

*lOffset*<br/>
읽기/쓰기 포인터를 파일에 이동할 오프셋 (바이트)입니다.

*nFrom*<br/>
오프셋에 대 한 상대 참조입니다. 다음 값 중 하나여야 합니다.

- `CFile::begin` 파일 포인터를 파일의 시작 부분에서 앞으로 *lOff* 바이트 앞으로 이동 합니다.

- `CFile::current` 파일의 현재 위치에서 *lOff* bytes 파일 포인터를 이동 합니다.

- `CFile::end` 파일의 끝에서 *lOff* 바이트까지 파일 포인터를 이동 합니다. 기존 파일을 검색 하려면 *lOff* 가 음수 여야 합니다. 양수 값은 파일의 끝을 지 나 검색 합니다.

### <a name="return-value"></a>반환 값

요청 된 위치가 유효한 경우 파일의 시작 부분부터의 새 바이트 오프셋입니다. 그렇지 않으면 값이 정의 되지 않으며 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체가 throw 됩니다.

### <a name="remarks"></a>설명

`Seek`함수는 포인터를 지정 된 양 (절대적 또는 상대적)으로 이동 하 여 파일의 내용에 대 한 임의 액세스를 허용 합니다. 검색 하는 동안 실제로 데이터를 읽을 수 없습니다.

현재이 멤버 함수에 대 한 호출은 개체와 연결 된 데이터에 대해서만 지원 됩니다 `CHttpFile` . FTP 또는 gopher 요청은 지원 되지 않습니다. `Seek`이러한 지원 되지 않는 서비스 중 하나에 대해를 호출 하면 ERROR_INTERNET_INVALID_OPERATION Win32 오류 코드로 다시 전달 됩니다.

파일이 열리면 파일 포인터는 파일의 시작 부분에 있는 오프셋 0에 있습니다.

> [!NOTE]
> `Seek`를 사용 하면 암시적 호출이 [플러시](#flush)될 수 있습니다.

### <a name="example"></a>예제

  기본 클래스 구현에 대 한 예제 ( [CFile:: Seek](../../mfc/reference/cfile-class.md#seek))를 참조 하세요.

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a> CInternetFile:: SetReadBufferSize

파생 개체에서 사용 하는 임시 읽기 버퍼의 크기를 설정 하려면이 멤버 함수를 호출 `CInternetFile` 합니다.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>매개 변수

*nReadSize*<br/>
원하는 버퍼 크기(바이트)입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

기본 WinInet Api는 버퍼링을 수행 하지 않으므로 읽을 데이터 양에 관계 없이 응용 프로그램이 데이터를 효율적으로 읽을 수 있도록 하는 버퍼 크기를 선택 합니다. 각 [읽기](#read) 에 대 한 각 호출에 일반적으로 많은 양의 데이터가 포함 된 경우 (예: 4kb 이상)에는 버퍼가 필요 하지 않습니다 aount. 그러나를 호출 `Read` 하 여 작은 데이터 청크를 가져오거나 [ReadString](#readstring) 를 사용 하 여 한 번에 개별 줄을 읽는 경우 읽기 버퍼는 응용 프로그램 성능을 향상 시킵니다.

기본적으로 개체는 `CInternetFile` 읽을 버퍼링을 제공 하지 않습니다. 이 멤버 함수를 호출 하는 경우 파일이 읽기 액세스를 위해 열려 있는지 확인 해야 합니다.

언제 든 지 버퍼 크기를 늘릴 수 있지만 버퍼를 축소 해도 아무런 효과가 없습니다. 먼저 `SetReadBufferSize`를 호출하지 않고 [ReadString](#readstring)를 호출하는 경우 4096 바이트의 버퍼를 가져옵니다.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a> CInternetFile:: SetWriteBufferSize

파생 개체에서 사용 하는 임시 쓰기 버퍼의 크기를 설정 하려면이 멤버 함수를 호출 `CInternetFile` 합니다.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>매개 변수

*nWriteSize*<br/>
버퍼 크기(바이트)입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

기본 WinInet Api는 버퍼링을 수행 하지 않으므로 쓸 데이터 양에 관계 없이 응용 프로그램에서 데이터를 효율적으로 쓸 수 있는 버퍼 크기를 선택 합니다. [쓰기](#write) 에 대 한 각 호출에 일반적으로 많은 양의 데이터가 포함 된 경우 (예: 한 번에 4 개 이상) 버퍼가 필요 하지 않습니다. 그러나 [write](#write) 를 호출 하 여 작은 데이터 청크를 쓰는 경우 쓰기 버퍼를 통해 응용 프로그램의 성능이 향상 됩니다.

기본적으로 개체는 `CInternetFile` 쓰기에 대 한 버퍼링을 제공 하지 않습니다. 이 멤버 함수를 호출 하는 경우 파일이 쓰기 권한으로 열려 있는지를 알고 있어야 합니다. 언제 든 지 쓰기 버퍼의 크기를 변경할 수 있지만 이렇게 하면 암시적 호출이 [플러시](#flush)됩니다.

## <a name="cinternetfilewrite"></a><a name="write"></a> CInternetFile:: Write

이 멤버 함수를 호출 하 여 지정 된 메모리 ( *Lpvbuf*)에 지정 된 바이트 수 ( *ncount*)를 씁니다.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
쓸 첫 번째 바이트에 대 한 포인터입니다.

*nCount*<br/>
쓸 바이트 수를 지정 합니다.

### <a name="remarks"></a>설명

데이터를 쓰는 동안 오류가 발생 하는 경우 함수는 오류를 설명 하는 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 throw 합니다.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a> CInternetFile:: WriteString

이 함수는 연결 된 파일에 null로 끝나는 문자열을 씁니다.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>매개 변수

*pstr*<br/>
쓸 콘텐츠를 포함 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터를 쓰는 동안 오류가 발생 하는 경우 함수는 오류를 설명 하는 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 throw 합니다.

## <a name="see-also"></a>참고 항목

[CStdioFile 클래스](../../mfc/reference/cstdiofile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)
