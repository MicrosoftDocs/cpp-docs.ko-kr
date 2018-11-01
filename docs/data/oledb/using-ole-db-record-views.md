---
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
ms.openlocfilehash: 631e78e1a397ec360b1f3b2d94d7340e96925e23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582714"
---
# <a name="using-ole-db-record-views"></a>OLE DB 레코드 뷰 사용

MFC 클래스를 사용 하 여 MFC 응용 프로그램에서 OLE DB 행 집합 데이터를 표시 하려는 경우 [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)합니다. 레코드 뷰 개체에서 만든 `COleDBRecordView` MFC 컨트롤의 데이터베이스 레코드를 표시할 수 있습니다. 레코드 뷰는 만든 OLE DB 행 집합 개체에 직접 연결 하는 대화 상자 폼 보기의 `CRowset` 템플릿 클래스입니다. 행 집합 개체에 대 한 핸들을 시작 하는 것은 간단 합니다.

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

보기의 필드를 표시 합니다 `CRowset` 대화 상자의 컨트롤에는 개체입니다. 합니다 `COleDBRecordView` 대화 상자 데이터 교환 (DDX)을 사용 하 여 개체 및 탐색 기능에 기본 제공 `CRowset` (`MoveFirst`, `MoveNext`를 `MovePrev`, 및 `MoveLast`) 양식의 컨트롤 간에 데이터 이동을 자동화할 수 및 행 집합의 필드입니다. `COleDBRecordView` 추적 행 집합에서 사용자의 위치 레코드 뷰 사용자 인터페이스 및 공급 장치를 업데이트할 수 있도록를 [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) 메서드 간에 이동 하기 전에 현재 레코드를 업데이트 합니다.

DDX 함수를 사용할 수 있습니다 `COleDbRecordView` 데이터베이스 레코드 집합에서 직접 데이터 가져오기 및 대화 상자 컨트롤에 표시 합니다. 사용 하 여는 **DDX_** <strong>\*</strong> 메서드 (같은 `DDX_Text`)이 아니라는 **DDX_Field** <strong>\*</strong> (함수 와 같은 `DDX_FieldText`)와 `COleDbRecordView`합니다.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView 클래스](../../mfc/reference/coledbrecordview-class.md)<br/>
