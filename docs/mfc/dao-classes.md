---
description: '자세한 정보: DAO 클래스'
title: DAO 클래스
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: bf30a4d985947ca435c53391ce9529caf9ec2c81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169413"
---
# <a name="dao-classes"></a>DAO 클래스

DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

이러한 클래스는 다른 응용 프로그램 프레임 워크 클래스와 함께 작동 하 여 Microsoft Visual Basic 및 Microsoft Access와 동일한 데이터베이스 엔진을 사용 하는 DAO (Data Access Object) 데이터베이스에 쉽게 액세스할 수 있도록 합니다. 또한 DAO 클래스는 ODBC (Open Database Connectivity) 드라이버를 사용할 수 있는 광범위 한 데이터베이스에 액세스할 수 있습니다.

DAO 데이터베이스를 사용 하는 프로그램에는 적어도 `CDaoDatabase` 개체와 `CDaoRecordset` 개체가 있습니다.

> [!NOTE]
> Visual C++ 환경과 마법사는 더 이상 DAO를 지원 하지 않습니다 (DAO 클래스가 포함 되어 있지만 여전히 사용할 수 있음). 새 MFC 프로젝트에는 ODBC를 사용 하는 것이 좋습니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 해야 합니다.

[CDaoWorkspace](reference/cdaoworkspace-class.md)<br/>
로그인에서 로그 오프 한 것으로 명명 된 암호로 보호 된 데이터베이스 세션을 관리 합니다. 대부분의 프로그램은 기본 작업 영역을 사용 합니다.

[CDaoDatabase](reference/cdaodatabase-class.md)<br/>
데이터에 대해 작업을 수행할 수 있는 데이터베이스에 대 한 연결입니다.

[CDaoRecordset](reference/cdaorecordset-class.md)<br/>
데이터 소스에서 선택한 레코드 집합을 나타냅니다.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
컨트롤에 데이터베이스 레코드를 표시하는 뷰입니다.

[CDaoQueryDef](reference/cdaoquerydef-class.md)<br/>
일반적으로 데이터베이스에 저장 되는 쿼리 정의를 나타냅니다.

[CDaoTableDef](reference/cdaotabledef-class.md)<br/>
기본 테이블 또는 연결된 테이블의 저장된 정의를 나타냅니다.

[CDaoException](reference/cdaoexception-class.md)<br/>
DAO 클래스에서 발생 하는 예외 상태를 나타냅니다.

[CDaoFieldExchange](reference/cdaofieldexchange-class.md)<br/>
DAO 데이터베이스 클래스에서 사용하는 DAO 레코드 필드 교환(DFX) 루틴을 지원합니다. 일반적으로이 클래스는 직접 사용 하지 않습니다.

## <a name="related-classes"></a>관련 클래스

[CLongBinary](reference/clongbinary-class.md)<br/>
비트맵과 같은 BLOB (binary large object)의 저장소에 대 한 핸들을 캡슐화 합니다. `CLongBinary` 개체는 데이터베이스 테이블에 저장 된 대량 데이터 개체를 관리 하는 데 사용 됩니다.

[COleCurrency](reference/colecurrency-class.md)<br/>
소수점 앞에 15 자리가 있고 그 뒤에 4 자리가 있는 고정 소수점 산술 형식인 OLE 자동화 형식 **통화** 에 대 한 래퍼입니다.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 자동화 형식 **날짜** 에 대 한 래퍼입니다. 날짜 및 시간 값을 나타냅니다.

[COleVariant](reference/colevariant-class.md)<br/>
OLE 자동화 유형 **변형** 에 대 한 래퍼입니다. **VARIANT** 의 데이터는 다양 한 형식으로 저장할 수 있습니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
