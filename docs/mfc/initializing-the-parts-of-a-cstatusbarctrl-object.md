---
description: '자세히 알아보기: CStatusBarCtrl 개체의 파트 초기화'
title: CStatusBarCtrl 개체의 일부 초기화
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: 52eb738f5fe54a54e54a6415a602a68123869b32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197532"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>CStatusBarCtrl 개체의 일부 초기화

기본적으로 상태 표시줄은 별도의 창을 사용 하 여 상태 정보를 표시 합니다. 이러한 창 (부품이 라고도 함)에는 텍스트 문자열, 아이콘 또는 둘 다 포함 될 수 있습니다.

[Setparts](reference/cstatusbarctrl-class.md#setparts) 를 사용 하 여 상태 표시줄의 수 및 길이를 정의 합니다. 상태 표시줄의 파트를 만든 후에는 [SetText](reference/cstatusbarctrl-class.md#settext) 및 [seticon](reference/cstatusbarctrl-class.md#seticon) 을 호출 하 여 상태 표시줄의 특정 부분에 대 한 텍스트 또는 아이콘을 설정 합니다. 파트가 성공적으로 설정 되 면 컨트롤이 자동으로 다시 그려집니다.

다음 예에서는 `CStatusBarCtrl` 네 개의 창으로 기존 개체 ()를 초기화 한 `m_StatusBarCtrl` 다음 두 번째 부분에서 아이콘 (IDI_ICON1) 및 일부 텍스트를 설정 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#31](codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

개체의 모드를 simple로 설정 하는 방법에 대 한 자세한 내용은 `CStatusBarCtrl` [CStatusBarCtrl 개체의 모드 설정](setting-the-mode-of-a-cstatusbarctrl-object.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CStatusBarCtrl 사용](using-cstatusbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
