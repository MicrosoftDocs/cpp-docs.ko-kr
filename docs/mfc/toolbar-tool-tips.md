---
description: '자세한 정보: 도구 모음 도구 설명'
title: 도구 모음 도구 설명
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
ms.openlocfilehash: bbf60246e778b60c2a6eacbcb55441806c00fad2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264286"
---
# <a name="toolbar-tool-tips"></a>도구 모음 도구 설명

도구 설명은 단추 위에 마우스를 놓으면 도구 모음 단추의 용도에 대 한 간단한 설명을 제공 하는 작은 팝업 창입니다. 도구 모음이 있는 응용 프로그램 마법사를 사용 하 여 응용 프로그램을 만드는 경우 도구 설명 지원이 제공 됩니다. 이 문서에서는 응용 프로그램 마법사에서 만든 도구 설명 지원과 응용 프로그램에 도구 설명 지원을 추가 하는 방법에 대해 설명 합니다.

이 문서에서는 다음 내용을 설명합니다.

- [도구 설명 활성화](#_core_activating_tool_tips)

- [Flyby 상태 표시줄 업데이트](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a> 도구 설명 활성화

응용 프로그램에서 도구 설명을 활성화 하려면 다음 두 가지 작업을 수행 해야 합니다.

- CBRS_TOOLTIPS 스타일을 *dwstyle* 매개 변수로 전달 되는 다른 스타일 (예: WS_CHILD, WS_VISIBLE 및 기타 **CBRS_** 스타일)에 [CToolBar:: Create](../mfc/reference/ctoolbar-class.md#create) 함수 또는 [set 스타일](../mfc/reference/ccontrolbar-class.md#setbarstyle)에 추가 합니다.

- 아래 절차에 설명 된 대로 도구 모음 명령에 대 한 명령줄 프롬프트를 포함 하는 문자열 리소스에 줄 바꿈 문자 (' \n ')로 구분 된 도구 모음 팁 텍스트를 추가 합니다. 문자열 리소스는 도구 모음 단추의 ID를 공유 합니다.

#### <a name="to-add-the-tool-tip-text"></a>도구 설명 텍스트를 추가 하려면

1. 도구 모음 편집기에서 도구 모음을 편집 하는 동안 지정 된 단추에 대 한 **도구 모음 단추 속성** 창을 엽니다.

1. **프롬프트** 상자에서 해당 단추에 대 한 도구 설명에 표시할 텍스트를 지정 합니다.

> [!NOTE]
> 도구 모음 편집기에서 텍스트를 단추 속성으로 설정 하 여 이전 프로시저를 대체 합니다 .이 프로시저는 문자열 리소스를 열고 편집 해야 했습니다.

도구 설명이 활성화 된 컨트롤 막대에 자식 컨트롤이 있으면 컨트롤 막대에 다음 조건을 충족 하는 한 컨트롤 막대의 모든 자식 컨트롤에 대 한 도구 설명이 표시 됩니다.

- 컨트롤의 ID가-1이 아닌 경우

- 리소스 파일의 자식 컨트롤과 ID가 같은 문자열-테이블 항목에 도구 설명 문자열이 있습니다.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a> Flyby 상태 표시줄 업데이트

도구 설명에 관련 된 기능은 "flyby" 상태 표시줄 업데이트입니다. 기본적으로 상태 표시줄의 메시지는 단추가 활성화 될 때 특정 도구 모음 단추만 설명 합니다. 에 전달 된 스타일 목록에 CBRS_FLYBY를 포함 하 여 `CToolBar::Create` 단추를 실제로 활성화 하지 않고 도구 모음 위로 마우스 커서를 가져갈 때 이러한 메시지를 업데이트할 수 있습니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [MFC 도구 모음 구현 (도구 모음에 대 한 개요 정보)](../mfc/mfc-toolbar-implementation.md)

- [도구 모음 고정 및 고정 해제](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) 및 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 클래스

- [도구 모음 컨트롤 사용](../mfc/working-with-the-toolbar-control.md)

- [이전 도구 모음 사용](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>참고 항목

[MFC 도구 모음 구현](../mfc/mfc-toolbar-implementation.md)
