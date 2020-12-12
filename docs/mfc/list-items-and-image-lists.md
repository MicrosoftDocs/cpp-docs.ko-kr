---
description: '자세히 알아보기: 목록 항목 및 이미지 목록'
title: 목록 항목 및 이미지 목록
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 674c67c2eb104d86f0bd80732469129b6c70e0f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283370"
---
# <a name="list-items-and-image-lists"></a>목록 항목 및 이미지 목록

목록 컨트롤 ([CListCtrl](reference/clistctrl-class.md))의 "항목"은 아이콘, 레이블 및 기타 정보 ("하위 항목")로 구성 됩니다.

목록 컨트롤 항목에 대 한 아이콘은 이미지 목록에 포함 되어 있습니다. 아이콘 보기에 사용 되는 전체 아이콘을 포함 하는 하나의 이미지 목록입니다. 선택적인 두 번째 이미지 목록에는 컨트롤의 다른 뷰에서 사용 하기 위해 동일한 아이콘의 더 작은 버전이 포함 되어 있습니다. 세 번째 선택적 목록에는 특정 보기의 작은 아이콘 앞에 표시 하기 위한 확인란 등의 "상태" 이미지가 포함 되어 있습니다. 네 번째 선택적 목록에는 목록 컨트롤의 개별 헤더 항목에 표시 되는 이미지가 포함 되어 있습니다.

> [!NOTE]
> LVS_SHAREIMAGELISTS 스타일을 사용 하 여 목록 뷰 컨트롤을 만든 경우 더 이상 사용 하지 않을 때 이미지 목록을 소멸 해야 합니다. 여러 목록 뷰 컨트롤에 동일한 이미지 목록을 할당 하는 경우이 스타일을 지정 합니다. 그렇지 않으면 둘 이상의 컨트롤이 동일한 이미지 목록을 삭제 하려고 할 수 있습니다.

목록 항목에 대 한 자세한 내용은 Windows SDK의 [목록 뷰 이미지 목록](/windows/win32/Controls/using-list-view-controls) 및 [항목 및 하위](/windows/win32/Controls/using-list-view-controls) 항목을 참조 하세요. 또한 *MFC 참조* 의 클래스 [CImageList](reference/cimagelist-class.md) 및이 문서 패밀리의 [CImageList 사용](using-cimagelist.md) 을 참조 하세요.

목록 컨트롤을 만들려면 목록에 새 항목을 삽입할 때 사용할 이미지 목록을 제공 해야 합니다. 다음 예에서는이 프로시저를 보여 줍니다. 여기서 *m_pImagelist* 는 형식의 포인터이 `CImageList` 고 *m_listctrl* 는 `CListCtrl` 데이터 멤버입니다.

[!code-cpp[NVC_MFCControlLadenDialog#19](codesnippet/cpp/list-items-and-image-lists_1.cpp)]

그러나 목록 뷰나 목록 컨트롤에 아이콘을 표시 하지 않으려는 경우에는 이미지 목록이 필요 하지 않습니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
