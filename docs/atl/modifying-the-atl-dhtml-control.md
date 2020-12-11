---
description: '자세한 정보: ATL DHTML 컨트롤 수정'
title: ATL DHTML 컨트롤 수정
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: 7ae9c102addd7a33341a8f16105a3581de10481e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159455"
---
# <a name="modifying-the-atl-dhtml-control"></a>ATL DHTML 컨트롤 수정

ATL 컨트롤 마법사는 컨트롤을 빌드 및 실행할 수 있도록 시작 코드를 제공 하므로 프로젝트 파일에 메서드를 작성 하는 방법 및 디스패치 메서드를 사용 하 여 DHTML이 컨트롤의 c + + 코드를 호출 하는 방법을 확인할 수 있습니다. 인터페이스에 디스패치 메서드를 추가할 수 있습니다. 그런 다음 HTML 리소스에서 메서드를 호출할 수 있습니다.

## <a name="to-modify-the-atl-dhtml-control"></a>ATL DHTML 컨트롤을 수정 하려면

1. **클래스 뷰** 에서 컨트롤 프로젝트를 확장 합니다.

   "UI"로 끝나는 인터페이스에는 메서드가 하나 `OnClick` 있습니다. "UI"로 끝나지 않는 인터페이스에는 메서드가 없습니다.

1. "UI"로 끝나지 않는 인터페이스에 호출 된 메서드를 추가 `MethodInvoked` 합니다.

   이 메서드는 DHTML에서 컨트롤과 상호 작용 하는 데 사용 되는 인터페이스가 아니라 컨테이너 상호 작용을 위해 컨트롤 컨테이너에서 사용 되는 인터페이스에 추가 됩니다. 컨테이너만이 메서드를 호출할 수 있습니다.

1. .Cpp 파일에서 스텁 메서드를 찾고 다음과 같이 메시지 상자를 표시 하는 코드를 추가 합니다.

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. 호출 된 다른 메서드를 추가 `HelloHTML` 합니다 .이 메서드는 "UI"로 끝나는 인터페이스에 추가 합니다. `HelloHTML`.Cpp 파일에서 스텁 메서드를 찾고 다음과 같이 메시지 상자를 표시 하는 코드를 추가 합니다.

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. "UI"로 끝나지 않는 세 번째 메서드인를 `GoToURL` 인터페이스에 추가 합니다. 다음과 같이 [IWebBrowser2:: Navigate](/previous-versions//aa752133\(v=vs.85\))를 호출 하 여이 메서드를 구현 합니다.

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   `IWebBrowser2`ATL은 .h 파일에서 해당 인터페이스에 대 한 포인터를 제공 하기 때문에 메서드를 사용할 수 있습니다.

다음으로, 만든 메서드를 호출 하도록 HTML 리소스를 수정 합니다. 이러한 메서드를 호출 하는 세 가지 단추를 추가 합니다.

## <a name="to-modify-the-html-resource"></a>HTML 리소스를 수정 하려면

1. **솔루션 탐색기** 에서 htm 파일을 두 번 클릭 하 여 HTML 리소스를 표시 합니다.

   HTML, 특히 외부 Windows 디스패치 방법에 대 한 호출을 검사 합니다. HTML은 프로젝트의 `OnClick` 메서드를 호출 하 고, 매개 변수는 컨트롤의 본문 ( `theBody` )과 할당할 색 ("")을 표시 합니다 `red` . 메서드 호출 다음의 텍스트는 단추에 표시 되는 레이블입니다.

1. 다른 `OnClick` 메서드를 추가 하 고 색만 변경 합니다. 예를 들어:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   이 메서드는 **새로 고침** 이라는 레이블이 지정 된 단추를 만들어 사용자가이 단추를 클릭 하 여 컨트롤을 원래의 흰색 배경으로 되돌릴 수 있습니다.

1. 만든 메서드에 호출을 추가 `HelloHTML` 합니다. 예를 들어:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   이 메서드는 사용자가 클릭 하 여 메시지 상자를 표시할 수 있는 **HelloHTML** 레이블이 지정 된 단추를 만듭니다 `HelloHTML` .

이제 [수정 된 DHTML 컨트롤을](../atl/testing-the-modified-atl-dhtml-control.md)빌드 및 테스트할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DHTML 컨트롤에 대한 지원](../atl/atl-support-for-dhtml-controls.md)
