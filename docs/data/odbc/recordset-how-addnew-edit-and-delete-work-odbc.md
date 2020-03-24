---
title: '레코드 집합: AddNew, Edit 및 Delete의 작동 방식(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212911"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>레코드 집합: AddNew, Edit 및 Delete의 작동 방식(ODBC)

이 항목은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 클래스 `CRecordset`의 `AddNew`, `Edit`및 `Delete` 멤버 함수를 사용 하는 방법에 대해 설명 합니다. 다음 내용을 다룹니다.

- [레코드를 추가 하는 방법](#_core_adding_a_record)

- [추가 된 레코드의 표시 유형](#_core_visibility_of_added_records)

- [레코드 편집 작동 방법](#_core_editing_an_existing_record)

- [레코드 삭제 작동 방식](#_core_deleting_a_record)

> [!NOTE]
>  이 토픽은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 사용 하는 경우 레코드 [집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

추가 기능으로, [레코드 필드 교환: Rfx 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md), 업데이트 작업에서 rfx의 해당 역할을 설명 하는 것을 확인할 수 있습니다.

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>레코드 추가

레코드 집합에 새 레코드를 추가 하려면 레코드 집합의 [AddNew](../../mfc/reference/crecordset-class.md#addnew) 멤버 함수를 호출 하 고, 새 레코드의 필드 데이터 멤버 값을 설정 하 고, [Update](../../mfc/reference/crecordset-class.md#update) 멤버 함수를 호출 하 여 데이터 소스에 레코드를 써야 합니다.

`AddNew`를 호출 하기 위한 사전 조건으로, 레코드 집합을 읽기 전용으로 열지 않아야 합니다. `CanUpdate` 및 `CanAppend` 멤버 함수를 사용 하 여 이러한 조건을 확인할 수 있습니다.

`AddNew`를 호출 하는 경우:

- 편집 버퍼의 레코드는 저장 되므로 작업이 취소 되 면 해당 콘텐츠를 복원할 수 있습니다.

- 필드 데이터 멤버에 플래그가 지정 되어 나중에 변경 내용을 검색할 수 있습니다. 필드 데이터 멤버도 clean (변경 되지 않음)으로 표시 되 고를 Null로 설정 합니다.

`AddNew`를 호출한 후 편집 버퍼는 새 빈 레코드를 나타내며 값으로 채워질 준비가 완료 된 것입니다. 이렇게 하려면 값을 할당 하 여 수동으로 설정 합니다. 필드에 대 한 실제 데이터 값을 지정 하는 대신 `SetFieldNull`를 호출 하 여 Null 값을 지정할 수 있습니다.

변경 내용을 커밋하려면 `Update`를 호출 합니다. 새 레코드에 대 한 `Update`를 호출 하는 경우:

- ODBC 드라이버가 `::SQLSetPos` ODBC API 함수를 지 원하는 경우 MFC는 함수를 사용 하 여 데이터 원본에 레코드를 추가 합니다. `::SQLSetPos`에서 MFC는 SQL 문을 생성 하 고 처리할 필요가 없기 때문에 더 효율적으로 레코드를 추가할 수 있습니다.

- `::SQLSetPos`를 사용할 수 없는 경우 MFC는 다음을 수행 합니다.

   1. 변경 내용이 검색 되지 않으면 `Update`은 아무 작업도 수행 하지 않고 0을 반환 합니다.

   1. 변경 사항이 있는 경우 `Update` SQL **INSERT** 문을 생성 합니다. 모든 더티 필드 데이터 멤버가 나타내는 열이 **INSERT** 문에 나열 됩니다. 열을 강제로 포함 하려면 [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) 멤버 함수를 호출 합니다.

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`는 새 레코드를 커밋합니다. 즉, **INSERT** 문이 실행 되 고, 트랜잭션이 진행 되 고 있지 않은 경우 레코드는 데이터 원본의 테이블 (및 스냅숏이 아닌 경우 레코드 집합)에 커밋됩니다.

   1. 저장 된 레코드가 편집 버퍼로 복원 됩니다. **INSERT** 문이 성공적으로 실행 되었는지 여부에 관계 없이 `AddNew`를 호출 하기 전의 레코드는 현재 다시 실행 됩니다.

   > [!TIP]
   > 새 레코드에 대 한 완전 한 제어를 사용 하려면 값을 포함 하는 필드의 값을 설정한 다음 필드에 대 한 포인터와 매개 변수 TRUE (기본값)를 사용 하 여 `SetFieldNull`를 호출 하 여 Null로 유지 될 필드를 명시적으로 설정 합니다. 필드가 데이터 원본에 기록 되지 않도록 하려면 필드에 대 한 포인터와 매개 변수 FALSE를 사용 하 여 `SetFieldDirty`를 호출 하 고 필드의 값을 수정 하지 마십시오. 필드가 Null 일 수 있는지 여부를 확인 하려면 `IsFieldNullable`를 호출 합니다.

   > [!TIP]
   > 레코드 집합 데이터 멤버의 값이 변경 되는 경우를 감지 하기 위해 MFC는 레코드 집합에 저장할 수 있는 각 데이터 형식에 적합 한 PSEUDO_NULL 값을 사용 합니다. 필드를 명시적으로 PSEUDO_NULL 값으로 설정 해야 하 고 필드를 Null로 표시 해야 하는 경우에는 `SetFieldNull`를 호출 하 여 첫 번째 매개 변수의 필드 주소를 전달 하 고 두 번째 매개 변수에서 FALSE를 전달 해야 합니다.

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>추가 된 레코드의 표시 유형

추가 된 레코드가 레코드 집합에 표시 되는 경우 추가 된 레코드는 다음과 같은 두 가지 항목에 따라 표시 되 고 때때로 표시 되지 않을 수도 있습니다.

- 드라이버를 사용할 수 있습니다.

- 프레임 워크에서 사용할 수 있는 작업입니다.

ODBC 드라이버가 `::SQLSetPos` ODBC API 함수를 지 원하는 경우 MFC는 함수를 사용 하 여 레코드를 추가 합니다. `::SQLSetPos`를 사용 하 여 업데이트 가능한 모든 MFC 레코드 집합에 추가 된 레코드를 볼 수 있습니다. 함수를 지원 하지 않으면 추가 된 레코드가 표시 되지 않으므로 `Requery`를 호출 하 여 해당 레코드를 확인 해야 합니다. 또한 `::SQLSetPos`를 사용 하는 것이 더 효율적입니다.

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>기존 레코드 편집

레코드 집합에서 기존 레코드를 편집 하려면 레코드를 스크롤하고, 레코드 집합의 [Edit](../../mfc/reference/crecordset-class.md#edit) 멤버 함수를 호출 하 고, 새 레코드의 필드 데이터 멤버 값을 설정 하 고, [Update](../../mfc/reference/crecordset-class.md#update) 멤버 함수를 호출 하 여 변경 된 레코드를 데이터 소스에 써야 합니다.

`Edit`를 호출 하기 위한 사전 조건으로 레코드 집합을 업데이트할 수 있어야 합니다. `CanUpdate` 및 `IsDeleted` 멤버 함수를 사용 하 여 이러한 조건을 확인할 수 있습니다. 또한 현재 레코드는 아직 삭제 되지 않아야 하며 레코드 집합에 레코드가 있어야 합니다 (`IsBOF` 및 `IsEOF` 0 반환).

`Edit`를 호출 하면 편집 버퍼 (현재 레코드)의 레코드가 저장 됩니다. 저장 된 레코드의 값은 나중에 필드가 변경 되었는지 여부를 검색 하는 데 사용 됩니다.

`Edit`를 호출한 후에도 편집 버퍼는 현재 레코드를 나타내지만 이제 필드 데이터 멤버에 대 한 변경 내용을 적용할 준비가 된 것입니다. 레코드를 변경 하려면 편집 하려는 모든 필드 데이터 멤버의 값을 수동으로 설정 합니다. 필드에 대 한 실제 데이터 값을 지정 하는 대신 `SetFieldNull`를 호출 하 여 Null 값을 지정할 수 있습니다. 변경 내용을 커밋하려면 `Update`를 호출 합니다.

> [!TIP]
> `AddNew` 또는 `Edit` 모드를 시작 하려면 매개 변수 *AFX_MOVE_REFRESH*를 사용 하 여 `Move`를 호출 합니다.

`Update`를 호출 하기 위한 사전 조건으로 레코드 집합은 비어 있지 않아야 하 고 현재 레코드는 삭제 되지 않아야 합니다. `IsBOF`, `IsEOF`및 `IsDeleted` 모두 0을 반환 해야 합니다.

편집 된 레코드에 대 한 `Update`를 호출 하는 경우:

- ODBC 드라이버가 `::SQLSetPos` ODBC API 함수를 지 원하는 경우 MFC는 함수를 사용 하 여 데이터 원본에 대 한 레코드를 업데이트 합니다. `::SQLSetPos`에서 드라이버는 편집 버퍼를 서버에 있는 해당 레코드와 비교 하 여 두 서버가 서로 다른 경우 서버에서 해당 레코드를 업데이트 합니다. `::SQLSetPos`에서 MFC는 SQL 문을 생성 하 고 처리할 필요가 없기 때문에 더 효율적으로 레코드를 업데이트할 수 있습니다.

   \- 또는-

- `::SQLSetPos`를 사용할 수 없는 경우 MFC는 다음을 수행 합니다.

   1. 변경 내용이 없는 경우 `Update`은 아무 작업도 수행 하지 않고 0을 반환 합니다.

   1. 변경 사항이 있는 경우 `Update`는 SQL **UPDATE** 문을 생성 합니다. **UPDATE** 문에 나열 된 열은 변경 된 필드 데이터 멤버를 기반으로 합니다.

   1. `Update` 커밋- **update** 문을 실행 하 고, 트랜잭션이 진행 중일 때는 레코드가 변경 되지만 커밋되지는 않습니다 (트랜잭션이 업데이트에 미치는 영향에 대 한 자세한 내용은 [트랜잭션: 레코드 집합에서 트랜잭션 수행 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) 참조). ODBC는 레코드의 복사본을 유지 합니다 .이도 변경 됩니다.

   1. `AddNew`에 대 한 프로세스와 달리 `Edit` 프로세스는 저장 된 레코드를 복원 하지 않습니다. 편집 된 레코드는 현재 레코드로 그대로 남아 있습니다.

   > [!CAUTION]
   > `Update`를 호출 하 여 레코드 집합을 업데이트 하려면 레코드 집합에 테이블의 기본 키를 구성 하는 모든 열 (또는 테이블에 있는 고유 인덱스의 모든 열 또는 행을 고유 하 게 식별 하기 위한 충분 한 열)이 포함 되어 있는지 확인 합니다. 경우에 따라 프레임 워크는 레코드 집합에서 선택한 열만 사용 하 여 업데이트할 테이블의 레코드를 식별할 수 있습니다. 필요한 열이 없으면 테이블에서 여러 레코드를 업데이트할 수 있습니다. 이 경우 `Update`를 호출할 때 프레임 워크에서 예외를 throw 합니다.

   > [!TIP]
   > 이전에 함수를 호출 하 고 `Update`를 호출 하기 전에 `AddNew` 또는 `Edit`를 호출 하는 경우 편집 버퍼는 저장 된 레코드로 새로 고쳐지고 진행 중인 새 레코드 또는 편집 된 레코드를 대체 합니다. 이 동작은 `AddNew` 또는 `Edit`를 중단 하 고 새 작업을 시작 하는 방법을 제공 합니다. 진행 중인 레코드가 잘못 된 것으로 확인 되 면 `Edit` 또는 `AddNew`을 다시 호출 하기만 하면 됩니다.

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>레코드 삭제

레코드 집합에서 레코드를 삭제 하려면 레코드를 스크롤하고 레코드 집합의 [Delete](../../mfc/reference/crecordset-class.md#delete) 멤버 함수를 호출 해야 합니다. `AddNew` 및 `Edit`와 달리 `Delete`는 `Update`에 대 한 일치 호출이 필요 하지 않습니다.

`Delete`를 호출 하기 위한 사전 조건으로 레코드 집합은 업데이트 가능 해야 하며 레코드에 있어야 합니다. `CanUpdate`, `IsBOF`, `IsEOF`및 `IsDeleted` 멤버 함수를 사용 하 여 이러한 조건을 확인할 수 있습니다.

`Delete`를 호출 하는 경우:

- ODBC 드라이버가 `::SQLSetPos` ODBC API 함수를 지 원하는 경우 MFC는 함수를 사용 하 여 데이터 원본에 대 한 레코드를 삭제 합니다. 일반적으로 `::SQLSetPos`는 SQL을 사용 하는 것 보다 더 효율적입니다.

   \- 또는-

- `::SQLSetPos`를 사용할 수 없는 경우 MFC는 다음을 수행 합니다.

   1. 편집 버퍼의 현재 레코드는 `AddNew` 및 `Edit`와 같이 백업 되지 않습니다.

   1. `Delete` 레코드를 제거 하는 SQL **DELETE** 문을 생성 합니다.

      편집 버퍼의 현재 레코드는 `AddNew` 및 `Edit`저장 되지 않습니다.

   1. 삭제를 커밋하는 `Delete`- **DELETE** 문을 실행 합니다. 레코드는 데이터 원본에서 삭제 된 것으로 표시 되며, 레코드는 스냅숏이 면 ODBC에서로 표시 됩니다.

   1. 삭제 된 레코드의 값은 여전히 레코드 집합의 필드 데이터 멤버에 있지만 필드 데이터 멤버는 Null로 표시 되 고 레코드 집합의 `IsDeleted` 멤버 함수는 0이 아닌 값을 반환 합니다.

   > [!NOTE]
   > 레코드를 삭제 한 후에는 다른 레코드로 스크롤하여 편집 버퍼를 새 레코드의 데이터로 다시 채워야 합니다. `Delete`을 다시 호출 하거나 `Edit`를 호출 하면 오류가 발생 합니다.

업데이트 작업에 사용 되는 SQL 문에 대 한 자세한 내용은 [sql](../../data/odbc/sql.md)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 업데이트에 대한 추가 정보(ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[RFX(레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)
