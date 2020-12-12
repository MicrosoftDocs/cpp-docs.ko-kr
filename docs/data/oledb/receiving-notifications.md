---
description: '자세히 알아보기: 알림 받기'
title: 알림 수신
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 1885223a7d2b3e932cf449312eab989ecf1d2554
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316884"
---
# <a name="receiving-notifications"></a>알림 수신

OLE DB는 이벤트가 발생할 때 알림을 받기 위한 인터페이스를 제공 합니다. 이러한 내용은 **OLE DB 프로그래머 참조** 의 [OLE DB 개체 알림에](/previous-versions/windows/desktop/ms725406(v=vs.85)) 설명 되어 있습니다. 이러한 이벤트의 설치에는 표준 COM 연결 지점 메커니즘이 사용 됩니다. 예를 들어를 통해 이벤트를 검색 하려는 ATL 개체는 `IRowsetNotify` `IRowsetNotify` `IRowsetNotify` 클래스 파생 목록에를 추가 하 고 COM_INTERFACE_ENTRY 매크로를 통해 노출 하 여 인터페이스를 구현 합니다.

`IRowsetNotify` 에는 여러 번 호출 될 수 있는 세 가지 메서드가 있습니다. 이러한 방법 중 하나에만 응답 하려면 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) 클래스를 사용할 수 있습니다 .이 클래스는 관심이 없는 메서드에 대 한 E_NOTIMPL를 반환 합니다.

행 집합을 만들 때 반환 된 행 집합 개체에서 지원 하도록 공급자에 게 `IConnectionPointContainer` 알림을 설정 하는 데 필요한 것을 알려야 합니다.

다음 코드에서는 ATL 개체에서 행 집합을 열고 함수를 사용 하 여 알림 싱크를 설정 하는 방법을 보여 줍니다 `AtlAdvise` . `AtlAdvise` 를 호출할 때 사용 되는 쿠키를 반환 합니다 `AtlUnadvise` .

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

그런 다음, 다음 코드에서 사용 됩니다.

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
