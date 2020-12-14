---
description: '자세한 정보: 예외 처리'
title: 예외 처리
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: add942991a4792cb88e82dee0bfd033612b68eb2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219826"
---
# <a name="exception-processing"></a>예외 처리

프로그램이 실행 되 면 "예외" 라는 여러 비정상 조건 및 오류가 발생할 수 있습니다. 여기에는 메모리 부족, 리소스 할당 오류, 파일 찾기 실패 등이 포함 될 수 있습니다.

MFC 라이브러리는 c + + 용 ANSI 표준 위원회에서 제안 된 것 보다 긴밀 하 게 모델링 된 예외 처리 체계를 사용 합니다. 비정상적인 상황이 발생할 수 있는 함수를 호출 하기 전에 예외 처리기를 설정 해야 합니다. 함수가 비정상 상태를 발견 한 경우 예외를 throw 하 고 제어가 예외 처리기에 전달 됩니다.

MFC 라이브러리 포함 된 여러 매크로는 예외 처리기를 설정 합니다. 필요한 경우 다양 한 전역 함수를 통해 특수 한 예외를 throw 하 고 프로그램을 종료할 수 있습니다. 이러한 매크로 및 전역 함수는 다음과 같은 범주로 분류 됩니다.

- 예외 처리기를 구성 하는 예외 매크로

- 예외 throw 함수)는 특정 형식의 예외를 생성 합니다.

- 종료 함수-프로그램 종료를 발생 시킵니다.

예제 및 자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="exception-macros"></a>예외 매크로

|Name|설명|
|-|-|
|[하려고](#try)|예외 처리에 대 한 코드 블록을 지정 합니다.|
|[TRY-CATCH](#catch)|이전 **TRY** 블록에서 예외를 catch 하는 코드 블록을 지정 합니다.|
|[CATCH_ALL](#catch_all)|이전 **TRY** 블록에서 모든 예외를 catch 하는 코드 블록을 지정 합니다.|
|[AND_CATCH](#and_catch)|이전 **TRY** 블록에서 추가 예외 형식을 catch 하는 코드 블록을 지정 합니다.|
|[AND_CATCH_ALL](#and_catch_all)|이전 **TRY** 블록에서 throw 된 다른 모든 추가 예외 형식을 catch 하는 코드 블록을 지정 합니다.|
|[END_CATCH](#end_catch)|마지막 **CATCH** 또는 **AND_CATCH** 코드 블록을 종료 합니다.|
|[END_CATCH_ALL](#end_catch_all)|마지막 **CATCH_ALL** 코드 블록을 종료 합니다.|
|[THROW](#throw)|지정 된 예외를 throw 합니다.|
|[THROW_LAST](#throw_last)|현재 처리 된 예외를 다음 외부 처리기에 throw 합니다.|

### <a name="exception-throwing-functions"></a>Exception-Throwing 함수

|Name|설명|
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|보관 예외를 throw 합니다.|
|[AfxThrowFileException](#afxthrowfileexception)|파일 예외를 throw 합니다.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|잘못 된 인수 예외를 throw 합니다.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|메모리 예외를 throw 합니다.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|지원 되지 않는 예외를 throw 합니다.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Windows 리소스를 찾을 수 없는 예외를 throw 합니다.|
|[AfxThrowUserException](#afxthrowuserexception)|사용자가 시작한 프로그램 작업에서 예외를 throw 합니다.|

MFC는 OLE 예외에 대해 다음과 같은 두 가지 예외 throw 함수를 제공 합니다.

### <a name="ole-exception-functions"></a>OLE 예외 함수

|Name|설명|
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|OLE 자동화 함수 내에서 예외를 throw 합니다.|
|[AfxThrowOleException](#afxthrowoleexception)|OLE 예외를 throw 합니다.|

데이터베이스 예외를 지원 하기 위해 데이터베이스 클래스는 두 가지 예외 클래스인 `CDBException` 및 및 `CDaoException` 전역 함수를 제공 하 여 예외 형식을 지원 합니다.

### <a name="dao-exception-functions"></a>DAO 예외 함수

|Name|설명|
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|사용자 고유의 코드에서 [CDaoException](../../mfc/reference/cdaoexception-class.md) 를 throw 합니다.|
|[AfxThrowDBException](#afxthrowdbexception)|사용자의 코드에서 [Cdbexception](../../mfc/reference/cdbexception-class.md) 을 throw 합니다.|

MFC는 다음과 같은 종료 함수를 제공 합니다.

### <a name="termination-functions"></a>종료 함수

|Name|설명|
|-|-|
|[AfxAbort](#afxabort)|심각한 오류가 발생 하면 응용 프로그램을 종료 하기 위해 호출 됩니다.|

## <a name="try"></a><a name="try"></a> 하려고

**TRY** 블록을 설정 합니다.

```
TRY
```

### <a name="remarks"></a>설명

**TRY** 블록은 예외를 throw 할 수 있는 코드 블록을 식별 합니다. 이러한 예외는 다음과 같은 **CATCH** 블록과 **AND_CATCH** 블록에서 처리 됩니다. 재귀가 허용 됨: 예외를 무시 하거나 THROW_LAST 매크로를 사용 하 여 외부 **TRY** 블록에 예외를 전달할 수 있습니다. END_CATCH 또는 END_CATCH_ALL 매크로를 사용 하 여 **TRY** 블록을 종료 합니다.

자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[CATCH](#catch)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

헤더: afx.h

## <a name="catch"></a><a name="catch"></a> TRY-CATCH

이전 **TRY** 블록에서 throw 된 첫 번째 예외 형식을 catch 하는 코드 블록을 정의 합니다.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>매개 변수

*exception_class*<br/>
테스트할 예외 형식을 지정 합니다. 표준 예외 클래스 목록은 [Cexception](../../mfc/reference/cexception-class.md)클래스를 참조 하세요.

*exception_object_pointer_name*<br/>
매크로에 의해 생성되는 예외-개체 포인터에 대한 이름을 지정합니다. 포인터 이름을 사용 하 여 **CATCH** 블록 내에서 예외 개체에 액세스할 수 있습니다. 이 변수는 자동으로 선언됩니다.

### <a name="remarks"></a>설명

예외 처리 코드는 필요한 경우 예외 개체를 확인하여 예외의 특정 원인에 대한 추가 정보를 가져올 수 있습니다. THROW_LAST 매크로를 호출 하 여 처리를 다음 외부 예외 프레임으로 이동 합니다. END_CATCH 매크로를 사용 하 여 **TRY** 블록을 종료 합니다.

*Exception_class* 클래스 이면 `CException` 모든 예외 형식이 catch 됩니다. [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) 멤버 함수를 사용 하 여 throw 된 특정 예외를 확인할 수 있습니다. 여러 종류의 예외를 catch 하는 더 좋은 방법은 각각 다른 예외 형식을 사용 하 여 순차적 **AND_CATCH** 문을 사용 하는 것입니다.

예외 개체 포인터는 매크로에 의해 생성 됩니다. 사용자가 직접 선언 하지 않아도 됩니다.

> [!NOTE]
> **CATCH** 블록은 중괄호로 구분 되는 c + + 범위로 정의 됩니다. 이 범위에서 변수를 선언하면 해당 범위 내에서만 액세스할 수 있습니다. 이는 *exception_object_pointer_name* 에도 적용 됩니다.

예외 및 CATCH 매크로에 대 한 자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a> CATCH_ALL

이전 **TRY** 블록에서 throw 된 모든 예외 형식을 catch 하는 코드 블록을 정의 합니다.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>매개 변수

*exception_object_pointer_name*<br/>
매크로에 의해 생성되는 예외-개체 포인터에 대한 이름을 지정합니다. 포인터 이름을 사용해서 `CATCH_ALL` 블록 내에서 예외 개체에 액세스할 수 있습니다. 이 변수는 자동으로 선언됩니다.

### <a name="remarks"></a>설명

예외 처리 코드는 필요한 경우 예외 개체를 확인하여 예외의 특정 원인에 대한 추가 정보를 가져올 수 있습니다. `THROW_LAST` 매크로를 호출하여 다음 외부 예외 프레임으로 처리를 이동합니다. **CATCH_ALL** 사용 하는 경우 END_CATCH_ALL 매크로를 사용 하 여 **TRY** 블록을 종료 합니다.

> [!NOTE]
> **CATCH_ALL** 블록은 중괄호로 구분 된 c + + 범위로 정의 됩니다. 이 범위에서 변수를 선언하면 해당 범위 내에서만 액세스할 수 있습니다.

예외에 대 한 자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[CFile:: Abort](../../mfc/reference/cfile-class.md#abort)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="and_catch"></a><a name="and_catch"></a> AND_CATCH

이전 **TRY** 블록에서 throw 된 추가 예외 형식을 catch 하는 코드 블록을 정의 합니다.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>매개 변수

*exception_class*<br/>
테스트할 예외 형식을 지정 합니다. 표준 예외 클래스 목록은 [Cexception](../../mfc/reference/cexception-class.md)클래스를 참조 하세요.

*exception_object_pointer_name*<br/>
매크로에 의해 생성 되는 예외 개체 포인터의 이름입니다. 포인터 이름을 사용 하 여 **AND_CATCH** 블록 내에서 예외 개체에 액세스할 수 있습니다. 이 변수는 자동으로 선언됩니다.

### <a name="remarks"></a>설명

CATCH 매크로를 사용 하 여 한 가지 예외 형식을 catch 한 다음 AND_CATCH 매크로를 사용 하 여 각 후속 형식을 catch 합니다. END_CATCH 매크로를 사용 하 여 **TRY** 블록을 종료 합니다.

예외 처리 코드는 필요한 경우 예외 개체를 확인하여 예외의 특정 원인에 대한 추가 정보를 가져올 수 있습니다. **AND_CATCH** 블록 내의 THROW_LAST 매크로를 호출 하 여 처리를 다음 외부 예외 프레임으로 이동 합니다. **AND_CATCH** 는 위의 **CATCH** 또는 **AND_CATCH** 블록의 끝을 표시 합니다.

> [!NOTE]
> **AND_CATCH** 블록은 c + + 범위 (중괄호로 구분)로 정의 됩니다. 이 범위에서 변수를 선언 하는 경우 해당 범위 내 에서만 액세스할 수 있다는 점에 주의 해야 합니다. 이는 *exception_object_pointer_name* 변수에도 적용 됩니다.

### <a name="example"></a>예제

[CATCH](#catch)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="and_catch_all"></a><a name="and_catch_all"></a> AND_CATCH_ALL

이전 **TRY** 블록에서 throw 된 추가 예외 형식을 catch 하는 코드 블록을 정의 합니다.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>매개 변수

*exception_object_pointer_name*<br/>
매크로에 의해 생성 되는 예외 개체 포인터의 이름입니다. 포인터 이름을 사용 하 여 **AND_CATCH_ALL** 블록 내에서 예외 개체에 액세스할 수 있습니다. 이 변수는 자동으로 선언됩니다.

### <a name="remarks"></a>설명

**Catch** 매크로를 사용 하 여 한 가지 예외 형식을 catch 한 다음 AND_CATCH_ALL 매크로를 사용 하 여 다른 모든 후속 형식을 catch 합니다. AND_CATCH_ALL 사용 하는 경우 END_CATCH_ALL 매크로를 사용 하 여 **TRY** 블록을 종료 합니다.

예외 처리 코드는 필요한 경우 예외 개체를 확인하여 예외의 특정 원인에 대한 추가 정보를 가져올 수 있습니다. **AND_CATCH_ALL** 블록 내의 THROW_LAST 매크로를 호출 하 여 처리를 다음 외부 예외 프레임으로 이동 합니다. **AND_CATCH_ALL** 는 위의 **CATCH** 또는 **AND_CATCH_ALL** 블록의 끝을 표시 합니다.

> [!NOTE]
> **AND_CATCH_ALL** 블록은 c + + 범위 (중괄호로 구분)로 정의 됩니다. 이 범위에서 변수를 선언 하는 경우 해당 범위 내 에서만 액세스할 수 있다는 점에 주의 해야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="end_catch"></a><a name="end_catch"></a> END_CATCH

마지막 **CATCH** 또는 **AND_CATCH** 블록의 끝을 표시 합니다.

```
END_CATCH
```

### <a name="remarks"></a>설명

END_CATCH 매크로에 대 한 자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="end_catch_all"></a><a name="end_catch_all"></a> END_CATCH_ALL

마지막 **CATCH_ALL88** 또는 **AND_CATCH_ALL** 블록의 끝을 표시 합니다.

```
END_CATCH_ALL
```

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="throw-mfc"></a><a name="throw"></a> THROW (MFC)

지정 된 예외를 throw 합니다.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>매개 변수

*exception_object_pointer*<br/>
에서 파생 된 예외 개체를 가리킵니다 `CException` .

### <a name="remarks"></a>설명

프로그램 실행 **을 중단 하** 고 프로그램에서 연결 된 **CATCH** 블록에 컨트롤을 전달 합니다. **CATCH** 블록을 제공 하지 않은 경우 컨트롤은 오류 메시지를 인쇄 하 고 종료 하는 MFC 라이브러리 모듈에 전달 됩니다.

자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="throw_last"></a><a name="throw_last"></a> THROW_LAST

예외를 다음 외부 **CATCH** 블록으로 다시 throw 합니다.

```
THROW_LAST()
```

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 로컬로 만든 예외를 throw 할 수 있습니다. 방금 catch 한 예외를 throw 하려고 하면 일반적으로 범위를 벗어난 후 삭제 됩니다. **THROW_LAST** 를 사용 하면 예외가 다음 **CATCH** 처리기에 올바르게 전달 됩니다.

자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

### <a name="example"></a>예제

[CFile:: Abort](../../mfc/reference/cfile-class.md#abort)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a> AfxThrowArchiveException

보관 예외를 throw 합니다.

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>매개 변수

*cause*<br/>
예외에 대 한 이유를 나타내는 정수를 지정 합니다. 가능한 값 목록은 [CArchiveException:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)를 참조 하세요.

*lpszArchiveName*<br/>
`CArchive`예외를 발생 시킨 개체 (사용 가능한 경우)의 이름을 포함 하는 문자열을 가리킵니다.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a> AfxThrowFileException

파일 예외를 throw 합니다.

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>매개 변수

*cause*<br/>
예외에 대 한 이유를 나타내는 정수를 지정 합니다. 가능한 값 목록은 [Cfileexception:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause)를 참조 하세요.

*lOsError*<br/>
예외에 대 한 이유를 나타내는 운영 체제 오류 번호 (사용 가능한 경우)를 포함 합니다. 오류 코드 목록은 운영 체제 설명서를 참조 하십시오.

*lpszFileName*<br/>
예외를 발생 시킨 파일의 이름 (사용 가능한 경우)을 포함 하는 문자열을 가리킵니다.

### <a name="remarks"></a>설명

운영 체제 오류 코드를 기반으로 원인을 결정 해야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a> AfxThrowInvalidArgException

잘못 된 인수 예외를 throw 합니다.

### <a name="syntax"></a>구문

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>설명

이 함수는 잘못 된 인수를 사용 하는 경우 호출 됩니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a> AfxThrowMemoryException

메모리 예외를 throw 합니다.

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>설명

기본 시스템 메모리 할당자 (예: **malloc** 및 [globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 함수)에 대 한 호출이 실패 하는 경우이 함수를 호출 합니다. **`new`** **`new`** 메모리 할당이 실패 하는 경우에서 자동으로 메모리 예외를 throw 하기 때문에에 대해이 메서드를 호출할 필요가 없습니다.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a> AfxThrowNotSupportedException

지원 되지 않는 기능 요청 결과인 예외를 throw 합니다.

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a> AfxThrowResourceException

리소스 예외를 throw 합니다.

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>설명

이 함수는 일반적으로 Windows 리소스를 로드할 수 없을 때 호출 됩니다.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a> AfxThrowUserException

최종 사용자 작업을 중지 하는 예외를 throw 합니다.

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>설명

이 함수는 일반적으로 `AfxMessageBox` 사용자에 게 오류를 보고 한 직후 호출 됩니다.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a> AfxThrowOleDispatchException

이 함수를 사용 하 여 OLE 자동화 함수 내에서 예외를 throw 합니다.

```cpp
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>매개 변수

*wCode*<br/>
응용 프로그램 관련 오류 코드입니다.

*lpszDescription*<br/>
오류에 대 한 구두 설명입니다.

*nDescriptionID*<br/>
구두 오류 설명에 대 한 리소스 ID입니다.

*nHelpID*<br/>
응용 프로그램 도움말에 대 한 도움말 컨텍스트입니다 (. .HLP) 파일입니다.

### <a name="remarks"></a>설명

이 함수에 제공 되는 정보는 구동 응용 프로그램 (Microsoft Visual Basic 또는 다른 OLE 자동화 클라이언트 응용 프로그램)에서 표시할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a> AfxThrowOleException

형식의 개체를 만들고 `COleException` 예외를 throw 합니다.

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>매개 변수

*번체*<br/>
예외에 대 한 이유를 나타내는 OLE 상태 코드입니다.

*시간*<br/>
예외에 대 한 이유를 나타내는 결과 코드에 대 한 핸들입니다.

### <a name="remarks"></a>설명

HRESULT를 인수로 사용 하는 버전은 해당 결과 코드를 해당 하는로 변환 합니다. HRESULT 및에 대 한 자세한 내용은 Windows SDK의 [COM 오류 코드 구조](/windows/win32/com/structure-of-com-error-codes) 를 참조 하십시오.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a> AfxThrowDaoException

사용자 코드에서 [CDaoException](../../mfc/reference/cdaoexception-class.md) 형식의 예외를 throw 하려면이 함수를 호출 합니다.

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>매개 변수

*nAfxDaoError*<br/>
[CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)아래에 나열 된 값 중 하나일 수 있는 DAO 확장 오류 코드를 나타내는 정수 값입니다.

*scode*<br/>
형식에 대 한 DAO의 OLE 오류 코드입니다. 자세한 내용은 [CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)를 참조 하세요.

### <a name="remarks"></a>설명

프레임 워크는도 호출 `AfxThrowDaoException` 합니다. 호출에서 매개 변수 중 하나 또는 둘 다를 전달할 수 있습니다. 예를 들어 **CDaoException:: nAfxDaoError** 에 정의 된 오류 중 하나를 발생 시 키 지 않고, *매개 변수를 고려* 하지 않으려면 *nAfxDaoError* 매개 변수에 유효한 코드를 전달 하 고,이 기본값을 적용 합니다 *.*

MFC DAO 클래스와 관련 된 예외에 대 한 자세한 내용은 `CDaoException` 이 설명서의 클래스 및 [예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)문서를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdb

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a> AfxThrowDBException

사용자 고유의 코드에서 형식의 예외를 throw 하려면이 함수를 호출 `CDBException` 합니다.

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>매개 변수

*nRetCode*<br/>
예외를 throw 한 오류의 유형을 정의 하는 RETCODE 형식의 값입니다.

*.pdb*<br/>
`CDatabase`예외와 관련 된 데이터 소스 연결을 나타내는 개체에 대 한 포인터입니다.

*hstmt*<br/>
예외와 관련 된 문 핸들을 지정 하는 ODBC HSTMT 핸들입니다.

### <a name="remarks"></a>설명

이 프레임 워크는 `AfxThrowDBException` ODBC API 함수 호출에서 ODBC RETCODE을 수신 하 고 expectable 오류가 아닌 예외 조건으로 RETCODE을 해석 하는 경우를 호출 합니다. 예를 들어 디스크 읽기 오류로 인해 데이터 액세스 작업이 실패할 수 있습니다.

ODBC에 정의 된 RETCODE 값에 대 한 자세한 내용은 Windows SDK의 8 장, "상태 및 오류 정보 검색"을 참조 하십시오. 이러한 코드에 대 한 MFC 확장에 대 한 자세한 내용은 [Cdbexception](../../mfc/reference/cdbexception-class.md)클래스를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="afxabort"></a><a name="afxabort"></a> AfxAbort

MFC에서 제공 하는 기본 종료 함수입니다.

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>설명

`AfxAbort` 는 처리할 수 없는 catch 되지 않은 예외와 같이 오류가 발생할 때 MFC 멤버 함수에서 내부적으로 호출 됩니다. `AfxAbort`드물지만 복구할 수 없는 치명적인 오류가 발생 하는 경우에는를 호출할 수 있습니다.

### <a name="example"></a>예제

[CATCH](#catch)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afx

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[CException 클래스](cexception-class.md)<br/>
[CInvalidArgException 클래스](cinvalidargexception-class.md)
