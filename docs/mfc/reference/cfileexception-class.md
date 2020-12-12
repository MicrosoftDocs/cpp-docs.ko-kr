---
description: '자세한 정보: CFileException 클래스'
title: CFileException 클래스
ms.date: 06/09/2020
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: a7540ffb22005ef0fe93954396f6fca1a5ae93af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184519"
---
# <a name="cfileexception-class"></a>CFileException 클래스

파일 관련 예외 상태를 나타냅니다.

## <a name="syntax"></a>구문

```
class CFileException : public CException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFileException:: CFileException](#cfileexception)|`CFileException` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFileException:: ErrnoToException](#errnotoexception)|런타임 오류 번호에 해당 하는 코드를 반환 합니다.|
|[CFileException:: GetErrorMessage](#geterrormessage)|예외를 설명 하는 메시지를 검색 합니다.|
|[CFileException:: OsErrorToException](#oserrortoexception)|운영 체제 오류 코드에 해당 하는 원인 코드를 반환 합니다.|
|[CFileException:: ThrowErrno](#throwerrno)|런타임 오류 번호를 기반으로 파일 예외를 throw 합니다.|
|[CFileException:: ThrowOsError](#throwoserror)|운영 체제 오류 번호를 기반으로 파일 예외를 throw 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CFileException:: m_cause](#m_cause)|예외 원인에 해당 하는 이식 가능한 코드를 포함 합니다.|
|[CFileException:: m_lOsError](#m_loserror)|관련 된 운영 체제 오류 번호를 포함 합니다.|
|[CFileException:: m_strFileName](#m_strfilename)|이 예외에 대 한 파일 이름을 포함 합니다.|

## <a name="remarks"></a>설명

클래스에는 `CFileException` 이식 가능한 원인 코드 및 운영 체제별 오류 번호를 포함 하는 공용 데이터 멤버가 포함 되어 있습니다. 또한 클래스는 파일 예외를 throw 하 고 운영 체제 오류 및 C 런타임 오류에 대 한 원인 코드를 반환 하는 정적 멤버 함수를 제공 합니다.

`CFileException` 개체는 `CFile` 멤버 함수 및 파생 클래스의 멤버 함수에서 생성 및 throw 됩니다. 이러한 개체는 **CATCH** 식의 범위 내에서 액세스할 수 있습니다. 이식성을 위해 원인 코드만 사용 하 여 예외에 대 한 이유를 가져옵니다. 예외에 대 한 자세한 내용은 [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a> CFileException:: CFileException

`CFileException`개체의 원인 코드와 운영 체제 코드를 저장 하는 개체를 생성 합니다.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>매개 변수

*cause*<br/>
예외에 대 한 이유를 나타내는 열거형 형식 변수입니다. 가능한 값 목록은 [Cfileexception:: m_cause](#m_cause) 를 참조 하세요.

*lOsError*<br/>
사용 가능한 경우 예외에 대 한 운영 체제 관련 이유입니다. *LOsError* 매개 변수 *는 보다 자세한* 정보를 제공 합니다.

*lpszArchiveName*<br/>
예외를 발생 시킨 개체의 이름을 포함 하는 문자열을 가리킵니다 `CFile` .

### <a name="remarks"></a>설명

이 생성자는 직접 사용 하지 말고 [AfxThrowFileException](exception-processing.md#afxthrowfileexception)전역 함수를 호출 합니다.

> [!NOTE]
> *LOsError* 변수는 및 개체에만 적용 됩니다 `CFile` `CStdioFile` . `CMemFile`클래스는이 오류 코드를 처리 하지 않습니다.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a> CFileException:: ErrnoToException

지정 된 런타임 라이브러리 오류 값을 `CFileException` 열거 된 오류 값으로 변환 합니다.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>매개 변수

*nErrno*<br/>
런타임 include 파일 ERRNO에 정의 된 정수 오류 코드입니다.

### <a name="return-value"></a>반환 값

지정 된 런타임 라이브러리 오류 값에 해당 하는 열거형 값입니다.

### <a name="remarks"></a>설명

가능한 열거형 값 목록은 [Cfileexception:: m_cause](#m_cause) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a> CFileException:: GetErrorMessage

예외를 설명 하는 텍스트를 검색 합니다.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>매개 변수

*lpszError*<br/>
[in, out] 오류 메시지를 수신 하는 버퍼에 대 한 포인터입니다.

*nMaxError*<br/>
진행 지정 된 버퍼에 포함할 수 있는 최대 문자 수입니다. 여기에는 null 종결 문자가 포함 됩니다.

*pnHelpContext*<br/>
[in, out] 도움말 컨텍스트 ID를 받는 부호 없는 정수에 대 한 포인터입니다. 인 경우 `NULL` ID가 반환 되지 않습니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

지정 된 버퍼가 너무 작으면 오류 메시지가 잘립니다.

### <a name="example"></a>예제

다음 예에서는 `CFileException::GetErrorMessage`를 사용합니다.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a> CFileException:: m_cause

`CFileException` 열거형 형식으로 정의되는 값을 포함합니다.

```
int m_cause;
```

### <a name="remarks"></a>설명

이 데이터 멤버는 형식의 공용 변수입니다 **`int`** . 아래에 열거자와 해당 의미가 나와 있습니다.

| 오류 | 값 및 의미 |
|--|--|
| `CFileException::none` |    0: 오류가 발생하지 않았습니다. |
| `CFileException::genericException` |    1: 지정되지 않은 오류가 발생했습니다. |
| `CFileException::fileNotFound` |    2: 파일을 찾을 수 없습니다. |
| `CFileException::badPath` |    3: 경로의 전체 또는 일부가 잘못되었습니다. |
| `CFileException::tooManyOpenFiles` |    4: 열도록 허용되는 파일 수가 초과되었습니다. |
| `CFileException::accessDenied` |    5: 파일에 액세스할 수 없습니다. |
| `CFileException::invalidFile` |    6: 잘못된 파일 핸들을 사용하려고 했습니다. |
| `CFileException::removeCurrentDir` |    7: 현재 작업 디렉터리를 제거할 수 없습니다. |
| `CFileException::directoryFull` |    8: 디렉터리 항목이 더 이상 없습니다. |
| `CFileException::badSeek` |    9: 파일 포인터를 설정하는 동안 오류가 발생했습니다. |
| `CFileException::hardIO` |    10: 하드웨어 오류가 발생했습니다. |
| `CFileException::sharingViolation` |    11: SHARE.EXE가 로드되지 않았거나 공유 영역이 잠겼습니다. |
| `CFileException::lockViolation` |    12: 이미 잠긴 영역을 잠그려고 했습니다. |
| `CFileException::diskFull` | 13: 디스크가 꽉 찼습니다. |
| `CFileException::endOfFile` | 14: 파일의 끝에 도달 했습니다. |

> [!NOTE]
> 이러한 `CFileException` 원인 열거자는 `CArchiveException` 원인 열거자와는 다릅니다.

> [!NOTE]
> `CArchiveException::generic`는 사용되지 않습니다. 대신 `genericException`를 사용하세요. 응용 프로그램에서 **제네릭을** 사용 하 고/clr을 사용 하 여 빌드한 경우에는 결과 구문 오류를 쉽게 해독할 수 없습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a> CFileException:: m_lOsError

이 예외에 대 한 운영 체제 오류 코드를 포함 합니다.

```
LONG m_lOsError;
```

### <a name="remarks"></a>설명

오류 코드 목록은 운영 체제 기술 설명서를 참조 하세요. 이 데이터 멤버는 LONG 형식의 공용 변수입니다.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a> CFileException:: m_strFileName

이 예외 조건에 대 한 파일 이름을 포함 합니다.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a> CFileException:: OsErrorToException

지정 된 *lOsError* 값에 해당 하는 열거자를 반환 합니다. 오류 코드를 알 수 없는 경우 함수는를 반환 `CFileException::generic` 합니다.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>매개 변수

*lOsError*<br/>
운영 체제 관련 오류 코드입니다.

### <a name="return-value"></a>반환 값

지정 된 운영 체제 오류 값에 해당 하는 열거 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a> CFileException:: ThrowErrno

지정 된 `CFileException` *nErrno* 값에 해당 하는 개체를 생성 한 다음 예외를 throw 합니다.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>매개 변수

*nErrno*<br/>
런타임 include 파일 ERRNO에 정의 된 정수 오류 코드입니다.

*lpszFileName*<br/>
예외를 발생 시킨 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다 (사용 가능한 경우).

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a> CFileException:: ThrowOsError

지정 된 `CFileException` *lOsError* 값에 해당 하는을 throw 합니다. 오류 코드를 알 수 없는 경우 함수는로 코딩 된 예외를 throw `CFileException::generic` 합니다.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>매개 변수

*lOsError*<br/>
운영 체제 관련 오류 코드입니다.

*lpszFileName*<br/>
예외를 발생 시킨 파일의 이름을 포함 하는 문자열에 대 한 포인터입니다 (사용 가능한 경우).

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>참고 항목

[CException 클래스](../../mfc/reference/cexception-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[예외 처리](../../mfc/reference/exception-processing.md)
