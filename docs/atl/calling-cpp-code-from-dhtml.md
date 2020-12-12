---
description: '자세한 정보: DHTML에서 c + + 코드 호출'
title: DHTML에서 c + + 코드 호출
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: d880b0e9cb2f0b9d5228df7da4fc96fceeb87943
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148488"
---
# <a name="calling-c-code-from-dhtml"></a>DHTML에서 c + + 코드 호출

DHTML 컨트롤은 테스트 컨테이너 또는 Internet Explorer와 같은 컨테이너에서 호스팅될 수 있습니다. 테스트 컨테이너에 액세스 하는 방법에 대 한 자세한 내용은 [테스트 컨테이너로 속성 및 이벤트](../mfc/testing-properties-and-events-with-test-container.md) 테스트를 참조 하세요.

컨트롤을 호스팅하는 컨테이너는 일반 컨트롤 인터페이스를 사용 하 여 컨트롤과 통신 합니다. DHTML은 "UI"로 끝나는 디스패치 인터페이스를 사용 하 여 c + + 코드 및 HTML 리소스와 통신 합니다. [ATL DHTML 컨트롤을 수정할](../atl/modifying-the-atl-dhtml-control.md)때 이러한 여러 인터페이스에 의해 호출 되는 메서드를 추가 하는 것을 연습할 수 있습니다.

DHTML에서 c + + 코드를 호출 하는 예제를 보려면 ATL 컨트롤 마법사를 사용 하 여 [dhtml 컨트롤을 만들고](../atl/creating-an-atl-dhtml-control.md) 헤더 파일 및 HTML 파일의 코드를 검사 합니다.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>헤더 파일에서 WebBrowser 메서드 선언

DHTML UI에서 c + + 메서드를 호출 하려면 컨트롤의 UI 인터페이스에 메서드를 추가 해야 합니다. 예를 들어 ATL 컨트롤 마법사에서 만든 헤더 파일에는 마법사에서 생성 된 `OnClick` 컨트롤의 UI 인터페이스 멤버인 c + + 메서드가 포함 되어 있습니다.

`OnClick`컨트롤의 .h 파일에서를 검사 합니다.

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

첫 번째 매개 변수인 *pdispBody* 는 body 개체의 디스패치 인터페이스에 대 한 포인터입니다. 두 번째 매개 변수인 *Varcolor* 는 컨트롤에 적용할 색을 식별 합니다.

## <a name="calling-c-code-in-the-html-file"></a>HTML 파일에서 c + + 코드 호출

헤더 파일에서 WebBrowser 메서드를 선언 하 고 나면 HTML 파일에서 메서드를 호출할 수 있습니다. HTML 파일에서 ATL 컨트롤 마법사는 세 가지 Windows 디스패치 메서드를 삽입 합니다 .이 메서드는 메시지를 디스패치 하 여 `OnClick` 컨트롤의 배경색을 변경 합니다.

HTML 파일의 메서드 중 하나를 검사 합니다.

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

위의 HTML 코드에서 창 외부 메서드 `OnClick` 가 단추 태그의 일부로 호출 됩니다. 메서드에는 두 개의 매개 변수인가 있습니다 .이 매개 변수는 `theBody` HTML 문서의 본문을 참조 하 고, `"red"` 단추를 클릭 하면 컨트롤의 배경색이 빨강으로 변경 됨을 나타냅니다. `Red`다음 태그는 단추의 레이블입니다.

사용자 고유의 메서드를 제공 하는 방법에 대 한 자세한 내용은 [ATL DHTML 컨트롤 수정](../atl/modifying-the-atl-dhtml-control.md) 을 참조 하세요. HTML 파일에 대 한 자세한 내용은 [DHTML 컨트롤 프로젝트의 요소 식별](../atl/identifying-the-elements-of-the-dhtml-control-project.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[DHTML 컨트롤에 대한 지원](../atl/atl-support-for-dhtml-controls.md)
