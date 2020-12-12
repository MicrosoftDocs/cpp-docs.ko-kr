---
description: '자세히 알아보기: 레코드 필드 교환: RFX 사용'
title: '레코드 필드 교환: RFX 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 9ded7bc2a10bc37f7f1f835f8706d385b543af9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298801"
---
# <a name="record-field-exchange-using-rfx"></a>레코드 필드 교환: RFX 사용

이 항목에서는 프레임 워크에서 수행 하는 작업을 기준으로 RFX를 사용 하기 위해 수행 하는 작업을 설명 합니다.

> [!NOTE]
> 이 항목은 대량 행 페치가 구현 되지 않은 [CRecordset](../../mfc/reference/crecordset-class.md) 에서 파생 된 클래스에 적용 됩니다. 대량 행 페치를 사용하는 경우 대량 레코드 필드 교환(대량 RFX)이 구현됩니다. 대량 RFX는 RFX와 비슷합니다. 차이점을 이해 하려면 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

다음 항목에는 관련 정보가 포함 되어 있습니다.

- [레코드 필드 교환: 마법사 코드 작업](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) 에서는 rfx의 주요 구성 요소를 소개 하 고 Mfc 응용 프로그램 마법사와 **클래스 추가** ( [mfc ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)에 설명 된 대로)에서 rfx를 지 원하는 코드와 마법사 코드를 수정 하는 방법을 설명 합니다.

- [레코드 필드 교환: Rfx 함수를 사용 하 여](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) 재정의에서 rfx 함수에 대 한 호출을 작성 하는 방법을 설명 합니다 `DoFieldExchange` .

다음 표에서는 프레임 워크가 사용자를 위해 수행 하는 작업과 관련 된 역할을 보여 줍니다.

### <a name="using-rfx-you-and-the-framework"></a>RFX 사용: 사용자 및 프레임 워크

|사용자|프레임워크|
|---------|-------------------|
|마법사를 사용 하 여 레코드 집합 클래스를 선언 합니다. 필드 데이터 멤버의 이름 및 데이터 형식을 지정 합니다.|이 마법사는 클래스를 파생 `CRecordset` 시키고 각 필드 데이터 멤버에 대 한 RFX 함수 호출을 포함 하 여 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 재정의를 작성 합니다.|
|필드 필요한 매개 변수 데이터 멤버를 클래스에 수동으로 추가 합니다. `DoFieldExchange`각 매개 변수 데이터 멤버에 대 한 RFX 함수 호출을 수동으로 추가 하 고, 매개 변수 그룹에 대해 [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 에 대 한 호출을 추가 하 고, [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)의 총 매개 변수 수를 지정 합니다. [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.||
|필드 필드 데이터 멤버에 추가 열을 수동으로 바인딩합니다. [M_nFields](../../mfc/reference/crecordset-class.md#m_nfields)를 수동으로 증가 시킵니다. [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)을 참조 하세요.||
|레코드 집합 클래스의 개체를 생성 합니다. 개체를 사용 하기 전에 매개 변수 데이터 멤버의 값을 설정 합니다 (있는 경우).|효율성을 위해 프레임 워크는 ODBC를 사용 하 여 매개 변수를 prebinds 합니다. 매개 변수 값을 전달 하면 프레임 워크에서이 값을 데이터 원본에 전달 합니다. 정렬 및/또는 필터 문자열이 변경 된 경우를 제외 하 고는 매개 변수 값만 쿼리를 위해 전송 됩니다.|
|[CRecordset:: open](../../mfc/reference/crecordset-class.md#open)을 사용 하 여 레코드 집합 개체를 엽니다.|레코드 집합의 쿼리를 실행 하 고, 레코드 집합의 필드 데이터 멤버에 열을 바인딩하고, `DoFieldExchange` 를 호출 하 여 첫 번째 선택한 레코드와 레코드 집합의 필드 데이터 멤버 간에 데이터를 교환 합니다.|
|[CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) 또는 메뉴 또는 도구 모음 명령을 사용 하 여 레코드 집합에서 스크롤합니다.|`DoFieldExchange`를 호출 하 여 새 현재 레코드에서 필드 데이터 멤버로 데이터를 전송 합니다.|
|레코드를 추가, 업데이트 및 삭제 합니다.|를 호출 하 여 데이터를 `DoFieldExchange` 데이터 원본으로 전송 합니다.|

## <a name="see-also"></a>참고 항목

[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[레코드 집합: 합계 및 다른 집계 결과 구하기 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 클래스](../../mfc/reference/cfieldexchange-class.md)<br/>
[매크로, 전역 함수 및 전역 변수](../../mfc/reference/mfc-macros-and-globals.md)
