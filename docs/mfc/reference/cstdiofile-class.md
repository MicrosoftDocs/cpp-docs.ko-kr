---
description: '자세히 알아보기: CStdioFile 클래스'
title: CStdioFile 클래스
ms.date: 08/29/2019
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: 9eda9054026635fd986cc5555d6f3260422438d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318626"
---
# <a name="cstdiofile-class"></a>CStdioFile 클래스

런타임 함수 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)에서 연 것과 같은 C 런타임 스트림 파일을 나타냅니다.

## <a name="syntax"></a>구문

```
class CStdioFile : public CFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|`CStdioFile`경로 또는 파일 포인터에서 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStdioFile:: Open](#open)|오버로드됨. Open은 기본 생성자와 함께 사용 하도록 설계 되었습니다 `CStdioFile` ( [CFile:: Open](../../mfc/reference/cfile-class.md#open)재정의).|
|[CStdioFile:: ReadString](#readstring)|텍스트 한 줄을 읽습니다.|
|[CStdioFile:: Seek](#seek)|현재 파일 포인터를 배치 합니다.|
|[CStdioFile:: WriteString](#writestring)|텍스트 한 줄을 씁니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CStdioFile:: m_pStream](#m_pstream)|열린 파일에 대 한 포인터를 포함 합니다.|

## <a name="remarks"></a>설명

스트림 파일은 버퍼링 되며 텍스트 모드 (기본값) 또는 이진 모드에서 열 수 있습니다.

텍스트 모드는 캐리지 리턴-줄 바꿈 쌍에 대 한 특수 한 처리를 제공 합니다. 텍스트 모드 개체에 줄 바꿈 (줄 바꿈) 문자 (0x0A)를 작성 하면 `CStdioFile` 바이트 쌍 (0x0D, 0x0A)이 파일에 전송 됩니다. 읽을 때 바이트 쌍 (0x0D, 0x0A)은 단일 0x0A 바이트로 변환 됩니다.

에서는 [CFile](../../mfc/reference/cfile-class.md) 함수 [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [Lockrange](../../mfc/reference/cfile-class.md#lockrange)및 [unlockrange](../../mfc/reference/cfile-class.md#unlockrange) 가 지원 되지 않습니다 `CStdioFile` .

에서 이러한 함수를 호출 하는 경우 `CStdioFile` [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)을 받게 됩니다.

사용에 대 한 자세한 내용은 `CStdioFile` *런타임 라이브러리 참조* 에서 [MFC의 파일](../../mfc/files-in-mfc.md) 및 [파일 처리](../../c-runtime-library/file-handling.md) 문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a> CStdioFile::CStdioFile

`CStdioFile` 개체를 생성하고 초기화합니다.

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>매개 변수

*pOpenStream*<br/>
C 런타임 함수 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)에 대 한 호출에서 반환 되는 파일 포인터를 지정 합니다.

*lpszFileName*<br/>
원하는 파일의 경로인 문자열을 지정 합니다. 경로는 상대적이거나 절대적일 수 있습니다.

*nOpenFlags*<br/>
파일 만들기, 파일 공유 및 파일 액세스 모드에 대 한 옵션을 지정 합니다. 비트 or () 연산자를 사용 하 여 여러 옵션을 지정할 수 있습니다 **|** .

하나의 파일 액세스 모드 옵션이 필요 합니다. 다른 모드는 선택 사항입니다. 모드 옵션 및 기타 플래그 목록은 [cfile:: CFile](../../mfc/reference/cfile-class.md#cfile) 을 참조 하세요. MFC 버전 3.0 이상에서는 공유 플래그를 사용할 수 있습니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 생성자는 파일을 개체에 연결 하지 않습니다 `CStdioFile` . 이 생성자를 사용 하는 경우 메서드를 사용 `CStdioFile::Open` 하 여 파일을 열고 개체에 연결 해야 합니다 `CStdioFile` .

단일 매개 변수 생성자는 열린 파일 스트림을 개체에 연결 합니다 `CStdioFile` . 허용 되는 포인터 값에는 미리 정의 된 입력/출력 파일 포인터 *stdin*, *stdout* 또는 *stderr* 이 포함 됩니다.

두 매개 변수 생성자는 개체를 만들고 `CStdioFile` 지정 된 경로를 사용 하 여 해당 파일을 엽니다.

*Popenstream* 또는 *LPSZFILENAME* 에 대해 NULL을 전달 하는 경우 생성자는을 throw `CInvalidArgException*` 합니다.

파일을 열거나 만들 수 없으면 생성자는을 throw `CFileException*` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a> CStdioFile:: m_pStream

`m_pStream`데이터 멤버는 C 런타임 함수에서 반환 되는 열린 파일에 대 한 포인터입니다 `fopen` .

```
FILE* m_pStream;
```

### <a name="remarks"></a>설명

파일이 열려 있거나 종결 되지 않은 경우에는 NULL입니다.

## <a name="cstdiofileopen"></a><a name="open"></a> CStdioFile:: Open

오버로드됨. Open은 기본 생성자와 함께 사용 하도록 설계 되었습니다 `CStdioFile` .

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
원하는 파일의 경로인 문자열입니다. 경로는 상대적이거나 절대적일 수 있습니다.

*nOpenFlags*<br/>
공유 및 액세스 모드 파일을 열 때 수행할 동작을 지정 합니다. 비트 or (&#124;) 연산자를 사용 하 여 옵션을 조합할 수 있습니다. 하나의 액세스 권한 및 하나의 공유 옵션이 필요 합니다. modeCreate 및 modeNoInherit 모드는 선택 사항입니다.

*pError*<br/>
실패 한 작업의 상태를 수신 하는 기존 파일-예외 개체에 대 한 포인터입니다.

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cstdiofilereadstring"></a><a name="readstring"></a> CStdioFile:: ReadString

개체와 연결 된 파일에서 텍스트 데이터를 버퍼 ( *n 일별 최대*-1 자까지)로 읽어옵니다 `CStdioFile` .

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>매개 변수

*lpsz*<br/>
Null로 종료 되는 텍스트 문자열을 받을 사용자 제공 버퍼에 대 한 포인터를 지정 합니다.

*nMax*<br/>
Null 종결 문자를 제외 하 고 읽을 최대 문자 수를 지정 합니다.

*rString*<br/>
`CString`함수가 반환 될 때 문자열을 포함 하는 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

텍스트 데이터를 포함 하는 버퍼에 대 한 포인터입니다. 데이터를 읽지 않고 파일의 끝에 도달한 경우 NULL입니다. 또는 부울 인 경우 데이터를 읽지 않고 파일의 끝에 도달한 경우 FALSE입니다.

### <a name="remarks"></a>설명

첫 번째 줄 바꿈 문자에 의해 읽기가 중지 됩니다. 이 경우 *n 일별 최대* 자 미만의 문자를 읽은 경우 줄 바꿈 문자는 버퍼에 저장 됩니다. 두 경우 모두 null 문자 (' \ 0 ')가 추가 됩니다.

[CFile:: Read](../../mfc/reference/cfile-class.md#read) 는 텍스트 모드 입력에도 사용할 수 있지만 캐리지 리턴-줄 바꿈 쌍에서는 종료 되지 않습니다.

> [!NOTE]
> `CString`이 함수의 버전은가 있는 경우를 제거 합니다. `'\n'` LPTSTR 버전은 그렇지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a> CStdioFile:: Seek

이전에 연 파일에서 포인터의 위치를 재배치 합니다.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>매개 변수

*lOff*<br/>
포인터를 이동 하는 바이트 수입니다.

*nFrom*<br/>
포인터 이동 모드입니다. 다음 값 중 하나여야 합니다.

- `CFile::begin`: 파일 포인터를 파일의 시작 부분에서 *lOff* 바이트 앞으로 이동 합니다.

- `CFile::current`: 파일 포인터를 파일의 현재 위치에서 *lOff* 바이트로 이동 합니다.

- `CFile::end`: 파일의 끝에서 *lOff* 바이트까지 파일 포인터를 이동 합니다. 기존 파일을 검색 하려면 *lOff* 가 음수 여야 합니다. 양수 값은 파일의 끝을 지 나 검색 합니다.

### <a name="return-value"></a>반환 값

요청 된 위치가 유효 하면는 `Seek` 파일의 시작 부분에서 새 바이트 오프셋을 반환 합니다. 그렇지 않으면 반환 값이 정의 되지 않고 `CFileException` 개체가 throw 됩니다.

### <a name="remarks"></a>설명

`Seek`함수는 포인터를 지정 된 양 (절대적 또는 상대적)으로 이동 하 여 파일의 내용에 대 한 임의 액세스를 허용 합니다. 검색 하는 동안 실제로 데이터를 읽을 수 없습니다. 요청 된 위치가 파일 크기 보다 크면 파일 길이는 해당 위치로 확장 되 고 예외가 throw 되지 않습니다.

파일이 열리면 파일 포인터는 파일의 시작 부분에 있는 오프셋 0에 배치 됩니다.

의이 구현은 `Seek` CRT (Run-Time 라이브러리) 함수를 기반으로 `fseek` 합니다. 텍스트 모드에서 열린 스트림의 사용에는 몇 가지 제한이 있습니다 `Seek` . 자세한 내용은 [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)를 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는를 사용 하 여 `Seek` 포인터 1000 바이트를 파일의 시작 부분에서 이동 하는 방법을 보여 줍니다 `cfile` . 는 `Seek` 데이터를 읽지 않으므로 나중에 [CStdioFile:: ReadString](#readstring) 를 호출 하 여 데이터를 읽어야 합니다.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a> CStdioFile:: WriteString

버퍼의 데이터를 개체와 연결 된 파일에 씁니다 `CStdioFile` .

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>매개 변수

*lpsz*<br/>
Null로 끝나는 문자열을 포함 하는 버퍼에 대 한 포인터를 지정 합니다.

### <a name="remarks"></a>설명

종료 null 문자 ( `\0` )는 파일에 기록 되지 않습니다. 이 메서드는 *lpsz* 의 줄 바꿈 문자를 캐리지 리턴-줄 바꿈 쌍으로 파일에 씁니다.

Null로 종료 되지 않는 데이터를 파일에 쓰려면 `CStdioFile::Write` 또는 [CFile:: write](../../mfc/reference/cfile-class.md#write)를 사용 합니다.

`CInvalidArgException*` *Lpsz* 매개 변수에 NULL을 지정 하는 경우이 메서드는을 throw 합니다.

이 메서드는 `CFileException*` 파일 시스템 오류에 대 한 응답으로을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>참고 항목

[CFile 클래스](../../mfc/reference/cfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFile 클래스](../../mfc/reference/cfile-class.md)<br/>
[CFile::D u)](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile:: LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile:: UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException 클래스](../../mfc/reference/cnotsupportedexception-class.md)
