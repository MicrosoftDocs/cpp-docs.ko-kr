---
description: '자세한 정보: 트리 컨트롤 이미지 목록'
title: 트리 컨트롤 이미지 목록
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: ce76cca5642208d4158b36c45c150202270258e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264156"
---
# <a name="tree-control-image-lists"></a>트리 컨트롤 이미지 목록

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))의 각 항목에는 연결 된 비트맵 이미지 쌍이 있을 수 있습니다. 이미지는 항목 레이블의 왼쪽에 표시 됩니다. 항목이 선택 되 면 하나의 이미지가 표시 되 고, 항목을 선택 하지 않으면 다른 이미지가 표시 됩니다. 예를 들어 항목을 선택 하면 열려 있는 폴더를 표시 하 고 선택 하지 않으면 폴더를 닫을 수 있습니다.

항목 이미지를 사용 하려면 [CImageList](../mfc/reference/cimagelist-class.md) 개체를 생성 하 고 [CImageList:: create](../mfc/reference/cimagelist-class.md#create) 함수를 사용 하 여 연결 된 이미지 목록을 만들어 이미지 목록을 만들어야 합니다. 그런 다음 원하는 비트맵을 목록에 추가 하 고 [sedesired agelist](../mfc/reference/ctreectrl-class.md#setimagelist) 멤버 함수를 사용 하 여 목록을 트리 컨트롤과 연결 합니다. 기본적으로 모든 항목은 선택 된 상태와 nonselected 상태 모두의 이미지 목록에 첫 번째 이미지를 표시 합니다. [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) 멤버 함수를 사용 하 여 트리 컨트롤에 항목을 추가할 때 선택 된 이미지와 nonselected 이미지의 인덱스를 지정 하 여 특정 항목에 대 한 기본 동작을 변경할 수 있습니다. [Setitemimage](../mfc/reference/ctreectrl-class.md#setitemimage) 멤버 함수를 사용 하 여 항목을 추가한 후 인덱스를 변경할 수 있습니다.

트리 컨트롤의 이미지 목록에는 항목 이미지에 겹쳐서 표시 되도록 디자인 된 오버레이 이미지가 포함 될 수도 있습니다. 트리 컨트롤 항목의 상태에서 0이 아닌 값은 오버레이 이미지의 1부터 기반으로 하는 인덱스를 지정 합니다 (0은 오버레이 이미지를 표시 하지 않음). 4 비트의 1부터 시작 하는 인덱스를 사용 하기 때문에 오버레이 이미지는 이미지 목록에서 첫 15 이미지 사이에 있어야 합니다. 트리 컨트롤 항목 상태에 대 한 자세한 내용은이 항목의 앞부분에 나오는 [트리 컨트롤 항목 상태 개요](../mfc/tree-control-item-states-overview.md) 를 참조 하세요.

상태 이미지 목록이 지정 된 경우 트리 컨트롤은 상태 이미지에 대 한 각 항목의 아이콘 왼쪽에 공간을 예약 합니다. 응용 프로그램은 선택 된 확인란 및 선택 취소와 같은 상태 이미지를 사용 하 여 응용 프로그램 정의 항목 상태를 나타낼 수 있습니다. 비트 12-15의 0이 아닌 값은 상태 이미지의 인덱스 (0은 상태 이미지를 표시 하지 않음)를 지정 합니다.

이미지의 인덱스 대신 **I_IMAGECALLBACK** 값을 지정 하 여 항목을 다시 그릴 때까지 선택 된 이미지 또는 nonselected 이미지를 지정 하는 데 지연이 발생할 수 있습니다. **I_IMAGECALLBACK** 은 [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) 알림 메시지를 보내 응용 프로그램에 인덱스를 쿼리하도록 트리 컨트롤에 지시 합니다.

[Getimagelist](../mfc/reference/ctreectrl-class.md#getimagelist) 멤버 함수는 트리 컨트롤의 이미지 목록 핸들을 검색 합니다. 이 함수는 목록에 이미지를 더 추가 해야 하는 경우에 유용 합니다. 이미지 목록에 대 한 자세한 내용은 [CImageList 사용](../mfc/using-cimagelist.md), *MFC 참조* 에서 [CImageList](../mfc/reference/cimagelist-class.md) 사용 및 Windows SDK의 [이미지 목록](/windows/win32/controls/image-lists) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
