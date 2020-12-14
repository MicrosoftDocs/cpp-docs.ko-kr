---
description: '자세한 정보: 도구 설명 알림 처리'
title: 도구 설명 알림 처리
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 02bb1fb0760cf91c76e3c3be75fe097d5d57b71e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254861"
---
# <a name="handling-tool-tip-notifications"></a>도구 설명 알림 처리

**TBSTYLE_TOOLTIPS** 스타일을 지정 하면 도구 모음에서 도구 설명 컨트롤을 만들고 관리 합니다. 도구 설명은 도구 모음 단추를 설명 하는 텍스트 줄을 포함 하는 작은 팝업 창입니다. 도구 설명이 숨겨져 있습니다. 사용자가 도구 모음 단추에 커서를 놓고 약 0.5 초 동안 유지 되는 경우에만 나타납니다. 도구 설명이 커서 옆에 표시 됩니다.

도구 설명이 표시 되기 전에 **TTN_NEEDTEXT** 알림 메시지를 도구 모음의 소유자 창으로 보내 단추에 대 한 설명 텍스트를 검색 합니다. 도구 모음의 소유자 창이 창인 경우에는 `CFrameWnd` `CFrameWnd` **TTN_NEEDTEXT** 알림에 대 한 기본 처리기가 있기 때문에 도구 설명이 추가 작업 없이 표시 됩니다. 대화 상자나 폼 보기와 같은 도구 모음의 소유자 창이에서 파생 되지 않은 경우 `CFrameWnd` 소유자 창의 메시지 맵에 항목을 추가 하 고 메시지 맵에 알림 처리기를 제공 해야 합니다. 소유자 창의 메시지 맵에 대 한 항목은 다음과 같습니다.

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>설명

*memberFxn*<br/>
이 단추에 텍스트가 필요할 때 호출 되는 멤버 함수입니다.

도구 설명의 id는 항상 0입니다.

**TTN_NEEDTEXT** 알림 외에도 도구 설명 컨트롤은 도구 모음 컨트롤에 다음 알림을 보낼 수 있습니다.

|알림|의미|
|------------------|-------------|
|**TTN_NEEDTEXTA**|도구 설명 컨트롤에 ASCII 텍스트가 필요 합니다 (Windows 95에만 해당).|
|**TTN_NEEDTEXTW**|도구 설명 컨트롤에 유니코드 텍스트가 필요 합니다 (Windows NT에만 해당).|
|**TBN_HOTITEMCHANGE**|강조 표시 된 핫 항목을 변경 했음을 나타냅니다.|
|**NM_RCLICK**|사용자가 단추를 마우스 오른쪽 단추로 클릭 했음을 나타냅니다.|
|**TBN_DRAGOUT**|사용자가 단추를 클릭 하 고 포인터를 단추 밖으로 끌어 오고 있음을 나타냅니다. 응용 프로그램을 사용 하 여 도구 모음 단추에서 끌어서 놓기를 구현할 수 있습니다. 이 알림을 받으면 응용 프로그램에서 끌어서 놓기 작업을 시작 합니다.|
|**TBN_DROPDOWN**|사용자가 **TBSTYLE_DROPDOWN** 스타일을 사용 하는 단추를 클릭 했음을 나타냅니다.|
|**TBN_GETOBJECT**|사용자가 **TBSTYLE_DROPPABLE** 스타일을 사용 하는 단추 위로 포인터를 이동 했음을 나타냅니다.|

예제 처리기 함수 및 도구 설명을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [도구 설명](tool-tips-in-windows-not-derived-from-cframewnd.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](using-ctoolbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
