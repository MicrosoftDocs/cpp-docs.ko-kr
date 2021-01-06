---
description: '자세한 정보: CException 클래스'
title: CException 클래스
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: 5aa5377315d526102f6358f36cb9ed6a60a133be
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951543"
---
# <a name="cexception-class"></a>CException 클래스

MFC 라이브러리의 모든 예외에 대한 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CException:: CException](#cexception)|`CException` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CException::D e)](#delete)|개체를 삭제 `CException` 합니다.|
|[CException:: ReportError](#reporterror)|메시지 상자에 사용자에 게 오류 메시지를 보고 합니다.|

## <a name="remarks"></a>설명

`CException`는 추상 기본 클래스 이므로 직접 개체를 만들 수 없습니다. `CException` 파생 클래스의 개체를 만들어야 합니다. 사용자 고유의 스타일 클래스를 만들어야 하는 경우 `CException` 위에 나열 된 파생 클래스 중 하나를 모델로 사용 합니다. 파생 클래스가을 사용 하는지 확인 `IMPLEMENT_DYNAMIC` 합니다.

파생 클래스와 해당 설명이 아래에 나열 되어 있습니다.

|Name|설명|
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|리소스에 중요 한 MFC 예외의 기본 클래스입니다.|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|잘못 된 인수 예외 조건|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|메모리 부족 예외|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|지원 되지 않는 작업 요청|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|보관 특정 예외|
|[CFileException](../../mfc/reference/cfileexception-class.md)|파일 관련 예외|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows 리소스를 찾을 수 없거나 만들 수 없습니다.|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 예외|
|[CDBException](../../mfc/reference/cdbexception-class.md)|데이터베이스 예외 (즉, 오픈 데이터베이스 연결을 기반으로 하는 MFC 데이터베이스 클래스에 발생 하는 예외 조건)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE 디스패치 (자동화) 예외|
|[CUserException](../../mfc/reference/cuserexception-class.md)|리소스를 찾을 수 없음을 나타내는 예외입니다.|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|데이터 액세스 개체 예외 (즉, DAO 클래스에 발생 하는 예외 조건)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|인터넷 예외 (즉, 인터넷 클래스에 발생 하는 예외 조건).|

이러한 예외는 [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch)및 [end_catch](exception-processing.md#end_catch) 매크로와 함께 사용 하기 위한 것입니다. 예외에 대 한 자세한 내용은 예외 [처리](exception-processing.md)를 참조 하거나 [예외 처리 (MFC)](../exception-handling-in-mfc.md)문서를 참조 하세요.

특정 예외를 catch 하려면 적절 한 파생 클래스를 사용 합니다. 모든 형식의 예외를 catch 하려면를 사용 하 `CException` 고 [CObject:: IsKindOf](cobject-class.md#iskindof) 를 사용 하 여 `CException` 파생 클래스를 구분 합니다. 는 `CObject::IsKindOf` 동적 형식 검사를 활용 하기 위해 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) 매크로를 사용 하 여 선언 된 클래스에 대해서만 작동 합니다. `CException`사용자가 만드는 모든 파생 클래스는 매크로를 사용 해야 합니다 `IMPLEMENT_DYNAMIC` .

의 파생 클래스를 사용 하는 두 개의 멤버 함수 인 [Geterrormessage](cfileexception-class.md#geterrormessage) 또는 [ReportError](#reporterror)를 호출 하 여 사용자에 대 한 예외 정보를 보고할 수 있습니다 `CException` .

매크로 중 하나에서 예외를 catch 하는 경우 개체는 `CException` 자동으로 삭제 됩니다. 직접 삭제 하지 마십시오. 키워드를 사용 하 여 예외를 catch 하는 경우 **`catch`** 자동으로 삭제 되지 않습니다. 예외가 개체를 삭제 하는 경우에 대 한 자세한 내용은 [예외 처리 (MFC)](../exception-handling-in-mfc.md) 문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cexceptioncexception"></a><a name="cexception"></a> CException:: CException

이 멤버 함수는 개체를 생성 `CException` 합니다.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>매개 변수

*b_AutoDelete*<br/>
개체에 대 한 메모리가 힙에 할당 된 경우 TRUE를 지정 `CException` 합니다. 이렇게 하면 `CException` `Delete` 멤버 함수를 호출 하 여 예외를 삭제할 때 개체가 삭제 됩니다. `CException`개체가 스택에 있거나 전역 개체 이면 FALSE를 지정 합니다. 이 경우 `CException` 멤버 함수가 호출 되 면 개체가 삭제 되지 않습니다 `Delete` .

### <a name="remarks"></a>설명

일반적으로이 생성자는 직접 호출할 필요가 없습니다. 예외를 throw 하는 함수는 파생 클래스의 인스턴스를 만들고 `CException` 해당 생성자를 호출 하거나, [AfxThrowFileException](exception-processing.md#afxthrowfileexception)와 같은 MFC throw 함수 중 하나를 사용 하 여 미리 정의 된 형식을 throw 해야 합니다. 이 설명서는 완전성을 위해서만 제공 됩니다.

## <a name="cexceptiondelete"></a><a name="delete"></a> CException::D e)

이 함수는 힙에서 개체가 생성 되었는지 여부를 확인 하 고,이 `CException` 경우 **`delete`** 개체에 대해 연산자를 호출 합니다.

```cpp
void Delete();
```

### <a name="remarks"></a>설명

개체를 삭제 `CException` 하는 경우 `Delete` 멤버 함수를 사용 하 여 예외를 삭제 합니다. **`delete`** `CException` 개체가 전역 개체 이거나 스택에 만들어졌을 수 있으므로 연산자를 직접 사용 하지 마십시오.

개체가 생성 될 때 개체를 삭제할지 여부를 지정할 수 있습니다. 자세한 내용은 [cexception:: cexception](#cexception)을 참조 하세요.

`Delete`C + + 메커니즘을 사용 하는 경우에만를 호출 해야 **`try`** -  **`catch`** 합니다. MFC 매크로 **TRY** 및 **CATCH** 를 사용 하는 경우 이러한 매크로는이 함수를 자동으로 호출 합니다.

### <a name="example"></a>예제

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

## <a name="cexceptionreporterror"></a><a name="reporterror"></a> CException:: ReportError

메시지 상자의 오류 텍스트를 사용자에 게 보고 하려면이 멤버 함수를 호출 합니다.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>매개 변수

*nType*<br/>
메시지 상자의 스타일을 지정 합니다. [메시지 상자 스타일](styles-used-by-mfc.md#message-box-styles) 조합을 상자에 적용 합니다. 이 매개 변수를 지정 하지 않으면 기본값은 MB_OK입니다.

*nMessageID*<br/>
예외 개체에 오류 메시지가 없는 경우 표시할 메시지의 리소스 ID (문자열 테이블 항목)를 지정 합니다. 0 인 경우 "오류 메시지를 사용할 수 없습니다." 라는 메시지가 표시 됩니다.

### <a name="return-value"></a>반환 값

`AfxMessageBox`값입니다. 그렇지 않으면 메시지 상자를 표시 하는 데 충분 한 메모리가 없는 경우 0입니다. 가능한 반환 값은 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) 를 참조 하세요.

### <a name="example"></a>예제

다음은를 사용 하는 예입니다 `CException::ReportError` . 또 다른 예제는 [CATCH](exception-processing.md#catch)의 예제를 참조 하세요.

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>참조

[CObject 클래스](cobject-class.md)<br/>
[계층 구조 차트](../hierarchy-chart.md)<br/>
[예외 처리](exception-processing.md)
