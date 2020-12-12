---
description: '자세한 정보: 레코드 집합: 대량 데이터 항목 작업 (ODBC)'
title: '레코드 집합: 대형 데이터 항목 작업(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 7a4ca6de9c0b5be32626c8ca3c7c66cc516057e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204370"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>레코드 집합: 대형 데이터 항목 작업(ODBC)

이 항목은 MFC ODBC 클래스와 MFC DAO 클래스 모두에 적용 됩니다.

> [!NOTE]
> MFC DAO 클래스를 사용 하는 경우 [CLongBinary](../../mfc/reference/clongbinary-class.md)클래스 대신 [CByteArray](../../mfc/reference/cbytearray-class.md) 클래스를 사용 하 여 large data 항목을 관리 합니다. 대량 행 페치를 사용 하는 MFC ODBC 클래스를 사용 하는 경우 대신을 사용 `CLongBinary` `CByteArray` 합니다. 대량 행 페치에 대 한 자세한 내용은 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

데이터베이스에서 비트맵 (직원 사진, 지도, 제품 사진, OLE 개체 등) 등의 많은 데이터를 저장할 수 있다고 가정 합니다. 이러한 종류의 데이터를 종종 BLOB (Binary Large Object) 라고 합니다.

- 각 필드 값이 너무 깁니다.

- 숫자 및 기타 단순 데이터 형식과 달리 예측 가능한 크기는 없습니다.

- 데이터는 프로그램의 관점에서 더 작은 폼입니다.

이 항목에서는 데이터베이스 클래스가 이러한 개체를 사용 하기 위해 제공 하는 지원 기능에 대해 설명 합니다.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a> Large Objects 관리

레코드 집합에는 두 가지 방법으로 이진 개체를 관리 하는 데 어려움이 있습니다. 클래스 [CByteArray](../../mfc/reference/cbytearray-class.md) 를 사용 하거나 [CLongBinary](../../mfc/reference/clongbinary-class.md)클래스를 사용할 수 있습니다. 일반적으로 `CByteArray` 는 대량 이진 데이터를 관리 하는 기본 방법입니다.

`CByteArray``CLongBinary` [CByteArray 클래스](#_core_the_cbytearray_class)에 설명 된 것 보다 더 많은 오버 헤드가 필요 하지만 더 가능 합니다. `CLongBinary` 는 [CLongBinary 클래스](#_core_the_clongbinary_class)에 간략하게 설명 되어 있습니다.

을 사용 하 여 대량 데이터 항목으로 작업 하는 방법에 대 한 자세한 내용은 `CByteArray` [기술 참고 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)을 참조 하세요.

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a> CByteArray 클래스

`CByteArray` 는 MFC 컬렉션 클래스 중 하나입니다. `CByteArray`개체는 바이트의 동적 배열을 저장 하며, 필요한 경우 배열이 커질 수 있습니다. 클래스는 기본 제공 c + + 배열과 마찬가지로 인덱스에의 한 빠른 액세스를 제공 합니다. `CByteArray` 진단 목적으로 개체를 직렬화 및 덤프할 수 있습니다. 클래스는 지정 된 바이트를 가져오고 설정 하며 바이트를 삽입 및 추가 하 고 1 바이트 또는 모든 바이트를 제거 하는 멤버 함수를 제공 합니다. 이러한 기능을 통해 이진 데이터를 더 쉽게 구문 분석할 수 있습니다. 예를 들어, 이진 개체가 OLE 개체 이면 일부 헤더 바이트를 사용 하 여 실제 개체에 도달 해야 할 수 있습니다.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a> 레코드 집합에서 CByteArray 사용

레코드 집합의 필드 데이터 멤버에 형식을 지정 하 여 `CByteArray` [RFX](../../data/odbc/record-field-exchange-rfx.md) 가 레코드 집합과 데이터 소스 간에 이러한 개체의 전송을 관리할 수 있는 고정 기반을 제공 하 고 개체 내의 데이터를 조작할 수 있습니다. RFX는 검색 된 데이터에 대 한 특정 사이트가 필요 하며 기본 데이터에 액세스 하는 방법이 필요 합니다.

을 사용 하 여 대량 데이터 항목으로 작업 하는 방법에 대 한 자세한 내용은 `CByteArray` [기술 참고 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)을 참조 하세요.

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a> CLongBinary 클래스

[CLongBinary](../../mfc/reference/clongbinary-class.md) 개체는 `HGLOBAL` 힙에 할당 된 저장소 블록에 대 한 핸들 주위의 간단한 셸입니다. Blob은 blob (binary large object)을 포함 하는 테이블 열을 바인딩할 때 `HGLOBAL` 데이터를 레코드 집합으로 전송 해야 할 때 핸들을 할당 하 고 해당 핸들을 `CLongBinary` 레코드 집합의 필드에 저장 합니다.

그런 다음 핸들을 사용 하 여 `HGLOBAL` `m_hData` 데이터 자체를 처리 하 고 핸들 데이터에서와 같이 작동 합니다. 여기서 [CByteArray](../../mfc/reference/cbytearray-class.md) 는 기능을 추가 합니다.

> [!CAUTION]
> CLongBinary 개체는 함수 호출에서 매개 변수로 사용할 수 없습니다. 또한를 호출 하는이를 호출 하면 스크롤 `::SQLGetData` 가능한 스냅숏의 스크롤 성능이 저하 될 수도 있습니다. `::SQLGetData`직접 호출을 사용 하 여 동적 스키마 열을 검색 하는 경우에도이 문제가 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 합계 및 다른 집계 결과 구하기 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)
