---
description: '자세히 알아보기: CDaoException 클래스'
title: CDaoException 클래스
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: eb7da6746d2ce539a2ee7b0b28a9a4e9c6c6de64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250896"
---
# <a name="cdaoexception-class"></a>CDaoException 클래스

DAO(Data Access Objects)를 기반으로 하는 MFC 데이터베이스 클래스에서 발생하는 예외 상태를 나타냅니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
class CDaoException : public CException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|`CDaoException` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|데이터베이스 엔진의 Errors 컬렉션에서 발생 한 오류 수를 반환 합니다.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Errors 컬렉션의 특정 오류 개체에 대 한 오류 정보를 반환 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|MFC DAO 클래스의 오류에 대 한 확장 오류 코드를 포함 합니다.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|한 DAO 오류 개체에 대 한 정보를 포함 하는 [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) 개체에 대 한 포인터입니다.|
|[CDaoException:: m_scode](#m_scode)|오류와 연결 [된 값입니다](#m_scode) .|

## <a name="remarks"></a>설명

클래스에는 예외의 원인을 확인 하는 데 사용할 수 있는 공용 데이터 멤버가 포함 되어 있습니다. `CDaoException` 개체는 DAO 데이터베이스 클래스의 멤버 함수에 의해 생성 및 throw 됩니다.

> [!NOTE]
> DAO 데이터베이스 클래스는 ODBC (Open Database Connectivity)를 기반으로 하는 MFC 데이터베이스 클래스와는 다릅니다. 모든 DAO 데이터베이스 클래스 이름에는 "CDao" 접두사가 있습니다. 여전히 DAO 클래스를 사용 하 여 ODBC 데이터 원본에 액세스할 수 있습니다. 일반적으로 DAO 기반의 MFC 클래스는 ODBC를 기반으로 하는 MFC 클래스 보다 더 사용할 수 있습니다. DAO 기반 클래스는 자체 데이터베이스 엔진을 통해 ODBC 드라이버를 포함 하 여 데이터에 액세스할 수 있습니다. 또한 dao 기반 클래스는 DAO를 직접 호출 하지 않고도 클래스를 통해 테이블을 추가 하는 등의 DDL (데이터 정의 언어) 작업을 지원 합니다. ODBC 클래스에서 throw 되는 예외에 대 한 자세한 내용은 [Cdbexception](../../mfc/reference/cdbexception-class.md)을 참조 하십시오.

[CATCH](../../mfc/reference/exception-processing.md#catch) 식의 범위 내에서 예외 개체에 액세스할 수 있습니다. [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) global 함수를 사용하여 사용자 고유의 코드에서 `CDaoException` 개체를 throw할 수도 있습니다.

MFC에서 모든 DAO 오류는 형식의 예외로 표시 됩니다 `CDaoException` . 이 형식의 예외를 catch 할 때 멤버 함수를 사용 하 여 `CDaoException` 데이터베이스 엔진의 Errors 컬렉션에 저장 된 DAO 오류 개체에서 정보를 검색할 수 있습니다. 오류가 발생할 때마다 하나 이상의 오류 개체가 Errors 컬렉션에 배치 됩니다. 일반적으로 컬렉션은 하나의 오류 개체만 포함 합니다. ODBC 데이터 원본을 사용 하는 경우에는 여러 오류 개체를 가져올 가능성이 높습니다. 다른 DAO 작업에서 오류가 생성 되 면 Errors 컬렉션이 지워지고 새 error 개체가 Errors 컬렉션에 배치 됩니다. 오류를 생성 하지 않는 DAO 작업은 Errors 컬렉션에 영향을 주지 않습니다.

DAO 오류 코드는 DAOERR 파일을 참조 하세요. 관련 정보는 DAO 도움말의 "잡을 수 있는 데이터 액세스 오류" 항목을 참조 하십시오.

일반적인 예외 처리 또는 개체 정보에 대 한 자세한 내용은 `CDaoException` [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md) 및 [예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)문서를 참조 하세요. 두 번째 문서에는 DAO의 예외 처리를 보여 주는 예제 코드가 포함 되어 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a> CDaoException::CDaoException

`CDaoException` 개체를 생성합니다.

```
CDaoException();
```

### <a name="remarks"></a>설명

일반적으로 프레임 워크는 예외를 throw 하는 예외 개체를 만듭니다. 예외 개체를 명시적으로 생성 해야 하는 경우는 거의 없습니다. 사용자의 코드에서를 throw 하려면 `CDaoException` 전역 함수 [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)를 호출 합니다.

그러나 MFC 클래스가 캡슐화 하는 DAO 인터페이스 포인터를 통해 DAO를 직접 호출 하는 경우에는 예외 개체를 명시적으로 만들 수 있습니다. 이 경우 DAO에서 오류 정보를 검색 해야 할 수 있습니다. DAODatabases 인터페이스를 통해 작업 영역 데이터베이스 컬렉션에 대 한 DAO 메서드를 호출 하는 경우 DAO에서 오류가 발생 한다고 가정 합니다.

##### <a name="to-retrieve-the-dao-error-information"></a>DAO 오류 정보를 검색 하려면

1. 개체를 생성 `CDaoException` 합니다.

1. Exception 개체의 [GetErrorCount](#geterrorcount) 멤버 함수를 호출 하 여 데이터베이스 엔진의 Errors 컬렉션에 있는 오류 개체 수를 확인 합니다. (ODBC 데이터 원본을 사용 하지 않는 한 일반적으로 하나만)

1. Exception 개체의 [Geterrorinfo](#geterrorinfo) 멤버 함수를 호출 하 여 예외 개체를 통해 컬렉션의 인덱스 별로 특정 오류 개체를 한 번에 하나씩 검색 합니다. 예외 개체를 하나의 DAO 오류 개체에 대 한 프록시로 생각 합니다.

1. [](../../mfc/reference/cdaoerrorinfo-structure.md) `GetErrorInfo` [M_pErrorInfo](#m_perrorinfo) 데이터 멤버에서 반환 하는 현재 CDaoErrorInfo 구조체를 검사 합니다. 해당 멤버는 DAO 오류에 대 한 정보를 제공 합니다.

1. ODBC 데이터 원본의 경우 필요에 따라 3 단계와 4 단계를 반복 하 여 더 많은 오류 개체를 추가 합니다.

1. 힙에 예외 개체를 구성한 경우에는를 완료할 때 연산자를 사용 하 여 삭제 **`delete`** 합니다.

MFC DAO 클래스의 오류를 처리 하는 방법에 대 한 자세한 내용은 [예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)문서를 참조 하세요.

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a> CDaoException::GetErrorCount

이 멤버 함수를 호출 하 여 데이터베이스 엔진의 Errors 컬렉션에서 DAO 오류 개체 수를 검색 합니다.

```
short GetErrorCount();
```

### <a name="return-value"></a>반환 값

데이터베이스 엔진의 Errors 컬렉션에 있는 DAO 오류 개체의 수입니다.

### <a name="remarks"></a>설명

이 정보는 컬렉션에서 하나 이상의 DAO 오류 개체를 검색 하기 위해 Errors 컬렉션을 반복 하는 데 유용 합니다. 인덱스 또는 DAO 오류 번호로 오류 개체를 검색 하려면 [Geterrorinfo](#geterrorinfo) 멤버 함수를 호출 합니다.

> [!NOTE]
> 일반적으로 Errors 컬렉션에는 하나의 오류 개체만 있습니다. 그러나 ODBC 데이터 원본으로 작업 하는 경우에는 두 개 이상 있을 수 있습니다.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a> CDaoException:: GetErrorInfo

Errors 컬렉션의 특정 오류 개체에 대 한 오류 정보를 반환 합니다.

```cpp
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 데이터베이스 엔진의 Errors 컬렉션에 있는 오류 정보의 인덱스입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 예외에 대 한 다음과 같은 종류의 정보를 가져옵니다.

- 오류 코드

- 원본

- 설명

- 도움말 파일

- 도움말 컨텍스트

`GetErrorInfo` 예외 개체의 데이터 멤버에 정보를 저장 합니다 `m_pErrorInfo` . 반환 되는 정보에 대 한 간략 한 설명은 [m_pErrorInfo](#m_perrorinfo)를 참조 하세요. MFC에서 throw 된 형식의 예외를 catch 하는 경우 `CDaoException` `m_pErrorInfo` 멤버가 이미 입력 됩니다. DAO를 직접 호출 하도록 선택 하는 경우 예외 개체의 멤버 함수를 직접 호출 하 여 `GetErrorInfo` 채워야 합니다 `m_pErrorInfo` . 자세한 설명은 [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) 구조체를 참조 하세요.

DAO 예외 및 예제 코드에 대 한 자세한 내용은 [예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)문서를 참조 하세요.

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a> CDaoException:: m_nAfxDaoError

MFC 확장 오류 코드를 포함 합니다.

### <a name="remarks"></a>설명

이 코드는 MFC DAO 클래스의 특정 구성 요소가 erred 경우에 제공 됩니다.

가능한 값은 다음과 같습니다.

- 최근 작업 NO_AFX_DAO_ERROR MFC 확장 오류가 발생 하지 않았습니다. 그러나이 작업은 DAO 또는 OLE에서 다른 오류를 생성 했을 수 있으므로 [m_pErrorInfo](#m_perrorinfo) 를 확인 하 고 [m_scode](#m_scode)수도 있습니다.

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC에서 Microsoft Jet 데이터베이스 엔진을 초기화할 수 없습니다. OLE를 초기화 하지 못했거나 DAO 데이터베이스 엔진 개체의 인스턴스를 만들 수 없습니다. 이러한 문제는 일반적으로 DAO 또는 OLE의 잘못 된 설치를 제안 합니다.

- AFX_DAO_ERROR_DFX_BIND는 DAO 레코드 필드 교환 (DFX) 함수 호출에 사용 된 주소가 존재 하지 않거나 잘못 되었습니다 (주소를 데이터 바인딩에 사용 하지 않음). DFX 호출에 잘못 된 주소가 전달 되었거나 DFX 작업 간에 주소가 잘못 되었을 수 있습니다.

- 열 정의를 기반으로 하는 레코드 집합을 열거나 열려 있는 상태가 아닌 테이블 정의 개체를 열려고 했습니다. AFX_DAO_ERROR_OBJECT_NOT_OPEN

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a> CDaoException:: m_pErrorInfo

`CDaoErrorInfo` [Geterrorinfo](#geterrorinfo)를 호출 하 여 마지막으로 검색 한 DAO error 개체에 대 한 정보를 제공 하는 구조체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

이 개체에는 다음 정보가 포함 되어 있습니다.

|CDaoErrorInfo 멤버|정보 산업|의미|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|오류 코드|DAO 오류 코드|
|`m_strSource`|원본|처음에 오류를 생성 한 개체 또는 응용 프로그램의 이름입니다.|
|`m_strDescription`|설명|오류와 관련 된 설명이 포함 된 문자열입니다.|
|`m_strHelpFile`|도움말 파일|사용자가 문제에 대 한 정보를 가져올 수 있는 Windows 도움말 파일의 경로입니다.|
|`m_lHelpContext`|도움말 컨텍스트|DAO 도움말 파일의 항목에 대 한 컨텍스트 ID입니다.|

개체에 포함 된 정보에 대 한 자세한 내용은 `CDaoErrorInfo` [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) 구조체를 참조 하세요.

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a> CDaoException:: m_scode

`SCODE`오류를 설명 하는 형식의 값을 포함 합니다.

### <a name="remarks"></a>설명

이는 OLE 코드입니다. 거의 모든 경우에 다른 데이터 멤버에서 더 구체적인 MFC 또는 DAO 오류 정보를 사용할 수 있기 때문에이 값을 사용 해야 하는 경우는 거의 없습니다 `CDaoException` .

이에 대 한 자세한 내용은 Windows SDK에서 [OLE 오류 코드의 구조](/windows/win32/com/structure-of-com-error-codes) 항목을 참조 하십시오. 이 데이터 형식은 HRESULT 데이터 형식에 매핑됩니다.

## <a name="see-also"></a>참고 항목

[CException 클래스](../../mfc/reference/cexception-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CException 클래스](../../mfc/reference/cexception-class.md)
