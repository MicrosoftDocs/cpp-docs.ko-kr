---
description: '자세한 정보: DHTML 컨트롤 프로젝트의 요소 식별'
title: DHTML 컨트롤 프로젝트의 요소 식별
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 7f04857378564a86fc875e9874b79f6ae6c6a625
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148020"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>DHTML 컨트롤 프로젝트의 요소 식별

대부분의 DHTML 컨트롤 코드는 모든 ATL 컨트롤에 대해 만들어진 것과 정확히 동일 합니다. 일반 코드를 기본적으로 이해 하려면 [atl 자습서](../atl/active-template-library-atl-tutorial.md)를 수행 하 고 Atl [프로젝트 만들기](../atl/reference/creating-an-atl-project.md) 및 [Atl COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)섹션을 참조 하세요.

DHTML 컨트롤은 다음과 같은 경우를 제외 하 고 ATL 컨트롤과 비슷합니다.

- 컨트롤에서 구현 하는 일반 인터페이스 외에도 c + + 코드와 HTML UI (사용자 인터페이스) 간에 통신 하는 데 사용 되는 추가 인터페이스를 구현 합니다. HTML UI는이 인터페이스를 사용 하 여 c + + 코드를 호출 합니다.

- 컨트롤 UI에 대 한 HTML 리소스를 만듭니다.

- `m_spBrowser` [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))형식의 스마트 포인터인 멤버 변수를 통해 DHTML 개체 모델에 액세스할 수 있습니다. 이 포인터를 사용 하 여 DHTML 개체 모델의 모든 부분에 액세스할 수 있습니다.

다음 그림은 DLL, DHTML 컨트롤, 웹 브라우저 및 HTML 리소스 간의 관계를 보여 줍니다.

![DHTML 컨트롤 프로젝트의 요소](../atl/media/vc52en1.gif "DHTML 컨트롤 프로젝트의 요소")

> [!NOTE]
> 이 그래픽의 이름은 자리 표시자입니다. HTML 리소스의 이름과 컨트롤에 노출 되는 인터페이스는 ATL 컨트롤 마법사에서 할당 하는 이름을 기반으로 합니다.

이 그래픽에서 요소는 다음과 같습니다.

- **내 DLL** ATL 프로젝트 마법사를 사용 하 여 만든 DLL입니다.

-  `m_spBrowser` ATL 개체 마법사를 사용 하 여 만든 dhtml 컨트롤 () 이 컨트롤은 웹 브라우저 개체의 인터페이스,를 통해 웹 브라우저 개체 및 해당 메서드에 액세스 `IWebBrowser2` 합니다. 컨트롤 자체는 컨트롤에 필요한 다른 표준 인터페이스 외에도 다음과 같은 두 가지 인터페이스를 노출 합니다.

  - `IDHCTL1` 컨테이너 에서만 사용 하기 위해 컨트롤에서 노출 하는 인터페이스입니다.

  - `IDHCTLUI1` C + + 코드와 HTML 사용자 인터페이스 간의 통신을 위한 디스패치 인터페이스입니다. 웹 브라우저는 컨트롤의 디스패치 인터페이스를 사용 하 여 컨트롤을 표시 합니다. 을 호출 하 여이 디스패치 인터페이스의 메서드 이름 다음에 호출 하 여 컨트롤의 사용자 인터페이스에서이 디스패치 인터페이스의 여러 메서드를 호출할 수 있습니다 `window.external` . `window.external`HTML 내에서이 컨트롤에 대 한 UI를 구성 하는 스크립트 태그를 사용 하 여에 액세스할 수 있습니다. 리소스 파일에서 외부 메서드를 호출 하는 방법에 대 한 자세한 내용은 [DHTML에서 c + + 코드 호출](../atl/calling-cpp-code-from-dhtml.md)을 참조 하세요.

- **IDR_CTL1** HTML 리소스의 리소스 ID입니다. 파일 이름 (이 경우)은 DHCTL1UI.htm입니다. DHTML 컨트롤은 텍스트 편집기를 사용 하 여 편집할 수 있는 표준 HTML 태그 및 외부 창 디스패치 명령을 포함 하는 HTML 리소스를 사용 합니다.

- **웹 브라우저** HTML 리소스의 HTML을 기반으로 하는 컨트롤의 UI가 웹 브라우저에 표시 됩니다. 웹 브라우저의 인터페이스에 대 한 포인터는 dhtml `IWebBrowser2` 컨트롤에서 dhtml 개체 모델에 대 한 액세스를 허용 하는 데 사용할 수 있습니다.

ATL 컨트롤 마법사는 HTML 리소스와 .cpp 파일 모두에 기본 코드를 포함 하는 컨트롤을 생성 합니다. 마법사에서 생성 된 대로 컨트롤을 컴파일하고 실행 한 다음 웹 브라우저나 ActiveX 컨트롤 테스트 컨테이너에서 컨트롤을 볼 수 있습니다. 아래 그림은 테스트 컨테이너에 표시 되는 세 개의 단추가 있는 기본 ATL DHTML 컨트롤을 보여 줍니다.

![ATL DHTML 컨트롤](../atl/media/vc52en2.gif "ATL DHTML 컨트롤")

DHTML 컨트롤 빌드를 시작 하려면 [ATL Dhtml 컨트롤 만들기](../atl/creating-an-atl-dhtml-control.md) 를 참조 하세요. 테스트 컨테이너에 액세스 하는 방법에 대 한 자세한 내용은 [테스트 컨테이너로 속성 및 이벤트](../mfc/testing-properties-and-events-with-test-container.md) 테스트를 참조 하세요.

## <a name="see-also"></a>참고 항목

[DHTML 컨트롤에 대한 지원](../atl/atl-support-for-dhtml-controls.md)
