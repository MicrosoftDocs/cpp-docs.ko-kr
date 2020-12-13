---
description: '자세히 알아보기: OLE DB 레코드 뷰 사용'
title: OLE DB 레코드 뷰 사용
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
ms.openlocfilehash: 8230ba118038852f81159d21a51165b7448a26aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332463"
---
# <a name="using-ole-db-record-views"></a>OLE DB 레코드 뷰 사용

OLE DB 행 집합 데이터를 MFC 응용 프로그램에 표시 하려면 MFC 클래스 [Coledbrecordview](../../mfc/reference/coledbrecordview-class.md)를 사용 합니다. 에서 만든 record view 개체를 `COleDBRecordView` 사용 하면 MFC 컨트롤에 데이터베이스 레코드를 표시할 수 있습니다. 레코드 뷰는 템플릿 클래스에서 만든 OLE DB Rowset 개체에 직접 연결 된 대화 상자 폼 뷰입니다 `CRowset` . 행 집합 개체에 대 한 핸들 가져오기는 간단 합니다.

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

뷰는 `CRowset` 대화 상자의 컨트롤에 개체의 필드를 표시 합니다. `COleDBRecordView`개체는 DDX (대화 상자 데이터 교환) 및에 기본 제공 된 탐색 기능 `CRowset` (,, `MoveFirst` `MoveNext` `MovePrev` 및 `MoveLast` )을 사용 하 여 폼의 컨트롤과 행 집합의 필드 간 데이터 이동을 자동화 합니다. `COleDBRecordView` 레코드 뷰에서 사용자 인터페이스를 업데이트 하 고 다른 위치로 이동 하기 전에 현재 레코드를 업데이트 하기 위한 [Onmove](../../mfc/reference/coledbrecordview-class.md#onmove) 메서드를 제공할 수 있도록 행 집합에서 사용자의 위치를 추적 합니다.

에서 DDX 함수 `COleDbRecordView` 를 사용 하 여 데이터베이스 레코드 집합에서 직접 데이터를 가져오고 대화 상자 컨트롤에 표시할 수 있습니다. 와 같은  DDX_Field 함수 (예:)를 사용 <strong>\*</strong> 하지 않고 DDX_ 메서드 (예:)를 사용 `DDX_Text`  <strong>\*</strong> `DDX_FieldText` `COleDbRecordView` 합니다.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView 클래스](../../mfc/reference/coledbrecordview-class.md)<br/>
