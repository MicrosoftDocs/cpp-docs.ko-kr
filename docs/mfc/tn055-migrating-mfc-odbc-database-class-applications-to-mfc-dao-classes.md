---
description: '자세히 알아보기: TN055: mfc ODBC 데이터베이스 클래스 응용 프로그램을 MFC DAO 클래스로 마이그레이션'
title: 'TN055: MFC ODBC 데이터베이스 클래스 애플리케이션을 MFC DAO 클래스로 마이그레이션'
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
ms.openlocfilehash: d1afd599384bd6e5c3083abf661a7128c0154b22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214886"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: MFC ODBC 데이터베이스 클래스 애플리케이션을 MFC DAO 클래스로 마이그레이션

> [!NOTE]
> DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다. Visual C++ 환경과 마법사는 dao를 지원 하지 않습니다 (DAO 클래스가 포함 되어 있지만 계속 사용할 수 있음). 새 프로젝트에 [OLE DB 템플릿](../data/oledb/ole-db-templates.md) 또는 [ODBC 및 MFC](../data/odbc/odbc-and-mfc.md) 를 사용 하는 것이 좋습니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 해야 합니다.

## <a name="overview"></a>개요

대부분의 경우에는 MFC의 ODBC 데이터베이스 클래스를 사용하는 애플리케이션을 MFC의 DAO 데이터베이스 클래스로 변경하는 것이 바람직할 수 있습니다. 이 기술 노트에서는 MFC ODBC와 DAO 클래스 사이의 차이점에 대해 자세히 설명합니다. 이러한 차이점을 고려하면, 필요에 따라 ODBC 클래스에서 MFC 클래스로 애플리케이션을 마이그레이션하는 것이 너무 어렵지 않을 것입니다.

## <a name="why-migrate-from-odbc-to-dao"></a>ODBC에서 DAO로 마이그레이션해야 하는 이유

애플리케이션을 ODBC 데이터베이스 클래스에서 DAO 데이터베이스 클래스로 변경해야 하는 이유는 다양할 수 있지만 그러한 결정에 대한 이유가 반드시 간단하거나 명백한 것은 아닙니다. 한 가지 고려할 점은 DAO에서 사용되는 Microsoft Jet 데이터베이스 엔진은 ODBC 드라이버가 있는 모든 ODDB 데이터 소스를 읽을 수 있다는 점입니다. ODBC 데이터베이스 클래스를 사용하거나 ODBC를 사용자가 직접 호출하는 것이 더 효율적일 수 있지만, Microsoft Jet 데이터베이스 엔진은 ODBC 데이터를 읽을 수 있습니다.

ODBC/DAO 결정을 쉽게 만드는 몇 가지 간단한 사례. 예를 들어, Microsoft Jet 엔진이 직접 읽을 수 있는 형식(Access, Excel 형식 등)의 데이터만 액세스가 필요한 경우에는 DAO 데이터베이스 클래스를 사용하는 것이 확실한 선택입니다.

데이터가 하나의 서버 또는 여러 서버에 있는 경우에는 보다 복잡해집니다. 이 경우에는 ODBC 데이터베이스 클래스를 사용할지 아니면 DAO 데이터베이스 클래스를 사용할지 결정하기가 어렵습니다. 이기종 연결과 같은 구성이 필요한 경우(예: SQL Server나 Oracle과 같은 여러 형식의 서버 데이터 연결), Microsoft Jet 데이터베이스 엔진을 사용하면 ODBC 데이터베이스 클래스를 사용하거나 ODBC를 직접 호출할 경우에 필요한 작업을 강제로 수행하는 대신 이 연결이 자동으로 수행됩니다. 드라이버 커서를 지원하는 ODBC 드라이버를 사용 중일 때는 ODBC 데이터베이스 클래스를 사용하는 것이 가장 좋은 선택일 수 있습니다.

이렇게 선택이 복잡해질 수 있으므로, 특정 요구 사항에 따라 여러 방법의 성능을 테스트할 수 있도록 일부 샘플 코드를 작성해야 할 수 있습니다. 이 기술 노트에서는 사용자가 ODBC 데이터베이스 클래스를 DAO 데이터베이스 클래스로 변경하기로 결정했다고 가정합니다.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>ODBC 데이터베이스 클래스와 MFC DAO 데이터베이스 클래스 간의 유사점

MFC ODBC 클래스의 원래 설계는 Microsoft Access 및 Microsoft Visual Basic에서 사용되는 DAO 개체 모델을 기반으로 합니다. 즉, ODBC 및 DAO MFC 클래스 간에는 이 섹션에서 일일이 설명하지 않더라도 공통적인 기능이 많이 있습니다. 일반적으로 프로그래밍 모델은 동일합니다.

몇 가지 유사점은 다음과 같습니다.

- ODBC와 DAO 클래스에는 모두 기본 DBMS(데이터베이스 관리 시스템) 사용을 관리하는 데이터베이스 개체가 포함됩니다.

- 두 클래스 모두 DBMS에서 반환되는 결과 집합을 나타내는 레코드 집합 개체가 있습니다.

- DAO 데이터베이스 및 레코드 집합 개체는 ODBC 클래스와 거의 동일한 멤버를 가집니다.

- 두 클래스 집합에서 데이터를 검색하는 코드는 일부 개체와 멤버 이름 변경을 제외하고 동일합니다. 변경이 필요할 수 있지만, ODBC 클래스에서 DAO 클래스로 전환할 때 이름 변경은 보통 직관적으로 이뤄집니다.

예를 들어 두 모델 모두, 데이터를 검색하는 절차에서는 데이터베이스 개체를 생성하여 열고, 레코드 집합 개체를 생성하여 열고, 일부 작업 수행을 위해 데이터를 탐색(이동)하는 과정이 포함됩니다.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>ODBC와 DAO MFC 클래스의 차이점

DAO 클래스에는 더 많은 개체와 다양한 메서드 집합이 포함되지만 이 섹션에서는 비슷한 클래스와 기능의 차이점에 대해서만 설명합니다.

두 클래스 간에 가장 명백한 차이점은 유사한 클래스 및 전역 함수의 이름이 서로 다르다는 점입니다. 다음 목록은 각 데이터베이스 클래스와 연관된 개체, 메서드 및 전역 함수의 이름 차이를 보여줍니다.

|클래스 또는 함수|MFC DAO 클래스와 동일|
|-----------------------|-----------------------------------|
|`CDatabase`|`CDaoDatabase`|
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|
|`CRecordset`|`CDaoRecordset`|
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|
|`CFieldExchange`|`CDaoFieldExchange`|
|`RFX_Bool`|`DFX_Bool`|
|`RFX_Byte`|`DFX_Byte`|
|`RFX_Int`|`DFX_Short`|
|`RFX_Long`|`DFX_Long`|
||`DFX_Currency`|
|`RFX_Single`|`DFX_Single`|
|`RFX_Double`|`DFX_Double`|
|`RFX_Date`<sup>1</sup>|`DFX_Date` ( `COleDateTime` -기반)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> `RFX_Date` 함수는 및를 기반 `CTime` 으로 `TIMESTAMP_STRUCT` 합니다.

사용자 애플리케이션에 영향을 주거나 단순한 이름 차이 이상의 설명이 필요한 주요 기능 상의 차이는 아래에 나열되어 있습니다.

- 레코드 집합 열기 형식 및 레코드 집합 열기 옵션과 같은 항목을 지정하는 데 사용되는 상수 및 매크로가 변경되었습니다.

   ODBC 클래스의 경우 MFC에서는 매크로 또는 열거 형식을 통해 이러한 옵션을 정의해야 합니다.

   DAO 클래스의 경우, DAO는 헤더 파일(DBDAOINT.H)에서 이러한 옵션의 정의를 제공합니다. 따라서 레코드 집합 형식이 `CRecordset`의 열거된 멤버이지만 DAO에서는 상수입니다. 예를 들어 ODBC에서 유형을 지정할 때 **snapshot** 을 사용 `CRecordset` 하지만의 유형을 지정할 때에는 **DB_OPEN_SNAPSHOT** `CDaoRecordset` 합니다.

- 의 기본 레코드 집합 형식은 `CRecordset` **snapshot** 이지만의 기본 레코드 집합 형식은 `CDaoRecordset` **다이너셋** 입니다 (ODBC 클래스 스냅숏에 대 한 추가 문제는 아래 참고 참조).

- ODBC `CRecordset` 클래스에는 전달 전용 레코드 집합 형식을 생성하는 옵션이 포함됩니다. `CDaoRecordset` 클래스에서 전달 전용은 레코드 집합 형식이 아니고, 특정 유형의 레코드 집합이 갖는 속성(또는 옵션)입니다.

- `CRecordset` 개체를 열 때 추가 전용 레코드 집합은 레코드 집합의 데이터를 읽고 추가할 수만 있음을 의미합니다. `CDaoRecordset` 개체의 경우 추가 전용은 문자 그대로 레코드 집합의 데이터를 추가할 수만 있음(읽을 수 없음)을 의미합니다.

- ODBC 클래스의 트랜잭션 멤버 함수는 `CDatabase`의 멤버이고 데이터베이스 수준에서 작동합니다. DAO 클래스의 경우 트랜잭션 멤버 함수는 더 높은 수준의 클래스 멤버이고(`CDaoWorkspace`) 따라서 동일한 작업 공간(트랜잭션 공간)을 공유하는 여러 `CDaoDatabase` 개체에 영향을 줄 수 있습니다.

- 예외 클래스가 변경되었습니다. `CDBExceptions` 는 ODBC 클래스 및 DAO 클래스에서 throw 됩니다 `CDaoExceptions` .

- `RFX_Date``CTime`는를 `TIMESTAMP_STRUCT` 사용 하는 동안 및 개체를 사용 `DFX_Date` `COleDateTime` 합니다. 는 `COleDateTime` 와 거의 동일 `CTime` 하지만 4 바이트 **time_t** 아닌 8 바이트 OLE **날짜** 를 기반으로 하므로 훨씬 더 큰 범위의 데이터를 보유할 수 있습니다.

   > [!NOTE]
   > DAO(`CDaoRecordset`) 스냅샷은 읽기 전용이지만 ODBC(`CRecordset`) 스냅샷은 드라이버 및 ODBC 커서 라이브러리 사용에 따라 업데이트가 가능할 수 있습니다. 커서 라이브러리를 사용하는 경우 `CRecordset` 스냅샷을 업데이트할 수 있습니다. ODBC 커서 라이브러리 없이 Microsoft Desktop Driver Pack 3.0 드라이버를 사용 중이면 `CRecordset` 스냅샷이 읽기 전용입니다. 다른 드라이버를 사용 하는 경우에는 드라이버의 설명서를 확인 하 여 스냅숏 ( `STATIC_CURSORS` )이 읽기 전용인 지 확인 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
