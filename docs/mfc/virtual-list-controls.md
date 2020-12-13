---
description: '자세히 알아보기: 가상 목록 컨트롤'
title: 가상 목록 컨트롤
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1d441fc74ab6b1ae395ce0b23bcba08c1703213f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331356"
---
# <a name="virtual-list-controls"></a>가상 목록 컨트롤

가상 목록 컨트롤은 LVS_OWNERDATA 스타일이 있는 목록 뷰 컨트롤입니다. 이 스타일을 사용 하면 컨트롤이 **DWORD** 까지 항목 수를 지원할 수 있습니다. 기본 항목 수는로만 확장 **`int`** 됩니다. 그러나이 스타일에서 제공 하는 가장 큰 이점은 한 번에 메모리에 데이터 항목의 하위 집합만 포함 하는 기능입니다. 이를 통해 가상 목록 뷰 컨트롤은 데이터에 액세스 하는 특정 메서드가 이미 있는 많은 양의 정보 데이터베이스에서 사용할 수 있습니다.

> [!NOTE]
> MFC는의 가상 목록 기능을 제공 하는 것 외에 `CListCtrl` 도 [CListView](../mfc/reference/clistview-class.md) 클래스에서 동일한 기능을 제공 합니다.

가상 목록 컨트롤을 개발할 때 알아야 할 몇 가지 호환성 문제가 있습니다. 자세한 내용은 Windows SDK의 List-View 컨트롤 항목에서 호환성 문제 섹션을 참조 하세요.

## <a name="handling-the-lvn_getdispinfo-notification"></a>LVN_GETDISPINFO 알림 처리

가상 목록 컨트롤은 항목 정보를 거의 유지 하지 않습니다. 항목 선택 및 포커스 정보를 제외 하 고 모든 항목 정보는 컨트롤의 소유자가 관리 합니다. LVN_GETDISPINFO 알림 메시지를 통해 프레임 워크에서 정보를 요청 합니다. 요청 된 정보를 제공 하려면 가상 목록 컨트롤 (또는 컨트롤 자체)의 소유자가이 알림을 처리 해야 합니다. [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여이 작업을 쉽게 수행할 수 있습니다 ( [메시지를 함수에 매핑](../mfc/reference/mapping-messages-to-functions.md)참조). 결과 코드는 다음 예제와 유사 하 게 표시 됩니다. 여기서은 `CMyDialog` 가상 목록 컨트롤 개체를 소유 하 고 대화는 알림을 처리 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

LVN_GETDISPINFO 알림 메시지에 대 한 처리기에서 요청 된 정보 유형을 확인 해야 합니다. 가능한 값은 다음과 같습니다.

- `LVIF_TEXT`*PszText* 멤버를 채워야 합니다.

- `LVIF_IMAGE`*Iimage* 멤버를 채워야 합니다.

- `LVIF_INDENT`*Iindent* 멤버를 채워야 합니다.

- `LVIF_PARAM`*LParam* 멤버를 채워야 합니다. (하위 항목에 대해 제공 되지 않습니다.)

- `LVIF_STATE`*상태* 멤버를 채워야 합니다.

그러면 요청 된 모든 정보를 프레임 워크에 다시 제공 해야 합니다.

목록 컨트롤 개체에 대 한 알림 처리기의 본문에서 가져온 다음 예제는 항목의 텍스트 버퍼 및 이미지에 대 한 정보를 제공 하 여 가능한 한 가지 방법을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>캐싱 및 가상 목록 컨트롤

이러한 유형의 목록 컨트롤은 대량 데이터 집합을 위한 것 이므로 검색 성능을 향상 시키기 위해 요청 된 항목 데이터를 캐시 하는 것이 좋습니다. 프레임 워크는 LVN_ODCACHEHINT 알림 메시지를 전송 하 여 캐시를 최적화 하는 데 도움이 되는 캐시 힌트 메커니즘을 제공 합니다.

다음 예제에서는 처리기 함수에 전달 된 범위를 사용 하 여 캐시를 업데이트 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

캐시를 준비 하 고 유지 관리 하는 방법에 대 한 자세한 내용은 Windows SDK의 List-View 컨트롤 항목에서 캐시 관리 섹션을 참조 하세요.

## <a name="finding-specific-items"></a>특정 항목 찾기

LVN_ODFINDITEM 알림 메시지는 특정 목록 컨트롤 항목을 찾을 필요가 있을 때 가상 목록 컨트롤에서 보냅니다. 알림 메시지는 목록 보기 컨트롤이 빠른 키 액세스를 받거나 LVM_FINDITEM 메시지를 받을 때 전송 됩니다. 검색 정보는 **Nmlvfinditem** 구조의 멤버인 **Lvfindinfo** 구조 형식으로 전송 됩니다. `OnChildNotify`목록 컨트롤 개체의 함수를 재정의 하 고 처리기의 본문 내에서 LVN_ODFINDITEM 메시지를 확인 하 여이 메시지를 처리 합니다. 해당 하는 경우 적절 한 작업을 수행 합니다.

List view 컨트롤에서 제공 하는 정보와 일치 하는 항목을 검색 하도록 준비 해야 합니다. 성공 하면 항목의 인덱스를 반환 하 고, 일치 하는 항목이 없으면-1을 반환 해야 합니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](../mfc/using-clistctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
