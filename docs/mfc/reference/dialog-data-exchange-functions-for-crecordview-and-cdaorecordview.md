---
description: '자세히 알아보기: CRecordView 및 CDaoRecordView에 대 한 대화 상자 데이터 교환 함수'
title: CRecordView 및 CDaoRecordView에 대한 대화 상자 데이터 교환 함수
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 9b149c3cdc05bf63f69b94bbcaf084a84ec42a84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220034"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 및 CDaoRecordView에 대한 대화 상자 데이터 교환 함수

이 항목에서는 [CRecordset](../../mfc/reference/crecordset-class.md) 와 [CRecordView](../../mfc/reference/crecordview-class.md) 폼 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 와 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 폼 간에 데이터를 교환 하는 데 사용 되는 DDX_Field 함수를 나열 합니다. DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

> [!NOTE]
> DDX_Field 함수는 폼의 컨트롤과 데이터를 교환 한다는 점에서 DDX 함수와 비슷합니다. 그러나 DDX와는 달리 레코드 뷰 자체의 필드가 아니라 뷰의 관련 레코드 집합 개체 필드와 데이터를 교환 합니다. 자세한 내용은 클래스 및을 참조 `CRecordView` 하십시오 `CDaoRecordView` .

### <a name="ddx_field-functions"></a>DDX_Field 함수

|Name|설명|
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)의 콤보 상자에서 레코드 집합 필드 데이터 멤버와 현재 선택 항목의 인덱스 사이에 정수 데이터를 전송 합니다.|
|[DDX_FieldCBString](#ddx_fieldcbstring)|`CString`또는에서 콤보 상자의 편집 컨트롤 및 레코드 집합 필드 데이터 멤버 간에 데이터를 전송 `CRecordView` `CDaoRecordView` 합니다. 데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 지정 된 문자열의 문자로 시작 하는 콤보 상자에서 항목을 선택 합니다.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|`CString`또는에서 콤보 상자의 편집 컨트롤 및 레코드 집합 필드 데이터 멤버 간에 데이터를 전송 `CRecordView` `CDaoRecordView` 합니다. 데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 지정 된 문자열과 정확히 일치 하는 콤보 상자에서 항목을 선택 합니다.|
|[DDX_FieldCheck](#ddx_fieldcheck)|또는의 레코드 집합 필드 데이터 멤버와 확인란 간에 부울 데이터를 전송 `CRecordView` `CDaoRecordView` 합니다.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|또는의 목록 상자에서 레코드 집합 필드 데이터 멤버와 현재 선택 항목의 인덱스 간에 정수 데이터를 전송 `CRecordView` `CDaoRecordView` 합니다.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|목록 상자 컨트롤과 레코드 집합의 필드 데이터 멤버 간에 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 데이터의 전송을 관리 합니다. 데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 지정 된 문자열의 문자로 시작 하는 목록 상자에서 항목을 선택 합니다.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|`CString`목록 상자 컨트롤과 레코드 집합의 필드 데이터 멤버 간 데이터 전송을 관리 합니다. 데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 지정 된 문자열과 정확히 일치 하는 첫 번째 항목을 선택 합니다.|
|[DDX_FieldRadio](#ddx_fieldradio)|또는에서 레코드 집합 필드 데이터 멤버와 라디오 단추 그룹 간에 정수 데이터를 전송 `CRecordView` `CDaoRecordView` 합니다.|
|[DDX_FieldScroll](#ddx_fieldscroll)|또는에서 스크롤 막대 컨트롤의 스크롤 위치를 설정 하거나 가져옵니다 `CRecordView` `CDaoRecordView` . [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) 함수에서를 호출 합니다.|
|[DDX_FieldSlider](#ddx_fieldslider)|레코드 뷰 및 레코드 **`int`** 집합의 필드 데이터 멤버에서 slider 컨트롤의 thumb 위치를 동기화 합니다. |
|[DDX_FieldText](#ddx_fieldtext)|오버 로드 된 버전은 **`int`**  **`long`** `DWORD` [](../../atl-mfc-shared/reference/cstringt-class.md) **`float`** **`double`** **`short`** 레코드 집합 필드 데이터 멤버와 또는의 편집 상자 사이 [](../../atl-mfc-shared/reference/coledatetime-class.md) [](../../mfc/reference/colecurrency-class.md) 에서 `CRecordView` , UINT,,, CString,,,, COleDateTime 및 COleCurrency 데이터 `CDaoRecordView` 를 전송 하는 데 사용할 수 있습니다.|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a> DDX_FieldCBIndex

`DDX_FieldCBIndex`함수는 레코드 뷰에서 콤보 상자 컨트롤의 목록 상자 컨트롤에 있는 선택 된 항목의 인덱스와 **`int`** 레코드 뷰와 연결 된 레코드 집합의 필드 데이터 멤버를 동기화 합니다.

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*index*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 *인덱스* 에 지정 된 값에 따라 컨트롤에서 선택 항목을 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 MFC는 인덱스의 값을 0으로 설정 합니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있거나 선택 된 항목이 없는 경우에는 레코드 집합 필드가 0으로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 예는와 유사 `DDX_FieldCBIndex` 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a> DDX_FieldCBString

함수는 레코드 `DDX_FieldCBString` 뷰에서 콤보 상자 [](../../atl-mfc-shared/reference/cstringt-class.md) 컨트롤의 편집 컨트롤과 `CString` 레코드 뷰와 연결 된 레코드 집합의 필드 데이터 멤버 사이에서 CString 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 콤보 상자의 현재 선택 항목을 *값* 에 지정 된 문자열의 문자로 시작 하는 첫 번째 행으로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 모든 선택 항목이 콤보 상자에서 제거 되 고 콤보 상자의 편집 컨트롤은 빈 상태로 설정 됩니다. 컨트롤에서 레코드 집합으로의 전송 시 컨트롤이 비어 있으면 필드에서을 허용 하는 경우 레코드 집합 필드가 Null로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 이 예제에는에 대 한 호출이 포함 되어 `DDX_FieldCBString` 있습니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a> DDX_FieldCBStringExact

함수는 레코드 `DDX_FieldCBStringExact` 뷰에서 콤보 상자 [](../../atl-mfc-shared/reference/cstringt-class.md) 컨트롤의 편집 컨트롤과 `CString` 레코드 뷰와 연결 된 레코드 집합의 필드 데이터 멤버 사이에서 CString 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 콤보 상자의 현재 선택 항목을 *값* 에 지정 된 문자열과 정확히 일치 하는 첫 번째 행으로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 NULL 이면 모든 선택 항목이 콤보 상자에서 제거 되 고 콤보 상자의 편집 상자는 비어 있는 것으로 설정 됩니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있으면 레코드 집합 필드가 NULL로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 에 대 한 호출은 `DDX_FieldCBStringExact` 유사 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a> DDX_FieldCheck

함수는 대화 `DDX_FieldCheck` **`int`** 상자, 폼 뷰 또는 컨트롤 뷰 개체의 확인란 컨트롤과 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 확인란 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`DDX_FieldCheck`가 호출 되 면 *값* 이 확인란 컨트롤의 현재 상태로 설정 되 고, 전송 방향에 따라 컨트롤의 상태가 *value* 로 설정 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a> DDX_FieldLBIndex

함수는 레코드 `DDX_FieldLBIndex` 뷰의 목록 상자 컨트롤에서 선택한 항목의 인덱스와 **`int`** 레코드 뷰와 연결 된 레코드 집합의 필드 데이터 멤버를 동기화 합니다.

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*index*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 *인덱스* 에 지정 된 값에 따라 컨트롤에서 선택 항목을 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 MFC는 인덱스의 값을 0으로 설정 합니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있으면 레코드 집합 필드가 0으로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a> DDX_FieldLBString

는 레코드 `DDX_FieldLBString` 뷰에서 현재 선택 된 목록 상자 컨트롤을 레코드 뷰와 연결 된 레코드 집합의 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 필드 데이터 멤버에 복사 합니다.

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

반대 방향으로이 함수는 목록 상자에서 현재 선택 영역을 *값* 으로 지정 된 문자열의 문자로 시작 하는 첫 번째 행으로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 모든 선택 항목이 목록 상자에서 제거 됩니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있으면 레코드 집합 필드가 Null로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 에 대 한 호출은 `DDX_FieldLBString` 유사 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a> DDX_FieldLBStringExact

함수는 레코드 `DDX_FieldLBStringExact` 뷰에 있는 목록 상자 컨트롤의 현재 선택 영역을 레코드 뷰와 연결 된 레코드 집합의 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 필드 데이터 멤버에 복사 합니다.

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

반대 방향으로이 함수는 목록 상자에서 현재 선택 영역을 *값* 에 지정 된 문자열과 정확히 일치 하는 첫 번째 행으로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 모든 선택 항목이 목록 상자에서 제거 됩니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있으면 레코드 집합 필드가 Null로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 에 대 한 호출은 `DDX_FieldLBStringExact` 유사 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a> DDX_FieldRadio

함수는 레코드 뷰의 레코드 `DDX_FieldRadio` 집합에서 0부터 시작 하는 **`int`** 멤버 변수를 레코드 뷰의 라디오 단추 그룹에 있는 현재 선택 된 라디오 단추와 연결 합니다.

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 인접 라디오 단추 컨트롤에 대 한 그룹의 첫 번째 (스타일 WS_GROUP) ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

레코드 집합 필드에서 뷰로 전송할 때이 함수는 *n 번째* 라디오 단추 (0부터 시작)를 설정 하 고 다른 단추를 끕니다. 역방향으로이 함수는 레코드 집합 필드를 현재 설정 되어 있는 라디오 단추 (선택)의 서 수로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 단추가 선택 되지 않습니다. 컨트롤에서 레코드 집합으로 전송 하는 경우 컨트롤을 선택 하지 않으면 필드에서 허용 하는 경우 레코드 집합 필드가 Null로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 에 대 한 호출은 `DDX_FieldRadio` 유사 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a> DDX_FieldScroll

함수는 레코드 뷰 `DDX_FieldScroll` 및 레코드 **`int`** 뷰와 연결 된 레코드 집합의 필드 데이터 멤버 (또는이를 매핑하기 위해 선택한 정수 변수)의 스크롤 막대 컨트롤의 스크롤 위치를 동기화 합니다.

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 인접 라디오 단추 컨트롤에 대 한 그룹의 첫 번째 (스타일 WS_GROUP) ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다.

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 집합에서 컨트롤로 데이터를 이동 하는 경우이 함수는 스크롤 막대 컨트롤의 스크롤 위치를 *value* 에 지정 된 값으로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 scroll bar 컨트롤이 0으로 설정 됩니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있으면 레코드 집합 필드의 값은 0입니다.

ODBC 기반 클래스로 작업 하는 경우 첫 번째 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 두 번째 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 에 대 한 호출은 `DDX_FieldScroll` 유사 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a> DDX_FieldSlider

함수는 레코드 뷰 `DDX_FieldSlider` 및 레코드 **`int`** 뷰와 연결 된 레코드 집합의 필드 데이터 멤버 (또는 매핑할 정수 변수)에 있는 슬라이더 컨트롤의 thumb 위치를 동기화 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
슬라이더 컨트롤의 리소스 ID입니다.

*value*<br/>
교환할 값에 대 한 참조입니다. 이 매개 변수는 슬라이더 컨트롤의 현재 엄지 단추를 포함 하거나 설정 하는 데 사용 됩니다.

*pRecordset*<br/>
데이터를 교환 하는 데 사용 되는 연결 된 또는 개체에 대 한 포인터 `CRecordset` `CDaoRecordset` 입니다.

### <a name="remarks"></a>설명

데이터 집합의 데이터를 슬라이더로 이동 하는 경우이 함수는 슬라이더의 위치를 *value* 에 지정 된 값으로 설정 합니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 slider 컨트롤의 위치는 0으로 설정 됩니다. 컨트롤에서 레코드 집합으로의 전송 시 컨트롤이 비어 있으면 레코드 집합 필드의 값은 0입니다.

`DDX_FieldSlider` 는 범위 정보를 단순히 위치가 아닌 범위를 설정할 수 있는 슬라이더 컨트롤을 사용 하 여 교환 하지 않습니다.

ODBC 기반 클래스로 작업 하는 경우 함수의 첫 번째 재정의를 사용 합니다. DAO 기반 클래스에 두 번째 재정의를 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../dialog-data-exchange-and-validation.md)를 참조하세요. 및 필드의 DDX에 대 한 예제 및 자세한 내용은 `CRecordView` `CDaoRecordView` [레코드 뷰](../../data/record-views-mfc-data-access.md)를 참조 하세요. 슬라이더 컨트롤에 대 한 자세한 내용은 [CSliderCtrl 사용](../using-csliderctrl.md)을 참조 하세요.

### <a name="example"></a>예제

일반적인 DDX_Field 예제는 [DDX_FieldText](#ddx_fieldtext) 를 참조 하세요. 에 대 한 호출은 `DDX_FieldSlider` 유사 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a> DDX_FieldText

`DDX_FieldText`함수는 **`int`** **`short`** **`long`** [](../../atl-mfc-shared/reference/cstringt-class.md) **`float`** **`double`** 편집 상자 컨트롤과 레코드 집합의 필드 데이터 멤버 사이에서,,, DWORD, CString,,, **BOOL** 또는 **BYTE** 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md) 또는 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 개체의 컨트롤 ID입니다.

*value*<br/>
연결 된 또는 개체의 필드 데이터 멤버에 대 한 참조 `CRecordset` `CDaoRecordset` 입니다. 값의 데이터 형식은 사용 하는 오버 로드 된 버전에 따라 다릅니다 `DDX_FieldText` .

*pRecordset*<br/>
데이터를 교환 하는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체에 대 한 포인터입니다. 이 포인터는 `DDX_FieldText` 를 사용 하 여 Null 값을 검색 하 고 설정할 수 있습니다.

### <a name="remarks"></a>설명

[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체의 경우는 `DDX_FieldText` [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)및 [COleCurrency](../../mfc/reference/colecurrency-class.md) 값의 전송도 관리 합니다. 빈 편집 상자 컨트롤은 Null 값을 나타냅니다. 레코드 집합에서 컨트롤로 전송할 때 레코드 집합 필드가 Null 이면 편집 상자는 비어 있는 것으로 설정 됩니다. 컨트롤에서 레코드 집합으로의 전송에서 컨트롤이 비어 있으면 레코드 집합 필드가 Null로 설정 됩니다.

ODBC 기반 클래스로 작업 하는 경우 [CRecordset](../../mfc/reference/crecordset-class.md) 매개 변수가 있는 버전을 사용 합니다. DAO 기반 클래스로 작업 하는 경우 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 매개 변수가 있는 버전을 사용 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. [CRecordView](../../mfc/reference/crecordview-class.md) 및 [CDAORECORDVIEW](../../mfc/reference/cdaorecordview-class.md) 필드의 DDX에 대 한 예제 및 자세한 내용은 [레코드 뷰](../../data/record-views-mfc-data-access.md)문서를 참조 하세요.

### <a name="example"></a>예제

[CRecordView](../../mfc/reference/crecordview-class.md)에 대한 다음 `DoDataExchange`함수는 세 개의 데이터 형식에 대한 `DDX_FieldText` 함수 호출을 포함합니다. `IDC_COURSELIST`는 콤보 상자이며 다른 두 컨트롤은 편집 상자입니다. DAO 프로그래밍의 경우 *m_pSet* 매개 변수는 [CRecordset](../../mfc/reference/crecordset-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)에 대 한 포인터입니다.

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)
