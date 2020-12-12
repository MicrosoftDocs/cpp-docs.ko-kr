---
description: 'TN053: DAO 데이터베이스 클래스에 대 한 사용자 지정 DFX 루틴에 대 한 자세한 정보'
title: 'TN053: DAO 데이터베이스 클래스에 대한 사용자 지정 DFX 루틴'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: cbe34963ec3f46a88e41521f119191e7d0afe1e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214977"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: DAO 데이터베이스 클래스에 대한 사용자 지정 DFX 루틴

> [!NOTE]
> DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다. Visual C++ 환경과 마법사는 dao를 지원 하지 않습니다 (DAO 클래스가 포함 되어 있지만 계속 사용할 수 있음). 새 프로젝트에 [OLE DB 템플릿](../data/oledb/ole-db-templates.md) 또는 [ODBC 및 MFC](../data/odbc/odbc-and-mfc.md) 를 사용 하는 것이 좋습니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 해야 합니다.

이 기술 정보는 DAO 레코드 필드 교환 (DFX) 메커니즘을 설명 합니다. DFX 루틴에서 발생 하는 상황을 이해 하는 데 도움이 되도록 `DFX_Text` 함수는 예제로 자세히 설명 됩니다. 이 기술 정보에 대 한 추가 정보 소스로 서 다른 개별 DFX 함수의 코드를 검사할 수 있습니다. 사용자 지정 RFX 루틴이 필요할 때 (ODBC 데이터베이스 클래스와 함께 사용 됨) 사용자 지정 DFX 루틴이 필요 하지 않을 수 있습니다.

이 기술 참고 사항은 다음과 같습니다.

- DFX 개요

- DAO 레코드 필드 교환 및 동적 바인딩을 사용 하는 [예제](#_mfcnotes_tn053_examples)

- [DFX 작동 방법](#_mfcnotes_tn053_how_dfx_works)

- [사용자 지정 DFX 루틴의 기능](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text의 세부 정보](#_mfcnotes_tn053_details_of_dfx_text)

**DFX 개요**

DAO 레코드 필드 교환 메커니즘 (DFX)은 클래스를 사용할 때 데이터를 검색 하 고 업데이트 하는 절차를 간소화 하는 데 사용 됩니다 `CDaoRecordset` . 클래스의 데이터 멤버를 사용 하 여 프로세스를 간소화 합니다 `CDaoRecordset` . 에서 파생 하 여 `CDaoRecordset` 테이블 또는 쿼리의 각 필드를 나타내는 파생 클래스에 데이터 멤버를 추가할 수 있습니다. 이 "정적 바인딩" 메커니즘은 간단 하지만 모든 응용 프로그램에 대해 선택 하는 데이터 인출/업데이트 방법이 아닐 수도 있습니다. DFX는 현재 레코드가 변경 될 때마다 바인딩된 모든 필드를 검색 합니다. 통화가 변경 될 때 모든 필드를 인출 하지 않아도 되는 성능에 민감한 응용 프로그램을 개발 하는 경우 및를 통해 "동적 바인딩"을 선택 하는 것이 좋습니다 `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` .

> [!NOTE]
> DFX 및 동적 바인딩은 함께 사용할 수 없으므로 정적 및 동적 바인딩의 하이브리드 사용을 사용할 수 있습니다.

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a> 예 1-DAO 레코드 필드 교환과 사용

(가정 `CDaoRecordset` -파생 클래스가 `CMySet` 이미 열려 있는 경우)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**예 2-동적 바인딩만 사용**

(클래스를 사용 한다고 가정 하 `CDaoRecordset` `rs` 고 이미 열려 있는 경우)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**예제 3-DAO 레코드 필드 교환 및 동적 바인딩 사용**

(파생 클래스를 사용 하 여 직원 데이터를 검색 하는 것으로 가정 `CDaoRecordset` `emp` )

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a> DFX 작동 방법

DFX 메커니즘은 MFC ODBC 클래스에서 사용 하는 RFX (레코드 필드 교환) 메커니즘과 비슷한 방식으로 작동 합니다. DFX 및 RFX의 원칙은 동일 하지만 많은 내부 차이점이 있습니다. DFX 함수의 디자인은 거의 모든 코드를 개별 DFX 루틴에서 공유 하는 것입니다. 가장 높은 수준에서 DFX는 몇 가지 작업을 수행 합니다.

- DFX는 필요한 경우 SQL **SELECT** 절과 sql **PARAMETERS** 절을 생성 합니다.

- DFX는 DAO의 함수에서 사용 하는 바인딩 구조를 생성 `GetRows` 합니다 (나중에 자세히).

- DFX는 더티 필드를 검색 하는 데 사용 되는 데이터 버퍼를 관리 합니다 (이중 버퍼링이 사용 되는 경우).

- DFX는 **NULL** 및 **더티** 상태 배열을 관리 하 고 업데이트에 필요한 경우 값을 설정 합니다.

DFX 메커니즘의 핵심은 `CDaoRecordset` 파생 클래스의 `DoFieldExchange` 함수입니다. 이 함수는 적절 한 작업 형식의 개별 DFX 함수에 대 한 호출을 디스패치합니다. `DoFieldExchange`내부 MFC 함수를 호출 하기 전에 작업 유형을 설정 합니다. 다음 목록에서는 다양 한 작업 유형 및 간단한 설명을 보여 줍니다.

|작업(Operation)|Description|
|---------------|-----------------|
|`AddToParameterList`|빌드 매개 변수 절|
|`AddToSelectList`|빌드 SELECT 절|
|`BindField`|바인딩 구조를 설정 합니다.|
|`BindParam`|매개 변수 값을 설정 합니다.|
|`Fixup`|NULL 상태 설정|
|`AllocCache`|더티 검사를 위해 캐시를 할당 합니다.|
|`StoreField`|현재 레코드를 캐시에 저장 합니다.|
|`LoadField`|캐시를 멤버 값으로 복원 합니다.|
|`FreeCache`|캐시 해제|
|`SetFieldNull`|필드 상태 & 값을 NULL로 설정 합니다.|
|`MarkForAddNew`|의사 (PSEUDO) NULL이 아닌 경우 더티 필드를 표시 합니다.|
|`MarkForEdit`|캐시와 일치 하지 않는 경우 더티 필드 표시|
|`SetDirtyField`|변경 된 것으로 표시 된 필드 값 설정|

다음 섹션에서는에 대 한 각 작업에 대해 자세히 설명 `DFX_Text` 합니다.

DAO 레코드 필드 교환 프로세스를 이해 하는 가장 중요 한 기능은 개체의 기능을 사용 한다는 것입니다 `GetRows` `CDaoRecordset` . DAO `GetRows` 함수는 여러 가지 방법으로 작동할 수 있습니다. 이 기술 참고 사항은 `GetRows` 이 기술 정보에 대 한 범위를 벗어나므로 간략하게 설명 합니다.
DAO `GetRows` 는 여러 가지 방법으로 작동할 수 있습니다.

- 여러 레코드와 여러 데이터 필드를 한 번에 페치할 수 있습니다. 이렇게 하면 대량 데이터 구조를 처리 하는 것이 복잡 하 고, 각 필드에 대 한 적절 한 오프셋과 구조에 있는 각 데이터 레코드에 대 한 적절 한 오프셋을 사용 하는 것이 복잡 하 게 됩니다. MFC는이 다중 레코드 인출 메커니즘을 활용 하지 않습니다.

- 또 다른 방법은 `GetRows` 프로그래머가 한 데이터 레코드에 대해 각 필드의 검색 된 데이터에 대 한 바인딩 주소를 지정할 수 있도록 하는 것입니다.

- 또한 호출자가 메모리를 할당할 수 있도록 하기 위해 DAO는 가변 길이 열에 대해 호출자에 게 "콜백" 합니다. 이 두 번째 기능을 통해 데이터의 복사본 수를 최소화 하 고 데이터를 클래스의 멤버 (파생 클래스)로 직접 저장할 수 `CDaoRecordset` 있습니다. 이 두 번째 메커니즘은 MFC에서 파생 클래스의 데이터 멤버에 바인딩하는 데 사용 하는 메서드입니다 `CDaoRecordset` .

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> 사용자 지정 DFX 루틴의 기능

모든 DFX 함수에서 구현 되는 가장 중요 한 작업은 성공적인 호출을 위해 필요한 데이터 구조를 설정 하는 기능 이어야 한다는 것을 알 수 `GetRows` 있습니다. DFX 함수 에서도 지원 해야 하는 다른 작업은 여러 가지가 있지만, 호출을 올바르게 준비 하는 것은 중요 하거나 복잡 하지 않습니다 `GetRows` .

DFX 사용에 대해서는 온라인 설명서에 설명 되어 있습니다. 기본적으로 두 가지 요구 사항이 있습니다. 먼저 `CDaoRecordset` 각 바인딩된 필드 및 매개 변수에 대해 파생 클래스에 멤버를 추가 해야 합니다. 다음 `CDaoRecordset::DoFieldExchange` 은 재정의 되어야 합니다. 멤버의 데이터 형식이 중요 합니다. 데이터베이스에 있는 필드의 데이터와 일치 하거나 적어도 해당 형식으로 변환할 수 있어야 합니다. 예를 들어 정수 (long)와 같은 데이터베이스의 숫자 필드는 항상 텍스트로 변환 하 여 멤버에 바인딩할 수 `CString` 있지만, 데이터베이스의 텍스트 필드는 long 정수와 같은 숫자 표현으로 변환 되는 것이 아니라 긴 정수 멤버에 바인딩될 수 있습니다. DAO 및 Microsoft Jet 데이터베이스 엔진은 MFC가 아닌 변환을 담당 합니다.

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a> DFX_Text의 세부 정보

앞서 언급 했 듯이, DFX의 작동 방식을 설명 하는 가장 좋은 방법은 예제를 사용 하는 것입니다. 이러한 목적을 위해의 내부를 살펴보면 `DFX_Text` DFX를 최소한으로 이해 하는 데 유용 하 게 사용할 수 있습니다.

- `AddToParameterList`

   이 작업을 수행 하면 Jet에 필요한 SQL **PARAMETERS** 절 (" `Parameters <param name>, <param type> ... ;` ")이 작성 됩니다. 각 매개 변수는 RFX 호출에 지정 된 대로 이름이 지정 되 고 형식화 됩니다. `CDaoFieldExchange::AppendParamType`개별 형식의 이름을 보려면 함수 함수를 참조 하세요. 의 경우 `DFX_Text` 사용 되는 형식은 **text** 입니다.

- `AddToSelectList`

   SQL **SELECT** 절을 작성 합니다. 이는 DFX 호출로 지정 된 열 이름이 추가 ("") 되는 것 처럼 간단 `SELECT <column name>, ...` 합니다.

- `BindField`

   가장 복잡 한 작업입니다. 앞에서 설명한 것 처럼에서 사용 하는 DAO 바인딩 구조가 `GetRows` 설정 됩니다. `DFX_Text`구조에 있는 정보 형식의 코드에서 볼 수 있듯이 사용 된 DAO 형식 (**DAO_CHAR** 또는의 경우 **DAO_WCHAR** )이 포함 `DFX_Text` 됩니다. 또한 사용 되는 바인딩 형식을 설정 합니다. 이전 섹션에서는 `GetRows` 간략하게 설명 했지만 MFC에서 사용 하는 바인딩 형식이 항상 **DAOBINDING_DIRECT**(직접 주소 바인딩) 임을 설명 하기에 충분 했습니다. 변수 길이 열 바인딩 (예:) 외에도 `DFX_Text` , MFC에서 메모리 할당을 제어 하 고 올바른 길이의 주소를 지정할 수 있도록 콜백 바인딩이 사용 됩니다. 즉, MFC에서 항상 데이터를 저장 하기 위해 DAO에 지시할 수 있으므로 멤버 변수에 직접 바인딩을 허용 합니다. 바인딩 구조의 나머지 부분은 메모리 할당 콜백 함수의 주소와 열 바인딩 유형 (열 이름으로 바인딩)과 같은 항목으로 채워집니다.

- `BindParam`

   이는 `SetParamValue` 매개 변수 멤버에 지정 된 매개 변수 값을 사용 하 여를 호출 하는 간단한 작업입니다.

- `Fixup`

   각 필드에 대 한 **NULL** 상태를 채웁니다.

- `SetFieldNull`

   이 작업은 각 필드 상태를 **NULL** 로 표시 하 고 멤버 변수의 값을 **PSEUDO_NULL** 로 설정 합니다.

- `SetDirtyField`

   `SetFieldValue`커밋되지 않은 것으로 표시 된 각 필드에 대해를 호출 합니다.

나머지 작업은 모두 데이터 캐시를 사용 하는 것만을 처리 합니다. 데이터 캐시는 특정 작업을 단순화 하는 데 사용 되는 현재 레코드의 추가 버퍼입니다. 예를 들어 "더티" 필드는 자동으로 검색 될 수 있습니다. 온라인 설명서에 설명 된 대로 완전히 끄거나 필드 수준에서 해제할 수 있습니다. 버퍼의 구현은 맵을 활용 합니다. 이 맵은 "bound" 필드 (또는 `CDaoRecordset` 파생 된 데이터 멤버)의 주소를 사용 하 여 동적으로 할당 된 데이터 복사본을 일치 시키는 데 사용 됩니다.

- `AllocCache`

   캐시 된 필드 값을 동적으로 할당 하 고 맵에 추가 합니다.

- `FreeCache`

   캐시 된 필드 값을 삭제 하 고 맵에서 제거 합니다.

- `StoreField`

   현재 필드 값을 데이터 캐시에 복사 합니다.

- `LoadField`

   캐시 된 값을 필드 멤버에 복사 합니다.

- `MarkForAddNew`

   현재 필드 값이 **NULL** 이 아닌지 여부를 확인 하 고 필요한 경우 변경 된 값으로 표시 합니다.

- `MarkForEdit`

   현재 필드 값을 데이터 캐시와 비교 하 고 필요한 경우 더티 값을 표시 합니다.

> [!TIP]
> 표준 데이터 형식에 대 한 기존 DFX 루틴에 대 한 사용자 지정 DFX 루틴을 모델링 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
