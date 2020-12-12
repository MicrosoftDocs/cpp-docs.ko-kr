---
description: '자세히 알아보기: Rich Edit 컨트롤의 개요'
title: Rich Edit 컨트롤의 개요
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9971eb7340ddf270c6094d239737c89cff66e6e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205969"
---
# <a name="overview-of-the-rich-edit-control"></a>Rich Edit 컨트롤의 개요

> [!IMPORTANT]
> 응용 프로그램이 SDI, MDI 또는 대화 상자 기반 인지에 관계 없이 대화 상자에서 rich edit 컨트롤을 사용 하는 경우 대화 상자가 표시 되기 전에 [AfxInitRichEdit](reference/application-information-and-management.md#afxinitrichedit) 를 한 번 호출 해야 합니다. 이 함수를 호출 하는 일반적인 장소는 프로그램의 `InitInstance` 멤버 함수에 있습니다. 이 대화 상자는 처음에만 표시할 때마다 호출할 필요가 없습니다. 를 사용 하는 경우를 호출할 필요가 없습니다 `AfxInitRichEdit` `CRichEditView` .

[CRichEditCtrl](reference/cricheditctrl-class.md)(Rich edit controls)는 텍스트 서식 지정을 위한 프로그래밍 인터페이스를 제공 합니다. 그러나 응용 프로그램은 사용자가 서식 지정 작업을 사용 하도록 설정 하는 데 필요한 모든 사용자 인터페이스 구성 요소를 구현 해야 합니다. 즉, rich edit 컨트롤은 선택한 텍스트의 문자 또는 단락 특성 변경을 지원 합니다. 문자 특성의 몇 가지 예로 굵게, 기울임꼴, 글꼴 패밀리 및 포인트 크기가 있습니다. 단락 특성의 예로는 맞춤, 여백 및 탭 정지가 있습니다. 그러나 도구 모음 단추, 메뉴 항목 또는 서식 문자 대화 상자를 사용 하 여 사용자 인터페이스를 제공 하는 것은 사용자에 게 있습니다. 또한 현재 선택 항목의 특성에 대 한 rich edit 컨트롤을 쿼리 하는 함수도 있습니다. 이러한 함수를 사용 하 여 특성에 대 한 현재 설정을 표시 합니다. 예를 들어 선택 항목에 굵은 문자 서식 특성이 있는 경우 명령 UI에 확인 표시를 설정 합니다.

문자 및 단락 서식 지정에 대 한 자세한 내용은이 항목의 뒷부분에 나오는 [문자 서식 지정](character-formatting-in-rich-edit-controls.md) 및 [단락 서식 지정](paragraph-formatting-in-rich-edit-controls.md) 을 참조 하세요.

Rich edit 컨트롤은 여러 줄 편집 컨트롤에서 사용 하는 거의 모든 작업 및 알림 메시지를 지원 합니다. 따라서 편집 컨트롤을 이미 사용 하는 응용 프로그램은 rich edit 컨트롤을 사용 하도록 쉽게 변경할 수 있습니다. 추가 메시지 및 알림을 통해 응용 프로그램은 rich edit 컨트롤에 고유한 기능에 액세스할 수 있습니다. 편집 컨트롤에 대 한 자세한 내용은 [CEdit](reference/cedit-class.md)를 참조 하세요.

알림에 대 한 자세한 내용은이 항목의 뒷부분에 나오는 [Rich Edit 컨트롤의 알림](notifications-from-a-rich-edit-control.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
