---
title: ATL Active Server Page 구성 요소 추가
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: 0180077de7ab96cb75736d34e112731e47b9589b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499360"
---
# <a name="adding-an-atl-active-server-page-component"></a>ATL Active Server Page 구성 요소 추가

::: moniker range="vs-2019"

Visual Studio 2019 이상에서는 ATL Active Server Pages 구성 요소 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=vs-2017"

ATL(액티브 템플릿 라이브러리) 개체를 프로젝트에 추가하려면 프로젝트가 COM ATL 애플리케이션 또는 ATL 지원이 포함된 MFC 애플리케이션으로 만든 것이어야 합니다. [ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)를 사용하여 ATL 애플리케이션을 만들 수 있으며 [클래스 대화 상자 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자에서 **MFC에 ATL 지원 추가**를 선택하거나 [MFC 애플리케이션에 ATL 개체를 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)하여 MFC 애플리케이션용 ATL 지원을 구현할 수 있습니다.

Active Server Pages 구성 요소는 다음과 같은 고급 웹 개발 기능을 제공하는 인터넷 정보 서비스 아키텍처의 일부입니다.

- HTML 페이지에 ASP 구성 요소를 포함하여 브라우저에 독립적인 동적 콘텐츠를 만들 수 있습니다.

- ASP 페이지를 사용하여 표준 기반 데이터베이스 연결을 제공할 수 있습니다.

- 웹 기반 애플리케이션에 ASP 오류 처리 기능을 사용할 수 있습니다.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>ATL Active Server Pages 구성 요소를 프로젝트에 추가하려면

1. **솔루션 탐색기**에서 ATL Active Server Pages 구성 요소를 추가할 프로젝트의 이름을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **추가**를 클릭한 다음, **클래스 추가**를 클릭합니다.

1. [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자의 **템플릿** 창에서 **Active Server Page 구성 요소**를 클릭한 다음, **열기**를 클릭하여 [ATL Active Server Page 구성 요소 마법사](../../atl/reference/atl-active-server-page-component-wizard.md)를 표시합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[ATL 프로젝트에 새 인터페이스 추가](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[개체에 연결 요소 추가](../../atl/adding-connection-points-to-an-object.md)<br/>
[메서드 추가](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC 클래스](../../mfc/reference/adding-an-mfc-class.md)<br/>
[일반 C++ 클래스 추가](../../ide/adding-a-generic-cpp-class.md)
