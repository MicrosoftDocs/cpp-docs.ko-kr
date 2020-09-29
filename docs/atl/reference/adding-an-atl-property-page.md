---
title: ATL 속성 페이지 추가
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 4cd7444d18d26124f8c3c642bba55fb7592f5c8b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499319"
---
# <a name="adding-an-atl-property-page"></a>ATL 속성 페이지 추가

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL 속성 페이지 마법사를 사용할 수 없습니다.

ATL(액티브 템플릿 라이브러리) 속성 페이지를 프로젝트에 추가하려면 프로젝트가 ATL 애플리케이션 또는 ATL 지원이 포함된 MFC 애플리케이션으로 만든 것이어야 합니다. Atl [프로젝트 마법사](../../atl/reference/atl-project-wizard.md) 를 사용 하 여 atl 응용 프로그램을 만들거나 mfc [응용](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) 프로그램에 atl 개체를 추가 하 여 mfc 응용 프로그램에 대 한 atl 지원을 구현할 수 있습니다.

컨트롤의 속성 페이지를 추가하는 경우 컨트롤에서 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 인터페이스를 지원해야 합니다. 기본적으로, 이 인터페이스는 [ATL 컨트롤 마법사](../../atl/reference/atl-control-wizard.md)를 사용하여 [ATL 컨트롤을 만들](../../atl/reference/adding-an-atl-control.md) 때 컨트롤 클래스의 파생 목록에 있습니다.

> [!NOTE]
> 컨트롤 클래스의 파생 목록에 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)이 없으면 수동으로 추가해야 합니다.

## <a name="to-add-an-atl-property-page-to-your-project"></a>프로젝트에 ATL 속성 페이지를 추가하려면 다음을 수행합니다.

1. **솔루션 탐색기** 또는 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 ATL 속성 페이지를 추가할 프로젝트의 이름을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **클래스 추가**를 클릭 합니다.

1. [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자의 **템플릿** 창에서 **ATL 속성 페이지**를 클릭한 다음, **열기**를 클릭하여 [ATL 속성 페이지 마법사](../../atl/reference/atl-property-page-wizard.md)를 표시합니다.

컨트롤의 속성 페이지를 만든 후에 컨트롤의 속성 맵에 [PROP_PAGE](property-map-macros.md#prop_page) 항목을 제공해야 합니다.

## <a name="see-also"></a>참고 항목

[속성 페이지](../../atl/atl-com-property-pages.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[예제: 속성 페이지 구현](../../atl/example-implementing-a-property-page.md)
