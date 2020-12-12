---
description: '자세히 알아보기: 도구 설명 컨트롤에 대 한 설정'
title: 도구 설명 컨트롤에 대한 설정
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
ms.openlocfilehash: 789f33a7e8e960f52589588bcda49a12889fa0d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217031"
---
# <a name="settings-for-the-tool-tip-control"></a>도구 설명 컨트롤에 대한 설정

도구 설명 컨트롤([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md))을 활성 또는 비활성으로 설정할 수 있습니다. 활성으로 설정하는 경우 커서로 도구를 가리키면 도구 설명 컨트롤이 나타납니다. 비활성으로 설정하는 경우 커서로 도구를 가리켜도 도구 설명 컨트롤이 나타나지 않습니다. 도구 설명 컨트롤을 활성화 또는 비활성화하려면 [활성화](../mfc/reference/ctooltipctrl-class.md#activate) 를 호출합니다.

도구 설명 컨트롤의 소유자 창이 활성 또는 비활성 상태인지에 관계없이 TTS_ALWAYSTIP 스타일을 사용하여 커서로 도구를 가리킬 때 도구 설명을 표시하도록 활성 도구 설명을 설정할 수 있습니다. 이 스타일을 사용하지 않을 경우 도구의 소유자 창이 활성 상태이면 도구 설명 컨트롤이 나타나지만 비활성 상태이면 나타나지 않습니다.

대부분의 애플리케이션에는 메뉴 명령에 해당하는 도구를 포함하는 도구 모음이 있습니다. 이러한 도구의 경우 도구 설명 컨트롤이 해당 메뉴 항목과 동일한 텍스트를 표시하는 것이 편리합니다. 컨트롤에 TTS_NOPREFIX 스타일이 없을 경우 도구 설명 컨트롤에 전달된 모든 문자열에서 앰퍼샌드(&) 액셀러레이터 문자가 자동으로 제거됩니다.

## <a name="see-also"></a>참고 항목

[CToolTipCtrl 사용](../mfc/using-ctooltipctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
