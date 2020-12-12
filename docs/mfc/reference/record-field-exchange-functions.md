---
description: '자세히 알아보기: 레코드 필드 교환 함수'
title: 레코드 필드 교환 함수
ms.date: 09/17/2019
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
ms.openlocfilehash: 2ba3a83bdda21f91913d7eda435a845b0977e8a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218955"
---
# <a name="record-field-exchange-functions"></a>레코드 필드 교환 함수

이 항목에서는 레코드 집합 개체와 해당 데이터 소스 간의 데이터 전송을 자동화하고 데이터에 대한 다른 작업을 수행하는 데 사용되는 레코드 필드 교환(RFX, 대량 RFX, 및 DFX) 함수를 나열합니다.

ODBC 기반 클래스를 사용하고 대량 행 페치를 구현한 경우 데이터 소스 열에 해당하는 각 데이터 멤버에 대해 대량 RFX 함수를 호출하여 `DoBulkFieldExchange` 의 `CRecordset` 멤버 함수를 수동으로 재정의해야 합니다.

ODBC 기반 클래스에서 대량 행 페치를 구현 하지 않았거나 DAO 기반 클래스 (사용 되지 않음)를 사용 하는 경우에는 클래스 마법사가 `DoFieldExchange` `CRecordset` `CDaoRecordset` 레코드 집합의 각 필드 데이터 멤버에 대해 RFX 함수 (ODBC 클래스의 경우) 또는 DFX 함수 (DAO 클래스의 경우)를 호출 하 여 또는의 멤버 함수를 재정의 합니다.

레코드 필드 교환 함수는 프레임워크에서 `DoFieldExchange` 또는 `DoBulkFieldExchange`를 호출할 때마다 데이터를 전송합니다. 각 함수는 특정 데이터 형식을 전송합니다.

이러한 함수의 사용 방법에 대한 자세한 내용은 [레코드 필드 교환: RFX 작동 방식(ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.

동적으로 바인딩하는 데이터 열의 경우 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)문서에 설명된 대로 RFX 또는 DFX 함수를 직접 호출할 수도 있습니다. 또한 Technical Note [43](../../mfc/tn043-rfx-routines.md) (ODBC) 및 Technical Note [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (DAO)에 설명된 대로 사용자 고유의 사용자 지정 RFX 또는 DFX 루틴을 작성할 수 있습니다.

및 함수에 표시 되는 RFX 및 대량 RFX 함수에 대 한 예제는 `DoFieldExchange` `DoBulkFieldExchange` [RFX_Text](#rfx_text) 및 [RFX_Text_Bulk] #rfx_text_bulk)를 참조 하세요. DFX 함수는 RFX 함수와 매우 유사합니다.

### <a name="rfx-functions-odbc"></a>RFX 함수(ODBC)

|Name|설명|
|-|-|
|[RFX_Binary](#rfx_binary)|[CByteArray](cbytearray-class.md)형식의 바이트 배열을 전송합니다.|
|[RFX_Bool](#rfx_bool)|부울 데이터를 전송합니다.|
|[RFX_Byte](#rfx_byte)|단일 바이트 데이터를 전송합니다.|
|[RFX_Date](#rfx_date)|[CTime](../../atl-mfc-shared/reference/ctime-class.md) 또는 TIMESTAMP_STRUCT를 사용 하 여 시간 및 날짜 데이터를 전송 합니다.|
|[RFX_Double](#rfx_double)|배정밀도 부동 소수점 수 데이터를 전송합니다.|
|[RFX_Int](#rfx_int)|정수 데이터를 전송합니다.|
|[RFX_Long](#rfx_long)|정수(Long) 데이터를 전송합니다.|
|[RFX_LongBinary](#rfx_longbinary)|[CLongBinary](clongbinary-class.md) 클래스의 개체와 함께 BLOB(Binary Large Object) 데이터를 전송합니다.|
|[RFX_Single](#rfx_single)|부동 소수점 수 데이터를 전송합니다.|
|[RFX_Text](#rfx_text)|문자열 데이터를 전송합니다.|

### <a name="bulk-rfx-functions-odbc"></a>대량 RFX 함수(ODBC)

|Name|설명|
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|바이트 데이터 배열을 전송합니다.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|부울 데이터 배열을 전송합니다.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|단일 바이트 배열을 전송합니다.|
|[RFX_Date_Bulk](#rfx_date_bulk)|TIMESTAMP_STRUCT 형식의 데이터 배열을 전송합니다.|
|[RFX_Double_Bulk](#rfx_double_bulk)|배정밀도 부동 소수점 데이터 배열을 전송합니다.|
|[RFX_Int_Bulk](#rfx_int_bulk)|정수 데이터 배열을 전송합니다.|
|[RFX_Long_Bulk](#rfx_long_bulk)|정수(Long) 데이터 배열을 전송합니다.|
|[RFX_Single_Bulk](#rfx_single_bulk)|부동 소수점 데이터 배열을 전송합니다.|
|[RFX_Text_Bulk](#rfx_text_bulk)|LPSTR 형식의 데이터 배열을 전송합니다.|

### <a name="dfx-functions-dao"></a>DFX 함수(DAO)

|Name|설명|
|-|-|
|[DFX_Binary](#dfx_binary)|[CByteArray](cbytearray-class.md)형식의 바이트 배열을 전송합니다.|
|[DFX_Bool](#dfx_bool)|부울 데이터를 전송합니다.|
|[DFX_Byte](#dfx_byte)|단일 바이트 데이터를 전송합니다.|
|[DFX_Currency](#dfx_currency)|[COleCurrency](colecurrency-class.md)형식의 통화 데이터를 전송합니다.|
|[DFX_DateTime](#dfx_datetime)|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)형식의 날짜 및 시간 데이터를 전송합니다.|
|[DFX_Double](#dfx_double)|배정밀도 부동 소수점 수 데이터를 전송합니다.|
|[DFX_Long](#dfx_long)|정수(Long) 데이터를 전송합니다.|
|[DFX_LongBinary](#dfx_longbinary)|`CLongBinary` 클래스의 개체와 함께 BLOB(Binary Large Object) 데이터를 전송합니다. DAO의 경우 대신 [DFX_Binary](#dfx_binary) 를 사용하는 것이 좋습니다.|
|[DFX_Short](#dfx_short)|정수(Short) 데이터를 전송합니다.|
|[DFX_Single](#dfx_single)|부동 소수점 수 데이터를 전송합니다.|
|[DFX_Text](#dfx_text)|문자열 데이터를 전송합니다.|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a> RFX_Binary

개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드 열 (SQL_BINARY, SQL_VARBINARY 또는 SQL_LONGVARBINARY 사이의 바이트 배열을 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 지정 된 데이터 멤버에서 [CByteArray](cbytearray-class.md)형식의 값을 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*nMaxLength*<br/>
전송 되는 문자열 또는 배열의 최대 허용 길이입니다. *Nmaxlength* 의 기본값은 255입니다. 올바른 값은 1 INT_MAX입니다. 프레임 워크는 데이터에이 크기의 공간을 할당 합니다. 최상의 성능을 위해 원하는 가장 큰 데이터 항목을 수용할 만큼 충분히 큰 값을 전달 합니다.

### <a name="remarks"></a>설명

이러한 형식의 데이터 원본에 있는 데이터는 레코드 집합의 형식에 매핑됩니다 `CByteArray` .

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_bool"></a><a name="rfx_bool"></a> RFX_Bool

개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드의 열 간에 부울 데이터를 전송 SQL_BIT 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 BOOL 형식의 값은 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_byte"></a><a name="rfx_byte"></a> RFX_Byte

는 개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드의 열 간에 단일 바이트를 전송 SQL_TINYINT 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 소스로 전송하기 위해 BYTE 형식의 값을 지정된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_date"></a><a name="rfx_date"></a> RFX_Date

`CTime`개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 유형의 데이터 원본에 있는 레코드의 열 SQL_DATE, SQL_TIME 또는 SQL_TIMESTAMP 간에 데이터를 전송 하거나 TIMESTAMP_STRUCT 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시 된 데이터 멤버에 저장 된 값입니다. 전송할 값입니다. 함수의 다양 한 버전은 값에 대해 서로 다른 데이터 형식을 사용 합니다.

함수의 첫 번째 버전은 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체에 대 한 참조를 사용 합니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우이 값은 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

함수의 두 번째 버전은 구조체에 대 한 참조를 사용 합니다 `TIMESTAMP_STRUCT` . 이 구조는 호출 전에 직접 설정 해야 합니다. 이 버전에서는 DDX (대화 상자 데이터 교환) 지원 및 코드 마법사 지원도 모두 사용할 수 있습니다. 함수의 세 번째 버전은 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 대 한 참조를 사용 한다는 점을 제외 하 고 첫 번째 버전과 유사 하 게 작동 합니다.

### <a name="remarks"></a>설명

`CTime`함수의 버전은 일부 중간 처리의 오버 헤드를 적용 하며 범위는 약간 제한 됩니다. 이러한 요인 중 하나를 너무 제한 하는 경우 함수의 두 번째 버전을 사용 합니다. 그러나 코드 마법사와 DDX를 지원 하지 않으며 구조를 직접 설정 하는 요구 사항을 기억해 야 합니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_double"></a><a name="rfx_double"></a> RFX_Double

개체  의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드의 열 간에 이중 float 데이터를 전송 SQL_DOUBLE 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`double`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_int"></a><a name="rfx_int"></a> RFX_Int

개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드의 열 간에 정수 데이터를 전송 SQL_SMALLINT 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`int`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_long"></a><a name="rfx_long"></a> RFX_Long

개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드의 열 간에 정수 (long) 데이터를 전송 하는 SQL_INTEGER 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`long`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a> RFX_LongBinary

는 클래스 [CLongBinary](clongbinary-class.md) 를 사용 하 여 BLOB (binary large object) 데이터를 전송 합니다 .이 데이터는 개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드 열 SQL_LONGVARBINARY 또는 SQL_LONGVARCHAR 사이에서 전송 됩니다.

### <a name="syntax"></a>구문

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 `CLongBinary` 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_single"></a><a name="rfx_single"></a> RFX_Single

개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드 열 간에 부동 소수점 데이터를 전송 SQL_REAL 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`float`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_text"></a><a name="rfx_text"></a> RFX_Text

`CString`는 개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 유형의 데이터 원본에 있는 레코드의 열 SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL 또는 SQL_NUMERIC 간에 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
클래스의 개체에 대 한 포인터 `CFieldExchange` 입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 `CString` 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*nMaxLength*<br/>
전송 되는 문자열 또는 배열의 최대 허용 길이입니다. *Nmaxlength* 의 기본값은 255입니다. 올바른 값은 1에서 INT_MAX)입니다. 프레임 워크는 데이터에이 크기의 공간을 할당 합니다. 최상의 성능을 위해 원하는 가장 큰 데이터 항목을 수용할 만큼 충분히 큰 값을 전달 합니다.

*nColumnType*<br/>
주로 매개 변수에 사용 됩니다. 매개 변수의 데이터 형식을 나타내는 정수입니다. 형식은 **SQL_XXX** 형식의 ODBC 데이터 형식입니다.

*nScale*<br/>
ODBC 유형 SQL_DECIMAL 또는 SQL_NUMERIC의 값에 대 한 소수 자릿수를 지정 합니다. *Nscale* 은 매개 변수 값을 설정할 때만 유용 합니다. 자세한 내용은 *ODBC SDK 프로그래머 참조* 의 부록 D에서 "전체 자릿수, 소수 자릿수, 길이 및 표시 크기" 항목을 참조 하세요.

### <a name="remarks"></a>설명

이러한 모든 형식의 데이터 원본에 있는 데이터는 레코드 집합의 및에서 매핑됩니다 `CString` .

### <a name="example"></a>예제

이 예제에서는에 대 한 여러 호출을 보여 줍니다 `RFX_Text` . 또한에 대 한 두 호출을 살펴봅니다 `CFieldExchange::SetFieldType` . 매개 변수의 경우에 대 한 호출과 해당 RFX 호출을 작성 해야 합니다 `SetFieldType` . 출력 열 호출 및 연결 된 RFX 호출은 일반적으로 코드 마법사를 통해 작성 됩니다.

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a> RFX_Binary_Bulk

ODBC 데이터 원본 열에서 파생 개체의 해당 배열에 바이트 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgByteVals*<br/>
바이트 값 배열에 대 한 포인터입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgByteVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

*nMaxLength*<br/>
*PrgByteVals* 가 가리키는 배열에 저장 된 값의 최대 허용 길이입니다. 데이터가 잘리지 않도록 하려면 원하는 가장 큰 데이터 항목을 수용할 만큼 충분히 큰 값을 전달 합니다.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 형식의 SQL_BINARY, SQL_VARBINARY 또는 SQL_LONGVARBINARY 있을 수 있습니다. 레코드 집합은 포인터 형식의 필드 데이터 멤버를 BYTE로 정의 해야 합니다.

*PrgByteVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a> RFX_Bool_Bulk

ODBC 데이터 원본 열에서 파생 개체의 해당 배열에 부울 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgBoolVals*<br/>
BOOL 값 배열에 대 한 포인터입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgBoolVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 유형 SQL_BIT 있어야 합니다. 레코드 집합은 포인터 형식의 필드 데이터 멤버를 BOOL로 정의 해야 합니다.

*PrgBoolVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a> RFX_Byte_Bulk

ODBC 데이터 원본 열에서 파생 개체의 해당 배열에 단일 바이트의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgByteVals*<br/>
바이트 값 배열에 대 한 포인터입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgByteVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 유형 SQL_TINYINT 있어야 합니다. 레코드 집합은 포인터 형식의 필드 데이터 멤버를 BYTE로 정의 해야 합니다.

*PrgByteVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a> RFX_Date_Bulk

ODBC 데이터 원본 열에서 파생 개체의 해당 배열에 TIMESTAMP_STRUCT 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgTSVals*<br/>
TIMESTAMP_STRUCT 값 배열에 대 한 포인터입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다. TIMESTAMP_STRUCT 데이터 형식에 대 한 자세한 내용은 *ODBC SDK 프로그래머 참조* 의 부록 D에서 "C 데이터 형식" 항목을 참조 하세요.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgTSVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 형식의 SQL_DATE, SQL_TIME 또는 SQL_TIMESTAMP 있을 수 있습니다. 레코드 집합은 TIMESTAMP_STRUCT 포인터 형식의 필드 데이터 멤버를 정의 해야 합니다.

*PrgTSVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a> RFX_Double_Bulk

ODBC 데이터 원본의 열에서 파생 된 개체의 해당 배열까지 배정밀도 부동 소수점 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgDblVals*<br/>
값 배열에 대 한 포인터 **`double`** 입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgDblVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 유형 SQL_DOUBLE 있어야 합니다. 레코드 집합은 포인터 형식의 필드 데이터 멤버를로 정의 해야 합니다 **`double`** .

*PrgDblVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a> RFX_Int_Bulk

개체의 필드 데이터 멤버 `CRecordset` 와 ODBC 형식의 데이터 원본에 있는 레코드의 열 간에 정수 데이터를 전송 SQL_SMALLINT 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 개체가 지정할 수 있는 작업에 대 한 자세한 내용은 `CFieldExchange` [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`int`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

### <a name="example"></a>예제

[RFX_Text](#rfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a> RFX_Long_Bulk

ODBC 데이터 원본의 열에서 파생 개체의 해당 배열까지 long 정수 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgLongVals*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgLongVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 유형 SQL_INTEGER 있어야 합니다. 레코드 집합은 포인터 형식의 필드 데이터 멤버를로 정의 해야 합니다 **`long`** .

*PrgLongVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a> RFX_Single_Bulk

ODBC 데이터 원본의 열에서 파생 개체의 해당 배열에 부동 소수점 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgFltVals*<br/>
값 배열에 대 한 포인터 **`float`** 입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgFltVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 유형 SQL_REAL 있어야 합니다. 레코드 집합은 포인터 형식의 필드 데이터 멤버를로 정의 해야 합니다 **`float`** .

*PrgFltVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

[RFX_Text_Bulk](#rfx_text_bulk)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a> RFX_Text_Bulk

ODBC 데이터 원본 열에서 파생 개체의 해당 배열에 문자 데이터의 여러 행을 전송 `CRecordset` 합니다.

### <a name="syntax"></a>구문

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CFieldExchange](cfieldexchange-class.md) 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조 하세요.

*szName*<br/>
데이터 열의 이름입니다.

*prgStrVals*<br/>
LPSTR 값 배열에 대 한 포인터입니다. 이 배열은 데이터 원본에서 레코드 집합으로 전송 될 데이터를 저장 합니다. 최신 버전의 ODBC를 사용 하는 경우 이러한 값은 유니코드로 설정할 수 없습니다.

*prgLengths*<br/>
Long 정수 배열에 대 한 포인터입니다. 이 배열은 *prgStrVals* 가 가리키는 배열에 있는 각 값의 길이 (바이트)를 저장 합니다. 이 길이는 null 종결 문자를 제외 합니다. 해당 데이터 항목에 Null 값이 포함 되어 있으면 SQL_NULL_DATA 값이 저장 됩니다. 자세한 내용은 `SQLBindCol` *Odbc SDK 프로그래머 참조* 의 odbc API 함수를 참조 하세요.

*nMaxLength*<br/>
Null 종결 문자를 포함 하 여 *prgStrVals* 가 가리키는 배열에 저장 된 값의 최대 허용 길이입니다. 데이터가 잘리지 않도록 하려면 원하는 가장 큰 데이터 항목을 수용할 만큼 충분히 큰 값을 전달 합니다.

### <a name="remarks"></a>설명

데이터 원본 열에는 ODBC 형식의 SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL 또는 SQL_NUMERIC 있을 수 있습니다. 레코드 집합은 LPSTR 형식의 필드 데이터 멤버를 정의 해야 합니다.

*PrgStrVals* 및 *prgLengths* 를 NULL로 초기화 하면 해당 배열이 가리키는 배열이 자동으로 할당 되며, 크기는 행 집합 크기와 같습니다.

> [!NOTE]
> 대량 레코드 필드 교환은 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 합니다 `SQLSetPos` .

자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [레코드 필드 교환 (RFX)](../../data/odbc/record-field-exchange-rfx.md)문서를 참조 하세요.

### <a name="example"></a>예제

재정의에서 수동으로 호출을 작성 해야 합니다 `DoBulkFieldExchange` . 이 예제에서는 `RFX_Text_Bulk` `RFX_Long_Bulk` 데이터 전송에 대 한 호출 뿐만 아니라에 대 한 호출을 보여 줍니다. 이러한 호출은 앞에 [CFieldExchange:: SetFieldType](cfieldexchange-class.md#setfieldtype)를 호출 합니다. 매개 변수의 경우 대량 RFX 함수 대신 RFX 함수를 호출 해야 합니다.

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="dfx_binary"></a><a name="dfx_binary"></a> DFX_Binary

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 사이에 바이트 배열을 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 지정 된 데이터 멤버에서 [CByteArray](cbytearray-class.md)형식의 값을 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*nPreAllocSize*<br/>
프레임 워크는이 크기의 메모리를 사전에 할당 합니다. 데이터가 더 큰 경우 프레임 워크에서 필요에 따라 더 많은 공간을 할당 합니다. 성능을 향상 시키려면이 크기를 재할당을 방지 하기에 충분히 큰 값으로 설정 합니다. 기본 크기는 AFXDAO에서 정의 됩니다. H 파일 AFX_DAO_BINARY_DEFAULT_SIZE입니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_DISABLE_FIELD_CACHE는 이중 버퍼링을 사용 하지 않으므로 [SetFieldDirty](cdaorecordset-class.md#setfielddirty) 및 [SetFieldNull](cdaorecordset-class.md#setfieldnull) 를 직접 호출 해야 합니다. 가능한 다른 값인 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 하며, 필드를 변경 하거나 Null로 표시 하기 위해 추가 작업을 수행할 필요가 없습니다. 성능 및 메모리의 이유로 이진 데이터가 비교적 작은 경우가 아니면이 값을 사용 하지 마십시오.

> [!NOTE]
> 기본적으로 [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)를 설정 하 여 모든 필드에 대 한 데이터를 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

DAO의 형식 DAO_BYTES 간에 데이터가 매핑되고 레코드 집합에 [CByteArray](cbytearray-class.md) 형식이 있습니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_bool"></a><a name="dfx_bool"></a> DFX_Bool

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 부울 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 BOOL 형식의 값은 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

데이터는 DAO의 형식 DAO_BOOL 사이에 매핑되고 레코드 집합에서 BOOL 형식으로 매핑됩니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_byte"></a><a name="dfx_byte"></a> DFX_Byte

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 단일 바이트를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 소스로 전송하기 위해 BYTE 형식의 값을 지정된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

데이터는 DAO의 DAO_BYTES 형식과 레코드 집합의 BYTE 형식 사이에 매핑됩니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_currency"></a><a name="dfx_currency"></a> DFX_Currency

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 통화 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우이 값은 [COleCurrency](colecurrency-class.md)형식의 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

DAO의 형식 DAO_CURRENCY 간에 데이터가 매핑되고 레코드 집합에 [COleCurrency](colecurrency-class.md) 형식이 있습니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a> DFX_DateTime

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 시간 및 날짜 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 함수는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 대 한 참조를 사용 합니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우이 값은 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

DAO의 형식 DAO_DATE 간에 데이터가 매핑되고 레코드 집합에 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 형식이 있습니다.

> [!NOTE]
> `COleDateTime` DAO 클래스에서이 목적에 대 한 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 및 TIMESTAMP_STRUCT를 대체 합니다. `CTime` 및 TIMESTAMP_STRUCT은 여전히 ODBC 기반 데이터 액세스 클래스에 사용 됩니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_double"></a><a name="dfx_double"></a> DFX_Double

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 **이중 float** 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`double`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

DAO의 형식 DAO_R8 간에 데이터가 매핑되고 레코드 집합에 **double float** 형식이 있습니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_long"></a><a name="dfx_long"></a> DFX_Long

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 정수 (long) 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`long`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

데이터는 DAO의 형식 DAO_I4와 **`long`** 레코드 집합의 형식 간에 매핑됩니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a> DFX_LongBinary

**중요** 이 함수 대신 [DFX_Binary](#dfx_binary) 를 사용 하는 것이 좋습니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 지정 된 데이터 멤버에서 [CLongBinary](clongbinary-class.md)형식의 값을 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwPreAllocSize*<br/>
프레임 워크는이 크기의 메모리를 사전에 할당 합니다. 데이터가 더 큰 경우 프레임 워크에서 필요에 따라 더 많은 공간을 할당 합니다. 성능을 향상 시키려면이 크기를 재할당을 방지 하기에 충분히 큰 값으로 설정 합니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DISABLE_FIELD_CACHE는 이중 버퍼링을 사용 하지 않습니다. 다른 가능한 값은 AFX_DAO_ENABLE_FIELD_CACHE입니다. 에서는 이중 버퍼링을 사용 하며, 필드를 변경 하거나 Null로 표시 하기 위해 추가 작업을 수행할 필요가 없습니다. 성능 및 메모리의 이유로 이진 데이터가 비교적 작은 경우가 아니면이 값을 사용 하지 마십시오.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

`DFX_LongBinary` 는 MFC ODBC 클래스와의 호환성을 위해 제공 됩니다. `DFX_LongBinary`함수는 `CLongBinary` [CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 클래스를 사용 하 여 BLOB (binary large object) 데이터를 전송 합니다. DAO의 형식 DAO_BYTES 간에 데이터가 매핑되고 레코드 집합에 [CLongBinary](clongbinary-class.md) 형식이 있습니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_short"></a><a name="dfx_short"></a> DFX_Short

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 short 정수 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`short`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

데이터는 DAO의 형식 DAO_I2와 **`short`** 레코드 집합의 형식 간에 매핑됩니다.

> [!NOTE]
> `DFX_Short` 는 ODBC 기반 클래스의 [RFX_Int](#rfx_int) 와 동일 합니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_single"></a><a name="dfx_single"></a> DFX_Single

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 부동 소수점 데이터를 전송 합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 형식의 값은 **`float`** 지정 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

데이터는 DAO의 형식 DAO_R4와 **`float`** 레코드 집합의 형식 간에 매핑됩니다.

### <a name="example"></a>예제

[DFX_Text](#dfx_text)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="dfx_text"></a><a name="dfx_text"></a> DFX_Text

[CDaoRecordset](cdaorecordset-class.md) 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 열 간에 `CString` 데이터를 전송합니다.

### <a name="syntax"></a>구문

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)클래스의 개체에 대 한 포인터입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.

*szName*<br/>
데이터 열의 이름입니다.

*value*<br/>
표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 데이터 원본으로 전송 하는 경우 지정 된 데이터 멤버에서 [CString](../../atl-mfc-shared/reference/cstringt-class.md)형식의 값을 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.

*nPreAllocSize*<br/>
프레임 워크는이 크기의 메모리를 사전에 할당 합니다. 데이터가 더 큰 경우 프레임 워크에서 필요에 따라 더 많은 공간을 할당 합니다. 성능을 향상 시키려면이 크기를 재할당을 방지 하기에 충분히 큰 값으로 설정 합니다.

*dwBindOptions*<br/>
변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본값 AFX_DAO_ENABLE_FIELD_CACHE는 이중 버퍼링을 사용 합니다. 다른 가능한 값은 AFX_DAO_DISABLE_FIELD_CACHE입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. [SetFieldDirty](cdaorecordset-class.md#setfielddirty) 및 [SetFieldNull](cdaorecordset-class.md#setfieldnull) 를 직접 호출 해야 합니다.

> [!NOTE]
> [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)을 설정 하 여 데이터를 기본적으로 이중 버퍼링 할지 여부를 제어할 수 있습니다.

### <a name="remarks"></a>설명

데이터는 DAO에서 형식 DAO_CHAR 사이에 매핑되고 (_UNICODE 기호가 정의 된 경우 DAO_WCHAR) 레코드 집합에 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 을 입력 합니다.  n

### <a name="example"></a>예제

이 예제에서는에 대 한 여러 호출을 보여 줍니다 `DFX_Text` . [CDaoFieldExchange:: SetFieldType](cdaofieldexchange-class.md#setfieldtype)에 대 한 두 번의 호출도 확인 합니다. 에 대 한 첫 번째 호출과 `SetFieldType` 해당 **DFX** 호출을 작성 해야 합니다. 두 번째 호출 및 이와 관련 된 **DFX** 호출은 일반적으로 클래스를 생성 한 코드 마법사를 통해 작성 됩니다.

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
