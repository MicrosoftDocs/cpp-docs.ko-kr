---
description: '자세한 정보: 트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)'
title: '트랜잭션: 레코드 집합에서 트랜잭션 수행(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: bb041d35e7ab0bfc7e19f2658a8cdadae4bd8c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333881"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>트랜잭션: 레코드 집합에서 트랜잭션 수행(ODBC)

이 항목에서는 레코드 집합에서 트랜잭션을 수행 하는 방법에 대해 설명 합니다.

> [!NOTE]
> 한 수준의 트랜잭션만 지원 됩니다. 트랜잭션을 중첩할 수 없습니다.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>레코드 집합에서 트랜잭션을 수행 하려면

1. `CDatabase`개체의 `BeginTrans` 멤버 함수를 호출 합니다.

1. 대량 행 페치를 구현 하지 않은 경우 필요에 따라 `AddNew/Update` `Edit/Update` `Delete` 동일한 데이터베이스의 하나 이상의 레코드 집합 개체에 대 한, 및 멤버 함수를 호출 합니다. 자세한 내용은 레코드 [집합: 레코드 추가, 업데이트 및 삭제 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)를 참조 하세요. 대량 행 페치를 구현한 경우 고유한 함수를 작성 하 여 데이터 원본을 업데이트 해야 합니다.

1. 마지막으로 `CDatabase` 개체의 `CommitTrans` 멤버 함수를 호출 합니다. 업데이트 중 하나에서 오류가 발생 하거나 변경 내용을 취소 하기로 결정 한 경우 해당 멤버 함수를 호출 `Rollback` 합니다.

다음 예에서는 두 개의 레코드 집합을 사용 하 여 학교 등록 데이터베이스에서 학생의 등록을 삭제 하 고 학생이 등록 된 모든 클래스에서 학생을 제거 합니다. `Delete`두 레코드 집합의 호출이 모두 성공 해야 하므로 트랜잭션이 필요 합니다. 이 예제에서는가 존재 하 고 `m_dbStudentReg` , `CDatabase` 데이터 소스에 이미 연결 된 형식의 멤버 변수 및 레코드 집합 클래스와가 있다고 가정 합니다 `CEnrollmentSet` `CStudentSet` . `strStudentID`변수는 사용자 로부터 가져온 값을 포함 합니다.

```
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )
{
    // remove student from all the classes
    // the student is enrolled in

    if ( !m_dbStudentReg.BeginTrans( ) )
        return FALSE;

    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )
        return FALSE;

    CStudentSet rsStudentSet(&m_dbStudentReg);
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsStudentSet.Open(CRecordset::dynaset) )
        return FALSE;

    TRY
    {
        while ( !rsEnrollmentSet.IsEOF( ) )
        {
            rsEnrollmentSet.Delete( );
            rsEnrollmentSet.MoveNext( );
        }

        // delete the student record
        rsStudentSet.Delete( );

        m_dbStudentReg.CommitTrans( );
    }

    CATCH_ALL(e)
    {
        m_dbStudentReg.Rollback( );
        return FALSE;
    }
    END_CATCH_ALL

    rsEnrollmentSet.Close( );
    rsStudentSet.Close( );

    return TRUE;

}
```

> [!NOTE]
> `BeginTrans`또는를 호출 하지 않고를 다시 호출 `CommitTrans` `Rollback` 하면 오류가 발생 합니다.

## <a name="see-also"></a>참고 항목

[트랜잭션(ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[트랜잭션: 트랜잭션이 업데이트에 미치는 영향 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 클래스](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)
