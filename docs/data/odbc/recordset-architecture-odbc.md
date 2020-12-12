---
description: '자세한 정보: 레코드 집합: 아키텍처 (ODBC)'
title: '레코드 집합: 아키텍처(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
ms.openlocfilehash: 0a7be1104cf16f9cc11effac1cd4151749167436
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186131"
---
# <a name="recordset-architecture-odbc"></a>레코드 집합: 아키텍처(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 레코드 집합 개체의 아키텍처를 구성하는 데이터 멤버를 설명합니다.

- [필드 데이터 멤버](#_core_field_data_members)

- [매개 변수 데이터 멤버](#_core_parameter_data_members)

- [m_nFields 및 m_nParams 데이터 멤버 사용](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 개체에 적용됩니다. 대량 행 페치를 구현하는 경우 아키텍처는 유사합니다. 차이점을 이해 하려면 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

## <a name="sample-class"></a><a name="_core_a_sample_class"></a> 샘플 클래스

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

**클래스 추가** 에서 [MFC ODBC 소비자 마법사](../../mfc/reference/adding-an-mfc-odbc-consumer.md)를 사용하여 `CRecordset`에서 파생된 레코드 집합 클래스를 선언하면 클래스는 다음과 같은 간단한 클래스에 표시된 일반 구조를 가집니다.

```cpp
class CCourse : public CRecordset
{
public:
   CCourse(CDatabase* pDatabase = NULL);
   ...
   CString m_strCourseID;
   CString m_strCourseTitle;
   CString m_strIDParam;
};
```

클래스의 시작 부분에서 마법사는 [필드 데이터 멤버](#_core_field_data_members) 세트를 작성합니다. 클래스를 만들 때 하나 이상의 필드 데이터 멤버를 지정해야 합니다. 클래스가 매개 변수화된 경우 샘플 클래스는 (데이터 멤버 `m_strIDParam`을 사용하여) [매개 변수 데이터 멤버](#_core_parameter_data_members)를 수동으로 추가해야 합니다. 마법사는 클래스에 매개 변수 추가를 지원하지 않습니다.

## <a name="field-data-members"></a><a name="_core_field_data_members"></a> 필드 데이터 멤버

레코드 집합 클래스의 가장 중요한 멤버는 필드 데이터 멤버입니다. 데이터 원본에서 선택한 각 열에 대해 클래스에는 해당 열에 대한 적절한 데이터 형식의 데이터 멤버가 포함됩니다. 예를 들어 이 항목의 시작 부분에 표시된 [샘플 클래스](#_core_a_sample_class)에는 `m_strCourseID` 및 `m_strCourseTitle`이라는 `CString` 형식의 두 가지 필드 데이터 멤버가 있습니다.

레코드 집합이 레코드 세트를 선택하면 프레임워크는 현재 레코드의 열(`Open` 호출 후 첫 번째 레코드가 현재 상태임)을 개체의 필드 데이터 멤버에 자동으로 바인딩합니다. 즉, 프레임워크는 레코드 열의 내용을 저장하는 버퍼로 적절한 필드 데이터 멤버를 사용합니다.

사용자가 새 레코드로 스크롤하면 프레임워크는 필드 데이터 멤버를 사용하여 현재 레코드를 나타냅니다. 프레임워크는 이전 레코드의 값을 대체하여 필드 데이터 멤버를 새로 고칩니다. 필드 데이터 멤버는 현재 레코드를 업데이트하고 새 레코드를 추가하는 데도 사용됩니다. 레코드 업데이트 프로세스의 일부로 적절한 필드 데이터 멤버 또는 멤버에 직접 값을 할당하여 업데이트 값을 지정합니다.

## <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a> 매개 변수 데이터 멤버

클래스가 매개 변수화된 경우 하나 이상의 매개 변수 데이터 멤버가 있습니다. 매개 변수가 있는 클래스를 사용하면 런타임 시 가져오거나 계산한 정보에 대한 레코드 집합 쿼리를 기반으로 할 수 있습니다.

일반적으로 매개 변수는 다음 예제와 같이 선택 항목을 줄이는 데 도움이 됩니다. 이 항목의 시작 부분에 있는 [샘플 클래스](#_core_a_sample_class)에 기반하여 레코드 집합 개체가 다음 SQL 문을 실행할 수 있습니다.

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?"는 런타임 시 제공하는 매개 변수 값에 대한 자리 표시자입니다. 레코드 집합을 구성하고 해당 `m_strIDParam` 데이터 멤버를 MATH101로 설정할 때 레코드 집합에 대한 유효한 SQL 문은 다음과 같습니다.

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

매개 변수 데이터 멤버를 정의하면 SQL 문자열의 매개 변수에 대해 프레임워크에 알립니다. 프레임워크는 매개 변수를 바인딩합니다. 이를 통해 ODBC에서 자리 표시자를 대체할 값을 가져올 위치를 알 수 있습니다. 이 예제에서 결과 레코드 집합은 값이 MATH101인 CourseID 열을 통해 Course 테이블에서 레코드만 포함합니다. 이 레코드의 지정된 모든 열이 선택됩니다. 필요한 만큼 매개 변수(및 자리 표시자)를 지정할 수 있습니다.

> [!NOTE]
> MFC는 매개 변수와 관련하여 아무 작업도 수행하지 않습니다. 특히, 텍스트 대체는 수행하지 않습니다. 대신 MFC는 매개 변수를 가져올 위치를 ODBC에 알려줍니다. ODBC는 데이터를 검색하고 필요한 매개 변수화를 수행합니다.

> [!NOTE]
> 매개 변수의 순서가 중요합니다. 이에 대 한 자세한 내용 및 매개 변수에 대 한 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.

## <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a> m_nFields 및 m_nParams 사용

마법사가 클래스에 대한 생성자를 작성할 때 클래스의 [필드 데이터 멤버](#_core_field_data_members) 수를 지정하는 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 데이터 멤버도 초기화합니다. 클래스에 [매개 변수](#_core_parameter_data_members)를 추가하는 경우 매개 변수 데이터 멤버 수를 지정하는 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 데이터 멤버에 대한 초기화도 추가해야 합니다. 프레임워크는 이러한 값을 사용하여 데이터 멤버를 작업합니다.

자세한 내용 및 예제는 [레코드 필드 교환: RFX 사용](../../data/odbc/record-field-exchange-using-rfx.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 테이블에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)
