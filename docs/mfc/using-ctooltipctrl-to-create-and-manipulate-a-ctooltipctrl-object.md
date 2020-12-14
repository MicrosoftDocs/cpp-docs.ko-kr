---
description: '자세히 알아보기: CToolTipCtrl를 사용 하 여 CToolTipCtrl 개체 만들기 및 조작'
title: CToolTipCtrl을 사용하여 CToolTipCtrl 개체 만들기 및 조작
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 363d46ce078b71cf88d742ae390ab674a73ab935
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202342"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>CToolTipCtrl을 사용하여 CToolTipCtrl 개체 만들기 및 조작

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) 사용의 예는 다음과 같습니다.

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>CToolTipCtrl을 만들고 조작하려면

1. `CToolTipCtrl` 개체를 생성합니다.

1. [Create](../mfc/reference/ctooltipctrl-class.md#create) 를 호출 하 여 Windows 도구 설명 공용 컨트롤을 만들고 개체에 연결 `CToolTipCtrl` 합니다.

1. 도구에 커서가 있을 때 도구 설명에 저장 된 정보가 표시 되도록 [Addtool](../mfc/reference/ctooltipctrl-class.md#addtool) 을 호출 하 여 도구를 도구 설명 컨트롤에 등록 합니다.

1. [Settoolinfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) 를 호출 하 여 도구에 대 한 도구 설명에서 유지 관리 되는 정보를 설정 합니다.

1. [Settoolrect](../mfc/reference/ctooltipctrl-class.md#settoolrect) 를 호출 하 여 도구에 대 한 새 경계 사각형을 설정 합니다.

1. [System.windows.media.visualtreehelper.hittest](../mfc/reference/ctooltipctrl-class.md#hittest) 를 호출 하 여 지정 된 도구의 경계 사각형 내에 있는지 여부를 확인 하 고, 해당 하는 경우 도구에 대 한 정보를 검색 합니다.

1. [Gettoolcount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) 를 호출 하 여 도구 설명 컨트롤에 등록 된 도구 수를 검색 합니다.

## <a name="see-also"></a>참고 항목

[CToolTipCtrl 사용](../mfc/using-ctooltipctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
