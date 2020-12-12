---
description: '자세한 정보: 레코드 집합: 데이터 열 동적 바인딩 (ODBC)'
title: '레코드 집합: 데이터 열 동적 바인딩(ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: cb141874fa39b06e8e000c03e538021650facf91
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322381"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>레코드 집합: 데이터 열 동적 바인딩(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

레코드 집합은 디자인 시간에 지정하는 테이블 열의 바인딩을 관리하지만 디자인 시간에 알려지지 않은 열을 바인딩하려는 경우가 있습니다. 이 토픽에서는 다음 내용을 설명합니다.

- [레코드 집합에 동적으로 열을 바인딩하려는 경우](#_core_when_you_might_bind_columns_dynamically)

- [런타임에 동적으로 열을 바인딩하는 방법](#_core_how_to_bind_columns_dynamically)

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 여기서 설명하는 방법은 대량 행 페치를 사용 중인 경우 일반적으로 권장되지 않습니다. 대량 행 페치에 대 한 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

## <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a> 동적으로 열을 바인딩하려는 경우

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

디자인 타임에 MFC 애플리케이션 마법사 또는 [MFC ODBC 소비자 마법사](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(**클래스 추가** 에서 나온)는 데이터 원본의 알려진 테이블 및 열을 기반으로 레코드 집합 클래스를 만듭니다. 해당 테이블 및 열을 디자인할 때와 나중에 애플리케이션이 런타임에 이들을 사용할 때의 사이에 데이터베이스를 변경할 수 있습니다. 개발자 또는 다른 사용자가 애플리케이션의 레코드 집합이 의존하는 테이블에서 테이블을 추가 또는 삭제하거나 열을 추가 또는 삭제할 수 있습니다. 아마도 모든 데이터 액세스 애플리케이션의 경우 이 상황은 문제가 없지만, 데이터베이스 스키마가 변경된 경우 다시 디자인하고 다시 컴파일하는 방법 외에 다른 해결 방법이 있을까요? 이 토픽의 목적은 바로 이 질문에 답하는 것입니다.

이 토픽에서는 동적으로 열을 바인딩할 수 있는 가장 일반적인 상황을 설명합니다. 먼저, 알려진 데이터베이스 스키마를 기반으로 하는 레코드 집합으로 시작하고 런타임에 추가 열을 처리하려고 합니다. 또한 이 토픽에서는 추가 열이 `CString` 데이터 멤버에 매핑된다고 가정하지만(가장 일반적인 경우), 다른 데이터 형식을 관리하는 데 도움이 되는 추천도 제공합니다.

약간의 추가 코드를 사용하여 다음을 수행할 수 있습니다.

- [런타임에 사용 가능한 열 확인](#_core_how_to_bind_columns_dynamically)

- [런타임에 동적으로 추가 열을 레코드 집합에 바인딩](#_core_adding_the_columns)

레코드 집합은 여전히 디자인 타임에 알고 있는 열에 대한 데이터 멤버를 포함합니다. 또한 새 열이 대상 테이블에 추가되었는지 여부를 동적으로 결정하고, 추가된 경우 해당 새 열을 할당된 스토리지(레코드 집합 데이터 멤버가 아닌)에 동적으로 바인딩하는 약간의 추가 코드도 포함합니다.

삭제된 테이블 또는 열 등의 다른 동적 바인딩 사례는 이 토픽에서 다루지 않습니다. 그러한 경우에는 ODBC API 호출을 더 직접적으로 사용해야 합니다. 자세한 내용은 [ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference)를 참조 하세요.

## <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a> 동적으로 열을 바인딩하는 방법

동적으로 열을 바인딩하려면 추가 열의 이름을 알고 있어야(또는 결정할 수 있어야) 합니다. 또한 추가 필드 데이터 멤버에 대한 스토리지를 할당하고, 해당 이름 및 형식을 지정하고, 추가하는 열 수를 지정해야 합니다.

다음 설명에서는 두 개의 서로 다른 레코드 집합을 언급합니다. 첫 번째는 대상 테이블에서 레코드를 선택하는 기본 레코드 집합입니다. 두 번째는 대상 테이블의 열에 대 한 정보를 가져오는 데 사용되는 특수 열 레코드 집합입니다.

### <a name="general-process"></a><a name="_core_the_general_process"></a> 일반 프로세스

가장 일반적인 수준에서 다음 단계를 따릅니다.

1. 기본 레코드 집합 개체를 생성합니다.

   필요에 따라 열린 `CDatabase`에 대한 포인터를 전달하거나 무언가 다른 방법으로 열 레코드 집합에 연결 정보를 제공할 수 있습니다.

1. 동적으로 열을 추가하는 단계를 수행합니다.

   아래의 열 추가에서 설명하는 프로세스를 참조하세요.

1. 기본 레코드 집합을 엽니다.

   레코드 집합은 레코드를 선택하고 RFX(레코드 필드 교환)를 사용하여 정적 열(레코드 집합 필드 데이터 멤버에 매핑된 열) 및 동적 열(할당하는 추가 스토리지에 매핑된 열)을 모두 바인딩합니다.

### <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a> 열 추가

런타임에 추가된 열을 동적으로 바인딩하려면 다음 단계를 수행해야 합니다.

1. 런타임에 대상 테이블에 있는 열을 결정합니다. 레코드 집합 클래스가 디자인되었으므로 테이블에 추가된 열의 목록에서 해당 정보를 추출합니다.

   데이터 원본에서 대상 테이블에 대한 열 정보(예: 열 이름 및 데이터 형식)를 쿼리하도록 디자인된 열 레코드 집합 클래스를 사용하는 것이 좋은 방법입니다.

1. 새 필드 데이터 멤버에 대한 스토리지를 제공합니다. 기본 레코드 집합 클래스는 알려지지 않은 열에 대한 필드 데이터 멤버를 포함하지 않으므로 이름, 결과 값, 그리고 아마도 데이터 형식 정보(열의 데이터 형식이 다른 경우)를 저장할 위치를 제공해야 합니다.

   한 가지 방법은 하나 이상의 동적 목록을 만드는 것입니다(예: 새 열의 이름에 대한 목록, 해당 결과 값에 대한 목록 및 해당 데이터 형식에 대한 목록(필요한 경우)). 이 목록, 특히 값 목록은 해당 정보 및 바인딩에 필요한 스토리지를 제공합니다. 다음 그림은 목록 만들기를 보여줍니다.

   ![동적으로 바인딩할 열 목록 만들기](../../data/odbc/media/vc37w61.gif "동적으로 바인딩할 열 목록 만들기")<br/>
   동적으로 바인딩할 열 목록 만들기

1. 각 추가된 열에 대한 기본 레코드 집합의 `DoFieldExchange` 함수에 RFX 함수 호출을 추가합니다. 해당 RFX 호출은 추가 열을 포함한 레코드를 페치하는 작업과 레코드 집합 데이터 멤버 또는 동적으로 제공된 멤버용 스토리지에 열을 바인딩하는 작업을 수행합니다.

   한 가지 방법은 기본 레코드 집합의 `DoFieldExchange` 함수에 새 열의 목록을 순환하면서 목록의 각 열에 적절한 RFX 함수를 호출하는 루프를 추가하는 것입니다. 각 RFX 호출 시, 열 이름 목록의 열 이름 및 결과 값 목록의 해당 멤버의 스토리지 위치를 전달합니다.

### <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a> 열 목록

작업해야 하는 목록 4개는 다음 표와 같습니다.

| 목록 | 설명 |
|--|--|
| **Current-Table-Columns** | (그림에서 목록 1) 데이터 원본의 테이블에 현재 있는 열의 목록입니다. 이 목록은 레코드 집합에 현재 바인딩된 열의 목록과 일치할 수 있습니다. |
| **Bound-Recordset-Columns** | (그림에서 목록 2) 레코드 집합에 바인딩된 열의 목록입니다. 이 열은 `DoFieldExchange` 함수에 RFX 문을 이미 포함합니다. |
| **Columns-To-Bind-Dynamically** | (그림에서 목록 3) 테이블에 있지만 레코드 집합에 없는 열의 목록입니다. 이는 동적으로 바인딩할 열입니다. |
| **Dynamic-Column-Values** | (그림에서 목록 4) 동적으로 바인딩하는 열에서 검색한 값에 대한 스토리지를 포함하는 목록입니다. 이 목록의 요소는 Columns-to-Bind-Dynamically의 요소와 일대일로 대응합니다. |

### <a name="building-your-lists"></a><a name="_core_building_your_lists"></a> 목록 만들기

일반적인 전략을 염두에 두고 세부 정보를 설정할 수 있습니다. 이 토픽의 나머지 부분에 나오는 절차는 [열 목록](#_core_lists_of_columns)에 표시된 목록을 만드는 방법을 보여줍니다. 이 절차는 다음과 같은 작업을 안내합니다.

- [레코드 집합에 없는 열 이름 확인](#_core_determining_which_table_columns_are_not_in_your_recordset)

- [테이블에 새로 추가된 열에 대한 동적 스토리지 제공](#_core_providing_storage_for_the_new_columns)

- [새 열에 대한 RFX 호출을 동적으로 추가](#_core_adding_rfx_calls_to_bind_the_columns)

### <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> 레코드 집합에 없는 테이블 열 결정

기본 레코드 집합에 이미 바인딩된 열의 목록을 포함하는 목록(Bound-Recordset-Columns, 그림에서 목록 2)을 만듭니다. 그런 다음, 데이터 원본의 테이블에 있지만 기본 레코드 집합에 없는 열 이름을 포함하는 목록(Columns-to-Bind-Dynamically: Current-Table-Columns와 Bound-Recordset-Columns에서 파생됨)을 만듭니다.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>레코드 집합에 없는 열(Columns-to-Bind-Dynamically)의 이름을 확인하려면 다음을 수행합니다.

1. 기본 레코드 집합에 이미 바인딩된 열의 목록(Bound-Recordset-Columns)을 만듭니다.

   한 가지 방법은 디자인 타임에 Bound-Recordset-Columns를 만드는 것입니다. 레코드 집합의 `DoFieldExchange` 함수에서 RFX 함수 호출을 시각적으로 검사하여 해당 이름을 가져올 수 있습니다. 그런 다음, 목록을 해당 이름으로 초기화된 배열로 설정합니다.

   예를 들어 다음 그림은 요소가 3개인 Bound-Recordset-Columns(목록 2)를 보여줍니다. Bound-Recordset-Columns에는 Current-Table-Columns(목록 1)에 표시된 전화 번호 열이 없습니다.

1. Current-Table-Columns와 Bound-Recordset-Columns를 비교하여 기본 레코드 집합에 아직 바인딩되지 않은 열의 목록(Columns-to-Bind-Dynamically)을 만듭니다.

   한 가지 방법은 런타임에 테이블의 열 목록(Current-Table-Columns) 및 레코드 집합에 이미 바인딩된 열의 목록(Bound-Recordset-Columns)을 병렬로 순환하는 것입니다. Bound-Recordset-Columns에 나타나지 않는 Current-Table-Columns의 이름을 Columns-to-Bind-Dynamically에 넣습니다.

   예를 들어 그림은 요소 한 개(전화 번호 열)가 있는 Columns-to-Bind-Dynamically(목록 3)를 보여줍니다. 전화 번호 열은 Current-Table-Columns(목록 1)에는 있지만 Bound-Recordset-Columns(목록 2)에는 없습니다.

1. 동적으로 바인딩할 열의 목록(Columns-to-Bind-Dynamically)에 저장된 각 열 이름에 해당하는 데이터 값을 저장하는 Dynamic-Column-Values의 목록(그림의 목록 4)을 만듭니다.

   이 목록의 요소는 새 레코드 집합 필드 데이터 멤버 역할을 하며, 동적 열이 바인딩되는 스토리지 위치입니다. 목록에 대한 자세한 내용은 [열 목록](#_core_lists_of_columns)을 참조하세요.

### <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a> 새 열에 대한 스토리지 제공

다음으로, 동적으로 바인딩할 열에 대한 스토리지 위치를 설정합니다. 그 목적은 각 열의 값을 저장하는 목록 요소를 제공하는 것입니다. 이 스토리지 위치는 일반적으로 바인딩된 열을 저장하는 레코드 집합 멤버 변수와 유사합니다.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>새 열(Dynamic-Column-Values)에 대한 동적 스토리지를 제공하려면 다음을 수행합니다.

1. 각 열에 있는 데이터의 값을 포함하는 Dynamic-Column-Values를
Columns-to-Bind-Dynamically와 병렬로 만듭니다.

   예를 들어 다음 그림에서는 하나의 요소가 있는 동적 열 값 (목록 4)을 보여 줍니다. `CString` 현재 레코드의 실제 전화 번호를 포함 하는 개체는 "555-1212"입니다.

   가장 일반적인 경우 Dynamic-Column-Values는 `CString` 형식의 요소를 포함합니다. 다양한 데이터 형식의 열을 처리하는 경우 다양한 형식의 요소를 포함할 수 있는 목록이 필요합니다.

위의 절차 결과는 두 가지 주요 목록입니다. 열-바인딩-열 이름과 현재 레코드의 열 값을 포함 하는 동적 열 값을 동적으로 포함 합니다.

> [!TIP]
> 새 열 중 일부의 데이터 형식이 다른 경우 열 목록에서 각 해당 요소의 형식을 어떻게든 정의하는 항목을 포함하는 추가 병렬 목록을 원할 수 있습니다. (원한다면 이를 위해 AFX_RFX_BOOL, AFX_RFX_BYTE 등의 값을 사용할 수 있습니다. 이러한 상수는 AFXDB에 정의 되어 있습니다. 열 데이터 형식을 표시 하는 방법에 따라 목록 유형을 선택 합니다.

### <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a> RFX 호출을 추가하여 열 바인딩

끝으로, 새 열에 대한 RFX 호출을 `DoFieldExchange` 함수에 배치하여 동적 바인딩이 일어나도록 배열합니다.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>새 열에 대한 RFX 호출을 동적으로 추가하려면 다음을 수행합니다.

1. 기본 레코드 집합의 `DoFieldExchange` 멤버 함수에서 새 열의 목록(Columns-to-Bind-Dynamically)을 순환하는 코드를 추가합니다. 각 루프에서는 Columns-to-Bind-Dynamically에서 열 이름을 추출하고 Dynamic-Column-Value에서 열에 대한 결과 값을 추출합니다. 해당 항목을 열의 데이터 형식에 적절한 RFX 함수 호출에 전달합니다. 목록에 대한 자세한 내용은 [열 목록](#_core_lists_of_columns)을 참조하세요.

일반적인 경우 Columns-to-Bind-Dynamically가 `m_listName`이라는 `CStringList`이고 Dynamic-Column-Values가 `m_listValue`라는 `CStringList`인 다음 코드 줄과 같이 `RFX_Text` 함수 호출에서 `CString` 개체를 목록에서 추출합니다.

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

RFX 함수에 대한 자세한 내용은 *클래스 라이브러리 참조* 의 [매크로 및 전역 요소](../../mfc/reference/mfc-macros-and-globals.md)를 참조하세요.

> [!TIP]
> 새 열의 데이터 형식이 다른 경우 루프에 switch 문을 사용하여 각 형식에 적절한 RFX 함수를 호출합니다.

프레임워크가 `Open` 프로세스 중에 `DoFieldExchange`를 호출하면 정적 열에 대한 RFX 호출이 해당 열을 바인딩합니다. 그러면 루프에서 동적 열에 대해 RFX 함수를 반복적으로 호출합니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 대량 데이터 항목 작업 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
