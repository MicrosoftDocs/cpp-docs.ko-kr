---
description: '자세히 알아보기: 레코드 집합: 대량 레코드 페치 (ODBC)'
title: '레코드 집합: 대량 레코드 페치(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: 6f77186a640971e6763160dde397f5aeb0b97f3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322353"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>레코드 집합: 대량 레코드 페치(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

클래스는 `CRecordset` 대량 행 페치를 지원 합니다. 즉, 데이터 원본에서 한 번에 하나의 레코드를 검색 하는 대신 단일 인출 중에 여러 레코드를 한 번에 검색할 수 있습니다. 파생 된 클래스 에서만 대량 행 페치를 구현할 수 있습니다 `CRecordset` . 데이터 원본에서 레코드 집합 개체로 데이터를 전송 하는 프로세스를 대량 RFX (대량 레코드 필드 교환) 라고 합니다. 파생 클래스에서 대량 행 페치를 사용 하지 않는 경우 `CRecordset` 데이터는 RFX (레코드 필드 교환)를 통해 전송 됩니다. 자세한 내용은 [RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)를 참조 하세요.

이 토픽에서는 다음 내용을 설명합니다.

- [CRecordset에서 대량 행 페치를 지 원하는 방법](#_core_how_crecordset_supports_bulk_row_fetching)입니다.

- [대량 행 페치를 사용 하는 경우의 몇 가지 특별 고려 사항](#_core_special_considerations)

- [대량 레코드 필드 교환을 구현 하는 방법](#_core_how_to_implement_bulk_record_field_exchange)입니다.

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a> CRecordset에서 대량 행 페치를 지 원하는 방법

레코드 집합 개체를 열기 전에 멤버 함수를 사용 하 여 행 집합 크기를 정의할 수 있습니다 `SetRowsetSize` . 행 집합 크기는 단일 인출 중에 검색 해야 하는 레코드 수를 지정 합니다. 대량 행 페치를 구현 하는 경우 기본 행 집합 크기는 25입니다. 대량 행 페치를 구현 하지 않는 경우 행 집합 크기는 1에서 고정 된 상태로 유지 됩니다.

행 집합 크기를 초기화 한 후에는 [Open](../../mfc/reference/crecordset-class.md#open) 멤버 함수를 호출 합니다. 여기에서 `CRecordset::useMultiRowFetch` 대량 행 페치를 구현 하려면 *dwOptions* 매개 변수의 옵션을 지정 해야 합니다. 옵션을 추가로 설정할 수 있습니다 `CRecordset::userAllocMultiRowBuffers` . 대량 레코드 필드 교환 메커니즘에서는 배열을 사용 하 여 인출 하는 동안 검색 된 데이터의 여러 행을 저장 합니다. 이러한 저장소 버퍼는 프레임 워크에 의해 자동으로 할당 되거나 수동으로 할당할 수 있습니다. 옵션을 지정 하면 할당을 수행 하는 것입니다 `CRecordset::userAllocMultiRowBuffers` .

다음 표에서는 `CRecordset` 대량 행 페치를 지원 하기 위해에서 제공 하는 멤버 함수를 보여 줍니다.

|멤버 함수|Description|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|인출 하는 동안 발생 하는 모든 오류를 처리 하는 가상 함수입니다.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|대량 레코드 필드 교환을 구현 합니다. 데이터 원본에서 레코드 집합 개체로 여러 행의 데이터를 전송 하기 위해 자동으로 호출 됩니다.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|행 집합 크기에 대 한 현재 설정을 검색 합니다.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|지정 된 인출 후 실제로 검색 된 행 수를 나타냅니다. 불완전 한 행 집합을 인출 하지 않는 한 대부분의 경우이는 행 집합 크기입니다.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|행 집합 내의 특정 행에 대 한 인출 상태를 반환 합니다.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|행 집합 내의 특정 행에 대 한 데이터와 상태를 새로 고칩니다.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|커서를 행 집합 내의 특정 행으로 이동 합니다.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|행 집합 크기 설정을 지정 된 값으로 변경 하는 가상 함수입니다.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a> 특별 고려 사항

대량 행 페치는 성능 향상 이지만 특정 기능은 다르게 작동 합니다. 대량 행 페치를 구현 하도록 결정 하기 전에 다음을 고려 하십시오.

- 프레임 워크는 자동으로 `DoBulkFieldExchange` 멤버 함수를 호출 하 여 데이터 원본에서 레코드 집합 개체로 데이터를 전송 합니다. 그러나 데이터는 레코드 집합에서 데이터 원본으로 다시 전송 되지 않습니다. `AddNew`, `Edit` , `Delete` 또는 멤버 함수를 호출 하면 `Update` 어설션이 실패 합니다. 는 `CRecordset` 현재 대량 데이터 행을 업데이트 하는 메커니즘을 제공 하지 않지만 ODBC API 함수를 사용 하 여 고유한 함수를 작성할 수 있습니다 `SQLSetPos` . 에 대 한 자세한 내용은 `SQLSetPos` [ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference)를 참조 하세요.

- `IsDeleted` `IsFieldDirty` `IsFieldNull` `IsFieldNullable` `SetFieldDirty` `SetFieldNull` 대량 행 페치를 구현 하는 레코드 집합에서는 멤버 함수,,,, 및를 사용할 수 없습니다. 그러나 대신 및 대신를 호출할 수 있습니다 `GetRowStatus` `IsDeleted` `GetODBCFieldInfo` `IsFieldNullable` .

- 작업은 행 집합을 `Move` 기준으로 레코드 집합의 위치를 합니다. 예를 들어 초기 행 집합 크기가 10 인 100 레코드가 있는 레코드 집합을 열려고 한다고 가정 합니다. `Open` 1부터 10 까지의 행을 인출 하 고 현재 레코드를 행 1에 배치 합니다. 다음 `MoveNext` 행이 아닌 다음 행 집합을 인출 하는를 호출 합니다. 이 행 집합은 행 11부터 20 까지의 행으로 구성 되며 현재 레코드는 11 행에 배치 됩니다. `MoveNext` `Move( 1 )` 대량 행 페치를 구현 하는 경우 및는 동일 하지 않습니다. `Move( 1 )` 현재 레코드에서 1 개의 행이 시작 되는 행 집합을 인출 합니다. 이 예제에서를 호출한 후를 호출 하면 `Move( 1 )` `Open` 행 2에서 11 행으로 구성 된 행 집합이 인출 되 고 현재 레코드는 2 행에 배치 됩니다. 자세한 내용은 [Move](../../mfc/reference/crecordset-class.md#move) member 함수를 참조 하세요.

- 레코드 필드 교환과 달리 마법사는 대량 레코드 필드 교환을 지원 하지 않습니다. 즉, 수동으로 필드 데이터 멤버를 선언 하 고 `DoBulkFieldExchange` 대량 RFX 함수에 대 한 호출을 작성 하 여 수동으로 재정의 해야 합니다. 자세한 내용은 *클래스 라이브러리 참조* 에서 [레코드 필드 교환 함수](../../mfc/reference/record-field-exchange-functions.md) 를 참조 하세요.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a> 대량 레코드 필드 교환을 구현 하는 방법

대량 레코드 필드 교환은 데이터 행 집합을 데이터 원본에서 레코드 집합 개체로 전송 합니다. 대량 RFX 함수는 배열을 사용 하 여이 데이터를 저장 하 고 배열을 사용 하 여 행 집합의 각 데이터 항목의 길이를 저장 합니다. 클래스 정의에서 필드 데이터 멤버를 포인터로 정의 하 여 데이터 배열에 액세스 해야 합니다. 또한 길이 배열에 액세스 하는 포인터 집합을 정의 해야 합니다. 모든 매개 변수 데이터 멤버를 포인터로 선언 하면 안 됩니다. 대량 레코드 필드 교환을 사용할 때 매개 변수 데이터 멤버를 선언 하는 것은 레코드 필드 교환을 사용할 때 선언 하는 것과 같습니다. 다음 코드에서는 간단한 예를 보여 줍니다.

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

이러한 저장소 버퍼를 수동으로 할당 하거나 프레임 워크에서 할당을 수행할 수 있습니다. 버퍼를 직접 할당 하려면 `CRecordset::userAllocMultiRowBuffers` 멤버 함수에서 *dwOptions* 매개 변수의 옵션을 지정 해야 합니다 `Open` . 배열의 크기를 적어도 행 집합 크기와 동일 하 게 설정 해야 합니다. 프레임 워크에서 할당을 수행 하도록 하려면 포인터를 NULL로 초기화 해야 합니다. 일반적으로이 작업은 레코드 집합 개체의 생성자에서 수행 됩니다.

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

마지막으로 멤버 함수를 재정의 해야 합니다 `DoBulkFieldExchange` . 필드 데이터 멤버의 경우 대량 RFX 함수를 호출 합니다. 매개 변수 데이터 멤버의 경우에는 RFX 함수를 호출 합니다. SQL 문이나 저장 프로시저를에 전달 하 여 레코드 집합을 연 경우 `Open` 대량 RFX 호출을 수행 하는 순서는 레코드 집합의 열 순서와 일치 해야 합니다. 마찬가지로 매개 변수에 대 한 RFX 호출의 순서는 SQL 문 또는 저장 프로시저의 매개 변수 순서와 일치 해야 합니다.

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
> `Close`파생 `CRecordset` 클래스가 범위를 벗어나기 전에 멤버 함수를 호출 해야 합니다. 이렇게 하면 프레임 워크에서 할당 한 모든 메모리가 해제 됩니다. `Close`대량 행 페치를 구현 했는지 여부에 관계 없이 항상 명시적으로를 호출 하는 것이 좋은 프로그래밍 습관입니다.

RFX (레코드 필드 교환)에 대 한 자세한 내용은 [레코드 필드 교환: Rfx 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)을 참조 하세요. 매개 변수 사용에 대 한 자세한 내용은 [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 및 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset:: m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
