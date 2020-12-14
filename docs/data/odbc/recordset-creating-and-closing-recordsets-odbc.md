---
description: '자세한 정보: 레코드 집합: 레코드 집합 만들기 및 닫기 (ODBC)'
title: '레코드 집합: 레코드 집합 만들기 및 닫기(ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: a8c79afe483ab9fcd03b2102ec93d6574092acf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186105"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>레코드 집합: 레코드 집합 만들기 및 닫기(ODBC)

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

이 토픽은 MFC ODBC 클래스에 적용됩니다.

레코드 집합을 사용하려면 레코드 집합 개체를 구성한 다음, 해당 `Open` 멤버 함수를 호출하여 레코드 집합의 쿼리를 실행하고 레코드를 선택합니다. 레코드 집합을 마치면 개체를 닫고 제거합니다.

이 토픽에서는 다음 내용을 설명합니다.

- [레코드 집합 개체를 만드는 시기 및 방법](#_core_creating_recordsets_at_run_time).

- [매개 변수화, 필터링, 정렬 또는 잠금을 통해 레코드 집합의 동작을 한정할 수 있는 시기 및 방법](#_core_setting_recordset_options).

- [레코드 집합 개체를 닫는 시기 및 방법](#_core_closing_a_recordset).

## <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a> 런타임에 레코드 집합 만들기

프로그램에서 레코드 집합 개체를 만들기 전에 일반적으로 애플리케이션별 레코드 집합 클래스를 작성합니다. 이 예비 단계에 대한 자세한 내용은 [MFC ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)를 참조하세요.

데이터 원본에서 레코드를 선택해야 하는 경우 다이너셋 또는 스냅샷 개체를 엽니다. 만들 개체의 형식은 애플리케이션의 데이터에서 수행해야 하는 작업과 ODBC 드라이버가 지원하는 작업에 따라 다릅니다. 자세한 내용은 [다이너셋](../../data/odbc/dynaset.md) 및 [스냅샷](../../data/odbc/snapshot.md)을 참조하세요.

#### <a name="to-open-a-recordset"></a>레코드 집합을 열려면

1. `CRecordset`에서 파생된 클래스의 개체를 만듭니다.

   힙 또는 함수의 스택 프레임에 개체를 생성할 수 있습니다.

1. 필요에 따라 기본 레코드 집합 동작을 수정합니다. 사용 가능한 옵션은 [레코드 집합 옵션 설정](#_core_setting_recordset_options)을 참조하세요.

1. 개체의 [열기](../../mfc/reference/crecordset-class.md#open) 멤버 함수를 호출합니다.

생성자에서 `CDatabase` 개체에 포인터를 전달하거나 NULL을 전달하여 [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) 멤버 함수에 의해 반환된 연결 문자열을 기반으로 프레임워크가 만들고 여는 임시 데이터베이스 개체를 사용합니다. `CDatabase` 개체가 이미 데이터 원본에 연결되었을 수 있습니다.

`Open`에 대한 호출은 SQL을 사용하여 데이터 원본에서 레코드를 선택합니다. 선택한 첫 번째 레코드(있는 경우)가 현재 레코드입니다. 이 레코드의 필드 값은 레코드 집합 개체의 필드 데이터 멤버에 저장됩니다. 레코드가 선택되면 `IsBOF` 및 `IsEOF` 멤버 함수는 모두 0을 반환합니다.

[열기](../../mfc/reference/crecordset-class.md#open) 호출에서 다음을 수행할 수 있습니다.

- 레코드 집합이 다이너셋인지 또는 스냅샷인지 여부를 지정합니다. 레코드 집합은 기본적으로 스냅샷으로 열립니다. 또는 한 번에 한 개의 레코드를 전진 스크롤만 허용하는 정향향 전용 레코드 집합을 지정할 수 있습니다.

   기본적으로 레코드 집합은 `CRecordset` 데이터 멤버 `m_nDefaultType`에 저장된 기본 유형을 사용합니다. 마법사는 `m_nDefaultType`을 마법사에서 선택한 레코드 집합 유형으로 초기화하는 코드를 작성합니다. 이 기본값을 수락하는 대신 다른 레코드 집합 형식으로 대체할 수 있습니다.

- 레코드 집합이 구성하는 기본 SQL **SELECT** 문을 대체할 문자열을 지정합니다.

- 레코드 집합이 읽기 전용인지 또는 추가 전용인지 여부를 지정합니다. 레코드 집합은 기본적으로 전체 업데이트를 허용하지만, 새 레코드만 추가하는 것으로 제한하거나 모든 업데이트를 허용하지 않을 수 있습니다.

다음 예제에서는 애플리케이션별 클래스인 `CStudentSet`의 읽기 전용 스냅샷 개체를 여는 방법을 보여줍니다.

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

`Open`을 호출한 후 개체의 멤버 함수와 데이터 멤버를 사용하여 레코드 작업을 수행합니다. 경우에 따라 데이터 원본에서 변경 내용을 포함하도록 레코드 집합을 다시 쿼리하거나 새로 고칠 수도 있습니다. 자세한 내용은 [레코드 집합: 레코드 집합 다시 쿼리 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)를 참조 하세요.

> [!TIP]
> 개발 중에 사용하는 연결 문자열은 최종 사용자에게 필요한 연결 문자열과 다를 수 있습니다. 이와 관련 하 여 응용 프로그램을 일반화 하는 방법에 대 한 아이디어는 [데이터 소스: 연결 관리 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)를 참조 하세요.

## <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a> 레코드 집합 옵션 설정

레코드 집합 개체를 구성한 후 `Open`을 호출하여 레코드를 선택하기 전에 레코드 집합의 동작을 제어하는 몇 가지 옵션을 설정할 수 있습니다. 모든 레코드 집합에 대해 다음을 수행할 수 있습니다.

- [필터](../../data/odbc/recordset-filtering-records-odbc.md)를 지정하여 레코드 선택을 제한합니다.

- 레코드에 대해 [정렬](../../data/odbc/recordset-sorting-records-odbc.md) 순서를 지정합니다.

- [매개 변수](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 지정하면 런타임에 가져오거나 계산된 정보를 사용하여 레코드를 선택할 수 있습니다.

조건이 맞는 경우 다음 옵션을 설정할 수도 있습니다.

- 레코드 집합을 업데이트할 수 있고 잠금 옵션을 지원하는 경우 업데이트에 사용되는 [잠금](../../data/odbc/recordset-locking-records-odbc.md) 메서드를 지정합니다.

> [!NOTE]
> 레코드 선택의 영향을 주려면 `Open` 멤버 함수를 호출하기 전에 이러한 옵션을 설정해야 합니다.

## <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a> 레코드 집합 닫기

레코드 집합을 마치면 레코드를 삭제하고 메모리를 할당 취소해야 합니다.

#### <a name="to-close-a-recordset"></a>레코드 집합을 닫으려면

1. [닫기](../../mfc/reference/crecordset-class.md#close) 멤버 함수를 호출합니다.

1. 레코드 집합 개체를 삭제합니다.

   함수의 스택 프레임에 선언한 경우 개체가 범위를 벗어나면 개체가 자동으로 삭제됩니다. 그렇지 않으면 연산자를 사용 **`delete`** 합니다.

`Close`는 레코드 집합의 `HSTMT` 핸들을 해제합니다. C++ 개체를 삭제하지 않습니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 스크롤(ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[레코드 집합: 레코드 추가, 업데이트 및 삭제 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
