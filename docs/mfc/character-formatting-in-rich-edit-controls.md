---
description: '자세히 알아보기: Rich Edit 컨트롤의 문자 서식 지정'
title: Rich Edit 컨트롤의 문자 서식 지정
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 47d44a7d586d52ba6a83314711af1350d1c2def6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339698"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Rich Edit 컨트롤의 문자 서식 지정

서식 있는 편집 컨트롤 ([CRichEditCtrl](reference/cricheditctrl-class.md))의 멤버 함수를 사용 하 여 문자 형식을 지정 하 고 형식 지정 정보를 검색할 수 있습니다. 문자에 대해 서체, 크기, 색 및 효과 (예: 굵게, 기울임꼴 및 보호)를 지정할 수 있습니다.

[SetSelectionCharFormat](reference/cricheditctrl-class.md#setselectioncharformat) 및 [SetWordCharFormat](reference/cricheditctrl-class.md#setwordcharformat) 멤버 함수를 사용 하 여 문자 형식을 적용할 수 있습니다. 선택한 텍스트의 현재 문자 서식을 확인 하려면 [GetSelectionCharFormat](reference/cricheditctrl-class.md#getselectioncharformat) 멤버 함수를 사용 합니다. [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) 구조체는 이러한 멤버 함수에서 문자 특성을 지정 하는 데 사용 됩니다. **CHARFORMAT** 의 중요 한 멤버 중 하나는 **dwmask** 입니다. `SetSelectionCharFormat`및에서 `SetWordCharFormat` **dwmask** 는이 함수 호출로 설정할 문자 특성을 지정 합니다. `GetSelectionCharFormat` 선택 영역에 있는 첫 번째 문자의 특성을 보고 합니다. **Dwmask** 는 선택 영역 전체에서 일치 하는 특성을 지정 합니다.

또한 이후 삽입 된 문자에 적용 되는 서식 인 "기본 문자 서식"을 가져오고 설정할 수 있습니다. 예를 들어 응용 프로그램에서 기본 문자 형식을 굵게 설정 하 고 사용자가 문자를 입력 하는 경우 해당 문자는 굵게 표시 됩니다. 기본 문자 형식을 가져오고 설정 하려면 [GetDefaultCharFormat](reference/cricheditctrl-class.md#getdefaultcharformat) 및 [SetDefaultCharFormat](reference/cricheditctrl-class.md#setdefaultcharformat) 멤버 함수를 사용 합니다.

"Protected" 문자 특성은 텍스트의 모양을 변경 하지 않습니다. 사용자가 보호 된 텍스트를 수정 하려고 하면 서식 있는 편집 컨트롤에서 부모 창에 **EN_PROTECTED** 알림 메시지를 보내 부모 창에서 변경을 허용 하거나 방지할 수 있습니다. 이 알림 메시지를 받으려면 [Seteventmask](reference/cricheditctrl-class.md#seteventmask) 멤버 함수를 사용 하 여이 알림 메시지를 사용 하도록 설정 해야 합니다. 이벤트 마스크에 대 한 자세한 내용은이 항목의 뒷부분에 나오는 [Rich Edit 컨트롤의 알림](notifications-from-a-rich-edit-control.md)을 참조 하세요.

전경색은 문자 특성 이지만, 배경색은 rich edit 컨트롤의 속성입니다. 배경색을 설정 하려면 [SetBackgroundColor](reference/cricheditctrl-class.md#setbackgroundcolor) 멤버 함수를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
