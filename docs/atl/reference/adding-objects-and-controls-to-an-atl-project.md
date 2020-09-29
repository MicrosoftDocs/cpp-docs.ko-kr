---
title: ATL 프로젝트에 개체 및 컨트롤 추가
ms.date: 05/09/2019
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: 6acd60d430f13906d11e9a9b3e7c5655ee94badb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499307"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>ATL 프로젝트에 개체 및 컨트롤 추가

> [!NOTE]
> ATL COM+ 1.0 구성 요소 마법사, ATL OLE DB 소비자 마법사 및 ATL Active Server Page 구성 요소 마법사는 Visual Studio 2019 이상에서 사용할 수 없습니다.

ATL 코드 마법사 중 하나를 사용하여 ATL 또는 MFC 기반 프로젝트에 개체나 컨트롤을 추가할 수 있습니다. 추가한 각 COM 개체 또는 컨트롤에 대해 마법사는 cpp 및 .h 파일과 스크립트 기반 레지스트리 지원을 위한.rgs 파일을 생성합니다. 다음 ATL 코드 마법사는 Visual Studio에서 사용할 수 있습니다.

- [ATL 단순 개체](../../atl/reference/atl-simple-object-wizard.md)
- [ATL 대화 상자](../../atl/reference/atl-dialog-wizard.md)
- [ATL 컨트롤](../../atl/reference/atl-control-wizard.md)
- [ATL 속성 페이지](../../atl/reference/atl-property-page-wizard.md)
- [ATL Active Server Page 구성 요소](../../atl/reference/atl-active-server-page-component-wizard.md)
- [ATL OLE DB 소비자](../../atl/reference/atl-ole-db-consumer-wizard.md)
- [MFC에 ATL 지원 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)
- [ATL COM+ 1.0 구성 요소 마법사](../../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [ATL OLE DB 공급자](../../atl/reference/atl-ole-db-provider-wizard.md)

> [!NOTE]
> ATL 개체를 프로젝트에 추가하기 전에 관련 도움말 항목에서 개체에 대한 세부 정보 및 요구 사항을 검토해야 합니다.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>ATL 컨트롤 마법사를 사용하여 개체 또는 컨트롤을 추가하려면

1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **추가**를 클릭합니다. **클래스 추가**를 클릭합니다.

   [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자가 나타납니다.

1. **범주** 창에서 **ATL** 폴더를 선택한 상태에서 **템플릿** 창에서 삽입할 개체를 선택합니다. **열기**를 클릭합니다. 선택한 개체에 대한 코드 마법사가 나타납니다.

   > [!NOTE]
   > MFC 프로젝트에 ATL 개체를 추가하려면 기존 프로젝트에 ATL 지원을 추가해야 합니다. [MFC 프로젝트에 ATL 지원 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)의 지침에 따라 이 작업을 수행할 수 있습니다.

   또는 이전에 ATL 지원을 추가하지 않고 MFC 프로젝트에 ATL 개체를 추가하려고 하면 Visual Studio에서 ATL 지원을 프로젝트에 추가할지 여부를 지정하라는 메시지가 표시됩니다. **예**를 클릭하여 프로젝트에 ATL 지원을 추가하고 선택한 ATL 마법사를 엽니다.

## <a name="see-also"></a>참고 항목

[ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[ATL 및 C 런타임 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
