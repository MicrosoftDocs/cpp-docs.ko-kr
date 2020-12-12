---
description: '자세히 알아보기: CDaoTableDef 클래스'
title: CDaoTableDef 클래스
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: ead41d1dae2d248324809690e778e8f623a73caf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248023"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef 클래스

기본 테이블 또는 연결된 테이블의 저장된 정의를 나타냅니다.

## <a name="syntax"></a>구문

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|`CDaoTableDef` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoTableDef:: Append](#append)|데이터베이스에 새 테이블을 추가 합니다.|
|[CDaoTableDef::CanUpdate](#canupdate)|테이블을 업데이트할 수 있는 경우 0이 아닌 값을 반환 합니다. 필드 또는 테이블 속성의 정의를 수정할 수 있습니다.|
|[CDaoTableDef:: Close](#close)|열려 있는 tabledef를 닫습니다.|
|[CDaoTableDef:: Create](#create)|[Append](#append)를 사용 하 여 데이터베이스에 추가할 수 있는 테이블을 만듭니다.|
|[CDaoTableDef::CreateField](#createfield)|테이블에 대 한 필드를 만들기 위해 호출 됩니다.|
|[CDaoTableDef:: CreateIndex](#createindex)|테이블에 대 한 인덱스를 만들기 위해 호출 됩니다.|
|[CDaoTableDef::D eleteField](#deletefield)|테이블에서 필드를 삭제 하기 위해 호출 됩니다.|
|[CDaoTableDef::D eleteIndex](#deleteindex)|테이블에서 인덱스를 삭제 하기 위해 호출 됩니다.|
|[CDaoTableDef:: GetAttributes](#getattributes)|개체의 특성을 하나 이상 나타내는 값을 반환 합니다 `CDaoTableDef` .|
|[CDaoTableDef:: GetConnect](#getconnect)|테이블의 원본에 대 한 정보를 제공 하는 값을 반환 합니다.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|개체의 기반이 되는 기본 테이블이 만들어진 날짜와 시간을 반환 합니다 `CDaoTableDef` .|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|기본 테이블 디자인에 대해 가장 최근에 변경한 날짜와 시간을 반환 합니다.|
|[CDaoTableDef:: GetFieldCount](#getfieldcount)|테이블의 필드 수를 나타내는 값을 반환 합니다.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|테이블의 필드에 대 한 특정 종류의 정보를 반환 합니다.|
|[CDaoTableDef:: GetIndexCount](#getindexcount)|테이블의 인덱스 수를 반환 합니다.|
|[CDaoTableDef:: GetIndexInfo](#getindexinfo)|테이블의 인덱스에 대 한 특정 종류의 정보를 반환 합니다.|
|[CDaoTableDef:: GetName](#getname)|테이블의 사용자 정의 이름을 반환 합니다.|
|[CDaoTableDef:: GetRecordCount](#getrecordcount)|테이블의 레코드 수를 반환 합니다.|
|[CDaoTableDef:: GetSourceTableName](#getsourcetablename)|원본 데이터베이스에 있는 연결 된 테이블의 이름을 지정 하는 값을 반환 합니다.|
|[CDaoTableDef:: GetValidationRule](#getvalidationrule)|필드가 변경 되거나 테이블에 추가 될 때 필드의 데이터 유효성을 검사 하는 값을 반환 합니다.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|필드 개체의 값이 지정 된 유효성 검사 규칙을 충족 하지 않는 경우 응용 프로그램에서 표시 하는 메시지의 텍스트를 지정 하는 값을 반환 합니다.|
|[CDaoTableDef:: IsOpen](#isopen)|테이블이 열려 있으면 0이 아닌 값을 반환 합니다.|
|[CDaoTableDef:: Open](#open)|데이터베이스의 TableDef's에 저장 된 기존 테이블 정의를 엽니다.|
|[CDaoTableDef:: RefreshLink](#refreshlink)|연결 된 테이블에 대 한 연결 정보를 업데이트 합니다.|
|[CDaoTableDef:: SetAttributes](#setattributes)|개체의 특성을 하나 이상 나타내는 값을 설정 합니다 `CDaoTableDef` .|
|[CDaoTableDef:: SetConnect](#setconnect)|테이블의 원본에 대 한 정보를 제공 하는 값을 설정 합니다.|
|[CDaoTableDef:: SetName](#setname)|테이블의 이름을 설정 합니다.|
|[CDaoTableDef:: SetSourceTableName](#setsourcetablename)|원본 데이터베이스에 있는 연결 된 테이블의 이름을 지정 하는 값을 설정 합니다.|
|[CDaoTableDef:: SetValidationRule](#setvalidationrule)|필드의 데이터를 변경 하거나 테이블에 추가할 때 해당 데이터의 유효성을 검사 하는 값을 설정 합니다.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|필드 개체의 값이 지정 된 유효성 검사 규칙을 충족 하지 않는 경우 응용 프로그램에서 표시 하는 메시지의 텍스트를 지정 하는 값을 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDaoTableDef:: m_pDAOTableDef](#m_pdaotabledef)|테이블 정의 개체 내부에 있는 DAO 인터페이스에 대 한 포인터입니다.|
|[CDaoTableDef:: m_pDatabase](#m_pdatabase)|이 테이블의 원본 데이터베이스입니다.|

## <a name="remarks"></a>설명

각 DAO 데이터베이스 개체는 저장 된 모든 DAO 테이블 정의 개체를 포함 하는 테이블 정의 라는 컬렉션을 유지 관리 합니다.

개체를 사용 하 여 테이블 정의를 조작 `CDaoTableDef` 합니다. 예를 들어, 다음을 수행할 수 있습니다.

- 데이터베이스에 있는 로컬, 연결 또는 외부 테이블의 필드 및 인덱스 구조를 검사 합니다.

- 연결 된 `SetConnect` `SetSourceTableName` 테이블에 대 한 및 멤버 함수를 호출 하 고 멤버 함수를 사용 하 여 연결 `RefreshLink` 된 테이블에 대 한 연결을 업데이트 합니다.

- `CanUpdate`멤버 함수를 호출 하 여 테이블에서 필드 정의를 편집할 수 있는지 확인 합니다.

- `GetValidationRule`및 및 `SetValidationRule` `GetValidationText` 및 멤버 함수를 사용 하 여 유효성 검사 조건을 가져오거나 설정 `SetValidationText` 합니다.

- `Open`멤버 함수를 사용 하 여 테이블, 다이너셋 또는 스냅숏 형식 개체를 만듭니다 `CDaoRecordset` .

    > [!NOTE]
    >  DAO 데이터베이스 클래스는 ODBC (Open Database Connectivity)를 기반으로 하는 MFC 데이터베이스 클래스와는 다릅니다. 모든 DAO 데이터베이스 클래스 이름에는 "CDao" 접두사가 있습니다. 여전히 DAO 클래스를 사용 하 여 ODBC 데이터 원본에 액세스할 수 있습니다. 일반적으로 DAO 클래스는 Microsoft Jet 데이터베이스 엔진과 관련 되므로 뛰어난 기능을 제공 합니다.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>테이블 정의 개체를 사용 하 여 기존 테이블에서 작업 하거나 새 테이블을 만들려면

1. 모든 경우에는 먼저 `CDaoTableDef` 테이블이 속한 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터를 제공 하 여 개체를 생성 합니다.

1. 그런 다음 원하는 항목에 따라 다음을 수행 합니다.

   - 기존에 저장 된 테이블을 사용 하려면 저장 된 테이블의 이름을 제공 하 여 tabledef 개체의 [Open](#open) 멤버 함수를 호출 합니다.

   - 새 테이블을 만들려면 테이블 이름을 제공 하 여 테이블 정의 개체의 [create](#create) member 함수를 호출 합니다. [CreateField](#createfield) 및 [createindex](#createindex) 를 호출 하 여 테이블에 필드 및 인덱스를 추가 합니다.

   - [Append](#append) 를 호출 하 여 테이블을 데이터베이스의 테이블 컬렉션 컬렉션에 추가 하 여 테이블을 저장 합니다. `Create` 테이블 정의를 열림 상태로 전환 하므로를 호출한 후에는를 `Create` 호출 하지 않습니다 `Open` .

        > [!TIP]
        >  저장 된 테이블을 만드는 가장 쉬운 방법은이를 만들어 Microsoft Access를 사용 하 여 데이터베이스에 저장 하는 것입니다. 그런 다음 MFC 코드에서 열고 사용할 수 있습니다.

열거나 만든 테이블 형식 개체를 사용 하려면 `CDaoRecordset` `dbOpenTable` *nOpenType* 매개 변수의 값을 사용 하 여 테이블 형식 이름을 지정 하 여 개체를 만들고 엽니다.

테이블 정의 개체를 사용 하 여 개체를 만들려면 `CDaoRecordset` 일반적으로 위에서 설명한 대로 테이블 정의를 만들거나 연 다음 [CDaoRecordset:: open](../../mfc/reference/cdaorecordset-class.md#open)을 호출할 때 테이블 정의 개체에 대 한 포인터를 전달 하 여 레코드 집합 개체를 생성 합니다. 전달 하는 tabledef는 열린 상태 여야 합니다. 자세한 내용은 클래스 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)를 참조 하세요.

테이블 정의 개체 사용을 마치면 [Close](../../mfc/reference/cdaorecordset-class.md#close) 멤버 함수를 호출 합니다. 그런 다음 테이블 정의 개체를 삭제 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaotabledefappend"></a><a name="append"></a> CDaoTableDef:: Append

[Create](#create) 를 호출 하 여 테이블 정의를 데이터베이스에 저장 하는 새 테이블 정의 개체를 만든 후이 멤버 함수를 호출 합니다.

```
virtual void Append();
```

### <a name="remarks"></a>설명

함수는 데이터베이스의 테이블 컬렉션에 개체를 추가 합니다. 테이블 정의를 추가 하지 않고 정의 하는 동안 임시 개체로 정의를 사용할 수 있지만 저장 하 고 사용 하려면를 호출 해야 `Append` 합니다.

> [!NOTE]
> Null 또는 빈 문자열을 포함 하는 명명 되지 않은 tabledef를 추가 하려고 하면 MFC에서 예외가 throw 됩니다.

관련 내용은 DAO 도움말의 "Append 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a> CDaoTableDef::CanUpdate

개체의 기반이 되는 테이블의 정의를 변경할 수 있는지 여부를 확인 하려면이 멤버 함수를 호출 `CDaoTableDef` 합니다.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>반환 값

테이블 구조 (스키마)를 수정할 수 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본적으로 개체를 기반으로 하는 새로 만든 테이블은 업데이트할 수 있으며, `CDaoTableDef` 개체의 내부 연결 된 테이블은 `CDaoTableDef` 업데이트할 수 없습니다. `CDaoTableDef`결과 레코드 집합을 업데이트할 수 없는 경우에도 개체를 업데이트할 수 있습니다.

관련 내용은 DAO 도움말의 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a> CDaoTableDef::CDaoTableDef

`CDaoTableDef` 개체를 생성합니다.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>매개 변수

*pDatabase*<br/>
[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

개체를 생성 한 후에는 [Create](#create) 또는 [Open](#open) 멤버 함수를 호출 해야 합니다. 개체를 마치면 [Close](#close) 멤버 함수를 호출 하 고 개체를 삭제 해야 합니다 `CDaoTableDef` .

## <a name="cdaotabledefclose"></a><a name="close"></a> CDaoTableDef:: Close

이 멤버 함수를 호출 하 여 테이블 정의 개체를 닫고 해제 합니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

일반적으로를 호출한 후에는를 사용 하 여 `Close` 할당 된 개체를 삭제 **`new`** 합니다.

를 호출한 후에는 [Open](#open) 을 다시 호출할 수 있습니다 `Close` . 이렇게 하면 테이블 정의 개체를 재사용할 수 있습니다.

관련 정보는 DAO 도움말의 "Close 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefcreate"></a><a name="create"></a> CDaoTableDef:: Create

이 멤버 함수를 호출 하 여 저장 된 새 테이블을 만듭니다.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
테이블의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*lAttributes*<br/>
테이블 정의 개체로 표시 되는 테이블의 특징에 해당 하는 값입니다. 비트 or를 사용 하 여 다음 상수를 결합할 수 있습니다.

|상수|설명|
|--------------|-----------------|
|`dbAttachExclusive`|Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 테이블은 단독으로 사용 하기 위해 열린 연결 된 테이블 임을 나타냅니다.|
|`dbAttachSavePWD`|Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 연결 된 테이블의 사용자 ID와 암호가 연결 정보로 저장 됨을 나타냅니다.|
|`dbSystemObject`|테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 시스템 테이블 임을 나타냅니다.|
|`dbHiddenObject`|테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 숨겨진 테이블 임을 나타냅니다.|

*lpszSrcTable*<br/>
원본 테이블 이름을 포함 하는 문자열에 대 한 포인터입니다. 기본적으로이 값은 NULL로 초기화 됩니다.

*lpszConnect*<br/>
기본 연결 문자열을 포함 하는 문자열에 대 한 포인터입니다. 기본적으로이 값은 NULL로 초기화 됩니다.

### <a name="remarks"></a>설명

테이블 정의의 이름을 지정한 후 [Append](#append) 를 호출 하 여 데이터베이스의 테이블 정의 컬렉션에 테이블 정의를 저장할 수 있습니다. 를 호출한 후에 `Append` 는 테이블 정의가 열린 상태 이며이를 사용 하 여 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 만들 수 있습니다.

관련 내용은 DAO 도움말의 "CreateTableDef 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a> CDaoTableDef::CreateField

테이블에 필드를 추가 하려면이 멤버 함수를 호출 합니다.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
이 필드의 이름을 지정 하는 문자열 식에 대 한 포인터입니다.

*nType*<br/>
필드의 데이터 형식을 나타내는 값입니다. 설정은 다음 값 중 하나일 수 있습니다.

|형식|크기(바이트)|설명|
|----------|--------------------|-----------------|
|`dbBoolean`|1바이트|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|통화 ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|날짜/시간 ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|텍스트 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (OLE 개체), [CLongBinary](../../mfc/reference/clongbinary-class.md) 또는 [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|메모 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
텍스트를 포함 하는 필드의 최대 크기 (바이트) 또는 텍스트 또는 숫자 값을 포함 하는 필드의 고정 크기를 나타내는 값입니다. 모든 텍스트 필드에 대해서는 *Lsize* 매개 변수가 무시 됩니다.

*lAttributes*<br/>
필드의 특징에 해당 하는 값으로, 비트 or를 사용 하 여 결합할 수 있습니다.

|상수|설명|
|--------------|-----------------|
|`dbFixedField`|필드 크기가 고정 되어 있습니다 (숫자 필드의 경우 기본값).|
|`dbVariableField`|필드 크기가 variable (텍스트 필드에만 해당)입니다.|
|`dbAutoIncrField`|새 레코드에 대 한 필드 값이 자동으로 변경 될 수 없는 고유한 정수 (long)로 증가 합니다. Microsoft Jet 데이터베이스 테이블에만 지원 됩니다.|
|`dbUpdatableField`|필드 값을 변경할 수 있습니다.|
|`dbDescending`|필드는 내림차순 (Z 또는 100-0) 순서로 정렬 됩니다 (인덱스 개체의 필드 컬렉션에 있는 필드 개체에만 적용 됨). 이 상수를 생략 하면 필드가 오름차순 (a-z 또는 0-100) 순서 (기본값)로 정렬 됩니다.|

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 구조체에 대 한 참조입니다.

### <a name="remarks"></a>설명

Ole ( `DAOField` ) 개체가 만들어지고 `DAOTableDef` (ole) 개체의 Fields 컬렉션에 추가 됩니다. 개체 속성을 검사 하는 데 사용 하는 것 외에도를 사용 `CDaoFieldInfo` 하 여 테이블 정의에 새 필드를 만들기 위한 입력 매개 변수를 생성할 수 있습니다. 의 첫 번째 버전은 `CreateField` 사용 하기 더 간단 하지만 보다 세부적인 제어를 원하는 경우 `CreateField` 매개 변수를 사용 하는 두 번째 버전의를 사용할 수 있습니다 `CDaoFieldInfo` .

매개 변수를 사용 하는 버전을 사용 하는 경우 `CreateField` `CDaoFieldInfo` 구조체의 다음 멤버를 신중 하 게 설정 해야 합니다 `CDaoFieldInfo` .

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

멤버의 나머지 멤버는 `CDaoFieldInfo` **0**, FALSE 또는 빈 문자열로 설정 되어야 합니다. 그렇지 않으면이 `CDaoException` 발생할 수 있습니다.

관련 내용은 DAO 도움말의 "CreateField 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a> CDaoTableDef:: CreateIndex

테이블에 인덱스를 추가 하려면이 함수를 호출 합니다.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>매개 변수

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 구조체에 대 한 참조입니다.

### <a name="remarks"></a>설명

인덱스는 데이터베이스 테이블에서 액세스 하는 레코드의 순서와 중복 레코드가 허용 되는지 여부를 지정 합니다. 인덱스는 데이터에 대 한 효율적인 액세스도 제공 합니다.

테이블에 대 한 인덱스를 만들 필요는 없으며 인덱싱되지 않은 테이블에는 특정 레코드에 액세스 하거나 레코드 집합을 만드는 데 시간이 오래 걸릴 수 있습니다. 반면에 너무 많은 인덱스를 만들면 모든 인덱스가 자동으로 업데이트 되므로 업데이트, 추가 및 삭제 작업의 속도가 느려집니다. 만들 인덱스를 결정할 때 이러한 요인을 고려 합니다.

구조체의 다음 멤버를 `CDaoIndexInfo` 설정 해야 합니다.

- `m_strName` 이름을 제공 해야 합니다.

- `m_pFieldInfos` 구조체의 배열을 가리켜야 합니다 `CDaoIndexFieldInfo` .

- `m_nFields` 구조체의 배열에 있는 필드 수를 지정 해야 합니다 `CDaoFieldInfo` .

FALSE로 설정 된 경우 나머지 멤버는 무시 됩니다. 또한 `m_lDistinctCount` 인덱스를 만드는 동안에는 멤버가 무시 됩니다.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a> CDaoTableDef::D eleteField

필드를 제거 하 고 액세스할 수 없게 하려면이 멤버 함수를 호출 합니다.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
기존 필드의 이름인 문자열 식에 대 한 포인터입니다.

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 테이블의 0부터 시작 하는 필드 컬렉션에 있는 필드의 인덱스입니다.

### <a name="remarks"></a>설명

데이터베이스에 추가 되지 않은 새 개체 또는 [CanUpdate](#canupdate) 에서 0이 아닌 값을 반환 하는 경우이 멤버 함수를 사용할 수 있습니다.

관련 내용은 DAO 도움말의 "Delete 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a> CDaoTableDef::D eleteIndex

기본 테이블의 인덱스를 삭제 하려면이 멤버 함수를 호출 합니다.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
기존 인덱스의 이름인 문자열 식에 대 한 포인터입니다.

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 데이터베이스의 0부터 시작 하는 테이블 컬렉션에 있는 인덱스 개체의 배열 인덱스입니다.

### <a name="remarks"></a>설명

데이터베이스에 추가 되지 않은 새 개체 또는 [CanUpdate](#canupdate) 에서 0이 아닌 값을 반환 하는 경우이 멤버 함수를 사용할 수 있습니다.

관련 내용은 DAO 도움말의 "Delete 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a> CDaoTableDef:: GetAttributes

개체의 경우 `CDaoTableDef` 반환 값은 개체가 나타내는 테이블의 특성을 지정 `CDaoTableDef` 하며 이러한 상수의 합이 될 수 있습니다.

```
long GetAttributes();
```

### <a name="return-value"></a>반환 값

개체의 특성을 하나 이상 나타내는 값을 반환 합니다 `CDaoTableDef` .

### <a name="remarks"></a>설명

|상수|설명|
|--------------|-----------------|
|`dbAttachExclusive`|Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 테이블은 단독으로 사용 하기 위해 열린 연결 된 테이블 임을 나타냅니다.|
|`dbAttachSavePWD`|Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 연결 된 테이블의 사용자 ID와 암호가 연결 정보로 저장 됨을 나타냅니다.|
|`dbSystemObject`|테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 시스템 테이블 임을 나타냅니다.|
|`dbHiddenObject`|테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 숨겨진 테이블 임을 나타냅니다.|
|`dbAttachedTable`|테이블은 Paradox 데이터베이스와 같은 비 ODBC 데이터베이스에서 연결 된 테이블 임을 나타냅니다.|
|`dbAttachedODBC`|테이블이 ODBC 데이터베이스에서 연결 된 테이블 임을 나타냅니다 (예: Microsoft SQL Server).|

시스템 테이블은 Microsoft Jet 데이터베이스 엔진에서 다양 한 내부 정보를 포함 하기 위해 만든 테이블입니다.

숨겨진 테이블은 Microsoft Jet 데이터베이스 엔진에서 임시로 사용 하기 위해 만든 테이블입니다.

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a> CDaoTableDef:: GetConnect

이 멤버 함수를 호출 하 여 데이터 소스에 대 한 연결 문자열을 가져옵니다.

```
CString GetConnect();
```

### <a name="return-value"></a>반환 값

`CString`테이블의 경로와 데이터베이스 유형을 포함 하는 개체입니다.

### <a name="remarks"></a>설명

연결 된 `CDaoTableDef` 테이블을 나타내는 개체의 경우 개체는 `CString` 한 부분 또는 두 부분으로 구성 됩니다 (데이터베이스 유형 지정자와 데이터베이스의 경로).

아래 표에 표시 된 경로는 데이터베이스 파일을 포함 하는 디렉터리의 전체 경로 이며 "DATABASE =" 식별자 앞에와 야 합니다. Microsoft Jet 및 Microsoft Excel 데이터베이스와 마찬가지로 특정 파일 이름이 데이터베이스 경로 인수에 포함 되는 경우도 있습니다.

[CDaoTableDef:: SetConnect](#setconnect) 의 테이블은 가능한 데이터베이스 형식 및 해당 데이터베이스 지정자와 경로를 표시 합니다.

Microsoft Jet 데이터베이스 기본 테이블의 경우 지정자는 빈 문자열 ("")입니다.

암호가 필요 하지만 제공 되지 않은 경우 ODBC 드라이버는 테이블에 처음 액세스할 때 로그인 대화 상자를 표시 하 고 연결을 닫은 후 다시 열 때 다시 열 수 있습니다. 연결 된 테이블에 특성이 있으면 `dbAttachSavePWD` 테이블을 다시 열 때 로그인 프롬프트가 표시 되지 않습니다.

관련 내용은 DAO 도움말의 "연결 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a> CDaoTableDef::GetDateCreated

이 함수를 호출 하 여 개체의 기반이 되는 테이블의 날짜 및 시간을 확인 `CDaoTableDef` 합니다.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>반환 값

개체의 기반이 되는 테이블이 생성 된 날짜 및 시간을 포함 하는 값 `CDaoTableDef` 입니다.

### <a name="remarks"></a>설명

날짜 및 시간 설정은 기본 테이블이 만들어지거나 마지막으로 업데이트 된 컴퓨터에서 파생 됩니다. 다중 사용자 환경에서는 불일치를 방지 하기 위해 사용자가 파일 서버에서 직접 이러한 설정을 가져와야 합니다. 즉, 모든 클라이언트는 한 서버에서 "표준" 시간 원본을 사용 해야 합니다.

관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a> CDaoTableDef::GetDateLastUpdated

개체가 마지막으로 업데이트 된 날짜와 시간을 확인 하려면이 함수를 호출 `CDaoTableDef` 합니다.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>반환 값

개체의 기반이 되는 테이블을 마지막으로 업데이트 한 날짜와 시간을 포함 하는 값입니다 `CDaoTableDef` .

### <a name="remarks"></a>설명

날짜 및 시간 설정은 기본 테이블이 만들어지거나 마지막으로 업데이트 된 컴퓨터에서 파생 됩니다. 다중 사용자 환경에서는 불일치를 방지 하기 위해 사용자가 파일 서버에서 직접 이러한 설정을 가져와야 합니다. 즉, 모든 클라이언트는 한 서버에서 "표준" 시간 원본을 사용 해야 합니다.

관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a> CDaoTableDef:: GetFieldCount

이 멤버 함수를 호출 하 여 테이블에 정의 된 필드 수를 검색 합니다.

```
short GetFieldCount();
```

### <a name="return-value"></a>반환 값

테이블의 필드 수입니다.

### <a name="remarks"></a>설명

값이 0 이면 컬렉션에 개체가 없습니다.

관련 정보는 DAO 도움말의 "Count 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a> CDaoTableDef:: GetFieldInfo

이 멤버 함수를 호출 하 여 테이블 정의에 정의 된 필드에 대 한 다양 한 종류의 정보를 가져옵니다.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 테이블의 0부터 시작 하는 필드 컬렉션에 있는 field 개체의 인덱스입니다.

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 구조체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 필드에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 작업과 함께 여기에 나열 됩니다.

- `AFX_DAO_PRIMARY_INFO` 기본 이름, 형식, 크기, 특성입니다. 가장 빠른 성능을 위해이 옵션을 사용 합니다.

- `AFX_DAO_SECONDARY_INFO` 기본 정보, 더하기: 서 수 위치, 필수, 0 길이 허용, 데이터 정렬 순서, 외래 이름, 원본 필드, 원본 테이블

- `AFX_DAO_ALL_INFO` 기본 및 보조 정보, 유효성 검사 규칙, 유효성 검사 텍스트, 기본값

*lpszName*<br/>
이름으로 조회할 필드 개체의 이름에 대 한 포인터입니다. 이름은 필드의 이름을 고유 하 게 하는 최대 64 문자를 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

한 버전의 함수를 사용 하 여 인덱스를 기준으로 필드를 조회할 수 있습니다. 다른 버전에서는 이름을 기준으로 필드를 조회할 수 있습니다.

반환 되는 정보에 대 한 설명은 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준에 대 한 정보도 얻을 수 있습니다.

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a> CDaoTableDef:: GetIndexCount

이 멤버 함수를 호출 하 여 테이블의 인덱스 수를 가져옵니다.

```
short GetIndexCount();
```

### <a name="return-value"></a>반환 값

테이블의 인덱스 수입니다.

### <a name="remarks"></a>설명

값이 0 이면 컬렉션에 인덱스가 없는 것입니다.

관련 정보는 DAO 도움말의 "Count 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a> CDaoTableDef:: GetIndexInfo

이 멤버 함수를 호출 하 여 테이블 정의에 정의 된 인덱스에 대 한 다양 한 종류의 정보를 가져옵니다.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
컬렉션에서의 위치에 따라 조회 하기 위해 테이블의 인덱스 (0부터 시작) 컬렉션에 있는 인덱스 개체의 숫자 인덱스입니다.

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 구조체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 인덱스에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 작업과 함께 여기에 나열 됩니다.

- `AFX_DAO_PRIMARY_INFO` 이름, 필드 정보, 필드입니다. 가장 빠른 성능을 위해이 옵션을 사용 합니다.

- `AFX_DAO_SECONDARY_INFO` 기본 정보 및 기본, 고유, 클러스터형, Null 무시, 필수, 외래

- `AFX_DAO_ALL_INFO` 기본 및 보조 정보, 및: 고유 카운트

*lpszName*<br/>
이름으로 조회할 인덱스 개체의 이름에 대 한 포인터입니다.

### <a name="remarks"></a>설명

한 버전의 함수를 사용 하 여 컬렉션에서 인덱스를 찾을 수 있습니다. 다른 버전에서는 이름을 기준으로 인덱스를 조회할 수 있습니다.

반환 되는 정보에 대 한 설명은 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준에 대 한 정보도 얻을 수 있습니다.

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetname"></a><a name="getname"></a> CDaoTableDef:: GetName

이 멤버 함수를 호출 하 여 기본 테이블의 사용자 정의 이름을 가져옵니다.

```
CString GetName();
```

### <a name="return-value"></a>반환 값

테이블에 대 한 사용자 정의 이름입니다.

### <a name="remarks"></a>설명

이 이름은 문자로 시작 하 고 최대 64 자를 포함할 수 있습니다. 숫자 및 밑줄 문자를 포함할 수 있지만 문장 부호 또는 공백을 포함할 수 없습니다.

관련 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a> CDaoTableDef:: GetRecordCount

이 멤버 함수를 호출 하 여 개체에 있는 레코드 수를 확인 `CDaoTableDef` 합니다.

```
long GetRecordCount();
```

### <a name="return-value"></a>반환 값

테이블 정의 개체에서 액세스 하는 레코드 수입니다.

### <a name="remarks"></a>설명

테이블 `GetRecordCount` 형식 개체에 대 한 호출은 테이블의 `CDaoTableDef` 대략적인 레코드 수를 반영 하며 테이블 레코드가 추가 되 고 삭제 되는 즉시 영향을 받습니다. [CDaoWorkSpace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)를 호출할 때까지 롤백된 트랜잭션은 레코드 수의 일부로 표시 됩니다. `CDaoTableDef`레코드가 없는 개체의 레코드 수 속성 설정은 0입니다. 연결 된 테이블 또는 ODBC 데이터베이스로 작업할 때는 `GetRecordCount` 항상-1을 반환 합니다.

관련 정보는 DAO 도움말의 "RecordCount 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a> CDaoTableDef:: GetSourceTableName

이 멤버 함수를 호출 하 여 원본 데이터베이스에서 연결 된 테이블의 이름을 검색 합니다.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>반환 값

`CString`연결 된 테이블의 원본 이름을 지정 하는 개체 또는 네이티브 데이터 테이블의 경우 빈 문자열입니다.

### <a name="remarks"></a>설명

연결 된 테이블은 Microsoft Jet 데이터베이스에 연결 된 다른 데이터베이스의 테이블입니다. 연결 된 테이블에 대 한 데이터는 다른 응용 프로그램에서 조작할 수 있는 외부 데이터베이스에 남아 있습니다.

관련 내용은 DAO 도움말의 "SourceTableName 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a> CDaoTableDef:: GetValidationRule

이 멤버 함수를 호출 하 여 테이블 정의에 대 한 유효성 검사 규칙을 검색 합니다.

```
CString GetValidationRule();
```

### <a name="return-value"></a>반환 값

`CString`필드의 데이터를 변경 하거나 테이블에 추가할 때 해당 데이터의 유효성을 검사 하는 개체입니다.

### <a name="remarks"></a>설명

유효성 검사 규칙은 업데이트 작업에 연결 하는 데 사용 됩니다. 테이블 정의에 유효성 검사 규칙이 포함 된 경우 해당 테이블 정의에 대 한 업데이트는 데이터를 변경 하기 전에 미리 결정 된 조건과 일치 해야 합니다. 변경 내용이 조건과 일치 하지 않는 경우 [GetValidationText](#getvalidationtext) 값을 포함 하는 예외가 throw 됩니다. 개체의 경우 `CDaoTableDef` 이 `CString` 는 기본 테이블에 대 한 읽기/쓰기와 연결 된 테이블에 대 한 읽기 전용입니다.

관련 내용은 DAO 도움말의 "ValidationRule 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a> CDaoTableDef::GetValidationText

사용자가 유효성 검사 규칙과 일치 하지 않는 데이터를 입력할 때 표시할 문자열을 검색 하려면이 함수를 호출 합니다.

```
CString GetValidationText();
```

### <a name="return-value"></a>반환 값

`CString`사용자가 유효성 검사 규칙과 일치 하지 않는 데이터를 입력 하는 경우 표시 되는 텍스트를 지정 하는 개체입니다.

### <a name="remarks"></a>설명

개체의 경우 `CDaoTableDef` 이 `CString` 는 기본 테이블에 대 한 읽기/쓰기와 연결 된 테이블에 대 한 읽기 전용입니다.

관련 내용은 DAO 도움말의 "ValidationText 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a> CDaoTableDef:: IsOpen

이 멤버 함수를 호출 하 여 개체가 현재 열려 있는지 여부를 확인 `CDaoTableDef` 합니다.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>반환 값

개체가 열려 있으면 0이 아니고 `CDaoTableDef` , 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a> CDaoTableDef:: m_pDatabase

이 테이블에 대 한 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a> CDaoTableDef:: m_pDAOTableDef

개체를 기반으로 하는 DAO 테이블 정의 개체의 OLE 인터페이스에 대 한 포인터를 포함 `CDaoTableDef` 합니다.

### <a name="remarks"></a>설명

DAO 인터페이스에 직접 액세스 해야 하는 경우이 포인터를 사용 합니다.

## <a name="cdaotabledefopen"></a><a name="open"></a> CDaoTableDef:: Open

이 멤버 함수를 호출 하 여 이전에 데이터베이스의 TableDef's에 저장 된 테이블 정의를 엽니다.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
테이블 이름을 지정 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a> CDaoTableDef:: RefreshLink

연결 된 테이블에 대 한 연결 정보를 업데이트 하려면이 멤버 함수를 호출 합니다.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>설명

해당 개체에 대해 [Setconnect](#setconnect) 를 호출한 `CDaoTableDef` 다음 멤버 함수를 사용 하 여 정보를 업데이트 하면 연결 된 테이블에 대 한 연결 정보를 변경할 수 있습니다 `RefreshLink` . 를 호출 하면 `RefreshLink` 연결 된 테이블의 속성은 변경 되지 않습니다.

수정 된 연결 정보를 강제로 적용 하려면이 테이블 정의를 기반으로 하는 모든 열린 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 닫아야 합니다.

관련 내용은 DAO 도움말의 "RefreshLink 메서드" 항목을 참조 하십시오.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a> CDaoTableDef:: SetAttributes

개체의 특성을 하나 이상 나타내는 값을 설정 합니다 `CDaoTableDef` .

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>매개 변수

*lAttributes*<br/>
개체로 표시 되는 테이블의 특성으로 `CDaoTableDef` , 이러한 상수의 합계를 사용할 수 있습니다.

|상수|설명|
|--------------|-----------------|
|`dbAttachExclusive`|Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 테이블은 단독으로 사용 하기 위해 열린 연결 된 테이블 임을 나타냅니다.|
|`dbAttachSavePWD`|Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 연결 된 테이블의 사용자 ID와 암호가 연결 정보로 저장 됨을 나타냅니다.|
|`dbSystemObject`|테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 시스템 테이블 임을 나타냅니다.|
|`dbHiddenObject`|테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 숨겨진 테이블 임을 나타냅니다.|

### <a name="remarks"></a>설명

여러 특성을 설정 하는 경우 비트 or 연산자를 사용 하 여 적절 한 상수의 합계를 구하고 조합할 수 있습니다. `dbAttachExclusive`연결 되지 않은 테이블에 대해를 설정 하면 예외가 발생 합니다. 다음 값을 결합 하면 예외도 생성 됩니다.

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a> CDaoTableDef:: SetConnect

연결 된 `CDaoTableDef` 테이블을 나타내는 개체의 경우 string 개체는 한 부분 또는 두 부분으로 구성 됩니다 (데이터베이스 유형 지정자와 데이터베이스의 경로).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>매개 변수

*lpszConnect*<br/>
ODBC 또는 설치 가능한 ISAM 드라이버에 전달할 추가 매개 변수를 지정 하는 문자열 식에 대 한 포인터입니다.

### <a name="remarks"></a>설명

아래 표에 표시 된 경로는 데이터베이스 파일을 포함 하는 디렉터리의 전체 경로 이며 "DATABASE =" 식별자 앞에와 야 합니다. Microsoft Jet 및 Microsoft Excel 데이터베이스와 마찬가지로 특정 파일 이름이 데이터베이스 경로 인수에 포함 되는 경우도 있습니다.

> [!NOTE]
> "DATABASE = drive: \path" 형식의 등호 (등호) 경로 문 주위에 공백을 포함 하지 마십시오 \\ . 이로 인해 예외가 throw 되 고 연결에 실패 합니다.

다음 표에서는 가능한 데이터베이스 유형과 해당 데이터베이스 지정자와 경로를 보여 줍니다.

|데이터베이스 유형|지정자|경로|
|-------------------|---------------|----------|
|Jet 데이터베이스 엔진을 사용 하는 데이터베이스|"[ `database`];"|" `drive` : \\ \  *경로* \\ \  *파일 이름* 입니다. 않았더라도|
|dBASE III|"dBASE III;"|" `drive` : \\ \  *path*"|
|dBASE IV|"dBASE IV;"|" `drive` : \\ \  *path*"|
|dBASE 5|"dBASE 5.0;"|" `drive` : \\ \  *path*"|
|Paradox 3(sp3)|"Paradox 3.x;"|" `drive` : \\ \  *path*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive` : \\ \  *path*"|
|Paradox .x|"Paradox 5.x;"|" `drive` : \\ \  *path*"|
|Excel 3.0|"Excel 3.0;"|" `drive` : \\ \  *경로* \\ \  *파일 이름* 입니다. X|
|Excel 4.0|"Excel 4.0;"|" `drive` : \\ \  *경로* \\ \  *파일 이름* 입니다. X|
|Excel 5.0 또는 Excel 95|"Excel 5.0;"|" `drive` : \\ \  *경로* \\ \  *파일 이름* 입니다. X|
|Excel 97|"Excel 8.0;"|" `drive` : \\ \  *경로* \  *파일 이름* 입니다. X|
|HTML 가져오기|"HTML 가져오기"|" `drive` : \\ \  *경로* \  *파일 이름*"|
|HTML 내보내기|"HTML 내보내기;"|" `drive` : \\ \  *path*"|
|텍스트|"텍스트;"|"drive: \\ \path"|
|ODBC|DB 데이터베이스 = `database` ; UID = *user*; PWD = *password*; DSN = *datasourcename;* LOGINTIMEOUT = *초;*" 이는 모든 서버에 대 한 완전 한 연결 문자열이 아닐 수 있습니다. 단지 예입니다. 매개 변수 사이에 공백을 포함 하지 않는 것이 중요 합니다.|없음|
|Exchange|교환의<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [프로필 = *프로필*;]<br /><br /> [PWD = *password*;]<br /><br /> [DATABASE = `database` ;] "|*"드라이브*: \\ \  *경로* \\ \  *파일 이름* 입니다. 않았더라도|

> [!NOTE]
> Btrieve는 DAO 3.5에서 더 이상 지원 되지 않습니다.

\\연결 문자열에서 이중 백슬래시 ()를 사용 해야 합니다 \\ . 를 사용 하 여 기존 연결의 속성을 수정한 경우 `SetConnect` 에는 [refreshlink](#refreshlink)를 호출 해야 합니다. 를 사용 하 여 연결 속성을 초기화 하는 경우에는를 `SetConnect` 호출할 필요가 `RefreshLink` 없지만 먼저 테이블 정의를 추가 해야 합니다.

암호가 필요 하지만 제공 되지 않은 경우 ODBC 드라이버는 테이블에 처음 액세스할 때 로그인 대화 상자를 표시 하 고 연결을 닫은 후 다시 열 때 다시 열 수 있습니다.

`CDaoTableDef`멤버 함수에 소스 인수를 제공 하 여 개체에 대 한 연결 문자열을 설정할 수 있습니다 `Create` . 데이터베이스의 유형, 경로, 사용자 ID, 암호 또는 ODBC 데이터 원본을 결정 하는 설정을 확인할 수 있습니다. 자세한 내용은 특정 드라이버에 대 한 설명서를 참조 하세요.

관련 내용은 DAO 도움말의 "연결 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefsetname"></a><a name="setname"></a> CDaoTableDef:: SetName

이 멤버 함수를 호출 하 여 테이블에 대 한 사용자 정의 이름을 설정 합니다.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
테이블의 이름을 지정 하는 문자열 식에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이름은 문자로 시작 해야 하며 최대 64 자를 포함할 수 있습니다. 숫자 및 밑줄 문자를 포함할 수 있지만 문장 부호 또는 공백을 포함할 수 없습니다.

관련 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a> CDaoTableDef:: SetSourceTableName

이 멤버 함수를 호출 하 여 `CDaoTableDef` 데이터의 원래 원본에 있는 것과 같이 개체가 기반으로 하는 기본 테이블의 이름 또는 연결 된 테이블의 이름을 지정 합니다.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>매개 변수

*lpszSrcTableName*<br/>
외부 데이터베이스의 테이블 이름을 지정 하는 문자열 식에 대 한 포인터입니다. 기본 테이블의 경우이 설정은 빈 문자열 ("")입니다.

### <a name="remarks"></a>설명

그런 다음 [Refreshlink](#refreshlink)를 호출 해야 합니다. 이 속성 설정은 기본 테이블에 대해서는 비어 있고 연결 된 테이블의 경우 읽기/쓰기 또는 컬렉션에 추가 되지 않은 개체의 경우에는 비어 있습니다.

관련 내용은 DAO 도움말의 "SourceTableName 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a> CDaoTableDef:: SetValidationRule

이 멤버 함수를 호출 하 여 테이블 정의에 대 한 유효성 검사 규칙을 설정 합니다.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>매개 변수

*lpszValidationRule*<br/>
작업의 유효성을 검사 하는 문자열 식에 대 한 포인터입니다.

### <a name="remarks"></a>설명

유효성 검사 규칙은 업데이트 작업에 연결 하는 데 사용 됩니다. 테이블 정의에 유효성 검사 규칙이 포함 된 경우 해당 테이블 정의에 대 한 업데이트는 데이터를 변경 하기 전에 미리 결정 된 조건과 일치 해야 합니다. 변경 내용이 조건과 일치 하지 않으면 [GetValidationText](#getvalidationtext) 텍스트를 포함 하는 예외가 표시 됩니다.

유효성 검사는 Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스에 대해서만 지원 됩니다. 식은 사용자 정의 함수, 도메인 집계 함수, SQL 집계 함수 또는 쿼리를 참조할 수 없습니다. 개체에 대 한 유효성 검사 규칙은 `CDaoTableDef` 해당 개체에서 여러 필드를 참조할 수 있습니다.

예를 들어 *hire_date* 및 *termination_date* 라는 필드의 경우 유효성 검사 규칙은 다음과 같을 수 있습니다.

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

관련 내용은 DAO 도움말의 "ValidationRule 속성" 항목을 참조 하십시오.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a> CDaoTableDef::SetValidationText

`CDaoTableDef`Microsoft Jet 데이터베이스 엔진에서 지 원하는 기본 테이블을 사용 하 여 개체에 대 한 유효성 검사 규칙의 예외 텍스트를 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>매개 변수

*lpszValidationText*<br/>
입력 한 데이터가 잘못 된 경우 표시 되는 텍스트를 지정 하는 문자열 식에 대 한 포인터입니다.

### <a name="remarks"></a>설명

연결 된 테이블의 유효성 검사 텍스트는 설정할 수 없습니다.

관련 내용은 DAO 도움말의 "ValidationText 속성" 항목을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 클래스](../../mfc/reference/cdaorecordset-class.md)
