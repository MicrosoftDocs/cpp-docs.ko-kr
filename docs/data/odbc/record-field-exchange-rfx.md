---
description: '자세한 정보: RFX (레코드 필드 교환)'
title: RFX
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: d181d779f74096dc035e9d492e50ef1823982b24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298892"
---
# <a name="record-field-exchange-rfx"></a>RFX

MFC ODBC 데이터베이스 클래스는 데이터 원본과 [레코드 집합](../../data/odbc/recordset-odbc.md) 개체 간에 데이터 이동을 자동화 합니다. [CRecordset](../../mfc/reference/crecordset-class.md) 에서 클래스를 파생 하 고 대량 행 페치를 사용 하지 않는 경우 데이터는 RFX (레코드 필드 교환) 메커니즘으로 전송 됩니다.

> [!NOTE]
> 파생 클래스에서 대량 행 페치를 구현한 경우 `CRecordset` 프레임 워크는 대량 RFX (대량 레코드 필드 교환) 메커니즘을 사용 하 여 데이터를 전송 합니다. 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

RFX는 DDX (대화 상자 데이터 교환)와 유사 합니다. 데이터 원본 및 레코드 집합의 필드 데이터 멤버 간에 데이터를 이동 하려면 레코드 집합의 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 함수를 여러 번 호출 하 고 프레임 워크와 [ODBC](../../data/odbc/odbc-basics.md)간의 상당한 상호 작용이 필요 합니다. RFX 메커니즘은 형식이 안전 하며와 같은 ODBC 함수를 호출 하는 작업을 저장 합니다 `::SQLBindCol` . DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

RFX는 대부분 투명 합니다. Mfc 응용 프로그램 마법사를 사용 하 여 레코드 집합 클래스를 선언 하거나 **클래스를 추가** 하는 경우 ( [Mfc ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)에 설명 된 대로) RFX가 자동으로 빌드됩니다. 레코드 집합 클래스는 `CRecordset` 프레임 워크에서 제공 하는 기본 클래스에서 파생 되어야 합니다. MFC 응용 프로그램 마법사를 사용 하 여 초기 레코드 집합 클래스를 만들 수 있습니다. **클래스 추가** 를 사용 하면 필요에 따라 다른 레코드 집합 클래스를 추가할 수 있습니다. 자세한 내용 및 예제는 [MFC ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)를 참조 하세요.

다음을 수행 하려는 경우 세 가지 경우에 적은 양의 RFX 코드를 수동으로 추가 해야 합니다.

- 매개 변수가 있는 쿼리를 사용 합니다. 자세한 내용은 [레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)를 참조 하세요.

- 두 개 이상의 테이블에서 열에 대해 하나의 레코드 집합을 사용 하 여 조인을 수행 합니다. 자세한 내용은 [레코드 집합: 조인 수행 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)을 참조 하세요.

- 데이터 열을 동적으로 바인딩합니다. 이는 매개 변수화 보다 일반적이 낮습니다. 자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)을 참조 하세요.

RFX에 대 한 고급 이해가 필요한 경우 [레코드 필드 교환: Rfx 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)을 참조 하세요.

다음 항목에서는 레코드 집합 개체를 사용 하는 방법에 대해 자세히 설명 합니다.

- [레코드 필드 교환: RFX 사용](../../data/odbc/record-field-exchange-using-rfx.md)

- [레코드 필드 교환: RFX 함수 사용](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC 사용](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[MFC 응용 프로그램 마법사, 데이터베이스 지원](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)
