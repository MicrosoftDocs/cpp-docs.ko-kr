---
title: 레코드 필드 교환 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 564d797a30e4b2d8518c73c5f7589aae205b6907
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-functions"></a>레코드 필드 교환 함수
이 항목에서는 레코드 필드 교환 (RFX, 대량 RFX와 DFX) 레코드 집합 개체와 해당 데이터 소스 간의 데이터 전송을 자동화 하 고 데이터에 다른 작업을 수행 하는 데 사용 되는 함수입니다.  
  
 ODBC 기반 클래스를 사용하고 대량 행 페치를 구현한 경우 데이터 소스 열에 해당하는 각 데이터 멤버에 대해 대량 RFX 함수를 호출하여 `DoBulkFieldExchange` 의 `CRecordset` 멤버 함수를 수동으로 재정의해야 합니다.  
  
 ODBC 기반 클래스에서 대량 행 페치를 구현하지 않았거나 DAO 기반 클래스를 사용하는 경우에는 클래스 마법사가 레코드 집합의 각 필드 데이터 멤버에 대해 RFX 함수(ODBC 클래스의 경우) 또는 DFX 함수(DAO 클래스의 경우)를 호출하여 `DoFieldExchange` 또는 `CRecordset` 의 `CDaoRecordset` 멤버 함수를 재정의합니다.  
  
 레코드 필드 교환 함수는 프레임워크에서 `DoFieldExchange` 또는 `DoBulkFieldExchange`를 호출할 때마다 데이터를 전송합니다. 각 함수는 특정 데이터 형식을 전송합니다.  
  
 이러한 함수의 사용 방법에 대한 자세한 내용은 [레코드 필드 교환: RFX 작동 방식(ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)문서를 참조하세요. 대량 행 페치에 대한 자세한 내용은 [레코드 집합: 대량 레코드 페치(ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)문서를 참조하세요.  
  
 동적으로 바인딩하는 데이터 열의 경우 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)문서에 설명된 대로 RFX 또는 DFX 함수를 직접 호출할 수도 있습니다. 또한 Technical Note [43](../../mfc/tn043-rfx-routines.md) (ODBC) 및 Technical Note [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (DAO)에 설명된 대로 사용자 고유의 사용자 지정 RFX 또는 DFX 루틴을 작성할 수 있습니다.  
  
 RFX 및 대량 RFX에 대 한 예제에 표시 된 대로 함수는 `DoFieldExchange` 및 `DoBulkFieldExchange` 함수 참조 [RFX_Text](#rfx_text) 및 #rfx_text_bulk [RFX_Text_Bulk]). DFX 함수는 RFX 함수와 매우 유사합니다.  
  
### <a name="rfx-functions-odbc"></a>RFX 함수(ODBC)  
  
|||  
|-|-|  
|[RFX_Binary](#rfx_binary)|[CByteArray](cbytearray-class.md)형식의 바이트 배열을 전송합니다.|  
|[RFX_Bool](#rfx_bool)|부울 데이터를 전송합니다.|  
|[RFX_Byte](#rfx_byte)|단일 바이트 데이터를 전송합니다.|  
|[RFX_Date](#rfx_date)|[CTime](../../atl-mfc-shared/reference/ctime-class.md) 또는 **TIMESTAMP_STRUCT**를 사용하여 시간 및 날짜 데이터를 전송합니다.|  
|[RFX_Double](#rfx_double)|배정밀도 부동 소수점 수 데이터를 전송합니다.|  
|[RFX_Int](#rfx_int)|정수 데이터를 전송합니다.|  
|[RFX_Long](#rfx_long)|정수(Long) 데이터를 전송합니다.|  
|[RFX_LongBinary](#rfx_longbinary)|[CLongBinary](clongbinary-class.md) 클래스의 개체와 함께 BLOB(Binary Large Object) 데이터를 전송합니다.|  
|[RFX_Single](#rfx_single)|부동 소수점 수 데이터를 전송합니다.|  
|[RFX_Text](#rfx_text)|문자열 데이터를 전송합니다.|  
  
### <a name="bulk-rfx-functions-odbc"></a>대량 RFX 함수(ODBC)  
  
|||  
|-|-|  
|[RFX_Binary_Bulk](#rfx_binary_bulk)|바이트 데이터 배열을 전송합니다.|  
|[RFX_Bool_Bulk](#rfx_bool_bulk)|부울 데이터 배열을 전송합니다.|  
|[RFX_Byte_Bulk](#rfx_byte_bulk)|단일 바이트 배열을 전송합니다.|  
|[RFX_Date_Bulk](#rfx_date_bulk)|**TIMESTAMP_STRUCT**형식의 데이터 배열을 전송합니다.|  
|[RFX_Double_Bulk](#rfx_double_bulk)|배정밀도 부동 소수점 데이터 배열을 전송합니다.|  
|[RFX_Int_Bulk](#rfx_int_bulk)|정수 데이터 배열을 전송합니다.|  
|[RFX_Long_Bulk](#rfx_long_bulk)|정수(Long) 데이터 배열을 전송합니다.|  
|[RFX_Single_Bulk](#rfx_single_bulk)|부동 소수점 데이터 배열을 전송합니다.|  
|[RFX_Text_Bulk](#rfx_text_bulk)|**LPSTR**형식의 데이터 배열을 전송합니다.|  
  
### <a name="dfx-functions-dao"></a>DFX 함수(DAO)  
  
|||
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

## <a name="rfx_binary"></a>  RFX_Binary
필드 데이터 멤버 간의 바이트 배열을 전송는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_BINARY**, **SQL_VARBINARY**, 또는 **SQL_ LONGVARBINARY**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Binary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CByteArray& value,  
   int nMaxLength = 255);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 [CByteArray](cbytearray-class.md), 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `nMaxLength`  
 최대 허용 길이 문자열 또는 전송 되는 배열입니다. 기본값 `nMaxLength` 은 255입니다. 올바른 값은 1 ~ `INT_MAX`합니다. 프레임 워크 데이터에 대 한이 공간의 크기를 할당합니다. 최상의 성능을 위해 예상 된 가장 큰 데이터 항목에 맞게 충분히 큰 값을 전달 합니다.  
  
### <a name="remarks"></a>설명  
 이러한 종류의 데이터 소스에 데이터 형식에서 매핑된 `CByteArray` 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_bool"></a>  RFX_Bool
필드 데이터 멤버 간에 부울 데이터를 전송는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_BIT**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Bool(  
   CFieldExchange* pFX,  
   const char* szName,  
   BOOL& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **BOOL**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_byte"></a>  RFX_Byte
전송 사이 단일 바이트의 필드 데이터 멤버는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_TINYINT**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Byte(  
   CFieldExchange* pFX,  
   const char* szName,  
   BYTE& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **바이트**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_date"></a>  RFX_Date
전송 `CTime` 또는 **TIMESTAMP_STRUCT** 의 필드 데이터 멤버 간에 데이터는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_DATE**, **SQL_TIME**, 또는 **SQL_TIMESTAMP**합니다.  
  
### <a name="syntax"></a>구문  
  
```
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
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시 된 데이터 멤버;에 저장 된 값 전송 될 값입니다. 값에 대 한 서로 다른 데이터 형식을 사용 하는 다양 한 버전의 함수가:  
  
 함수의 첫 번째 버전에서는에 대 한 참조는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 개체입니다. 데이터 원본에 레코드 집합에서 전송,이 값은 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 두 번째 버전의 함수 사용에 대 한 참조는 **TIMESTAMP_STRUCT** 구조입니다. 설정 해야이 구조를 직접 호출 전에. 두 대화 상자 데이터 교환 (DDX) 지원 하지도이 버전에 대 한 코드 마법사 지원 됩니다. 세 번째 버전의 함수 유사 하 게 작동 첫 번째 버전에 대 한 참조 한다는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다.  
  
### <a name="remarks"></a>설명  
 `CTime` 버전의 함수는 일부 중간 처리 오버 헤드가 있으며 다소 제한 된 범위입니다. 너무 제한적 이러한 요소 중 하나를 찾을 경우 두 번째 버전의 함수를 사용 합니다. 그러나 해당 코드 마법사 및 DDX 지원 및 요구 사항을 설정 하는 구조 직접 부족 합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_double"></a>  RFX_Double
전송 **double 부동 소수점** 의 필드 데이터 멤버 간에 데이터는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_DOUBLE**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Double(  
   CFieldExchange* pFX,  
   const char* szName,  
   double& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **double**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_int"></a>  RFX_Int
필드 데이터 멤버 간에 정수 데이터를 전송는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_SMALLINT**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 `int`, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_long"></a>  RFX_Long
필드 데이터 멤버 간에 정수 (long) 데이터를 전송는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_INTEGER**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Long(  
   CFieldExchange* pFX,  
   const char* szName,  
   LONG&   
value );  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **긴**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  
  
## <a name="rfx_longbinary"></a>  RFX_LongBinary
클래스를 사용 하 여 이진 대형 개체 (BLOB) 데이터 전송 [CLongBinary](clongbinary-class.md) 의 필드 데이터 멤버 간에 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_LONGVARBINARY**또는 **SQL_LONGVARCHAR**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_LongBinary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CLongBinary& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 `CLongBinary`, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_single"></a>  RFX_Single
부동 소수점 데이터의 필드 데이터 멤버 간에 전송 된 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_REAL**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Single(  
   CFieldExchange* pFX,  
   const char* szName,  
   float& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **float**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  
  

## <a name="rfx_text"></a>  RFX_Text
전송 `CString` 의 필드 데이터 멤버 간에 데이터는 `CRecordset` 개체 및 열에 ODBC 형식의 데이터 소스에서 레코드 **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_ VARCHAR**, **SQL_DECIMAL**, 또는 **SQL_NUMERIC**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Text(  
   CFieldExchange* pFX,  
   const char* szName,  
   CString& value,  
   int nMaxLength = 255,  
   int nColumnType = SQL_VARCHAR,  
   short nScale = 0);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 `CFieldExchange`합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 `CString`, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `nMaxLength`  
 최대 허용 길이 문자열 또는 전송 되는 배열입니다. 기본값 `nMaxLength` 은 255입니다. 유효한 값은 1 `INT_MAX`). 프레임 워크 데이터에 대 한이 공간의 크기를 할당합니다. 최상의 성능을 위해 예상 된 가장 큰 데이터 항목에 맞게 충분히 큰 값을 전달 합니다.  
  
 *nColumnType*  
 매개 변수에 대해 주로 사용 합니다. 매개 변수의 데이터 형식을 나타내는 정수입니다. 폼의 ODBC 데이터 형식 형식이 **SQL_XXX**합니다.  
  
 `nScale`  
 ODBC 형식의 값에 대 한 소수 자릿수를 지정 **SQL_DECIMAL** 또는 **SQL_NUMERIC**합니다. `nScale` 유용한 경우에 매개 변수 값을 설정 합니다. 자세한 내용은 부록 D /의 "전체 자릿수, 소수 자릿수, 길이 및 표시 크기" 항목을 참조는 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 이러한 형식의 모든 데이터 원본의 데이터에에서 매핑된 `CString` 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 이 예제를 여러 번 호출 `RFX_Text`합니다. 두 번 호출 또한 확인 `CFieldExchange::SetFieldType`합니다. 매개 변수에 대 한 호출을 작성 해야 `SetFieldType` 및 RFX 호출 합니다. 출력 열 호출 및 해당 관련된 RFX 호출 코드 마법사에 의해 일반적으로 기록 됩니다.  
  
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
 **헤더:** afxdb.h  


## <a name="rfx_binary_bulk"></a>  RFX_Binary_Bulk
ODBC 데이터 원본의 열에서 여러 행의 바이트 데이터를 전송 하에서 해당 배열에는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Binary_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgByteVals`  
 배열에 대 한 포인터 **바이트** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgByteVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
 `nMaxLength`  
 가 가리키는 배열의에 저장 된 값의 길이가 허용 되는 최대 `prgByteVals`합니다. 데이터는 잘리지 않습니다, 값을 전달 하기 위해 큰 데이터 항목을 수용할 수 있을 만큼 큰 예상 합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에 ODBC 유형의 점이 **SQL_BINARY**, **SQL_VARBINARY**, 또는 **SQL_LONGVARBINARY**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **바이트**합니다.  
  
 초기화 하는 경우 `prgByteVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_bool_bulk"></a>  RFX_Bool_Bulk
ODBC 데이터 원본의 열에서 해당 배열에 여러 행의 부울 데이터를 전송는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Bool_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL** prgBoolVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgBoolVals`  
 배열에 대 한 포인터 **BOOL** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgBoolVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에는 ODBC 유형의 있어야 **SQL_BIT**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **BOOL**합니다.  
  
 초기화 하는 경우 `prgBoolVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_byte_bulk"></a>  RFX_Byte_Bulk
ODBC 데이터 원본의 열에서 여러 행의 단일 바이트를 전송 하에서 해당 배열에는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Byte_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgByteVals`  
 배열에 대 한 포인터 **바이트** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgByteVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에는 ODBC 유형의 있어야 **SQL_TINYINT**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **바이트**합니다.  
  
 초기화 하는 경우 `prgByteVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  
  
## <a name="rfx_date_bulk"></a>  RFX_Date_Bulk
여러 행의 전송 **TIMESTAMP_STRUCT** 의 해당 배열에는 ODBC 데이터 원본의 열에서 데이터는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Date_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   TIMESTAMP_STRUCT** prgTSVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgTSVals`  
 배열에 대 한 포인터 **TIMESTAMP_STRUCT** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다. 에 대 한 자세한 내용은 **TIMESTAMP_STRUCT** 의 부록 D의 "C 데이터 형식" 항목을 참조 데이터 형식으로 *ODBC SDK Programmer's Reference*합니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgTSVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에 ODBC 유형의 점이 **SQL_DATE**, **SQL_TIME**, 또는 **SQL_TIMESTAMP**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **TIMESTAMP_STRUCT**합니다.  
  
 초기화 하는 경우 `prgTSVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_double_bulk"></a>  RFX_Double_Bulk
ODBC 데이터 원본의 열에서 배정밀도 부동 소수점 데이터의 여러 행에 해당 하는 배열은 전송는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Double_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   double** prgDblVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgDblVals`  
 배열에 대 한 포인터 **double** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgDblVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에는 ODBC 유형의 있어야 **SQL_DOUBLE**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **double**합니다.  
  
 초기화 하는 경우 `prgDblVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_int_bulk"></a>  RFX_Int_Bulk
필드 데이터 멤버 간에 정수 데이터를 전송는 `CRecordset` 개체 및 열에는 ODBC 형식의 데이터 소스에서 레코드 **SQL_SMALLINT**합니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CFieldExchange](cfieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 작업에 대 한 자세한 내용은 `CFieldExchange` 문서 참조 개체 지정할 수 있습니다 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 `int`, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text](#rfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_long_bulk"></a>  RFX_Long_Bulk
ODBC 데이터 원본의 열에서 여러 행의 정수 (long) 데이터를 전송 하에서 해당 배열에는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Long_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   long** prgLongVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgLongVals`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgLongVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에는 ODBC 유형의 있어야 **SQL_INTEGER**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **긴**합니다.  
  
 초기화 하는 경우 `prgLongVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  

## <a name="rfx_single_bulk"></a>  RFX_Single_Bulk
ODBC 데이터 원본의 열에서 여러 행의 부동 소수점 데이터를 전송 하에서 해당 배열에는 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Single_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   float** prgFltVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgFltVals`  
 배열에 대 한 포인터 **float** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgFltVals`합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에는 ODBC 유형의 있어야 **SQL_REAL**합니다. 레코드 집합에 대 한 형식 포인터의 필드 데이터 멤버를 정의 해야 **float**합니다.  
  
 초기화 하는 경우 `prgFltVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 참조 [RFX_Text_Bulk](#rfx_text_bulk)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdb.h  
  

## <a name="rfx_text_bulk"></a>  RFX_Text_Bulk
ODBC 데이터 원본의 열에서 해당 배열에 문자 데이터의 여러 행으로 전송 된 `CRecordset`-파생 된 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```
void RFX_Text_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   LPSTR* prgStrVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 에 대 한 포인터는 [CFieldExchange](cfieldexchange-class.md) 개체입니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다. 자세한 내용은 문서 참조 [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)합니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 `prgStrVals`  
 배열에 대 한 포인터 **LPSTR** 값입니다. 이 배열에는 데이터 소스에서 레코드 집합을 전송할 수 있도록 데이터가 저장 됩니다. ODBC의 현재 버전과이 값은 유니코드 될 수 없습니다.  
  
 `prgLengths`  
 정수 (long) 배열에 대 한 포인터입니다. 이 배열에서 가리키는 배열에 있는 각 값의 바이트에서 길이 저장할 됩니다 `prgStrVals`합니다. 이 길이 null 종결 문자를 제외합니다. 값 **SQL_NULL_DATA** 포함 된 Null 값이 해당 데이터 항목이 저장 됩니다. 자세한 내용은 ODBC API 함수를 참조 하십시오. **SQLBindCol** 에 *ODBC SDK Programmer's Reference*합니다.  
  
 `nMaxLength`  
 가 가리키는 배열의에 저장 된 값의 길이가 허용 되는 최대 `prgStrVals`, null 종결 문자를 포함 합니다. 데이터는 잘리지 않습니다, 값을 전달 하기 위해 큰 데이터 항목을 수용할 수 있을 만큼 큰 예상 합니다.  
  
### <a name="remarks"></a>설명  
 데이터 원본 열에 ODBC 유형의 점이 **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_VARCHAR**, **SQL_DECIMAL**, 또는 **SQL_NUMERIC**합니다. 레코드 집합 형식의 필드 데이터 멤버를 정의 해야 **LPSTR**합니다.  
  
 초기화 하는 경우 `prgStrVals` 및 `prgLengths` 를 **NULL**를 가리키는 배열 행 집합 크기와 동일한 크기에 따라 자동으로 할당 될 다음 합니다.  
  
> [!NOTE]
>  대량 레코드 필드 교환은만 recordset 개체에 데이터 원본에서 데이터를 전송합니다. 레코드 집합을 업데이트할 수 있도록 하려면 ODBC API 함수를 사용 해야 **SQLSetPos**합니다.  
  
 자세한 내용은 문서를 참조 [레코드 집합: 레코드 페치 대량 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 및 [Exchange RFX (레코드 필드)](../../data/odbc/record-field-exchange-rfx.md)합니다.  
  
### <a name="example"></a>예제  
 호출 직접 작성 해야 하면 `DoBulkFieldExchange` 재정의 합니다. 에 대 한 호출을 보여 주는이 예제 `RFX_Text_Bulk`에 대 한 호출 뿐 아니라 `RFX_Long_Bulk`, 데이터 전송에 대 한 합니다. 이러한 호출에 대 한 호출 다음에 오는 [CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md)합니다. 매개 변수를 대량 RFX 함수 대신 RFX 함수를 호출 해야 합니다.  
  
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
 **헤더:** afxdb.h  

## <a name="dfx_binary"></a>  DFX_Binary
필드 데이터 멤버 간의 바이트 배열을 전송는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Binary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CByteArray& value,  
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 [CByteArray](cbytearray-class.md), 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `nPreAllocSize`  
 프레임 워크의이 메모리가 preallocates 합니다. 데이터가 더 큰 경우 프레임 워크는 필요에 따라 더 많은 공간을 할당 합니다. 성능 향상을 위해이 크기를 다시 할당을 방지 하려면 충분히 큰 값으로 설정 합니다. 기본 크기는 AFXDAO에 정의 됩니다. H 파일로 **AFX_DAO_BINARY_DEFAULT_SIZE**합니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_DISABLE_FIELD_CACHE`, 버퍼링 하지 않고 사용 하 여 이중, 않으며 호출 해야 [SetFieldDirty](cdaorecordset-class.md#setfielddirty) 및 [SetFieldNull](cdaorecordset-class.md#setfieldnull) 직접 합니다. 다른 가능한 값 `AFX_DAO_ENABLE_FIELD_CACHE`, 이중 버퍼링 사용 하 고 필드를 표시할 추가 작업을 수행 하지 않아도 커밋되지 않음 또는 Null입니다. 성능 및 메모리 이유로 이진 데이터를 상대적으로 작은 경우가 아니면이 값을 하지 마십시오.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 모든 필드에 대해 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_BYTES** DAO 및 형식 [CByteArray](cbytearray-class.md) 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  
  

## <a name="dfx_bool"></a>  DFX_Bool
필드 데이터 멤버 간에 부울 데이터를 전송는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Bool(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **BOOL**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_BOOL** DAO 및 형식 **BOOL** 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_byte"></a>  DFX_Byte
전송 사이 단일 바이트의 필드 데이터 멤버는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Byte(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **바이트**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_BYTES** DAO 및 형식 **바이트** 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_currency"></a>  DFX_Currency
필드 데이터 멤버 간에 통화 데이터를 전송는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Currency(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleCurrency& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 형식의 지정 된 데이터 멤버에서이 값을 가져오는 데이터 원본에서 레코드 집합으로 전송 [COleCurrency](colecurrency-class.md)합니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_CURRENCY** DAO 및 형식 [COleCurrency](colecurrency-class.md) 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_datetime"></a>  DFX_DateTime
필드 데이터 멤버 간에 날짜 및 시간 데이터를 전송는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_DateTime(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleDateTime& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 함수 사용에 대 한 참조는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다. 데이터 원본에 레코드 집합에서 전송,이 값은 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_DATE** DAO 및 형식 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 레코드 집합의 합니다.  
  
> [!NOTE]
>  `COleDateTime` 대체 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 및 **TIMESTAMP_STRUCT** DAO 클래스에이 목적에 대 한 합니다. `CTime` 및 **TIMESTAMP_STRUCT** 않은 ODBC 기반 데이터 액세스 클래스에 사용 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_double"></a>  DFX_Double
전송 **double 부동 소수점** 의 필드 데이터 멤버 간에 데이터는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Double(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   double& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **double**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_R8** DAO 및 형식 **double 부동 소수점** 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_long"></a>  DFX_Long
필드 데이터 멤버 간에 정수 (long) 데이터를 전송는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Long(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   long& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **긴**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_I4** DAO 및 형식 **긴** 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  
  

## <a name="dfx_longbinary"></a>  DFX_LongBinary
**중요 한** 를 사용 하는 것이 좋습니다. [DFX_Binary](#dfx_binary) 이 함수 대신 합니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_LongBinary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CLongBinary& value,  
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 [CLongBinary](clongbinary-class.md), 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 *dwPreAllocSize*  
 프레임 워크의이 메모리가 preallocates 합니다. 데이터가 더 큰 경우 프레임 워크는 필요에 따라 더 많은 공간을 할당 합니다. 성능 향상을 위해이 크기를 다시 할당을 방지 하려면 충분히 큰 값으로 설정 합니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 **AFX_DISABLE_FIELD_CACHE**, 이중 버퍼링을 사용 하지 않습니다. 다른 가능한 값은 `AFX_DAO_ENABLE_FIELD_CACHE`입니다. 이중 버퍼링 사용 하 고 필드를 표시할 추가 작업을 수행 하지 않아도 커밋되지 않음 또는 Null입니다. 성능 및 메모리 이유로 이진 데이터를 상대적으로 작은 경우가 아니면이 값을 하지 마십시오.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 `DFX_LongBinary` MFC ODBC 클래스와 호환성을 위해 제공 됩니다. `DFX_LongBinary` 클래스를 사용 하 여 이진 대형 개체 (BLOB) 데이터를 전송 하는 함수 `CLongBinary` 의 필드 데이터 멤버 간에 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다. 형식 간에 데이터가 매핑되는 **DAO_BYTES** DAO 및 형식 [CLongBinary](clongbinary-class.md) 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_short"></a>  DFX_Short
전송 짧은 정수 데이터의 필드 데이터 멤버 간에 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Short(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   short& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **짧은**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_I2** DAO 및 형식 **짧은** 레코드 집합의 합니다.  
  
> [!NOTE]
>  `DFX_Short` 에 해당 [RFX_Int](#rfx_int) ODBC 기반 클래스에 대 한 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  
  

## <a name="dfx_single"></a>  DFX_Single
부동 소수점 데이터의 필드 데이터 멤버 간에 전송는 [CDaoRecordset](cdaorecordset-class.md) 개체와 데이터 소스에서 레코드의 열입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Single(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   float& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 **float**, 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. `SetFieldDirty` 및 `SetFieldNull`을 직접 호출해야 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_R4** DAO 및 형식 **float** 레코드 집합의 합니다.  
  
### <a name="example"></a>예제  
 참조 [DFX_Text](#dfx_text)합니다.  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  

## <a name="dfx_text"></a>  DFX_Text
전송 `CString` 의 필드 데이터 멤버 간에 데이터는 [CDaoRecordset](cdaorecordset-class.md) 개체 및 열에 데이터 소스에서 레코드입니다.  
  
### <a name="syntax"></a>구문  
  
```
void AFXAPI DFX_Text(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CString& value,  
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>매개 변수  
 `pFX`  
 클래스의 개체에 대 한 포인터 [CDaoFieldExchange](cdaofieldexchange-class.md)합니다. 이 개체에는 각 함수 호출에 대한 컨텍스트를 정의하는 정보가 포함됩니다.  
  
 `szName`  
 데이터 열의 이름입니다.  
  
 *값*  
 표시된 데이터 멤버에 저장된 값(전송할 값)입니다. 레코드 집합에서 전송 하기 위해서는 형식의 값을 데이터 원본에 대 한 [CString](../../atl-mfc-shared/reference/cstringt-class.md), 지정된 된 데이터 멤버에서 가져옵니다. 데이터 소스에서 레코드 집합으로 전송하기 위해서는 값이 지정된 데이터 멤버에 저장됩니다.  
  
 `nPreAllocSize`  
 프레임 워크의이 메모리가 preallocates 합니다. 데이터가 더 큰 경우 프레임 워크는 필요에 따라 더 많은 공간을 할당 합니다. 성능 향상을 위해이 크기를 다시 할당을 방지 하려면 충분히 큰 값으로 설정 합니다.  
  
 `dwBindOptions`  
 변경된 레코드 집합 필드를 검색할 수 있도록 MFC의 이중 버퍼링 메커니즘을 활용할 수 있게 해주는 옵션입니다. 기본적으로 `AFX_DAO_ENABLE_FIELD_CACHE`에는 이중 버퍼링이 사용됩니다. 다른 가능한 값은 `AFX_DAO_DISABLE_FIELD_CACHE`입니다. 이 값을 지정하면, MFC가 이 필드를 검사하지 않습니다. 호출 해야 [SetFieldDirty](cdaorecordset-class.md#setfielddirty) 및 [SetFieldNull](cdaorecordset-class.md#setfieldnull) 직접 합니다.  
  
> [!NOTE]
>  여부 데이터가 이중 버퍼링 되는지 기본적으로 설정 하 여 제어할 수 있습니다 [cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)합니다.  
  
### <a name="remarks"></a>설명  
 형식 간에 데이터가 매핑되는 **DAO_CHAR** DAO에서 (또는 경우 기호 **_UNICODE** 정의 된 **DAO_WCHAR**) 및 형식 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 에 레코드 집합입니다.  n
  
### <a name="example"></a>예제  
 이 예제를 여러 번 호출 `DFX_Text`합니다. 두 번 호출 또한 확인 [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype)합니다. 첫 번째 호출을 작성 해야 `SetFieldType` 및 해당 **DFX** 호출 합니다. 두 번째 호출 및 관련 **DFX** 호출은 클래스를 생성 하는 코드 마법사가 정상적으로 작성 됩니다.  
  
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
 **헤더:** afxdao.h  
  
## <a name="see-also"></a>참고 항목  
 [매크로 및 전역](mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)   
 [CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)   
 [CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)

