---
description: '자세한 정보: ODBC 클래스'
title: ODBC 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: ac03543a6dfd9cf85320f9ff051730c102f2e0bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318691"
---
# <a name="odbc-classes"></a>ODBC 클래스

이러한 클래스는 다른 응용 프로그램 프레임 워크 클래스를 사용 하 여 ODBC (Open Database Connectivity) 드라이버를 사용할 수 있는 광범위 한 데이터베이스에 쉽게 액세스할 수 있도록 합니다.

ODBC 데이터베이스를 사용 하는 프로그램에는 적어도 `CDatabase` 개체와 `CRecordset` 개체가 있습니다.

[CDatabase](reference/cdatabase-class.md)<br/>
데이터 원본에 대해 작업을 수행할 수 있는 데이터 원본에 대 한 연결을 캡슐화 합니다.

[CRecordset](reference/crecordset-class.md)<br/>
데이터 소스에서 선택한 레코드 집합을 캡슐화 합니다. 레코드 집합은 레코드에서 레코드를 스크롤하고, 레코드를 업데이트 하 고, 레코드를 추가, 편집 및 삭제 하 고, 선택 영역을 정렬 하 고, 선택 항목을 정렬 하 고, 런타임에 얻거나 계산 된 정보를 사용 하 여 선택 항목을 매개 변수화 할 수 있습니다.

[CRecordView](reference/crecordview-class.md)<br/>
레코드 집합 개체에 직접 연결 된 폼 뷰를 제공 합니다. DDX (대화 상자 데이터 교환) 메커니즘은 레코드 집합 및 레코드 뷰의 컨트롤 간에 데이터를 교환 합니다. 모든 폼 보기와 마찬가지로 레코드 뷰는 대화 상자 템플릿 리소스를 기반으로 합니다. 레코드 뷰를 통해 레코드를 레코드에서 레코드로 이동 하 고, 레코드를 업데이트 하 고, 레코드 뷰를 닫을 때 연결 된 레코드 집합을 닫을 수도 있습니다.

[CDBException](reference/cdbexception-class.md)<br/>
데이터 액세스 처리 오류로 인해 발생 하는 예외입니다. 이 클래스는 클래스 라이브러리의 예외 처리 메커니즘에서 다른 예외 클래스와 동일한 용도로 사용 됩니다.

[CFieldExchange](reference/cfieldexchange-class.md)<br/>
는 RFX (레코드 필드 교환)를 지 원하는 컨텍스트 정보를 제공 합니다 .이 정보는 레코드 집합 개체의 필드 데이터 멤버와 매개 변수 데이터 멤버와 데이터 원본의 해당 테이블 열 간에 데이터를 교환 합니다. DDX (대화 상자 데이터 교환)와 유사 하 게 사용 되는 [CDataExchange](reference/cdataexchange-class.md)클래스와 유사 합니다.

## <a name="related-classes"></a>관련 클래스

[CLongBinary](reference/clongbinary-class.md)<br/>
비트맵과 같은 BLOB (binary large object)의 저장소에 대 한 핸들을 캡슐화 합니다. `CLongBinary` 개체는 데이터베이스 테이블에 저장 된 대량 데이터 개체를 관리 하는 데 사용 됩니다.

[CDBVariant](reference/cdbvariant-class.md)<br/>
값의 데이터 형식에 대해 걱정 하지 않고 값을 저장할 수 있습니다. `CDBVariant` 공용 구조체에 저장 된 현재 값의 데이터 형식을 추적 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
