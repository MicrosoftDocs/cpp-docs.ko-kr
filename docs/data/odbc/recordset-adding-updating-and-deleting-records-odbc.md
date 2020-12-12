---
description: '자세한 정보: 레코드 집합: 레코드 추가, 업데이트 및 삭제 (ODBC)'
title: '레코드 집합: 레코드 추가, 업데이트 및 삭제(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 20af392182481cc786d65567b4db1547d703ba0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186144"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>레코드 집합: 레코드 추가, 업데이트 및 삭제(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

> [!NOTE]
> 이제 대량으로 대량 레코드를 추가할 수 있습니다. 자세한 내용은 [레코드 집합: 대량 레코드 추가 (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)를 참조 하세요.

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 사용 하는 경우 레코드 [집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

업데이트 가능한 스냅숏과 다이너셋을 사용 하면 레코드를 추가, 편집 (업데이트) 및 삭제할 수 있습니다. 이 토픽에서는 다음 내용을 설명합니다.

- [레코드 집합을 업데이트할 수 있는지 여부를 확인 하는 방법](#_core_determining_whether_your_recordset_is_updatable)입니다.

- [새 레코드를 추가 하는 방법](#_core_adding_a_record_to_a_recordset)입니다.

- [기존 레코드를 편집 하는 방법](#_core_editing_a_record_in_a_recordset)

- [레코드를 삭제 하는 방법](#_core_deleting_a_record_from_a_recordset)

업데이트를 수행 하는 방법과 업데이트가 다른 사용자에 게 표시 되는 방법에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)을 참조 하십시오. 일반적으로 레코드를 추가, 편집 또는 삭제할 때 레코드 집합은 데이터 원본을 즉시 변경 합니다. 대신 관련 업데이트 그룹을 트랜잭션으로 일괄 처리할 수 있습니다. 트랜잭션이 진행 중인 경우에는 트랜잭션을 커밋할 때까지 업데이트가 최종 상태가 되지 않습니다. 이렇게 하면 변경 내용을 다시 가져오거나 롤백할 수 있습니다. 트랜잭션에 대 한 자세한 내용은 [트랜잭션 (ODBC)](../../data/odbc/transaction-odbc.md)을 참조 하십시오.

다음 표에서는 업데이트 특성이 다른 레코드 집합에 사용할 수 있는 옵션을 요약 하 여 보여 줍니다.

### <a name="recordset-readupdate-options"></a>레코드 집합 읽기/업데이트 옵션

|형식|읽기|레코드 편집|레코드 삭제|새로 추가 (추가)|
|----------|----------|-----------------|-------------------|------------------------|
|읽기 전용|Y|N|N|N|
|추가 전용|Y|N|N|Y|
|완전히 업데이트 가능|Y|Y|Y|Y|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a> 레코드 집합을 업데이트할 수 있는지 여부 확인

데이터 소스를 업데이트할 수 있고 레코드 집합을 업데이트할 수 있는 것으로 연 경우에는 레코드 집합 개체를 업데이트할 수 있습니다. 또한 해당 업데이트는 사용 하는 SQL 문, ODBC 드라이버의 기능 및 ODBC 커서 라이브러리가 메모리 내에 있는지 여부에 따라 달라 집니다. 읽기 전용 레코드 집합 또는 데이터 원본을 업데이트할 수 없습니다.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>레코드 집합을 업데이트할 수 있는지 여부를 확인 하려면

1. 레코드 집합 개체의 [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) 멤버 함수를 호출 합니다.

   `CanUpdate` 는 레코드 집합을 업데이트할 수 있는 경우 0이 아닌 값을 반환 합니다.

기본적으로 레코드 집합은 완전히 업데이트할 수 있으며 `AddNew` , 및 작업을 수행할 수 있습니다 `Edit` `Delete` . 하지만 [appendOnly](../../mfc/reference/crecordset-class.md#open) 옵션을 사용 하 여 업데이트할 수 있는 레코드 집합을 열 수도 있습니다. 이러한 방식으로 열린 레코드 집합은를 사용 하 여 새 레코드를 추가할 수 있습니다 `AddNew` . 기존 레코드는 편집 하거나 삭제할 수 없습니다. [CanAppend](../../mfc/reference/crecordset-class.md#canappend) 멤버 함수를 호출 하 여 레코드 집합을 추가 하기 위해서만 열려 있는지 여부를 테스트할 수 있습니다. `CanAppend` 는 레코드 집합이 완전히 업데이트 가능 하거나 추가에 대해서만 열려 있는 경우 0이 아닌 값을 반환 합니다.

다음 코드에서는 `CanUpdate` 라는 레코드 집합 개체에 대해를 사용 하는 방법을 보여 줍니다 `rsStudentSet` .

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
> 을 호출 하 여 레코드 집합을 업데이트 하려면 `Update` 레코드 집합에 테이블의 기본 키를 구성 하는 모든 열 (또는 테이블의 모든 고유 인덱스 열)이 포함 되어 있는지 확인 해야 합니다. 경우에 따라 프레임 워크는 레코드 집합에서 선택한 열만 사용 하 여 업데이트할 테이블의 레코드를 식별할 수 있습니다. 필요한 열이 없으면 테이블에서 여러 레코드가 업데이트 되어 테이블의 참조 무결성을 손상 시킬 수 있습니다. 이 경우 프레임 워크는를 호출할 때 예외를 throw 합니다 `Update` .

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a> 레코드 집합에 레코드 추가

[CanAppend](../../mfc/reference/crecordset-class.md#canappend) 멤버 함수가 0이 아닌 값을 반환 하는 경우 레코드 집합에 새 레코드를 추가할 수 있습니다.

#### <a name="to-add-a-new-record-to-a-recordset"></a>레코드 집합에 새 레코드를 추가 하려면

1. 레코드 집합을 appendable 확인 합니다.

1. 레코드 집합 개체의 [AddNew](../../mfc/reference/crecordset-class.md#addnew) 멤버 함수를 호출 합니다.

   `AddNew` 편집 버퍼 역할을 할 레코드 집합을 준비 합니다. 모든 필드 데이터 멤버는 특수 값 Null로 설정 되 고 변경 되지 않은 것으로 표시 되므로 [Update](../../mfc/reference/crecordset-class.md#update)를 호출 하면 변경 된 값만 데이터 원본에 기록 됩니다.

1. 새 레코드의 필드 데이터 멤버 값을 설정 합니다.

   필드 데이터 멤버에 값을 할당 합니다. 할당 되지 않은 것은 데이터 원본에 기록 되지 않습니다.

1. 레코드 집합 개체의 `Update` 멤버 함수를 호출 합니다.

   `Update` 데이터 원본에 새 레코드를 작성 하 여 추가를 완료 합니다. 를 호출 하지 못한 경우 발생 하는 방법에 대 한 자세한 내용은 `Update` [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)을 참조 하세요.

레코드를 추가 하는 방법과 레코드 집합에 추가 된 레코드가 표시 되는 방법에 대 한 자세한 내용은 [레코드 집합: AddNew, Edit 및 Delete 작업 방법 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)을 참조 하십시오.

다음 예제에서는 새 레코드를 추가 하는 방법을 보여 줍니다.

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> 또는 호출을 취소 하려면 `AddNew` `Edit` 또는에 대 한 다른 호출을 수행 하거나 `AddNew` `Edit` `Move` *AFX_MOVE_REFRESH* 매개 변수를 사용 하 여를 호출 하면 됩니다. 데이터 멤버가 이전 값으로 다시 설정 되 고 또는 모드에 있습니다 `Edit` `Add` .

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a> 레코드 집합에서 레코드 편집

레코드 집합의 [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) 멤버 함수가 0이 아닌 값을 반환 하는 경우 기존 레코드를 편집할 수 있습니다.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>레코드 집합에서 기존 레코드를 편집 하려면

1. 레코드 집합을 업데이트할 수 있는지 확인 합니다.

1. 업데이트 하려는 레코드로 스크롤합니다.

1. 레코드 집합 개체의 [Edit](../../mfc/reference/crecordset-class.md#edit) 멤버 함수를 호출 합니다.

   `Edit` 편집 버퍼 역할을 할 레코드 집합을 준비 합니다. 모든 필드 데이터 멤버는 레코드 집합이 변경 되었는지 여부를 나중에 확인할 수 있도록 표시 됩니다. [Update](../../mfc/reference/crecordset-class.md#update)를 호출 하면 변경 된 필드 데이터 멤버의 새 값이 데이터 원본에 기록 됩니다.

1. 새 레코드의 필드 데이터 멤버 값을 설정 합니다.

   필드 데이터 멤버에 값을 할당 합니다. 값을 할당 하지 않는 값은 그대로 유지 됩니다.

1. 레코드 집합 개체의 `Update` 멤버 함수를 호출 합니다.

   `Update` 변경 된 레코드를 데이터 소스에 기록 하 여 편집을 완료 합니다. 를 호출 하지 못한 경우 발생 하는 방법에 대 한 자세한 내용은 `Update` [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)을 참조 하세요.

레코드를 편집한 후에는 편집 된 레코드가 현재 레코드를 유지 합니다.

다음 예제에서는 작업을 보여 줍니다 `Edit` . 사용자가 편집 하려는 레코드로 이동한 것으로 가정 합니다.

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> 또는 호출을 취소 하려면 `AddNew` `Edit` 또는에 대 한 다른 호출을 수행 하거나 `AddNew` `Edit` `Move` *AFX_MOVE_REFRESH* 매개 변수를 사용 하 여를 호출 하면 됩니다. 데이터 멤버가 이전 값으로 다시 설정 되 고 또는 모드에 있습니다 `Edit` `Add` .

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a> 레코드 집합에서 레코드 삭제

레코드 집합의 [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) 멤버 함수가 0이 아닌 값을 반환 하는 경우 레코드를 삭제할 수 있습니다.

#### <a name="to-delete-a-record"></a>레코드를 삭제 하려면

1. 레코드 집합을 업데이트할 수 있는지 확인 합니다.

1. 업데이트 하려는 레코드로 스크롤합니다.

1. 레코드 집합 개체의 [Delete](../../mfc/reference/crecordset-class.md#delete) 멤버 함수를 호출 합니다.

   `Delete` 레코드 집합 및 데이터 소스 모두에서 레코드를 삭제 된 것으로 즉시 표시 합니다.

   및와 달리에 `AddNew` `Edit` `Delete` 는 해당 하는 `Update` 호출이 없습니다.

1. 다른 레코드로 스크롤합니다.

   > [!NOTE]
   >  레코드 집합을 이동 하는 경우 삭제 된 레코드를 건너뛸 수 없습니다. 자세한 내용은 [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) 멤버 함수를 참조 하세요.

다음 예에서는 작업을 보여 줍니다 `Delete` . 사용자가 삭제 하려는 레코드로 이동한 것으로 가정 합니다. 가 호출 된 후에는를 `Delete` 새 레코드로 이동 하는 것이 중요 합니다.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

, 및 멤버 함수의 효과에 대 한 자세한 내용은 `AddNew` `Edit` `Delete` [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 레코드 잠금 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
