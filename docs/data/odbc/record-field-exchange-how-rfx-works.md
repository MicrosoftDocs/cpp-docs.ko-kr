---
description: '자세히 알아보기: 레코드 필드 교환: RFX 작동 방식'
title: '레코드 필드 교환: RFX 작동 방식'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 81b8d65c4c4f6344456c85ace057ad093c1c18b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268576"
---
# <a name="record-field-exchange-how-rfx-works"></a>레코드 필드 교환: RFX 작동 방식

이 항목에서는 RFX 프로세스에 대해 설명 합니다. 다음은이에 대 한 고급 항목입니다.

- [RFX 및 레코드 집합](#_core_rfx_and_the_recordset)

- [RFX 프로세스](#_core_the_record_field_exchange_process)

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 클래스에 적용됩니다. 대량 행 페치를 사용하는 경우 대량 레코드 필드 교환(대량 RFX)이 구현됩니다. 대량 RFX는 RFX와 비슷합니다. 차이점을 이해 하려면 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a> RFX 및 레코드 집합

레코드 집합 개체의 필드 데이터 멤버는 한 레코드의 선택 된 열을 포함 하는 편집 버퍼를 구성 합니다. 레코드 집합을 처음 열 때 첫 번째 레코드를 읽으려고 할 때 RFX는 선택한 각 열을 해당 필드 데이터 멤버의 주소에 바인딩합니다 (연결). 레코드 집합에서 레코드를 업데이트할 때 RFX는 ODBC API 함수를 호출 하 여 드라이버에 SQL **UPDATE** 또는 **INSERT** 문을 보냅니다. RFX는 필드 데이터 멤버에 대 한 정보를 사용 하 여 작성할 열을 지정 합니다.

프레임 워크는 특정 단계에서 편집 버퍼를 백업 하므로 필요한 경우 콘텐츠를 복원할 수 있습니다. RFX는 새 레코드를 추가 하기 전에 및 기존 레코드를 편집 하기 전에 편집 버퍼를 백업 합니다. 예를 들어 다음 호출 후에는 편집 버퍼를 복원 `Update` `AddNew` 합니다. 예를 들어를 호출 하기 전에 다른 레코드로 이동 하는 등의 방법으로 새로 변경한 편집 버퍼를 중단 하는 경우에는 편집 버퍼가 복원 되지 않습니다 `Update` .

데이터 원본과 레코드 집합의 필드 데이터 멤버 간에 데이터를 교환 하는 것 외에도 RFX는 바인딩 매개 변수를 관리 합니다. 레코드 집합이 열리면 매개 변수 데이터 멤버는을 생성 하는 SQL 문에서 "?" 자리 표시자의 순서에 따라 바인딩됩니다 `CRecordset::Open` . 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.

레코드 집합 클래스의 재정의는 `DoFieldExchange` 모든 작업을 수행 하 여 데이터를 양방향으로 이동 합니다. DDX (dialog data exchange)와 마찬가지로 RFX에는 클래스의 데이터 멤버에 대 한 정보가 필요 합니다. 마법사는 `DoFieldExchange` 마법사에서 지정한 필드 데이터 멤버 이름 및 데이터 형식에 따라의 레코드 집합 관련 구현을 작성 하 여 필요한 정보를 제공 합니다.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a> 레코드 필드 교환 프로세스

이 섹션에서는 레코드 집합 개체가 열릴 때와 레코드를 추가, 업데이트 및 삭제 하는 경우의 RFX 이벤트 시퀀스에 대해 설명 합니다. [레코드 집합을 여는 동안](#_core_sequence_of_rfx_operations_during_recordset_open) rfx 작업의 테이블 시퀀스와이 항목에서 스크롤 하는 [동안 rfx 작업의](#_core_sequence_of_rfx_operations_during_scrolling) 테이블 시퀀스는 rfx가 `Move` 레코드 집합에서 명령을 처리 하 고 rfx가 업데이트를 관리 하는 프로세스를 보여 줍니다. 이러한 프로세스 중에는 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 를 호출 하 여 다양 한 작업을 수행 합니다. `m_nOperation` [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 개체의 데이터 멤버는 요청 된 작업을 결정 합니다. 레코드 집합을 읽는 것이 유용할 수 있습니다. 레코드 집합에서 [레코드를 선택 하는 방법 (odbc)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) 및 레코드 집합:이 자료를 읽기 전에 레코드 집합에서 레코드를 업데이트 하는 방법 [(odbc)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: 열 및 매개 변수의 초기 바인딩

다음 RFX 작업은 레코드 집합 개체의 [Open](../../mfc/reference/crecordset-class.md#open) 멤버 함수를 호출할 때 표시 된 순서 대로 발생 합니다.

- 레코드 집합에 매개 변수 데이터 멤버가 있는 경우 프레임 워크는를 호출 하 여 매개 변수를 `DoFieldExchange` 레코드 집합의 SQL 문 문자열에 있는 매개 변수 자리 표시자에 바인딩합니다. 매개 변수 값의 데이터 형식 종속 표현은 **SELECT** 문에서 찾은 각 자리 표시자에 사용 됩니다. 이는 SQL 문이 준비 된 후 실행 되기 전에 발생 합니다. 문 준비에 대 한 자세한 내용은 `::SQLPrepare` ODBC *프로그래머 참조* 에서 함수를 참조 하세요.

- 프레임 워크는 `DoFieldExchange` 두 번째로를 호출 하 여 선택한 열의 값을 레코드 집합의 해당 필드 데이터 멤버에 바인딩합니다. 이렇게 하면 레코드 집합 개체가 첫 번째 레코드의 열을 포함 하는 편집 버퍼로 설정 됩니다.

- 레코드 집합은 SQL 문을 실행 하 고 데이터 소스는 첫 번째 레코드를 선택 합니다. 레코드의 열이 레코드 집합의 필드 데이터 멤버에 로드 됩니다.

다음 표에서는 레코드 집합을 열 때의 RFX 작업 순서를 보여 줍니다.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> 레코드 집합을 여는 동안 수행 되는 RFX 작업 시퀀스

|[operationName]|DoFieldExchange 작업|데이터베이스/s q m 작업|
|--------------------|-------------------------------|-----------------------------|
|1. 레코드 집합을 엽니다.|||
||2. SQL 문을 작성 합니다.||
|||3. SQL을 보냅니다.|
||4. 매개 변수 데이터 멤버를 바인딩합니다.||
||5. 필드 데이터 멤버를 열에 바인딩합니다.||
|||6. ODBC는 데이터를 이동 하 고 채웁니다.|
||7. c + +에 대 한 데이터를 수정 합니다.||

레코드 집합은 ODBC의 준비 된 실행을 사용 하 여 동일한 SQL 문으로 빠르게 다시 쿼리할 수 있도록 합니다. 준비 된 실행에 대 한 자세한 내용은 [ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference)를 참조 하세요.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a> RFX: 스크롤

레코드 간에 스크롤하면 프레임 워크가 `DoFieldExchange` 를 호출 하 여 이전에 필드 데이터 멤버에 저장 된 값을 새 레코드의 값으로 바꿉니다.

다음 표에서는 사용자가 레코드에서 레코드로 이동할 때의 RFX 작업 시퀀스를 보여 줍니다.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a> 스크롤 중의 RFX 작업 시퀀스

|[operationName]|DoFieldExchange 작업|데이터베이스/s q m 작업|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` 다른 Move 함수 중 하나를 호출 합니다.|||
|||2. ODBC는 데이터를 이동 하 고 채웁니다.|
||3. c + +에 대 한 데이터를 수정 합니다.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: 새 레코드를 추가 하 고 기존 레코드를 편집 합니다.

새 레코드를 추가 하는 경우 레코드 집합은 새 레코드의 콘텐츠를 빌드하기 위해 편집 버퍼로 작동 합니다. 레코드를 추가 하는 것과 마찬가지로 레코드를 편집 하려면 레코드 집합의 필드 데이터 멤버 값을 변경 해야 합니다. RFX 관점에서 시퀀스는 다음과 같습니다.

1. 레코드 집합의 [AddNew](../../mfc/reference/crecordset-class.md#addnew) 또는 [Edit](../../mfc/reference/crecordset-class.md#edit) 멤버 함수를 호출 하면 RFX는 나중에 복원할 수 있도록 현재 편집 버퍼를 저장 합니다.

1. `AddNew` 또는 `Edit` 는 RFX가 변경 된 필드 데이터 멤버를 검색할 수 있도록 편집 버퍼에서 필드를 준비 합니다.

   새 레코드에 새 레코드와 비교할 이전 값이 없기 때문에는 `AddNew` 각 필드 데이터 멤버의 값을 PSEUDO_NULL 값으로 설정 합니다. 나중에를 호출할 때 `Update` RFX는 각 데이터 멤버의 값을 PSEUDO_NULL 값과 비교 합니다. 차이가 있는 경우 데이터 멤버가 설정 된 것입니다. (PSEUDO_NULL는 true Null 값을 포함 하는 레코드 열과 같지 않으며 c + + NULL과 동일 하지 않습니다.)

   호출에서는에 `Update` 대 한 호출과 달리 `AddNew` PSEUDO_NULL를 `Update` `Edit` 사용 하는 대신 이전에 저장 된 값과 업데이트 된 값을 비교 합니다. 차이점은 비교를 `AddNew` 위해 이전에 저장 된 값이 없기 때문입니다.

1. 값을 편집 하거나 새 레코드로 채울 필드 데이터 멤버의 값을 직접 설정 합니다. 여기에는를 호출 하는 작업이 포함 `SetFieldNull` 됩니다.

1. 2 단계에서 설명한 대로 [업데이트](../../mfc/reference/crecordset-class.md#update) 를 호출 하면 변경 된 필드 데이터 멤버가 확인 됩니다 ( [스크롤 중에는 RFX 작업의 테이블 순서](#_core_sequence_of_rfx_operations_during_scrolling)참조). 변경 된 내용이 없는 경우는 `Update` 0을 반환 합니다. 일부 필드 데이터 멤버가 변경 된 경우는 `Update` 레코드의 모든 업데이트 된 필드에 대 한 값을 포함 하는 SQL **INSERT** 문을 준비 하 고 실행 합니다.

1. 의 `AddNew` 경우는 `Update` 호출 전에 현재 레코드의 이전에 저장 된 값을 복원 하는 것으로 끝납니다 `AddNew` . 의 경우 `Edit` 새로 편집한 값은 그대로 유지 됩니다.

다음 표에서는 새 레코드를 추가 하거나 기존 레코드를 편집할 때의 RFX 작업 시퀀스를 보여 줍니다.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>AddNew 및 Edit 중의 RFX 작업 시퀀스

|[operationName]|DoFieldExchange 작업|데이터베이스/s q m 작업|
|--------------------|-------------------------------|-----------------------------|
|1. 또는를 호출 합니다. `AddNew` `Edit`|||
||2. 편집 버퍼를 백업 합니다.||
||3 .의 경우 `AddNew` 필드 데이터 멤버를 "clean" 및 Null로 표시 합니다.||
|4. 레코드 집합 필드 데이터 멤버에 값을 할당 합니다.|||
|5. `Update` 를 호출 합니다.|||
||6. 변경 된 필드를 확인 합니다.||
||7. 용  `AddNew` 또는 **UPDATE** 문에 대해 SQL INSERT 문을 작성 합니다 `Edit` .||
|||8. SQL을 보냅니다.|
||9 .의 경우 `AddNew` 편집 버퍼를 백업 된 콘텐츠로 복원 합니다. `Edit`에서 백업을 삭제 합니다.||

### <a name="rfx-deleting-existing-records"></a>RFX: 기존 레코드 삭제

레코드를 삭제 하면 RFX는 모든 필드를 NULL로 설정 하 여 레코드를 삭제 하 고 해당 레코드를 외부로 이동 해야 한다는 알림을 표시 합니다. 다른 RFX 시퀀스 정보는 필요 하지 않습니다.

## <a name="see-also"></a>참고 항목

[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 사용](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[매크로, 전역 함수 및 전역 변수](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 클래스](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
