---
description: '자세히 알아보기: 레코드 필드 교환: 마법사 코드 작업'
title: '레코드 필드 교환: 마법사 코드 사용'
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: c6b44c7c5e3ec09e02e70ad5dd0fecfa434cc0a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278716"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>레코드 필드 교환: 마법사 코드 사용

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

이 항목에서는 MFC 애플리케이션 마법사 및 **클래스 추가**([MFC ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)에 설명된 대로)가 RFX를 지원하기 위해 작성한 코드와 해당 코드를 변경하는 방법을 설명합니다.

> [!NOTE]
> 이 항목은 대량 행 페치가 구현되지 않은 `CRecordset`에서 파생된 클래스에 적용됩니다. 대량 행 페치를 사용하는 경우 대량 레코드 필드 교환(대량 RFX)이 구현됩니다. 대량 RFX는 RFX와 비슷합니다. 차이점을 이해 하려면 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

MFC 애플리케이션 마법사 또는 **클래스 추가** 를 사용하여 레코드 집합 클래스를 만들 때 마법사는 마법사에서 선택한 데이터 원본, 테이블 및 열 선택을 기반으로 다음과 같은 RFX와 관련 요소를 작성합니다.

- 레코드 집합 클래스의 레코드 집합 필드 데이터 멤버 선언

- `CRecordset::DoFieldExchange`의 재정의

- 레코드 집합 클래스 생성자에서 레코드 집합 필드 데이터 멤버의 초기화

## <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a> 필드 데이터 멤버 선언

마법사는 `CSections` 클래스에 대해 다음과 유사한 .h 파일에 레코드 집합 클래스 선언을 작성합니다.

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

직접 바인딩하는 매개 변수 데이터 멤버 또는 새 필드 데이터 멤버를 추가하는 경우 마법사에서 생성한 멤버 뒤에 추가합니다.

또한 마법사가 클래스 `CRecordset`의 `DoFieldExchange` 멤버 함수를 재정의합니다.

## <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 재정의

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)는 RFX의 핵심입니다. 프레임워크는 데이터 원본에서 레코드 집합으로 또는 레코드 집합에서 데이터 원본으로 데이터를 이동해야 할 때마다 `DoFieldExchange`를 호출합니다. 또한 `DoFieldExchange`는 [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) 및 [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) 멤버 함수를 통해 필드 데이터 멤버에 대한 정보를 가져오는 것을 지원합니다.

다음 `DoFieldExchange` 재정의는 `CSections` 클래스에 대한 것입니다. 마법사는 레코드 집합 클래스에 대한 .cpp 파일의 함수를 작성합니다.

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

함수의 다음 주요 기능에 유의하세요.

- 함수의 이 섹션을 필드 맵이라고 합니다.

- `pFX` 포인터를 통해 `CFieldExchange::SetFieldType`에 대해 호출합니다. 이 호출은 `DoFieldExchange` 끝까지의 모든 RFX 함수 호출 또는 `SetFieldType`의 다음 호출이 출력 열임을 지정합니다. 자세한 내용은 [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)을 참조하세요.

- `RFX_Text` 글로벌 함수에 대한 여러 호출 - 필드 데이터 멤버당 하나(이 예제에서는 모두 `CString` 변수임). 이러한 호출은 데이터 원본의 열 이름과 필드 데이터 멤버 간의 관계를 지정합니다. RFX 함수는 실제 데이터 전송을 수행합니다. 클래스 라이브러리는 모든 일반 데이터 형식에 대해 RFX 함수를 제공합니다. RFX 함수에 대 한 자세한 내용은 [레코드 필드 교환: Rfx 함수 사용](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)을 참조 하세요.

    > [!NOTE]
    >  결과 집합의 열 순서는 `DoFieldExchange`의 RFX 함수 호출 순서와 일치해야 합니다.

- `DoFieldExchange`를 호출할 때 프레임워크가 전달하는 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 개체에 대한 `pFX` 포인터. `CFieldExchange` 개체는 `DoFieldExchange`가 수행할 작업, 전송 방향 및 기타 컨텍스트 정보를 지정합니다.

## <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a> 레코드 집합 생성자

마법사에서 작성하는 레코드 집합 생성자에는 RFX와 관련된 두 가지 항목이 포함되어 있습니다.

- 각 필드 데이터 멤버에 대한 초기화

- 필드 데이터 멤버의 수를 포함하는 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 필드 데이터 멤버에 대한 초기화

`CSections` 레코드 집합 예제의 생성자는 다음과 같습니다.

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
> 필드 데이터 멤버를 수동하는 추가하는 경우 새 열을 동적으로 바인딩할 때와 마찬가지로 `m_nFields`를 증분해야 합니다. 다음과 같은 다른 코드 줄을 추가하여 이 작업을 수행합니다.

```cpp
m_nFields += 3;
```

이는 세 개의 새 필드를 추가하는 코드입니다. 매개 변수 데이터 멤버를 추가하는 경우 매개 변수 데이터 멤버 수를 포함하는 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 데이터 멤버를 초기화해야 합니다. `m_nParams` 초기화를 대괄호 바깥쪽에 배치합니다.

## <a name="see-also"></a>참고 항목

[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)
