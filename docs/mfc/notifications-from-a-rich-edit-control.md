---
description: '자세히 알아보기: Rich Edit 컨트롤의 알림'
title: Rich Edit 컨트롤에서 보내는 알림
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: 83f76c2b0bf8c27d30d8c113fc1607f3cbd718fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254796"
---
# <a name="notifications-from-a-rich-edit-control"></a>Rich Edit 컨트롤에서 보내는 알림

알림 메시지는 rich edit 컨트롤에 영향을 주는 이벤트를 보고 합니다 ([CRichEditCtrl](reference/cricheditctrl-class.md)). 부모 창이 나 메시지 리플렉션을 사용 하 여 rich edit 컨트롤 자체에서 처리할 수 있습니다. Rich edit 컨트롤은 편집 컨트롤과 함께 사용 되는 모든 알림 메시지 뿐만 아니라 몇 가지 추가 기능을 지원 합니다. "이벤트 마스크"를 설정 하 여 rich edit 컨트롤에서 부모 창을 보내는 알림 메시지를 결정할 수 있습니다.

Rich edit 컨트롤에 대 한 이벤트 마스크를 설정 하려면 [Seteventmask](reference/cricheditctrl-class.md#seteventmask) 멤버 함수를 사용 합니다. [Geteventmask](reference/cricheditctrl-class.md#geteventmask) 멤버 함수를 사용 하 여 rich edit 컨트롤에 대 한 현재 이벤트 마스크를 검색할 수 있습니다.

다음 단락에는 몇 가지 특정 알림과 해당 사용이 나열 되어 있습니다.

- EN_MSGFILTER 알림을 처리 EN_MSGFILTER rich edit 컨트롤이 나 부모 창인 클래스가 컨트롤에 대 한 모든 키보드 및 마우스 입력을 필터링 할 수 있습니다. 처리기는 키보드 또는 마우스 메시지가 처리 되지 않도록 하거나 지정 된 [Msgfilter](/windows/win32/api/richedit/ns-richedit-msgfilter) 구조를 수정 하 여 메시지를 변경할 수 있습니다.

- EN_PROTECTED EN_PROTECTED 알림 메시지를 처리 하 여 사용자가 보호 된 텍스트를 수정 하려고 할 때 검색 합니다. 보호 되는 텍스트 범위를 표시 하려면 보호 된 문자 효과를 설정할 수 있습니다. 자세한 내용은 [Rich Edit 컨트롤의 문자 서식 지정](character-formatting-in-rich-edit-controls.md)을 참조 하세요.

- EN_DROPFILES EN_DROPFILES 알림 메시지를 처리 하 여 사용자가 rich edit 컨트롤에서 파일을 삭제 하도록 할 수 있습니다. 지정 된 [ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles) 구조체에는 삭제 되는 파일에 대 한 정보가 포함 됩니다.

- EN_SELCHANGE 응용 프로그램은 EN_SELCHANGE 알림 메시지를 처리 하 여 현재 선택이 변경 되는 시기를 감지할 수 있습니다. 알림 메시지는 새 선택 항목에 대 한 정보를 포함 하는 [Selchange](/windows/win32/api/richedit/ns-richedit-selchange) 구조를 지정 합니다.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
