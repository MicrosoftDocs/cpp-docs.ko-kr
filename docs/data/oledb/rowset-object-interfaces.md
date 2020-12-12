---
description: '자세히 알아보기: 행 집합 개체 인터페이스'
title: Rowset 개체 인터페이스
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: fc7cbb0ee7c15cc7414144334018afc93888da01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316858"
---
# <a name="rowset-object-interfaces"></a>Rowset 개체 인터페이스

다음 표에서는 행 집합 개체에 대해 OLE DB에 의해 정의 된 필수 및 선택적 인터페이스를 보여 줍니다.

|인터페이스|필수 여부|OLE DB 템플릿에서 구현 됩니까?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|필수|예|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|필수|예|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|필수|예|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|필수|예|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|필수|예|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|선택 사항|아니요|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|선택 사항|아니요|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|선택 사항|아니요|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|선택 사항|예 (ATL을 통해)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|선택 사항|아니요|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|선택 사항|아니요|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|선택 사항|예|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|선택 사항|아니요|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|선택 사항|아니요|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|선택 사항|아니요|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|선택 사항 (그러나 수준 0 공급자에 필요)|예|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|선택 사항|아니요|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|선택 사항|예|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|선택 사항|아니요|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|선택 사항|아니요|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|선택 사항|예|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|선택 사항|아니요|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|선택 사항|예|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|선택 사항|아니요|

마법사에서 생성 된 행 집합 개체는 `IAccessor` 상속을 통해, 및를 구현 합니다 `IRowset` `IRowsetInfo` . 는 `IAccessorImpl` 출력 열을 모두 바인딩합니다. `IRowset`인터페이스는 행과 데이터 페치를 처리 합니다. `IRowsetInfo`인터페이스는 행 집합 속성을 처리 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
