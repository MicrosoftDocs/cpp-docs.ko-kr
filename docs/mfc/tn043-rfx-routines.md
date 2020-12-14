---
description: 'TN043: RFX 루틴에 대해 자세히 알아보세요.'
title: 'TN043: RFX 루틴'
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 6e5ac8271739e5cab80b79cb915b07e7d25622cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215224"
---
# <a name="tn043-rfx-routines"></a>TN043: RFX 루틴

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 메모는 RFX (레코드 필드 교환) 아키텍처를 설명 합니다. 또한 **RFX_** 프로시저를 작성 하는 방법을 설명 합니다.

## <a name="overview-of-record-field-exchange"></a>레코드 필드 교환 개요

모든 레코드 집합 필드 함수는 c + + 코드를 사용 하 여 수행 됩니다. 특수 리소스 또는 매직 매크로가 없습니다. 메커니즘의 핵심은 모든 파생 된 레코드 집합 클래스에서 재정의 되어야 하는 가상 함수입니다. 항상 다음 형식으로 되어 있습니다.

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

특수 형식 AFX 주석은 클래스 마법사가이 함수 내에서 코드를 찾고 편집할 수 있도록 합니다. 클래스 마법사와 호환 되지 않는 코드는 특수 형식 주석 외부에 배치 해야 합니다.

위의 예제에서 \<recordset_exchange_field_type_call> 는 형식입니다.

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

및 \<recordset_exchange_function_call> 는 다음과 같은 형식입니다.

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

대부분의 **RFX_** 함수에는 위에 표시 된 것과 같은 세 개의 인수가 있지만 일부 (예: `RFX_Text` 및 `RFX_Binary` )에는 추가 선택적 인수가 있습니다.

각 함수에는 둘 이상의 **RFX_** 포함 될 수 있습니다 `DoDataExchange` .

MFC와 함께 제공 되는 모든 레코드 집합 필드 교환 루틴 목록은 ' afxdb '을 참조 하세요.

레코드 집합 필드 호출은 메모리 위치 (일반적으로 데이터 멤버)를 등록 하 여 클래스에 대 한 필드 데이터를 저장 하는 방법입니다 `CMySet` .

## <a name="notes"></a>참고

레코드 집합 필드 함수는 클래스 에서만 작동 하도록 디자인 되었습니다 `CRecordset` . 이러한 클래스는 일반적으로 다른 MFC 클래스에서 사용할 수 없습니다.

데이터의 초기 값은 일반적으로 및 주석이 있는 블록에서 표준 c + + 생성자에 설정 됩니다 `//{{AFX_FIELD_INIT(CMylSet)` `//}}AFX_FIELD_INIT` .

각 **RFX_** 함수는 필드를 편집 하려고 준비 하 여 필드를 보관 하기 위해 필드의 더티 상태 반환에서 다양 한 작업을 지원 해야 합니다.

(예를 들어,)를 호출 하는 각 함수는 `DoFieldExchange` `SetFieldNull` `IsFieldDirty` 에 대 한 호출을 기반으로 자체 초기화를 수행 `DoFieldExchange` 합니다.

## <a name="how-does-it-work"></a>작동 방식

레코드 필드 교환을 사용 하기 위해 다음 사항을 이해할 필요는 없습니다. 그러나이를 백그라운드에서 작동 하는 방식을 이해 하면 사용자 고유의 exchange 프로시저를 작성 하는 데 도움이 됩니다.

`DoFieldExchange`멤버 함수는 멤버 함수와 매우 유사 합니다. 즉, `Serialize` 외부 폼 (이 경우 ODBC 쿼리의 결과에서 열)에서/로 데이터를 가져오거나 설정 하는 일은 클래스의 멤버 데이터입니다. *PFX* 매개 변수는 데이터 교환을 수행 하기 위한 컨텍스트입니다 .의 *CArchive* 매개 변수와 비슷합니다 `CObject::Serialize` . *PFX* ( `CFieldExchange` 개체)에는와 유사 하지만 *CArchive* 방향 플래그의 일반화 인 작업 표시기가 있습니다. RFX 함수는 다음 작업을 지원 해야 할 수 있습니다.

- `BindParam` -ODBC가 매개 변수 데이터를 검색 해야 하는 위치를 나타냄

- `BindFieldToColumn` -ODBC에서 outputColumn 데이터를 검색/보관할 위치를 지정 합니다.

- `Fixup` - `CString/CByteArray` 길이 설정, NULL 상태 비트 설정

- `MarkForAddNew` -AddNew 호출 이후 값이 변경 된 경우 더티로 표시

- `MarkForUpdate` -호출 편집 이후 값이 변경 된 경우 더티 표시

- `Name` -변경 된 것으로 표시 된 필드에 대 한 필드 이름을 추가 합니다.

- `NameValue` -변경 된 \<column name> 것으로 표시 된 필드의 경우 "="를 추가 합니다.

- `Value` -", ' 또는 ' '와 같이" "뒤에 구분 기호를 추가 합니다.

- `SetFieldDirty` -상태 비트 더티 (즉, 변경 된) 필드를 설정 합니다.

- `SetFieldNull` -필드에 대해 null 값을 나타내는 상태 비트를 설정 합니다.

- `IsFieldDirty` -더티 상태 비트의 반환 값

- `IsFieldNull` -Null 상태 비트의 반환 값

- `IsFieldNullable` -필드에 NULL 값이 포함 될 수 있는 경우 TRUE를 반환 합니다.

- `StoreField` -보관 필드 값

- `LoadField` -보관 된 필드 값 다시 로드

- `GetFieldInfoValue` -필드에 대 한 일반 정보를 반환 합니다.

- `GetFieldInfoOrdinal` -필드에 대 한 일반 정보를 반환 합니다.

## <a name="user-extensions"></a>사용자 확장

기본 RFX 메커니즘을 확장 하는 방법에는 여러 가지가 있습니다. 이 문서의 설명에 따라 Azure Automation Hybrid Runbook Worker를 제거할 수 있습니다.

- 새 데이터 형식을 추가 합니다. 예를 들어:

    ```cpp
    CBookmark
    ```

- 새 exchange 프로시저 (RFX_)를 추가 합니다.

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- `DoFieldExchange`멤버 함수에 추가 RFX 호출 또는 다른 유효한 c + + 문이 조건부로 포함 되도록 합니다.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> 이러한 코드는 클래스 마법사를 사용 하 여 편집할 수 없으며 특수 형식 주석 외부 에서만 사용 해야 합니다.

## <a name="writing-a-custom-rfx"></a>사용자 지정 RFX 작성

사용자 고유의 사용자 지정 RFX 함수를 작성 하려면 기존 RFX 함수를 복사 하 여 용도에 맞게 수정 하는 것이 좋습니다. 복사할 적절 한 RFX를 선택 하면 작업을 훨씬 더 쉽게 수행할 수 있습니다. 일부 RFX 함수에는 복사할 방법을 결정할 때 고려해 야 하는 몇 가지 고유한 속성이 있습니다.

`RFX_Long` 및 `RFX_Int` : 가장 간단한 RFX 함수입니다. 데이터 값에는 특별 한 해석이 필요 하지 않으며 데이터 크기는 고정 되어 있습니다.

`RFX_Single` and `RFX_Double` : 위와 RFX_Int와 RFX_Long 마찬가지로 이러한 함수는 간단 하며 기본 구현을 광범위 하 게 사용할 수 있습니다. 그러나이는 명시적으로 참조 되는 경우에만 런타임 부동 소수점 라이브러리를 로드할 수 있도록 하는 것이 아니라 dbflt에 저장 됩니다.

`RFX_Text` 및 `RFX_Binary` :이 두 함수는 문자열/이진 정보를 저장 하기 위해 정적 버퍼를 미리 할당 하 고 &값을 등록 하는 대신 ODBC SQLBindCol에 이러한 버퍼를 등록 해야 합니다. 이 때문에 이러한 두 함수에는 다양 한 특수 한 사례 코드가 있습니다.

`RFX_Date`: ODBC는 자체 TIMESTAMP_STRUCT 데이터 구조에 날짜 및 시간 정보를 반환 합니다. 이 함수는 날짜/시간 데이터를 보내고 받는 "프록시"로 TIMESTAMP_STRUCT를 동적으로 할당 합니다. 다양 한 작업에서 c + + `CTime` 개체와 TIMESTAMP_STRUCT 프록시 사이의 날짜 및 시간 정보를 전송 해야 합니다. 이 기능을 사용 하는 것이 매우 복잡 하지만 데이터 전송에 프록시를 사용 하는 방법의 좋은 예입니다.

`RFX_LongBinary`: 데이터를 수신 및 전송 하는 데 열 바인딩을 사용 하지 않는 유일한 클래스 라이브러리 RFX 함수입니다. 이 함수는 BindFieldToColumn 작업을 무시 하 고 대신, 픽스업 작업 중에는 들어오는 SQL_LONGVARCHAR 또는 SQL_LONGVARBINARY 데이터를 저장 하기 위해 저장소를 할당 한 후 SQLGetData 호출을 수행 하 여 할당 된 저장소로 값을 검색 합니다. 데이터 값을 데이터 원본으로 다시 전송 하기 위해 준비 하는 경우 (예: NameValue 및 Value 작업)이 함수는 ODBC의 DATA_AT_EXEC 기능을 사용 합니다. SQL_LONGVARBINARY 및 SQL_LONGVARCHARs 사용에 대 한 자세한 내용은 [Technical Note 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) 을 참조 하세요.

사용자 고유의 **RFX_** 함수를 작성 하는 경우를 사용 하 여 `CFieldExchange::Default` 지정 된 작업을 구현할 수 있습니다. 해당 작업에 대 한 기본값 구현을 확인 합니다. **RFX_** 함수에서 작성 하는 작업을 수행 하는 경우에 위임할 수 있습니다 `CFieldExchange::Default` . Dbrfx .cpp에서를 호출 하는 예제를 확인할 수 있습니다 `CFieldExchange::Default` .

`IsFieldType`RFX 함수 시작 부분에서를 호출 하 고 FALSE를 반환 하는 경우 즉시 반환 하는 것이 중요 합니다. 이 메커니즘을 통해 *Outputcolumns* 에서 매개 변수 작업을 수행 하지 않고, `BindParam` *outputcolumns* 에서를 호출 하는 것과 같은 반대의 작업을 수행 합니다. 또한 `IsFieldType` 은 *outputcolumns* (*m_nFields*) 및 params (*m_nParams*) 수를 자동으로 추적 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
