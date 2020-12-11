---
description: '자세히 알아보기: Toolbar 컨트롤에서 이미지 목록 사용'
title: 도구 모음 컨트롤에서 이미지 목록 사용
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: dbdac26f1d17997e14ed4ba16875ef3794e46a71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154437"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>도구 모음 컨트롤에서 이미지 목록 사용

기본적으로 toolbar 컨트롤의 단추에 사용 되는 이미지는 단일 비트맵으로 저장 됩니다. 그러나 이미지 목록 집합에 단추 이미지를 저장할 수도 있습니다. Toolbar 컨트롤 개체는 최대 3 개의 개별 이미지 목록을 사용할 수 있습니다.

- 사용 하도록 설정 된 이미지 목록 현재 사용할 수 있는 도구 모음 단추에 대 한 이미지를 포함 합니다.

- 사용 하지 않도록 설정 된 이미지 목록 현재 사용할 수 없는 도구 모음 단추에 대 한 이미지를 포함 합니다.

- 강조 표시 된 이미지 목록 현재 강조 표시 된 도구 모음 단추에 대 한 이미지를 포함 합니다. 이 이미지 목록은 도구 모음에서 TBSTYLE_FLAT 스타일을 사용 하는 경우에만 사용 됩니다.

이러한 이미지 목록은 도구 모음 컨트롤을 개체에 연결할 때 사용 됩니다 `CToolBarCtrl` . 이 연결은 [CToolBarCtrl:: Se agelist](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)및 [sese agelist](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)를 호출 하 여 수행 됩니다.

기본적으로 MFC는 클래스를 사용 하 여 `CToolBar` mfc 응용 프로그램 도구 모음을 구현 합니다. 그러나 `GetToolBarCtrl` 멤버 함수를 사용 하 여 포함 된 개체를 검색할 수 있습니다 `CToolBarCtrl` . 그런 다음 반환 된 개체를 `CToolBarCtrl` 사용 하 여 멤버 함수를 호출할 수 있습니다.

다음 예제에서는 사용 () `m_ToolBarImages` 및 사용 안 함 () `m_ToolBarDisabledImages` 이미지 목록을 `CToolBarCtrl` 개체 ()에 할당 하 여이 기법을 보여 줍니다 `m_ToolBarCtrl` .

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Toolbar 개체에서 사용 하는 이미지 목록은 영구 개체 여야 합니다. 이러한 이유로, 일반적으로 MFC 클래스의 데이터 멤버입니다. 이 예제에서는 주 프레임 창 클래스입니다.

이미지 목록이 개체와 연결 되 면 `CToolBarCtrl` 프레임 워크에서 적절 한 단추 이미지를 자동으로 표시 합니다.

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](../mfc/using-ctoolbarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
