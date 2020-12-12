---
description: '자세히 알아보기: Rich Edit 컨트롤의 클립보드 작업'
title: Rich Edit 컨트롤의 클립보드 작업
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: 9a9fda9aebe3a749359776c1bc0d41e75deaef76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251208"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Rich Edit 컨트롤의 클립보드 작업

응용 프로그램은 사용 가능한 가장 적합 한 클립보드 형식이 나 특정 클립보드 형식을 사용 하 여 클립보드의 내용을 rich edit 컨트롤 ([CRichEditCtrl](reference/cricheditctrl-class.md))에 붙여 넣을 수 있습니다. 또한 서식 있는 편집 컨트롤에서 클립보드 형식 붙여넣기가 지원되는지 여부도 확인할 수 있습니다.

[Copy](reference/cricheditctrl-class.md#copy) 또는 [cut](reference/cricheditctrl-class.md#cut) 멤버 함수를 사용 하 여 현재 선택 항목의 내용을 복사 하거나 잘라낼 수 있습니다. 마찬가지로 [paste](reference/cricheditctrl-class.md#paste) 멤버 함수를 사용 하 여 클립보드의 내용을 rich edit 컨트롤에 붙여 넣을 수 있습니다. 컨트롤은 처음으로 인식되는 첫 번째 사용 가능한 형식을 가장 설명적인 형식으로 인지하고 이를 붙여넣습니다.

특정 클립보드 형식을 붙여넣으려면 [PasteSpecial](reference/cricheditctrl-class.md#pastespecial) 멤버 함수를 사용할 수 있습니다. 이 함수는 사용자가 클립보드 형식을 선택할 수 있게 해주는 선택하여 붙여넣기 명령이 있는 애플리케이션에서 유용합니다. [Canpaste](reference/cricheditctrl-class.md#canpaste) 멤버 함수를 사용 하 여 지정 된 형식이 컨트롤에서 인식 되는지 여부를 확인할 수 있습니다.

또한 `CanPaste`를 사용하면 사용 가능한 클립보드 형식이 서식 있는 편집 컨트롤에서 인식되는지 여부를 확인할 수 있습니다. 이 기능은 `OnInitMenuPopup` 처리기에서 유용합니다. 애플리케이션은 컨트롤이 모든 사용 가능한 형식을 붙여넣을 수 있는지 여부에 따라 해당 붙여넣기 명령을 활성화하거나 회색으로 표시할 수 있습니다.

서식 있는 편집 컨트롤은 복합 텍스트 형식과 RichEdit 텍스트 및 개체라고 부르는 형식의 두 가지 클립보드 형식을 등록합니다. 응용 프로그램은 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수를 사용 하 여 **CF_RTF** 및 **CF_RETEXTOBJ** 값을 지정 하 여 이러한 형식을 등록할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
